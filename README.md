Vremenska postaja
--------------------------------------------------------------------------------------------------------------------
Ideja
--------------------------------------------------------------------------------------------------------------------

Osnovna ideja vremenske postaje je, da bi postavil na eno zunanjo lokacijo škatlo oz. senzorje s katerimi bi meril v določenem kraju koliko je temperature, padavine, svetlost, vlažnost... In nato na drugi lokaciji nekje doma ali v sobi
bi s pomočjo ESP32 te podatke dobival in jih nato grafično prikazoval na računalniku kot grafe.

-------------------------------------------------------------------------------------------------------------------
Delovanje
-----------------------------------------------------------------------------------------------------------------

Celotni izdelek ima 2 glavni komponenti:

1. komponenta - Arduino vezje

Arduino vezje je bazirano na mikrokontrolerju Arduino Pro Mini 3.3V, 8 MHz. Ta mi omogoča da iz vseh senzorjev, ki so priklopljeni na njega pošlje na intervalu 15 sekund vse podatke o vremenu. Torej na vsakih 15 sekund mi senzor izmeri vse podatke in jih nato pregledno izpisuje. 
ima različne senzorje za merjenje različnih karakteristik.
1. BME280 je senzor, ki je vezan mi omogoča branje temperature, pritiska in vlažnost.
2. senzor je deževni senzor, ta je narejen za merjenje padavin oz. zazna koliko vode je na površini.
3. senzor je BH1750, na vezju prikazuje koliko je trenutna svetlost. Merim jo v enoti lux.

kot četrtka komponenta v vezju nastopa LoRa modul, ki omogoča komunikacijo z drugo komponento katera dejanske podatke, da na širni internet.


2. komponenta - ESP32 vezje

To vezje je po komponentah enostavnejše, saj imamo gor dejansko samo ESP32 in LoRa modul.
Je pa bolj težaven z vidika kodiranja, saj je treba vse te podatke ustrezno šifrirati, da jih lahko potem ESP32 poda naprej na API
in nato, na spletni strani ustrezno izriše grafe za vsako karakteristiko.
