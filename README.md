# ESP32_Falcon
Jest to customowa płytka deweloperska oparta na module ESP32-S3, była ona inspirowana designem STM32 Nucleo. Jest to projekt rekrutacyjny do koła naukowego FALCON na Politechnice Wrocławskiej. Został on całkowicie wykonany w KiCad.

## Specyfikacja
**Mikrokontroler:** ESP32-S3-WROOM-1.
**Komunikacja i Zasilanie:** Złącze USB-C z układem zabezpieczającym ESD.
**Czujniki:** Zintegrowany czujnik IMU BMI270 podłączony przez I2C.
**Rozszerzalność:** Wyprowadzenia sygnałowe na złączach goldpin w układzie Nucleo.

### 1. Schemat Ideowy
![Schemat Ideowy](TUTAJ_WKLEJ_LINK_DO_ZDJECIA_SCHEMATU.png)

### 2. Layout PCB
![Layout PCB](TUTAJ_WKLEJ_LINK_DO_ZDJECIA_PCB.png)

### 3. Model 3D
![Model 3D](TUTAJ_WKLEJ_LINK_DO_ZDJECIA_3D.png)

## 🧠 Główne Decyzje Projektowe i Zasady EMC
Podczas projektowania layoutu PCB szczególną uwagę zwróciłem na:
1. **Prowadzenie sygnałów USB (D+/D-):** Linie danych z USB-C zostały poprowadzone jako para różnicowa na jednej warstwie, łeb w łeb, bez użycia przelotek, w celu zachowania spójności impedancji. Ominąłem je szerokim łukiem od grubszych ścieżek zasilających.
2. **Zachowanie strefy Keepout dla anteny:** Moduł ESP32-S3 został umieszczony na krawędzi płytki, a jego antena znajduje się całkowicie poza obrysem miedzi i laminatu, aby uniknąć tłumienia sygnału Wi-Fi/Bluetooth.
3. **Dystrybucja Zasilania i Decoupling:** Zastosowałem topologię gwiazdy/drzewa, prowadząc grube ścieżki zasilające (0.4mm - 0.5mm) bezpośrednio do głównych odbiorników. Kondensatory filtrujące (100nF i 22uF) zostały umieszczone w bezpośrednim sąsiedztwie pinów zasilających ESP32 oraz BMI270, a ścieżki poprowadzono bezpośrednio przez ich pady.
4. **Wylewki GND (Copper Pours):** Zastosowałem wylewki masy na obu stronach laminatu (F.Cu oraz B.Cu). Aby wyeliminować problem "wysp miedzi" i zapewnić krótką drogę powrotną dla sygnałów, połacie masy zostały połączone za pomocą przelotek zszywających (Via Stitching).
5. **Dostosowanie produkcyjne:** Usunąłem błędy zwężania przerw między ścieżkami a układem BMI270 (necking down do 0.25mm) oraz wymusiłem pełne zalanie padów masy dla mniejszych komponentów, zapewniając zgodność z limitami DRC dla tanich fabryk (otwory 0.2mm).

## 📁 Zawartość Repozytorium
* `projekt_kicad/` - Pliki źródłowe projektu (schemat, layout).
* [cite_start]`gerbery/` - Gotowe pliki produkcyjne (Gerber + pliki owierceń)[cite: 23].
* [cite_start]`BOM.csv` - Zestawienie materiałowe wszystkich komponentów[cite: 23].
* [cite_start]`ESP32_Falcon.step` - Wyeksportowany model 3D całej płytki[cite: 27].
