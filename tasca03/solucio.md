# 🧰 T03: Seguretat Lògica — Recuperant accés a sistemes

## 📌 Introducció
El client va sol·licitar la **recuperació d'accés** a un portàtil **Zorin OS** on el directiu havia oblidat la contrasenya.  
Addicionalment, es va demanar la implementació de **mesures de seguretat per evitar futurs accessos no autoritzats** mitjançant la modificació del **GRUB**.

---

## 🧭 Fase 1: Recuperació d'Accés

### 🛠️ Preparació de l'Entorn de Treball
Primer, he creat una **màquina virtual a VirtualBox** amb les següents especificacions:

- Nom de la màquina i carpeta d’emmagatzematge (dins de “Documents”).  
- ISO de **Zorin OS**.

  ![Imatge de la configuració inical de la maquina](/tasca03/img/configuracioinicialmaquina.png)

- **Memòria RAM:** 8 GB.

  ![Imatge de la configuració inical de la maquina](/tasca03/img/configram.png)
  
- **Disc:** Connectat el disc virtual clonat del client.
  
  ![Imatge de la configuració inical de la maquina](/tasca03/img/configdisc.png)

---

### 🌀 Accés al GRUB i Modificació d'Arrencada
1. He iniciat la màquina virtual i he premut la tecla **Shift** + una lletra aleatòria del teclat.  
2. He accedit al **menú GRUB**.

![Imatge de la configuració inical de la maquina](/tasca03/img/advancedopt.png)
   
3. He entrat a **“Advanced options for Zorin”** i, un cop a dins, he seleccionat **Recovery Mode**.

![Imatge de la configuració inical de la maquina](/tasca03/img/recoverymode.png)

---

### 👤 Identificació d'Usuari i Canvi de Contrasenya
1. Un cop dins del **Recovery Mode**, he seleccionat l’opció **root** per obtenir accés d’administrador.

![Imatge de la configuració inical de la maquina](/tasca03/img/menuperentrarroot.png)
    
2. Ara ja puc executar comandes com a **root**.

![Imatge de la configuració inical de la maquina](/tasca03/img/terminalroot.png)

#### Procés del canvi de contrasenya
He executat la següent comanda per canviar la contrasenya de l’usuari:

passwd **NOM_USUARI**

En el meu cas:

**passwd Miquel**

![Imatge de la configuració inical de la maquina](/tasca03/img/canvipasswd.png)

El sistema em demana introduir la nova contrasenya dues vegades per confirmar.

### ✅ Verificació d'Accés
1. He reiniciat la màquina virtual.
2. He accedit amb la nova contrasenya.

![Imatge de la configuració inical de la maquina](/tasca03/img/comprobaciocontra.png)
   
3. He pogut entrar a l’escriptori sense problemes.

![Imatge de la configuració inical de la maquina](/tasca03/img/escriptori.png)

---

## 🔐 Configuració per Fortificar l’Accés al GRUB
Després de comprovar que es podia recuperar l’accés fàcilment, he procedit a **protegir el GRUB amb contrasenya.**

### 🧰 Generar el hash de la contrasenya
He accedit al **terminal** de la màquina Zorin i he executat:

![Imatge de la configuració inical de la maquina](/tasca03/img/terminal.png)

**grub-mkpasswd-pbkdf2**

![Imatge de la configuració inical de la maquina](/tasca03/img/capturahash.png)

Aquesta comanda crea un hash PBKDF2 de la contrasenya que servirà per protegir el GRUB.

💡 Com que Zorin té entorn gràfic, es pot copiar i enganxar el hash directament.
Si no hi hagués entorn gràfic (per exemple, a Ubuntu Server), es pot redirigir la sortida a un fitxer:

grub-mkpasswd-pbkdf2 | tee salida.txt

![Imatge de la configuració inical de la maquina](/tasca03/img/capturahashasalida.png)

### ✍️ Edició de la configuració del GRUB
El següent pas és editar l’arxiu /etc/grub.d/40_custom per afegir la configuració d’autenticació:

![Imatge de la configuració inical de la maquina](/tasca03/img/arxiuconfig.png)

1. Obro el fitxer salida.txt per copiar el hash generat.

![Imatge de la configuració inical de la maquina](/tasca03/img/entremarxiusalida.png)

- Utilitzo Ctrl + R per buscar el fitxer dins de nano.

- Un cop dins, per copiar la línia sencera:

  - Alt + A per seleccionar des del principi.

  - Alt + 6 per copiar.

2. Edició de l’arxiu /etc/grub.d/40_custom amb nano:

sudo nano /etc/grub.d/40_custom

3. Afegeixo les següents línies:

set superusers="nomusuari"
password_pbkdf2 nomusuari HASH_GENERAT

Substitueix nomusuari pel nom que vulguis utilitzar per protegir el GRUB i HASH_GENERAT pel hash copiat anteriorment.

### ♻️ Aplicar els canvis

Per aplicar els canvis i activar la protecció:

sudo update-grub
sudo reboot

### 🧪 Resultat Final

En reiniciar la màquina, el sistema ara **demana verificació per fer qualsevol acció al GRUB.**
Això evita que algú sense coneixements pugui reiniciar la contrasenya de l’usuari i accedir a les dades.

---

[Explicació de la tasca](README.md)

---

[Tornar a la pàgina principal](../)



