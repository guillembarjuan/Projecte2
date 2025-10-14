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

  ![Imatge de la configuració RAM de la maquina](/tasca03/img/configram.png)
  
- **Disc:** Connectat el disc virtual clonat del client.
  
  ![Imatge de la configuració del disc](/tasca03/img/configdisc.png)

---

### 🌀 Accés al GRUB i Modificació d'Arrencada
1. He iniciat la màquina virtual i he premut la tecla **Shift** + una lletra aleatòria del teclat.  
2. He accedit al **menú GRUB**.

![Imatge del GRUB triant la opció advanced](/tasca03/img/advancedopt.png)
   
3. He entrat a **“Advanced options for Zorin”** i, un cop a dins, he seleccionat **Recovery Mode**.

![Imatge del GRUB triant la opció de recovery mode](/tasca03/img/recoverymode.png)

---

### 👤 Identificació d'Usuari i Canvi de Contrasenya
1. Un cop dins del **Recovery Mode**, he seleccionat l’opció **root** per obtenir accés d’administrador.

![Imatge del menú del recovery mode triant la opció de root](/tasca03/img/menuperentrarroot.png)
    
2. Ara ja puc executar comandes com a **root**.

![Imatge del terminal del root](/tasca03/img/terminalroot.png)

#### Procés del canvi de contrasenya
He executat la següent comanda per canviar la contrasenya de l’usuari:

passwd **NOM_USUARI**

En el meu cas:

**passwd Miquel**

![Imatge del canvi de contrassenya en el terminal](/tasca03/img/canvipasswd.png)

El sistema em demana introduir la nova contrasenya dues vegades per confirmar.

### ✅ Verificació d'Accés
1. He reiniciat la màquina virtual.
2. He accedit amb la nova contrasenya.

![Imatge de la comprovació de la nova contrassenya](/tasca03/img/comprobaciocontra.png)
   
3. He pogut entrar a l’escriptori sense problemes.

![Imatge del escriptori de Zorin](/tasca03/img/escriptori.png)

---

## 🔐 Configuració per Fortificar l’Accés al GRUB
Després de comprovar que es podia recuperar l’accés fàcilment, he procedit a **protegir el GRUB amb contrasenya.**

### 🧰 Generar el hash de la contrasenya
He accedit al **terminal** de la màquina Zorin i he executat:

![Imatge del terminal de Zorin obert](/tasca03/img/terminal.png)

**grub-mkpasswd-pbkdf2**

![Imatge del terminal de Zorin amb la comanda grub-mkpasswd-pbkdf2 escrita i el resultat de la comanda](/tasca03/img/capturahash.png)

Aquesta comanda crea un hash PBKDF2 de la contrasenya que servirà per protegir el GRUB.

💡 Com que Zorin té entorn gràfic, es pot copiar i enganxar el hash directament.
Si no hi hagués entorn gràfic (per exemple, a Ubuntu Server), es pot redirigir la sortida a un fitxer:

grub-mkpasswd-pbkdf2 | tee salida.txt

![Imatge del terminal amb la comanda grub-mkpasswd-pbkdf2 | tee salida.txt escrita](/tasca03/img/capturahashasalida.png)

### ✍️ Edició de la configuració del GRUB
El següent pas és editar l’arxiu /etc/grub.d/40_custom per afegir la configuració d’autenticació:

![Imatge del terminal amb la comanda sudo nano /etc/grub.d/40_custom](/tasca03/img/comandaperentrararxiuconfig.png)

![Imatge dins del arxiu /etc/grub.d/40_custom](/tasca03/img/arxiuconfig.png)

1. Obro el fitxer salida.txt per copiar el hash generat.

- Utilitzo Ctrl + R per buscar el fitxer dins de nano.

![Imatge entrant al arxiu salida.txt](/tasca03/img/entremarxiusalida.png)

- Un cop dins, per copiar la línia sencera:

  - Alt + A per seleccionar des del principi.

  - Alt + 6 per copiar.

![Imatge del contingut del arxiu salida.txt](/tasca03/img/capturaarxiusalida.png)

2. Edició de l’arxiu /etc/grub.d/40_custom amb nano:

sudo nano /etc/grub.d/40_custom

3. Afegeixo les següents línies:

set superusers="nomusuari"
password_pbkdf2 nomusuari HASH_GENERAT

Substitueix nomusuari pel nom que vulguis utilitzar per protegir el GRUB i HASH_GENERAT pel hash copiat anteriorment.

![Imatge del arxiu /etc/grub.d/40_custom amb el contingut enganxat que hem copiat anteriorment](/tasca03/img/arxiuambtotenganxat.png)

### ♻️ Aplicar els canvis

Per aplicar els canvis i activar la protecció:

![Imatge de l'aplicació dels canvis](/tasca03/img/aplicaciócontrassenyaGRUB.png)

sudo reboot

![Imatge de la comanda reboot en el terminal per reiniciar la maquina](/tasca03/img/REBOOT.png)

### 🧪 Resultat Final

En reiniciar la màquina, el sistema ara **demana verificació per fer qualsevol acció al GRUB.**
Això evita que algú sense coneixements pugui reiniciar la contrasenya de l’usuari i accedir a les dades.

![Imatge de la verificació de l'usuari i la contrassenya d'acces al GRUB](/tasca03/img/VerificacióGRUB.png)

---

## 📝 Material de suport
- 🔗 [Recuperant Password en Linux (WayToIT)](https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/)
- 🔗 [protegint GRUB en Ubuntu Server](https://waytoit.wordpress.com/2019/09/15/protegiendo-grub-en-ubuntu-server/)

---

[Explicació de la tasca](README.md)

---

[Tornar a la pàgina principal](../)
