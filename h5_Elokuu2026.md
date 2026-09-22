**X) Tiivistä**
- 
**Karvinen 2022: Cracking Passwords with Hashcat**
- salasanat kääntyvät ohjelmissa "hash"heiksi joita ei pysty enään kääntämään annettuihin salasanoihin
- Työkalussa hashid parametri -m näyttää numeron, jota käytetään varsinaisessa murtamisessa
- komennolla 'hashid -m (hash)' saadaan numero jota käytetään salasanan murtamisessa
- komennolla 'hashcat -m (hashid komennosta saatu numero) ('hash') -o (tiedosto johon haluat vastauksen tallentuvan)
Lähden: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/ (Luettu 22.9.2026)

**Karvinen 2023: Crack File Password With John**
- John the ripper on ohjelma mikä murtaa tiedostosalasanat sanakirjahyökkäyksellä
- Ohjelmasta asennetaan jumbo-versio gitin kautta ja käännetään lähdekoodista
- Tiedostosta erotetaan hash komennolla '/zip2john jotain.zip > jotain.zip.hash'
- Sanakirjahyökkäys tehdään komennolla '/john jotain.zip.hash'
- Ohjleman mukana tulee kasa työkaluja, joiden avulla pystytään murtamaan salasanoja eri muodoista, esimerkiksi PDF, Office sekä SSH-avaimet

**a) Asenna Hashcat ja testaa sen toiminta murtamalla esimerkkisalasana.**
- 
- Hashcatin asennut olis vaivatonta:
<img width="622" height="348" alt="image" src="https://github.com/user-attachments/assets/ed771b28-4cac-41ae-9a86-0c844371e066" />

- loin uuden tiedoston johon toin nettiin ladattujen, jo murrettujen salasanojen listan
<img width="623" height="71" alt="image" src="https://github.com/user-attachments/assets/4970ee7a-5421-4590-88fa-29a88bb1d273" />

- Loin esimerkkisalasanan "password", katsoin sen Hashin jonka jälkeen tarkistin Hashin tyypin:
<img width="294" height="126" alt="image" src="https://github.com/user-attachments/assets/1f1c017a-22c6-4f26-8b01-ad83fa075996" />
<img width="425" height="351" alt="image" src="https://github.com/user-attachments/assets/c6705b8a-4e7b-46d8-b153-60d6fe1f9b97" />

- Yritin käyttää tyyppiä "MD5" murtamiseen, mutta tuli virheilmoitus:
<img width="616" height="367" alt="image" src="https://github.com/user-attachments/assets/7540d8ec-bc44-44db-9653-6bde5381e707" />

- En löytänyt vastausta googlaamalla, joten käytin chatGPT -tekoälyä vastauksen löytämiseen.
- Tekoäly vastasi näin: "Virhe johtuu siitä, että virtuaalikoneessa ei ole suoraa pääsyä näytönohjaimeen eikä sille ole asennettu suorittimelle tarkoitettua OpenCL-ajuria. Hashcat ei siis löydä laitetta, jolla laskenta suoritettaisiin.
- Tekoäly ohjeista lataamaan ohjelman "pocl-opencl-icd", mikä on linuxpaketti joka mahdollistaa OpenCL-laskennan suoraan CPU:lla ilman erillistä näytönohjainta.

- Sitten kokeilin uudestaan ajaa komentoa 'hashcat -m 0 '5f4dcc3b5aa765d61d8327deb882cf99' rockyou.txt -o solved' tuloksella:
<img width="630" height="356" alt="image" src="https://github.com/user-attachments/assets/05a957f4-38f4-41e4-9bac-f3ad8bdc959d" />
<img width="341" height="61" alt="image" src="https://github.com/user-attachments/assets/ac96c4fb-9925-4582-8296-8500ac171583" />
