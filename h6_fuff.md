**X) Tiivistä**
- 
**Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf**
- Fuff on brute force tietoturvatarkastukseen suunnattu monipuolinen työkalu 
- Työkalu lähettää automaattisesti suuria määriä HTTP-pyyntöjä kohteeseen sanalistoja hyödyntäen (ei tarvitse itse manuaalisesti kirjoittaa)
- Työkalun avulla voidaan tunnistaa poikkeamia suodattamalla vastauksia, esimerkiksi piilotettujen hakemistojen etsimistä

**a) Fuzzzz. Ratkaise dirfuz-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf.**
- Ensiksi latasin Teron sivuilta halutun tiedoston, annoin sille suoritus oikeudet sekä käynnistin sen:

<img width="920" height="376" alt="image" src="https://github.com/user-attachments/assets/c5a2435e-1f9c-4156-be30-df0e80f98c02" />

- sitten kokeilin että siihen saa yhteyden:

<img width="650" height="196" alt="image" src="https://github.com/user-attachments/assets/8d26b6ef-8cd2-4f0a-abdd-630fd3f77f91" />

- Avasin uuden terminaalin missä suoritin loput tehtävästä. Olin aikaisemmin jos ehtinyt ladata sanalistan

<img width="180" height="62" alt="image" src="https://github.com/user-attachments/assets/e348663e-7f32-4076-aa41-51656e5e8d0a" />

- Ffuf oli myös asennettuna aikaisemmin:

<img width="624" height="130" alt="image" src="https://github.com/user-attachments/assets/795afa49-e680-486b-814a-0b889ba573d8" />

- Ajoin sitten komennon 'ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ', joka antoi hirveän määrän vastauksia minkä koko on 154, sitten filteröin sen pois lisä parametrillä '-fs 154', ja vastaus oli tämä:

<img width="732" height="526" alt="image" src="https://github.com/user-attachments/assets/08abf3a1-7f61-4acc-bd59-f5a395b664f9" />

- Vastauksissa kävi ilmi kohta 'wp-admin', mikä voisi viitata ylläpitoon liittyvään haavoittuvuuteen jota kokeilin selaimessa:

<img width="522" height="190" alt="image" src="https://github.com/user-attachments/assets/8e80c08a-6ed9-4183-baa6-177b3d862fae" />

**b) Fuff me. Asenna FuffMe-harjoitusmaali. Karvinen 2023: Fuffme - Install Web Fuzzing Target on Debian**
- asensin ffufme:n, loin harjoitus kohde dockerin, käynnistin kohteen ja kokeilin että se toimii ilman ongelmia:

<img width="818" height="240" alt="image" src="https://github.com/user-attachments/assets/1468bb5a-d33f-40b3-8899-12eeb703065f" />

**c) Basic Content Discovery**
- Sitten asensin kaikki sanalistat ilman ongelmia, jonka jälkeen virtualboxista irrotin Kalin muusta verkosta ja kokeilin ffufia:

<img width="734" height="432" alt="image" src="https://github.com/user-attachments/assets/f3cfcabc-59c3-417c-96e4-d14dc773e331" />

- Ffuf antoi vastauksiksi 'class' ja 'development.log', ja kun ne lisäsi url osoitteeseen niin päästiin tavoitteeseen:

<img width="558" height="102" alt="image" src="https://github.com/user-attachments/assets/10fe79a6-6586-4b72-b88f-07fb40a490b2" />

<img width="642" height="104" alt="image" src="https://github.com/user-attachments/assets/7777b7b8-d3e1-46f5-a933-f4780a5cab3b" />

**d) Content Discovery With Recursion**
- Ensiksi ajoin komennon 'ffuf -w $HOME/wordlists/common.txt -u http://localhost/cd/recursion/FUZZ' mikä antoi vastaukseksi 'admin', kun lisäsin samaan komentoon 'recursio' parametrin '/admin' jne, kunnes lopullinen url-osoite oli 'http://localhost/cd/recursion/admin/users/96':

<img width="658" height="104" alt="image" src="https://github.com/user-attachments/assets/3eb10557-9fd5-4fd0-ad63-0c0a46a7a87d" />

<img width="718" height="412" alt="image" src="https://github.com/user-attachments/assets/0e18554a-2571-4e72-a3c8-34f75e2260ec" />

**e) Content Discovery With File Extensions**
- Ajoin komennon 'ffuf -w $HOME/wordlists/common.txt -u http://localhost/cd/ext/FUZZ', mikä antoi tuloksena 'logs', jonka liitin aikasemman komennon perään:

<img width="732" height="406" alt="image" src="https://github.com/user-attachments/assets/06fa6c2d-108b-463c-8acf-9756bf8e0823" />

