# ESP32_Falcon
Jest to customowa płytka deweloperska oparta na module ESP32-S3, była ona inspirowana designem STM32 Nucleo. Jest to projekt rekrutacyjny do koła naukowego FALCON na Politechnice Wrocławskiej. Został on całkowicie wykonany w KiCad.

## Specyfikacja
**Mikrokontroler:** ESP32-S3-WROOM-1.
* **Komunikacja i Zasilanie:** Złącze USB-C z układem zabezpieczającym ESD.
* **Czujniki:** Zintegrowany czujnik IMU BMI270 podłączony przez I2C.
* **Rozszerzalność:** Wyprowadzenia sygnałowe na złączach goldpin w układzie Nucleo.

### 1. Schemat 
<img width="1091" height="750" alt="schemat" src="https://github.com/user-attachments/assets/3b5f12c3-bf0b-4cf8-9656-b9ab7f76aa01" />

### 2. Layout PCB
<img width="432" height="705" alt="PCB" src="https://github.com/user-attachments/assets/ffe84b1b-a73e-4062-a804-951d1d8a037c" />


### 3. Model 3D
<img width="877" height="748" alt="3D" src="https://github.com/user-attachments/assets/30c8f13f-3bba-4105-83d7-789b016f3b9c" />

## Główne Decyzje Projektowe i Zasady EMC
1. **Prowadzenie sygnałów USB (D+/D-):** Linie danych z USB-C zostały poprowadzone jako para różnicowa na jednej warstwie, bez użycia przelotek, w celu zachowania spójności impedancji.
2. **Zachowanie strefy Keepout dla anteny:** Moduł ESP32-S3 został umieszczony na krawędzi płytki, a jego antena znajduje się całkowicie poza obrysem miedzi i laminatu, aby uniknąć tłumienia sygnału.
3. **Dystrybucja Zasilania i Decoupling:** Ścieżki zasilające mają odpowiednią grubość (0.4mm - 0.5mm) i są prowadzone bezpośrednio do głównych odbiorników. Kondensatory filtrujące zostały umieszczone w bezpośrednim sąsiedztwie pinów zasilających ESP32 oraz BMI270.
4. **Wylewki GND (Copper Pours):** Wylewki masy na obu stronach laminatu. Połacie masy zostały połączone za pomocą przelotek.
