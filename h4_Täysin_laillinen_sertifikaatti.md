<**x) Lue/katso ja tiivistä**
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

**A)Totally Legit Sertificate**
- 
- komennolla 'sudo apt install zaproxy' sain ladattua ohjelman ongelmitta
<img width="622" height="637" alt="image" src="https://github.com/user-attachments/assets/594a790d-e5b1-4683-9233-d03bf378c9c3" />

- Ohjelman ladattua avasin 'tools' valikosta 'options' josta menin kohtaan 'network' ja siitä 'server cetrificates' mistä generoin uuden sertifikaatin:
<img width="747" height="550" alt="image" src="https://github.com/user-attachments/assets/41b5165b-c4cd-43fd-a698-d8c52f34c456" />

- lisäsin äsken tallentamani Zap proxyn firefoxin sertifikaatteihin:
<img width="938" height="719" alt="image" src="https://github.com/user-attachments/assets/7d1a0195-0deb-4c1a-bf0f-6bfeb83a447e" />

- firefoxin 'about:config' -kohdasta laitoin 'network.proxy.allow_hijacking_localhost' asetuksen päälle
<img width="953" height="281" alt="image" src="https://github.com/user-attachments/assets/bf569a23-d96a-4e25-badf-f969ca50f069" />

- firefoxin nettiasetuksista annoin proxylle oikeat tiedot:
<img width="827" height="751" alt="image" src="https://github.com/user-attachments/assets/59337b53-5984-492d-94ac-8c5b5c8bccfb" />

- Proxyn oletusportti on '8080' ja osoite 127.0.0.1 on local host
<img width="747" height="581" alt="image" src="https://github.com/user-attachments/assets/2fd92bcd-f8fc-487e-a5a7-60410ba30130" />

- tarkistin että Zap tallentaa myös kuvia:
<img width="862" height="582" alt="image" src="https://github.com/user-attachments/assets/072b7dd9-d559-4132-9f97-45c1f7fd7b4b" />

Lähde: https://www.zaproxy.org/docs/desktop/addons/network/options/servercertificates/ (Luettu 15.9.2026)

**B) kettumaista**
- 
- Firefoxin verrkoasetuksista laitoin oletus proxy asetuksen päälle jotta foxyproxy pystyy hallita liikennettä yksin
<img width="410" height="194" alt="image" src="https://github.com/user-attachments/assets/4169b3fc-9681-4462-834a-bb6deb538ca6" />

- FoxyProxyn lataaminen firefox add-ons sivulta:
<img width="944" height="285" alt="image" src="https://github.com/user-attachments/assets/39c44f99-3b77-4bb6-b2bb-e433c13bbd66" />

- Lisätään FoxyProxyn Proxies sivustolle uusi Proxy ja annetaan sille nimi, osoite sekä portti ja annetaan patternit
<img width="917" height="438" alt="image" src="https://github.com/user-attachments/assets/a503b1cb-3927-49f2-aeeb-0d84d5ce5624" />


- 
