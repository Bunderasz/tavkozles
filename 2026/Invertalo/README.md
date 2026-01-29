# 📝 Mérési Jegyzőkönyv: Invertáló Erősítő vizsgálata

**Téma:** Műveleti erősítő alapkapcsolások – Invertáló erősítő
**Dátum:** 2026.01.29.

---

## 👤 Hallgatói adatok

* **Név:** Szihalmi Nándor
* **Intézmény:** Miskolci SZC Kandó Kálmán Informatikai Technikum
* **Helyszín:** v3 Labor
* **Tárgy:** Elektronika mérések

---

## 🎯 1. A mérés célja
A TL071 típusú műveleti erősítővel felépített invertáló alapkapcsolás vizsgálata. A kapcsolás feszültségerősítésének ($A_v$) meghatározása méréssel, valamint az elméleti (számított), a szimulált és a valós mérési eredmények összehasonlítása.

---

## 🛠️ 2. Felhasznált eszközök és alkatrészek

**Műszerek:**
* NI myDAQ Function Generator és Oszcilloszkóp
* Próbapanel (Breadboard)

**Alkatrészek:**

| Pozíciószám | Típus / Érték | Funkció |
| :--- | :--- | :--- |
| **IC1** | TL071 | Műveleti erősítő (JFET bemenetű) |
| **R1** | $11.77 \, \text{k}\Omega$ | Bemeneti ellenállás |
| **R2** | $99.7 \, \text{k}\Omega$ | Visszacsatoló ellenállás |
| **R3** | $11.95 \, \text{k}\Omega$ | Kompenzáló ellenállás (nem invertáló bemeneten) |

---

## 📐 3. Elméleti számítások

Az invertáló erősítő feszültségerősítése ideális esetben a visszacsatoló ($R_2$) és a bemeneti ($R_1$) ellenállás hányadosa:

$$A_{v} = -\frac{R_2}{R_1}$$

Behelyettesítve a mért ellenállás értékeket:

$$A_{v} = -\frac{99.7 \, \text{k}\Omega}{11.77 \, \text{k}\Omega} \approx \mathbf{-8.47}$$

Ez azt jelenti, hogy a kimeneti jel fázisban fordított ($180^\circ$) és kb. 8,47-szeres amplitudójú lesz a bemenethez képest.

---

## 🔌 4. Kapcsolási rajz és elrendezés

A mérés során az alábbi kapcsolást állítottuk össze:
* **Bemenet:** Invertáló láb (2-es pin) $R_1$-en keresztül.
* **Visszacsatolás:** Kimenet (6-os pin) és bemenet (2-es pin) között $R_2$.
* **Nem invertáló bemenet:** (3-as pin) $R_3$-on keresztül a Földre (GND) kötve.

<img width="975" height="525" alt="image (2)" src="https://github.com/user-attachments/assets/40b98338-e236-4bab-968a-798b06185b05" />

---

## 📊 5. Mérési eredmények és összehasonlítás

A mérést szinuszos vizsgálójelekkel végeztem. Az alábbi táblázat összehasonlítja a **szoftveres szimuláció** (pl. Tina / Multisim) és a **valós laboratóriumi mérés** eredményeit.

**Tápfeszültség:** $\pm 15\text{V}$

| Bemeneti Feszültség ($U_{be}$) | Szimulált Kimenet ($U_{ki, szim}$) | Valós Mért Kimenet ($U_{ki, mért}$) | Számított Erősítés ($A_{szim}$) | Valós Erősítés ($A_{mért}$) | Eltérés a szimulációtól |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **1.0 V** | -8.47 V | -8.461 V | -8.47 | -8.51 | -0.47% |

*Megjegyzés: A negatív előjel a fázisigordítást jelöli.*

<img width="519" height="598" alt="image (1)" src="https://github.com/user-attachments/assets/778b75b1-cdcf-4f2d-b49b-7fc089d3ca1e" />

---

<img width="1078" height="743" alt="image" src="https://github.com/user-attachments/assets/56b976cd-c417-450c-b3c8-1366bd36e615" />

---

## 📈 6. Kiértékelés

### Tapasztalatok
1.  **Erősítés:** A számított elméleti erősítés $A_v = -8.47$. A mérési eredmények alapján a kapcsolás stabilan tartotta ezt az értéket a kivezérlési tartományon belül.
2.  **Eltérések:** A szimulált és a valós értékek közötti eltérés minimális (<1%), ami az ellenállások tűréséből ($R_1, R_2$) és a műszerek mérési pontatlanságából adódik.
3.  **Kivezérlés:** 1.5V bemenő jelnél a kimenet kb. 12.7V, ami közelít a tápfeszültséghez ($\pm 15\text{V}$), de még nem vágta a jelet az IC.

### Konklúzió
A TL071-es műveleti erősítővel felépített kapcsolás helyesen, az elméleti számításoknak megfelelően invertáló erősítőként működött. Az $R_3$ ellenállás beépítése a nem invertáló bemenetre sikeresen minimalizálta a bemeneti offszet hibát.

---

*Aláírás:* **Szihalmi Nándor**
