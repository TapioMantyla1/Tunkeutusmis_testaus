x) Podcastin kuuntelu:
- Kuuntelin podcastin: Herrasmieshakkerit, jakso "Demokratian suojelija, vieraana Ahti Kurvinen | 0x1f" 6.7.2022
- Podcast jaksossa vetäjät puhuvat siitä kuinka lunnastroijalaiset virukset ovat muuttuneet aggressiivisemmaksi sekä vaarallisemmaksi. Hyökkääjät tekevät tietomurtoja joiden avulla kiristävät tiedonomistajia rahaa vastaan.
- Podcastin viereena oleva Ahti Kurvinen on valtioneuvoston turvallisuusjohtaja sekä valtioneuvoston valmiusyksikön johtaja.
- Kurvinen luettelee kuinka he takaavat ministereiden turvallisuuden. Tietoturvallisuuden he takaavat esimerkiksi kouluttamalla ministereitä oikeanlaiseen tietojen käsittelyyn.
- Kurvisen mielestä pestin aikana yksi vaikein tehtävä oli korona pandemia aika, jolloin he joutuivat turvaamaan ministereiden turvallisuutta kaikin keinoin muunmuassa itse virukselta.
- Toinen haastava hetki oli kun yhdysvallat vetäytyi Afganistanista jolloin he juotuivat evakuoimaan maasta suomalaiset diplomaatit sekä suomenkansalaisia.
- Kysymys: Olisi mielenkiintoista tietää mitä valmiusyksikössä konkreettisesti tekevät aktiivisen kyberhyökkäyksen aikana.

Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains 2011: 
- Artikkelissa kerrotaan että puolustuksen pitäisi perustua tiedusteluun ja ymmärtää kuka hyökkää, miten hyökkää ja mitä vastaan.
- Cyber kill chain jakautuu seitsemään eri vaiheeseen: tiedustelu > aseistaminen > toimitus > hyväksikäyttö > asennus > komenna ja kontrolloi > tavoitteiden varmistaminen
- Puolustajalla on etu ketjumallissa: Hyökkääjän on onnistuttava ketjun jokaisessa vaiheessa päästäkseen tavoitteeseen, kun taas puolustajan on havaittava ja tuhottava hyökkäys vain kerran.
- Jokaisesta tulevasta hyökkäyksestä/hyökkäysyrityksestä saadaan lisää tietoa sekä indikaattoreita tulevia hyökkäyksiä varten.

Surveying Essential Tools for Active Reconnaissance (video) 4.2019:
- Aktiivisessa tiedustelussa lähetetään paketteja kohde tietoverkkoon: porttiskannaus, verkkopalvelun arviointi sekä havoittuvuuden skannaus (asioista jotka saattavat herättää hälytyksiä)
- Ohjelmia: aikaisempiin tehtäviin suosituin ohjelma on nmap, jos portteja on paljon skannattavana niin nopein ohjelma on Masscan
- Esimerkki komento porttiskannaukseen: nmap -sS -vv -T4 -A
- jos verkkopalveluja on paljon niin niiden arviointiin hyvä ohjelma on EyeWitness koska se skannaa verkkopalvelut ja priorisoi ne puolestasi
- Huomio: olisi hyvä tietää miten näitä vastaan voi puolustatua

KKO 2003:36 8.4.2003:
- Artikkelissa kerrotaan kuinka 17-vuotias porttiskannasi pankin tietojärjestelmiä luvatta
- Palomuuri oli estänyt yrityksen joten teko jäi tietomurron yritykseksi
- Syytetty määrättiin maksamaan vahingonkorvauksia 110 000 markkaa.
Huomio: artikkeli on mielenkiintoinen ja antaa osviittaa siitä, miten varovainen ja tietoinen täytyy olla kun itse aiheen ympärillä käytännössä toimii

a) 
- Kali Linuxin lataamisessa, asentamisessa ja sen avaamisessa ei ollut mitään vaikeuksia. Kalin asensin heidän viralliselta verkkosivulta, samalla asennuksella latasin VirtualBoxin, versio on 2026.2

b)
- Poistin Kalin verkosta Virtualboxin asetuksista:

<img width="856" height="727" alt="image" src="https://github.com/user-attachments/assets/1f44db10-75db-4a77-ae35-bef80a41f89b" />

<img width="306" height="185" alt="image" src="https://github.com/user-attachments/assets/11624ade-2d24-4830-9b10-251734883788" />


c)

- Komento "nmap" avaa porttiskannaus ohjelman, komento "-T4" skannaa portit nopeammin, komento "-A" on aggressiivinen skannaus sekä "localhost" on osoite josta skannataan.

<img width="626" height="246" alt="image" src="https://github.com/user-attachments/assets/ea311b37-dd38-4a91-a2e0-1929de381c7a" />

- kaikki portit ovat kiinni
- asensin Apache2 sekä Openssh:n

<img width="639" height="139" alt="image" src="https://github.com/user-attachments/assets/64dcc0d4-104a-4130-8ad6-5621bd6c361b" />

- kun yritin uudelleen skannata localhostilla niin ei onnistunut
- mutta kun kirjoitin suoran ip:n niin vastaus muuttui ja asennetut daemonit ovat auki:

<img width="661" height="600" alt="image" src="https://github.com/user-attachments/assets/4dcbaaec-e831-419e-867b-1c475cf62f73" />

- Portit saisi kiinnii komennolla sudo systemctl stop (daemon)

d) HackTheBox
- Valitsin HackTheBoxista "Fawn" koneen koska olen aloittelija. Sain suoritettua kyseisen koneen mutta ei ongelmitta. Ongelmia oli löytää koneen loppupäässä kysyttävää FTP flagia, mutta sivuille olevan videon opastuksella sain sen suoritettua:

<img width="1383" height="224" alt="image" src="https://github.com/user-attachments/assets/d12378a1-960f-4f6e-bcc1-817e03f2530c" />

Lähteet:
- Hack The Box: https://app.hackthebox.com/machines/Fawn?sort_by=created_at&sort_type=desc
- How to get started in cybersecurity: HTB Labs - Episode #3: https://www.youtube.com/watch?v=xWP2Jw5Yiio
- Tero Karvinen laksu: https://terokarvinen.com/tunkeutumistestaus/#laksyt
