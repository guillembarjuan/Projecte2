# 🔌 T02: Selecció d’un SAI per una empresa client

---

## 1️⃣ Inventari d’equips

Els equips que connectaré al SAI són els següents:

- 💻 **4 ordinadors de sobretaula amb monitor inclòs** — [ThinkCentre M70a Gen 6](https://www.lenovo.com/es/es/p/desktops/thinkcentre/m-series-aio/lenovo-thinkcentre-m70a-gen-6-24-inch-intel/len102c0060#tech_specs)  
- 🌐 **1 router** — [Xiaomi Router 4A](https://www.mi.com/es/mi-router-4a/specs)

> 🖨️ La impressora no la connectaré al SAI, ja que **no és un element essencial** per a l’oficina i, si deixés de funcionar, la gent podria seguir treballant igualment.

### 💡 **Consum ordinadors (ThinkCentre M70a Gen 6)**

- 90 W (89% d’eficiència energètica)  
- El consum aproximat és de **100–110 VA** al 89% de càrrega.  
- En ús normal: **40–70 VA**.

**Càlcul**  

VA = W / Factor de potència
VA = 90 W / 0,90 = 100 VA

---

### 🌐 **Consum router**

- 12 V / 0,6 A → 7,2 W  
- Consum habitual: 7,2 VA

**Càlcul**  

Potència (W) = 12 V × 0,6 A = 7,2 W
Potència (VA) = 7,2 W / 1 = 7,2 VA

---

## 2️⃣ Càlcul de potència total

### 🧮 Potència dels equips

**Ordinadors (ThinkCentre M70a Gen 6)**  
- Consum per equip: 90 W  
- Factor de potència: 0,90  
- Voltamperis per equip: 100 VA  
- Total 4 ordinadors: 4 × 100 VA = 400 VA  
- Total en watts: 4 × 90 W = 360 W

**Router (Xiaomi 4A)**  
- Consum: 12 V × 0,6 A = 7,2 W  
- Factor de potència: 1 → 7,2 VA

---

### 📊 Potència total

**Sense reserva**
- Total VA = 400 + 7,2 = **407,2 VA**  
- Total W = 360 + 7,2 = **367,2 W**

**Amb reserva del 20%**
- VA amb reserva = 407,2 × 1,2 = **488,64 VA**  
- W amb reserva = 367,2 × 1,2 = **440,64 W**

✅ **Resultat final**
- Potència total sense reserva: **367 W / 407 VA**  
- Potència total amb reserva 20%: **441 W / 489 VA**

---

## 3️⃣ Determinació de l’autonomia

> 🕒 Un temps raonable per mantenir els equips en funcionament és **entre 10 i 15 minuts**, suficient per **guardar treballs i apagar correctament**.

---

## 4️⃣ Recerca de models de SAI

| Model                   | Potència (W) | Potència (VA) | Tipus            | Autonomia | Tipus de sortides                                                    | Preu (€) | Marca   |
|-------------------------|-------------:|--------------:|------------------|----------:|-----------------------------------------------------------------------|---------:|--------|
| **Back UPS Pro BR**     | 720 W        | 1200 VA       | Line-interactive | 10 min   | 6 de bateria + 2 protecció sobretensions                              | 494 €    | APC    |
| **CoolBox SCUDO3 SAI**  | 480 W        | 800 VA        | Line-interactive | 10 min   | 4 de bateria + 2 protecció sobretensions                              | 75 €     | CoolBox|

📎 [Back UPS Pro BR — Amazon](https://www.amazon.es/Back-UPS-APC-Schneider-Electric/dp/B07ZHHDTP2?th=1)  
📎 [CoolBox SCUDO3 SAI — Amazon](https://www.amazon.es/CoolBox-Alimentaci%C3%B3n-Ininterrumpida-Pantalla-Autonom%C3%ADa/dp/B0DP32KVDS/ref=sr_1_8?dib=eyJ2IjoiMSJ9.TPWIcXaP9WVUc9-GRhN_nFEkAemOmWxkxyzY2Lqhfk5y08onFrBLbjk_ShxTX8j1wdfLxOXEMeL3CT9qSuBwFqKujw66o-KeJNr8m8AUed2o41FMz4xmm0lWM-_la5n46hqXgQBYiXceyN0aYcZ7I3SNXwrqXw0SFzkP3Y-dJvP19sY6noGsHWRcJxYoir7C5tGyuedaCDmctgO51MHF-YmpMLJTDJaraPVSK3-mfUZ7o7lNBG6hisj3UAV6v_MGxOvADVCLeo-EQnQThmtLMDO90M1hpfCa8IjuAobBKDc.VTpQzgMRZslnKNy77XLSYfNSVyPZyBwMojaCnxZUwwI&dib_tag=se&keywords=comprar+sai&qid=1759255833&sr=8-8)

Imatge **Back UPS Pro BR**:

![Imatge del primer SAI, el Back UPS Pro BR](/tasca02/img/SAI1.png)

---

## 5️⃣ Informe tècnic

Després d’analitzar les necessitats energètiques de l’oficina i avaluar diferents alternatives, he seleccionat el **SAI més adequat** per a l’oficina.

### 📈 Anàlisi Tècnica Realitzada

**Càlcul de Requeriments Energètics**

- Equips a protegir: 4 ordinadors ThinkCentre M70a Gen 6 i 1 router Xiaomi 4A  
- Consum total calculat: **367,2 W / 407,2 VA**  
- Marge de seguretat del 20%: **440,64 W / 488,64 VA**  
- Autonomia objectiu: **10–15 minuts**

---

### 🧪 Models Avaluats

- **APC Back UPS Pro BR** → 720 W / 1200 VA — 494 €  
- **CoolBox SCUDO3 SAI** → 480 W / 800 VA — 75 €

---

### ⚡ Adequació Tècnica

- El **CoolBox SCUDO3** ofereix 480 W / 800 VA, superant els **441 W / 489 VA requerits**  
- Proporciona els **10–15 minuts d’autonomia** necessaris  
- Disposa de **4 sortides amb bateria**, suficients pels 4 ordinadors i el router

---

### 💰 Relació Cost–Benefici

- Preu significativament inferior (**75 €**) respecte a l’APC (**494 €**)  
- Les prestacions de l’APC són **excessives per a les necessitats reals**  
- Estalvi econòmic sense comprometre la funcionalitat

---

### 🧠 Característiques Pràctiques

- Tecnologia **line-interactive** adequada per a un entorn d’oficina  
- **Protecció contra sobretensions** inclosa  
- Disseny **compacte i adequat** per a l’espai disponible

---

### ✅ Conclusió

> El **CoolBox SCUDO3 SAI** representa **l’opció més equilibrada**, oferint totes les funcionalitats necessàries amb una inversió raonable i **sense prestacions superflues**.


