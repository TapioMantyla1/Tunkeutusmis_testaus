x)
**Buuri 2026: DORA and TLPT testing - Lecture for Haaga-Helia on 31 March 2026**
- DORA = EU:n finanssisektorin digitaalisen toimintavarmuuden sääntely; tuli sovellettavaksi tammikuussa 2025
- TLPT = vaativampi uhkaperusteinen penetraatiotestaus, jota edellytetään viranomaisen määrittelemiltä merkittäviltä toimijoilta; kaikille toimijoille kuuluu myös perustason resilienssitestausta
- TIBER-EU / TIBER-FI = uhkatietoon perustuvan red team -testauksen viitekehys. TIBER-FI on Suomessa sovellettu ja DORAn vaatimuksiin päivitetty versio. Tyypillinen testaus kestää 12-18kk alusta loppuun
- Red team simuloi hyökkäävää osapuolta. Red team on lähes aina taitava kolmas ulkopuoli palkattuna tekemään tämä työ
- Blue team puolestaa on kohde toimijan oma puolustava ryhmä joka pyrkii torjumaan hyökkäykset ja tunkeutumiset

**DORA (Regulation ... on digital operational resilience for the financial sector) (artiklat 26 & 27)**
- Viranomaisten osoittamat merkittävät finannssitoimijat joutuvat suorittamaan kehittynyttä testausta (eli TLPT Threat-Led penetration testing) vähintään kolmen vuoden välein
- Jokaisen testauksen on sisällettävä useita tai jopa kaikki finanssitoimijan kriittiset tai tärkeät toiminnot sekä testi on suoritettava näitä tukevissa tuotantojärjestelmissä
- Finanssitoimija itse kantaa vastuun DORA-asetusten noudattamisesta
- Tietyissä tilanteissa yhteinen TLPT (pooled testing) on mahdollista palveluntarjoajan sekä finanssitoimijan kesken sovittaen. Siinä testataan useampaa palveluntarjoajan asiakasta
- Viranomaiset antavat finanssitoimijalle todistuksen testauksen suorituksesta kun se on suoritettu vaatimusten mukaisesti

**TIBER-FI procedures and guidelines (vain kappaleen 5.4 johdanto)**
- Red teaming vaihe jaetaan kahteen eri osioon:
1. Red team test planning (RTTP) eli testauksen suunnittelun laatiminen
2. Aktiivinen testaus
- RTT:n (red team testing) tulisi testauksessa hyödyntää useita erilaisia TTP-menetelmiä (Tactics, Techniques & procedures)
- Tästä yksi esimerkki olisi cyber kill chain
- Testin realistinen simuloiminen on usein haasteellista resurssien puutteiden vuoksi, esimerkiksi oikeilla hyökkääjillä on usein kuukausia enemmän aikaa suunnitella hyökkäystä
- Tämän takia testeissä RTT:lle usein annetaan leg up:ja mitkä ovat lisätietoja kohteena olevista ihmisistä, prosesseista ja järjestelmistä


**a) 
sain ladattua sekä asennettua virtualboxiin metasploitable 2:n ongelmitta. Lisäksi ennen kuin avasin koneen niin verrkoasetuksista kytkin päälle "Host-only adapter"**

<img width="883" height="711" alt="image" src="https://github.com/user-attachments/assets/fc77949b-9b5a-45ca-b5dc-590787ce0b8e" />



**b & c)
sain luotua Host-Only adapterin avulla yhteiden kumpaankin virtuaalikoneeseen ilman että ne ovat yhteydessä muualle ja kokeilin sitä pingaamalla toisiaan:**

<img width="528" height="184" alt="image" src="https://github.com/user-attachments/assets/2fe5378f-8e61-4f4f-9408-25b7b2b42d4e" />

<img width="593" height="124" alt="image" src="https://github.com/user-attachments/assets/a5f4bb71-3976-42c2-b628-d16994aa3c07" />

ja sitten pingaus muihin verkkoihin:

<img width="372" height="44" alt="image" src="https://github.com/user-attachments/assets/71baac25-b460-418e-a63c-05c0bff21763" />

<img width="350" height="97" alt="image" src="https://github.com/user-attachments/assets/9c79a013-0d4b-47d5-851c-93683bc6b158" />



**d)
porttikannaamalla linuxilla löytyi metaspoiltablen ip osoite:**

<img width="596" height="299" alt="image" src="https://github.com/user-attachments/assets/c7928690-f7ae-4d83-a3af-790912c5bff3" />

Kun kirjoitti selaimen hakukenttään "http://(metasploitablen 2:n ip)" niin tuli tämä näkymä

<img width="564" height="490" alt="image" src="https://github.com/user-attachments/assets/0acf1358-9389-4b5d-b531-85559d2627f1" />



**e)
Porttiskannasin metasploitable 2:n onnistuneesti:**

<img width="1209" height="856" alt="image" src="https://github.com/user-attachments/assets/690ac970-ac71-46e7-ad99-87d88793a61e" />

porttiskanneri löysi kaikenkaikkiaan 30 avonaista porttia (65535 - 65505 = 30)
Kiinnostavimmat 2 porttia mitä löysin olivat:
- portti 21 (FTP) ei ole suojattu portti (kuten SFTP) jota kautta tunkeutujalla on pääsy sen dataan. Lisäksi nmap havaitsi että anonyymi kirjautuminen on sallittua
- portti 80 (tcp) altistaa verkkopalvelin sekä verkkosovellus hyökkäyksille kuten SQL-enjektioille. Teksti kulkee portin kautta suojaamattomana pelkkänä tekstinä


Lähteet:
Buuri 2026: DORA and TLPT testing - Lecture for Haaga-Helia on 31 March 2026 https://terokarvinen.com/buuri-2026-dora-and-threat-lead-penetration-testing/buuri-2026-dora-and-threat-lead-penetration-testing--teros-pentest-course.pdf Luettu 1.9.2026
DORA (Regulation ... on digital operational resilience for the financial sector) https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng Artikla 26 & 27 luettu 1.9.2026
Open ports at Metasploitable2. Are they vulnerable? https://medium.com/@raptopzen10/open-ports-at-metasploitable2-are-they-vulnerable-b8a11c4e40fb Luettu 1.9.2026
Port 80/TCP (HTTP) - Vulnerabilities, CVEs, Security Guide https://scanitex.com/en/resources/ports/tcp/80 Luettu 1.9.2026
TIBER-FI procedures and guidelines https://www.suomenpankki.fi/globalassets/bof/en/money-and-payments/the-bank-of-finland-as-catalyst-payments-council/tiber-fi/tiber-fi-2.0-procedures-and-guidelines.pdf kappaleen 5.4 johdanto luettu 1.9.2026
What are the vulnerabilities on port 23? [closed] https://security.stackexchange.com/questions/39692/what-are-the-vulnerabilities-on-port-23 Luettu 1.9.2026
