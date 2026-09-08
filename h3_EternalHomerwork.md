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

Lähde: Host discovery (: https://nmap.org/book/man-host-discovery.html (Lueattu 8.9.2026)
Luotettavuus: Lähde on Nmap kehittäjän omalta viralliselta nettisivulta poimittu. 


**Lähteet:**
What is fuzzing and fuzz testing? (29.7.2024): https://github.com/resources/articles/what-is-fuzz-testing luettu 8.9.2026
Host discovery (: https://nmap.org/book/man-host-discovery.html 