- Komento ei enään antanutkaan vastausta. Kokeilin lisätä komentoon '-e' jonka perään lisäsin eri tieodostopäätteitä, lopulta komento oli 'ffuf -w $HOME/wordlists/common.txt -u http://localhost/cd/ext/logs/FUZZ -e .log,.txt,.php,.bak', millä sain vastaukseksi 'users.log' mikä toimi. '-e' on lisäparametri, minkä avulla ffuf etsii urlista myös annettuiden tiedostopäätteiden avulla poikkeamia.

<img width="604" height="100" alt="image" src="https://github.com/user-attachments/assets/dbb05e05-5b0b-4053-9e7e-70190368013f" />

Lähde: https://github.com/ffuf/ffuf#usage (Luettu 28.9.2026)

**f) No 404 Status**
- Kirjoitin komennon 'ffuf -w $HOME/wordlists/common.txt -u http://localhost/cd/no404/FUZZ' jolloin sain suuren määrän vastauksia joiden koko oli 669, joten filteröin sen pois parametrillä '-fs 669' jonka jälkeen sain vastauksen 'secret':
  
<img width="726" height="426" alt="image" src="https://github.com/user-attachments/assets/b1f5c6e7-6a88-426b-81b6-0f3cf575ec16" />

<img width="574" height="108" alt="image" src="https://github.com/user-attachments/assets/70f09517-2839-43d0-8b6b-fcc3c066f2fb" />

**g) Param Mining**
- Liitin 'http://localhost/cd/param' sivulla löytyvän url-osoitteen terminaaliin mikä antoi vastauksen 'debug', vaihdoin url-osoitteesta FUZZ ja lisäsin sen tilalle annetun vastauksen:

<img width="636" height="108" alt="image" src="https://github.com/user-attachments/assets/71673bb8-b079-4eb8-a8ff-8c7bfefc4fe9" />

<img width="718" height="420" alt="image" src="https://github.com/user-attachments/assets/5c03e0fe-c22e-4946-9968-794cbcfc6dfc" />

**h) Rate Limited**
- Sivulle on lisätty enimmäismäärä mitä voi llähettää HTTP-pyyntöjä jolloin sivulla annettu 'ffuf -w ~/wordlists/common.txt -u http://ffuf.test/cd/rate/FUZZ -mc 200,429' -komento antaa vain erroria,on laskettava HTTP-pyyntöjen määrä per sekunti on laskettava joten täytyy antaa parametri '-p 0.1', mikä pitää tauon aina 0.1 sekuntia aina pyynnön jälkeen, lisätään myös parametri '-t 5', mikä luo 5 eri versiota ffufia, mikä tarkoittaa maksimimäärää 50 pyyntöä per sekunti.

<img width="734" height="432" alt="image" src="https://github.com/user-attachments/assets/e75719ae-3456-436b-86bf-d03dee179121" />

<img width="572" height="112" alt="image" src="https://github.com/user-attachments/assets/e46e0f55-e1c2-4702-af9c-4fbe7f1708b5" />

- Lähde: Content Discovery - Rate Limited (http://localhost/cd/rate)

**i) Subdomains - Virtual Host Enumeration**
- Tehtävässä annettu komento 'seq 1 1000 | ffuf -w - -u http://localhost/cd/pipes/user?id=FUZZ' antaa vastaukseksi '657', mikä viittaa siihen että oikeat vastaukset on hashattu joko base64 tai md5 koodatun hashin taakse joten täytyy luoda oma bash scripti ja antaa sille ajo oikeudet:
  
<img width="456" height="284" alt="image" src="https://github.com/user-attachments/assets/c88439df-f7dc-4fe7-a3ed-8a78878b7422" />


- Nyt kun skriptille annetaan ffufin antama hash, niin se ajaa hashin skriptin lävitse mikä muuttaa sen base64 tai md5 muotoon:

<img width="736" height="418" alt="image" src="https://github.com/user-attachments/assets/ea3d2353-cdf4-42e6-9138-6c8bf3ebcad1" />

- Vastauksena sain 'ODg4' ja kun sen liitin URL-osoitteeseen 'iser2?id=':n kanssa niin päästiin läpi:

<img width="730" height="414" alt="image" src="https://github.com/user-attachments/assets/e22b4889-8c1a-4ea3-a55c-732e32e5b573" />


<img width="634" height="112" alt="image" src="https://github.com/user-attachments/assets/230b50db-1152-496b-92b3-544bfe699259" />


- Kun ajoin komennon 'md5' skriptillä niin vastauksena sain oikean hashin jonka liitin URL-osoitteeseen 'user3?id=':n kanssa:

<img width="750" height="416" alt="image" src="https://github.com/user-attachments/assets/af8e773a-5669-4417-aac9-ab18a7b98cc2" />


<img width="746" height="104" alt="image" src="https://github.com/user-attachments/assets/583d4c67-aad0-4b94-b4bc-a17b2f2044bc" />
