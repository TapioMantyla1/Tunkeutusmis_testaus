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

**A)Totally Legit Sertificate**
- 
- komennolla 'sudo apt install zaproxy' sain ladattua ohjelman ongelmitta.
<img width="622" height="637" alt="image" src="https://github.com/user-attachments/assets/594a790d-e5b1-4683-9233-d03bf378c9c3" />


- Ohjelman ladattua avasin 'tools' valikosta 'options' josta menin kohtaan 'network' ja siitä 'server cetrificates' mistä generoin uuden sertifikaatin:
<img width="747" height="550" alt="image" src="https://github.com/user-attachments/assets/41b5165b-c4cd-43fd-a698-d8c52f34c456" />


- lisäsin äsken tallentamani Zap proxyn firefoxin sertifikaatteihin:
<img width="938" height="719" alt="image" src="https://github.com/user-attachments/assets/7d1a0195-0deb-4c1a-bf0f-6bfeb83a447e" />


- firefoxin 'about:config' -kohdasta laitoin 'network.proxy.allow_hijacking_localhost' asetuksen päälle.
<img width="953" height="281" alt="image" src="https://github.com/user-attachments/assets/bf569a23-d96a-4e25-badf-f969ca50f069" />


- firefoxin nettiasetuksista annoin proxylle oikeat tiedot:
<img width="827" height="751" alt="image" src="https://github.com/user-attachments/assets/59337b53-5984-492d-94ac-8c5b5c8bccfb" />


- Proxyn oletusportti on '8080' ja osoite 127.0.0.1 on local host.
<img width="747" height="581" alt="image" src="https://github.com/user-attachments/assets/2fd92bcd-f8fc-487e-a5a7-60410ba30130" />


- tarkistin että Zap tallentaa myös kuvia:
<img width="862" height="582" alt="image" src="https://github.com/user-attachments/assets/072b7dd9-d559-4132-9f97-45c1f7fd7b4b" />

Lähde: https://www.zaproxy.org/docs/desktop/addons/network/options/servercertificates/ (Luettu 15.9.2026).

**B) kettumaista**
- 
- Firefoxin verrkoasetuksista laitoin oletus proxy asetuksen päälle jotta foxyproxy pystyy hallita liikennettä yksin.
<img width="410" height="194" alt="image" src="https://github.com/user-attachments/assets/4169b3fc-9681-4462-834a-bb6deb538ca6" />


- FoxyProxyn lataaminen firefox add-ons sivulta:
<img width="944" height="285" alt="image" src="https://github.com/user-attachments/assets/39c44f99-3b77-4bb6-b2bb-e433c13bbd66" />


- Lisätään FoxyProxyn Proxies sivustolle uusi Proxy ja annetaan sille nimi, osoite sekä portti ja annetaan patternit.
<img width="903" height="444" alt="image" src="https://github.com/user-attachments/assets/23a061e6-aa31-442b-b182-2820ccbf2c0c" />

- Kokeilin Proxyä menemällä HaagaHelian sivuille eikä Zap proxyn historiaan tullut mitään, eli se toimii.
<img width="694" height="754" alt="image" src="https://github.com/user-attachments/assets/f42eaf53-c3e6-4b9a-b860-701889879330" />

Lähteet: 
- https://www.youtube.com/watch?v=jHGNLvSpaLs (Katsottu 15.9.2026).
- https://www.webshare.io/blog/foxyproxy-setup-guide (Luettu 15.9.2026).


**PortSwigger Labs**
-
**C) Reflected XSS into HTML context with nothing encoded**
- Labrassa kokeilin kirjoittaa blogin hakukenttään 'terve' jotta löytäisin sen Zapista:
<img width="738" height="269" alt="image" src="https://github.com/user-attachments/assets/98b4470b-c72e-44af-bc74-fcba43aa4a82" />

- ja se löytyi, eli nettisivu on haavoittuvainen ja sitä pystyy manipuloimaan syöttämällä HTML koodia.
<img width="848" height="338" alt="image" src="https://github.com/user-attachments/assets/7649f6c1-b79a-4f4d-bc9d-efbc8d7101c2" />

- kun hakukenttään kirjoittaa '<script>alert(1)</script>', niin nettisivu lukee sen syötettynä HTML koodina ja ajaa sen eli käyttäjän syötettä luettiin luotettun koodina eikä datana, tässä harjoituksessa HTML koodi on kertakäyttöinen.
<img width="540" height="199" alt="image" src="https://github.com/user-attachments/assets/eef1a418-44a6-47a4-a259-ff99ccfc47a2" />

