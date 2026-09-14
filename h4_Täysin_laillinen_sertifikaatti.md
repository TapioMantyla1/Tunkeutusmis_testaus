**x) Lue/katso ja tiivistä**
- 

**OWASP 2021: OWASP Top 10:2021 :** (Alkuperäinen linkki ei ilmeisesti ole enää voimassa joten tein Owaspin toiseen saman nimiseen aineistoon pohjautuen: https://community.owasp.org/Broken_Access_Control Luettu 14.9.2026)

- Verkkosovellusten pääsyhallinta on usein kehittäjien silmissä haastavaa sekä aliarvioitua, sillä sen malli kytkeytyy tiiviisti sivuston tarjoamiin sisältöihin ja toimintoihin.
- Tärkeitä pääsynhallinnan kannalta tehtäviä asioita ovat: tunkeutumistestaus, koodin yksityiskohtainen katselmointi, jos ylläpitorajaa ylläpidetää etäyhteydellä on tarkistettava että etäyhteys on suojattua, tiukat ylläpitäjäoikeudet sekä SQL-injektion kaltaiset haavoittuvuudet on estettävä ulkoisia komentoja ajettaessa
- Pääsynhallintasääntöjen määrittelyssä on erittäin suositeltua käyttää pääsynhallintamatriisia.
- Tunnisteiden validointi: Arvattaviin ID-tietoihin tai niiden salassapitoon ei saa luottaa; pyytäjän oikeus tietoon on aina varmistettava.
- Sivujen suojauksen hyppy: Syvemmällä olevien osoitteiden suojausta ei saa voida ohittaa hyppäämällä tarkistussivun ohi.
- Välimuistin hallinta: Arkaluontoisen datan tallentuminen julkisten koneiden selainvälimuistiin estetään HTTP-otsikoilla ja meta-tageilla.
- Ylläpidon eristäminen: Ylläpitoliittymiä ei tule asettaa julkiseen verkkoon, vaan etäyhteydet rajataan sisäverkkoon esimerkiksi VPN-yhteyden taakse.


**PortSwigget Academy:**

IDOR(insecure direct object reference):
- Pääsynhallinnan haavoittuvuustyyppi, mikä syntyy, kun sovellus käyttää käyttäjän antamaa syötettä viittaamaan suoraan objekteihin (nettisovelluksen linkkiä manipuloidaan niin, että hyökkääjä pääsee käsiksi taustatietokantaan).

Lähde: https://portswigger.net/web-security/access-control/idor (Luettu 14.9.2026)


Path Traversal:
- Haavoittuvuuden avulla hyökkääjä voi päästä lukemaan verkkosovellusta pyörittävän palvelimen tiedostoja.
- Linkissä merkkiyhdistelmä '../' tarkoittaa siirtymistä yhden tason ylemmäs hakemistorakenteessa, kolme peräkkäistä merkkiyhdistelmää siirtää polun suoraan tiedostojärjestelmän juureen.

Lähde: https://portswigger.net/web-security/file-path-traversal (Luettu 14.9.2026)


(XSS)Cross-site scripting:
- Haavoittuvuus, minkä avulla hyökkääjä voi vaarantaa käyttäjien vuorovaikutuksen haavoittuvan sovelluksen kanssa.
- Mahdollistaa yleensä sen, että hyökkääjä voi tekeytyä uhriksi joutuneeksi käyttäjäksi, suorittaa mitä tahansa toimintoja sekä päästä käsiksi kaikkiin käyttäjän tietoihin.
- Verkkosivustoa voidaan manipuloida niin, että se palauttaa haitallista JavaScript-koodia käyttäjälle, kun haitallinen koodi ajetaan uhrin selaimessa, pystyy hyökkääjä lukea uhrin antamia tietoja verkkosovelluksesta.

Lähde: https://portswigger.net/web-security/cross-site-scripting (Luettu 14.9.2026)
