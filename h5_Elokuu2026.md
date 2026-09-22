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
- Tekoäly ohjeisti lataamaan ohjelman "pocl-opencl-icd", mikä on linuxpaketti joka mahdollistaa OpenCL-laskennan suoraan CPU:lla ilman erillistä näytönohjainta.

- Sitten kokeilin uudestaan ajaa komentoa 'hashcat -m 0 '5f4dcc3b5aa765d61d8327deb882cf99' rockyou.txt -o solved' tuloksella:
<img width="630" height="356" alt="image" src="https://github.com/user-attachments/assets/05a957f4-38f4-41e4-9bac-f3ad8bdc959d" />
<img width="341" height="61" alt="image" src="https://github.com/user-attachments/assets/ac96c4fb-9925-4582-8296-8500ac171583" />

**c) Asenna John the Ripper ja testaa sen toiminta murtamalla jonkin esimerkkitiedoston salasana.**
- 
- Sain asennettua ohjelman, kuten https://terokarvinen.com/2023/crack-file-password-with-john/ ohjeissa näytettiin
- Latasin testikansiooni https://terokarvinen.com/2023/crack-file-password-with-john/ -sivulta zip-kansion

<img width="630" height="318" alt="image" src="https://github.com/user-attachments/assets/1ddce466-be08-4e52-9635-a67814a4c872" />

- sitten siirsin zip-tiedoston ja sitten tein sanakirja hyökkäyksen, salasana oli "butterfly":
<img width="634" height="134" alt="image" src="https://github.com/user-attachments/assets/99fb6cd3-16ac-4415-b89e-421b25ab0178" />
<img width="619" height="192" alt="image" src="https://github.com/user-attachments/assets/d10f3a2e-93c9-45bc-8297-ee6fe21ea7b8" />

**e) Tiedosto**
-
- Löysin netistä työkalun nimeltä "7zip", mikä on avoimenlähdekoodin pakkausohjelma. Se tekee kaksi pääasiaa:
- pakkaa tiedostot: kutistaa tiedostoja ja kansioita pienempään tilaan
- salaa sisällön
- Latasin kyseisen ohjelman ja loin zip-tiedoston:
<img width="369" height="70" alt="image" src="https://github.com/user-attachments/assets/7cdea410-147a-45a5-af76-d7cd1349a6cb" />
<img width="558" height="139" alt="image" src="https://github.com/user-attachments/assets/b4be3b15-55de-4837-bc35-0e28083c546b" />

- Loin uuden sanalista,n mikä sisältää käytetyn salasanan (koska 7z käyttää jotain salastapaa mikä muuttaa salasanan murtamisen äärimmäisen hitaaksi) ja mursin salasanan, mikä oli omena
<img width="632" height="379" alt="image" src="https://github.com/user-attachments/assets/63f9dce1-5893-4fd2-b78d-556f57508a1a" />

lähde: https://www.tutorialspoint.com/article/install-and-use-7zip-on-linux (Luettu 22.9.2026)

**f) tiiviste**
- 
- Loin uuden testikäyttäjän:
<img width="230" height="58" alt="image" src="https://github.com/user-attachments/assets/1156c506-2f4a-4c2d-859b-ddf7ea845016" />


- Annoin sille heikon salansanan ja erotin tiivisteen
<img width="629" height="137" alt="image" src="https://github.com/user-attachments/assets/519af33a-f12f-4148-abef-dfa69bedd85f" />

- Sitten mursin salasanan onnistuneesti:
<img width="626" height="294" alt="image" src="https://github.com/user-attachments/assets/e634c7df-d26e-4b13-8e3a-fb21a785b683" />

**g) sanakirja**
- 
- käytin "cewl" työkalua tehtävän suorittamiseen. Cewl on työkalu, mikä Luo sanakirjoja verkkosivujen sisällöstä.
<img width="618" height="332" alt="image" src="https://github.com/user-attachments/assets/5a10a5fc-c430-4198-a3e5-ac13d2e0b658" />
- Komennossa '-m 4' on parametri mikä kerää nettisivulta sanoja jotka ovat vähintään 4 kirjainta pitkiä. Parametri '-w' taas kertoo tiedoston nimen, johon tulokset kirjoitetaan.
Lähde: https://www.kali.org/tools/cewl/ (Luettu 22.9.2026)

**h) Hash rules**
-
- 