**D) Lab: Stored XSS into HTML context with nothing encoded**
- Harjoituksessa kun menin jonkun postauksen kommenttikenttään ja kirjoitin kommentiksi '<script>alert(1)</script>'.
<img width="737" height="640" alt="image" src="https://github.com/user-attachments/assets/59f42b66-a62e-4a92-8537-4ee28bb8ac0b" />

- Nettisivu lukee kommentin HTML koodina eikä datana ja täten se on XSS haavoittuvuus, tässä harjoituksessa koodi jää pysyvästi nettisivulle.
<img width="526" height="193" alt="image" src="https://github.com/user-attachments/assets/e864528d-8b11-44df-a2e4-f5f395a2fe54" />

**E) Selitä esimerkin avulla, mitä hyökkääjä hyötyy XSS-hyökkäyksestä.**
- 
- Hyökkääjä pystyy hyödyntämään haavoittuvuutta esimerkiksi siten että pystyy ajamaan haluamaansa koodia nettisivulle ja mahdollisesti voi päästä uhrin istuntoon ja tehdä tämän indentiteetillä mitä tahans toimintoja tämän tietämättä.
Lähde: https://community.owasp.org/attacks/xss/ (Luettu 15.9.2026).

**F) Lab: File path traversal, simple case**
- 
- Harjoituksessa sivusto hakee tuotekuvat suoraan palvelimen tiedostopolusta parametrilla filename=kuva.jpg. Se vain lätkäisee käyttäjän antaman tiedostonimen suoraan kuvakansion jatkeeksi.
<img width="340" height="400" alt="image" src="https://github.com/user-attachments/assets/ea69f8c4-4441-4e3e-818e-1e56e637d666" />

- Palvelin luottaa käyttäjään liikaa eikä tarkista syötettä ollenkaan. Koodi ei estä ../-siirtymiä, jolloin tiedostopolussa pääsee kiipeämään ulos sallitusta kuvakansiosta.
<img width="1424" height="131" alt="image" src="https://github.com/user-attachments/assets/a3fe894f-7444-468c-9eff-c0c921acfe48" />

**G) Lab: File path traversal, traversal sequences blocked with absolute path bypass**
- 
- Harjoituksessa kun kirjoittaa käytännössä saman osoitteen osoiteriville ilman '../' parameterjä, niin pääsee murtautumaan sivustolle. Erona on se, että nettisivu on suojautunut niin ettei se hyväksy '../' parametrejä.
<img width="1367" height="118" alt="image" src="https://github.com/user-attachments/assets/4b9aaa6f-1727-41ca-998c-321959ed2593" />
<img width="1317" height="376" alt="image" src="https://github.com/user-attachments/assets/efb72371-3b89-41ca-bebe-25a1b60b0afd" />

**H) Lab:File path traversal, traversal sequences stripped non-recursively**
-
- Harjoituksessa nettisivu yrittää suojautua suodattamalla kolme kertaa '../' parametrit mutta kun niitä kirjoittaa kuusi kappaletta, niin nettisivu poistaa niitä kolme, jolloin jäljelle parametrejä jää kolme, eli nettisivu on silti haavoittuvainen
<img width="1261" height="353" alt="image" src="https://github.com/user-attachments/assets/59889052-b2f6-41a7-ac82-fe71ed3e9815" />
<img width="1419" height="105" alt="image" src="https://github.com/user-attachments/assets/b3d3d907-63e7-40b0-9b15-6a224ebe4277" />

**I) Lab: Insecure direct object references**
-
- Harjoituksessa kun lataa chatin tekstitiedoston ja koipioi sen lataulinkin, josta osoiterivissä muuttaa numeron 2 numeroon 1 niin saadaan ladattua piilotettu tekstitiedosto
<img width="687" height="116" alt="image" src="https://github.com/user-attachments/assets/2705cfff-57e5-452e-9ec8-636a680b16d9" />

- Tekstitiedosto sisältää haavoittuvia tietotaja muunmuassa tukijärjestelmän salasanan jota käytetään murtautumisessa
- Harjoituksessa kun kirjatuu käyttäjä nimellä "carlos" ja syöttää tekstitiedoston sisältämän salasanan niin pääsee murtautumaan
<img width="454" height="335" alt="image" src="https://github.com/user-attachments/assets/9fff80cb-f699-43a3-9231-8d3ded6b7ad4" />
