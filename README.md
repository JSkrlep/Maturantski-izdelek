# Vremenska postaja

## Ideja
Osnovna ideja projekta je postaviti na zunanjo lokacijo napravo s senzorji, ki meri vremenske parametre – temperaturo, količino padavin, svetlost in vlažnost. Izmerjeni podatki se nato prek brezžične povezave prenesejo na drugo lokacijo (npr. domov ali v sobo), kjer jih ESP32 sprejme in posreduje na spletno stran, ki podatke grafično prikazuje v obliki grafov.

## Delovanje sistema
Sistem sestavljata dve glavni komponenti: **oddajna enota** (Arduino vezje s senzorji) in **sprejemna enota** (ESP32 vezje), ki med seboj komunicirata prek LoRa modulov.

### 1. Oddajna enota – Arduino vezje
Osnova oddajne enote je mikrokontroler **Arduino Pro Mini (3.3V, 8 MHz)**. Vezje na senzorjih vsakih **15 sekund** izmeri vse vremenske parametre in jih pošlje naprej.

**Uporabljeni senzorji:**

| Senzor | Merjena karakteristika |
|---|---|
| BME280 | Temperatura, zračni pritisk, vlažnost |
| Deževni senzor | Zaznava količine padavin/vode na površini |
| BH1750 | Svetlost (enota: lux) |

**Komunikacijski modul:**
- **LoRa SX1278** – omogoča brezžični prenos izmerjenih podatkov do sprejemne enote na drugi lokaciji.

### 2. Sprejemna enota – ESP32 vezje
Sprejemna enota je strojno enostavnejša, saj vsebuje le:
- **ESP32** mikrokontroler
- **LoRa modul SX1278** (sprejemnik)

Kljub enostavnejši strojni zasnovi je ta del zahtevnejši na programski strani, saj mora ESP32 prejete podatke ustrezno dekodirati/obdelati in jih posredovati naprej na **API**. Spletna stran nato na podlagi API podatkov izriše grafe za vsako izmerjeno karakteristiko (temperatura, pritisk, vlažnost, padavine, svetlost).

## Arhitektura prenosa podatkov

Senzorji -> Arduino Pro Mini -> LoRaSX1278 oddajnik -> LoRaSX1278 sprejemnik -> ESP32 -> API -> spletna stran

## Uporabljene komponente
- Arduino Pro Mini 3.3V, 8 MHz
- ESP32
- LoRa modul SX1278 (x2)
- Senzor BME280 (temperatura, pritisk, vlažnost)
- Deževni senzor
- Senzor BH1750 (svetlost)

## Avtor
Jure Škrlep
