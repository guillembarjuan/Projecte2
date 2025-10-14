# 🧰 T03: Seguretat Lògica — Recuperant accés a sistemes

## 📌 Breu descripció
Després de la primera feina exitosa, arriba un encàrrec urgent que requereix una actuació ràpida. Com a pas previ, rebreu una formació sobre **seguretat lògica**, que us donarà els coneixements necessaris per afrontar la tasca.

Un client ha portat un portàtil amb **Zorin OS (Linux)** utilitzat habitualment per un directiu. El problema és que ha **oblidat la contrasenya**, i cal **recuperar l’accés** per obtenir documentació important.  
Per evitar riscos sobre l’equip original, s’ha realitzat un **clonatge del disc** en un disc virtual perquè hi treballeu amb seguretat.

---

## 🎯 Objectius de la tasca
- Crear una màquina virtual i connectar-hi el disc clonat.  
- Accedir al sistema, identificar l’usuari existent i assignar-li una nova contrasenya.  
- Verificar que l’accés a l’equip funciona correctament.  
- Investigar com **protegir el GRUB amb contrasenya** per evitar que algú pugui reiniciar la contrasenya seguint el mateix procediment.  
- Configurar la màquina virtual amb aquesta protecció activada.  
- Documentar tot el procés amb captures i explicacions clares.

---

## 🧭 Procediment individual
1. **Vulnerar l’accés al GRUB** per entrar al sistema sense conèixer la contrasenya.  
2. **Identificar l’usuari** configurat al sistema.  
3. **Modificar la seva contrasenya** i comprovar que es pot accedir.  
4. **Investigar i aplicar mesures de fortificació** al GRUB, afegint-hi una contrasenya per impedir l’edició de les opcions d’arrencada.  
5. Documentar tot el procés pas a pas, incloent-hi **fonts d’informació utilitzades** i **captures de pantalla**.

---

## 📝 Material de suport
- 🖥️ **Disc virtual** proporcionat per a la pràctica.  
- 📚 **Apunts RA1AA4** — Seguretat Lògica.  
- 🔗 [Recuperant Password en Linux (WayToIT)](https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/)

---

## 📂 Lliurament
Aquesta activitat es documentarà en dos fitxers:
- `README.md` → Explicació general de la tasca (aquest fitxer).  
- `solucio.md` → Procediment complet, captures i resultats obtinguts.

---

[Solució de la tasca](solucio.md)

---

[Tornar a la pàgina principal](../)


