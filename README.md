# Komentokehote
Tämän tehtävän tarkoituksena oli tehdä opettajan antamia harjoituksia komentokehotteessa.

## Ympäristö

Hyper-V kotikoneella (Host):
- CPU: i5-9600K
- RAM: 16Gb
- HDD: 120Gb
- Win 11 Pro x64

Virtuaalikoneen speksit:
- 2 x CPU
- 4 Gb RAM
- 50 Gb HDD
- Generation 2 (Hyper-V pyytää määrittelemään)

## Micron asennus
Aloitin tehtävän 20.1.2023 klo 17.33 syöttämällä komentoriville seuraavan pätkän: sudo apt-get install micro
Tulos oli seuraavanlainen: </br>
![Kuva1](https://user-images.githubusercontent.com/122887740/213863049-2c372e43-66ab-4436-87d7-c7e7f9cae2b0.png) </br>

Tämä johtuu siitä, että latasin Micro työkalun jo oppitunnin aikana.
Päätin myös testata micro-työkalun käyttöä:</br>
![Kuva1 5](https://user-images.githubusercontent.com/122887740/213882865-2c48da5e-93a6-495a-92f4-8495531eff7d.png)</br>



## Rauta
Klo 17:35 </br>
Seuraavaksi tiedossa oli raudan läpikäynti virtuaalikoneella. Kokeilin komentoa sudo lshw -short -sanitize, mutta komentokehote palautti seuraavan tiedon: "sudo: lshw: command not found". Tämä johtui siitä, että koneella ei ollut kyseistä työkalua ja jouduin asentamaan sen koneelle käyttämällä komentoa: sudo apt-get install lshw.
Asennuksen jälkeen koitin uudelleen edellä mainittua komentoa sudo lshw -short -sanitize ja sain seuraavat tulokset: </br>
![Kuva2](https://user-images.githubusercontent.com/122887740/213863079-0555d014-e513-426b-ab37-d392de00d9a4.png) </br>

Listaus pitää sisällään virtuaalikoneeseen syötetyt tiedot, jotka määriteltiin konetta luotaessa, pois lukien prosessoria, joka on sama kuin fyysisessä raudassa.
- system: toimii järjestelmän luokkana / päätasona.
- bus: seuraava taso päätasosta.
- memory: tämä luokka pitää sisällään muistiin liittyvät tiedot, kuten virtuaalikoneelle konfiguroidun määrän.
- processor: prosessori, jota kone käyttää, tässä tapauksessa se on sama kuin mitä isäntä koneessa on käytössä.
- system: näyttää koneeseen liitetyt PnP (plug&play) laitteet.
- storage: tämä luokka toimii pääkategoriana sekä virtuaaliselle kiintolevylle, partitioille että liikutettaville medioille.
- disk: joko virtuaalinen levyasema, cd/dvd-asema tai muistitikku/kortti
- network: kytketty verkkokortti


## Kolme uutta komentoriviohjelmaa apt komennolla
Klo 17:51 </br>
Kävin aluksi etsimässä komentoriviohjelmia ja törmäsin artikkeliin Varun Kesarin kirjoittamaan artikkeliin otsikolla "Best Terminal Apps for Enhanced Linux Productivity", päädyin käyttämään sitä lähteenä kolmen eri komentoriviohjelman testaukseen. Valitsin seuraavat: </br>
- Terminator
- Terminology
- GNOME Terminal

Käytin komentoa "sudo apt-get install terminator terminology gnome-terminal -y" asentaakseni kaikki ohjelmat kerralla. Hommat jäivät tällä erää tähän 18.00 20.1.2023. </br> </br>

Homma jatkui seuraavana aamuna klo 11.15 21.1.2023.
Ensimmäisenä kokeilin Terminator ohjelmaa, käynnistin ohjelman ja kirjoitin ensimmäisenä komentona help. </br>
![Kuva3](https://user-images.githubusercontent.com/122887740/213863089-946de6a4-d140-4796-a8d6-9a867c2736cd.png) </br>


Ohjeiden perusteella Terminator toimii komentoriviemulaattorina. Tutkiessani tätä enemmän, paljastui Wikipedian artikkelista lisätietoa ja vaikuttaa siltä, että ohjelma on ohjelmoitu käyttäen Java-kieltä. Ulkoasu ohjelmalla on hyvin yksinkertainen ja samannäköinen kuin Debianin sisäänrakennetulla komentokehotteella. </br>

Toinen ohjelma oli nimeltään Terminology, tein ohjelmalle samat testit kuin aiemmin ja ajoin aivan aluksi komennon help. </br>
![Kuva4](https://user-images.githubusercontent.com/122887740/213863099-28c7ef10-51bc-4b98-9246-418d0e9150ea.png) </br>


Terminology osoittautuikin hiukan monipuolisemmaksi, kuin luulin, sillä kyseisellä ohjelmalla pystyy tekstin lisäksi käsittelemään myös ääntä, kuvaa ja animoituja gifejä. Ulkoasukin on myös monipuolisempi ohjelman salliessa eri värejä. Mielenkiintoinen ohjelmisto kokonaisuudessaan.

Viimeisenä oli kokeilussa GNOME Terminal ja se osoittautuikin hyvin perinteisen oloiseksi komentokehotteeksi. </br>
![Kuva5](https://user-images.githubusercontent.com/122887740/213863108-d069852d-6365-4ea3-82ea-f37c349b55ad.png) </br>


Wikipedian mukaan GNOME Terminal on kehitetty GNOME työpöydän rinnalle ja se tarjoaa samat perusmahdollisuudet kuin esimerkiksi Debianin komentokehote.



## Kansioiden esittely (Important Directories)
Klo 11.45 </br>
Aloitin tehtävän menemällä ensin juurikansioon käyttämällä komentoa: cd /

/ (root) - kansiossa käytin komentoja pwd ja ls, sain seuraavat tulokset: </br>
![Kuva6](https://user-images.githubusercontent.com/122887740/213863118-fa60e93f-5943-49de-8389-2483429e2198.png) </br>

Juurikansio on kaikkien kansioiden päätaso, josta pääsee tarvittaessa navigoimaan koneen kaikkiin tiedostoihin. Sen alta löytyy myös seuraavaksi käsiteltävien kansioiden kansiorakenteet.

/home/ - navigoin kyseiseen kansioon root kansiosta kirjoittamalla cd home. Kansiossa ajoin jälleen komennot pwd ja ls. </br>
![Kuva7](https://user-images.githubusercontent.com/122887740/213863126-c236c647-e6fa-4a24-a18b-7b4ef882ed34.png) </br>

Tämä kansio ei tarjonnut paljon tuloksia.

/home/mattis/ - kansio on jatkoa home-kansiolle ja tämä sisältää käyttäjäprofiilin / asetukset. Navigoin tänne käyttämällä jälleen cd komentoa. </br>
![Kuva8](https://user-images.githubusercontent.com/122887740/213863198-f80198c5-158d-4a1b-8b3f-4423b3335f95.png) </br>

Kansiosta löytyi oppitunnin aikana tehty tiedosto testi.md, jonka sisältöä kävin tutkimassa käyttämällä komentoa less testi.md </br>
![Kuva9](https://user-images.githubusercontent.com/122887740/213863205-ea874ee9-f09a-4a27-a7e7-0dd610a175ff.png) </br>

/etc/ - kansio löytyy suoraan root kansion alta.
![Kuva10](https://user-images.githubusercontent.com/122887740/213863221-cd10be23-4180-4a4b-8747-dacb6f4a9dbc.png) </br>

Kansiosta löytyy paljon erilaisia tiedostoja eri tiedostopäätteillä sekä alikansioita. Testasin avata yhden tiedostoista käyttäen less komentoa. </br>
![Kuva11](https://user-images.githubusercontent.com/122887740/213863238-bf78cd75-cbd1-4095-b27d-dd35069ce6a6.png) </br>

Kyseinen tiedosto xattr.conf viittaa ainakin tiedostopäätteen perusteella johonkin konfiguraatioon. Tätä muokkaamalla saa asiaa x konfiguroitua.
Kansio vaikuttaa olevan koti kaikille ohjelmille ja eri asetuksille.

/media/ - kansio on suoraan root kansion juuressa ja tänne tulee kaikki irroitettavat mediat, kuten USB-muistitikut, muistikortit, CD/DVD-levyt. </br>
![Kuva12](https://user-images.githubusercontent.com/122887740/213863250-c4e4cedf-41ca-4feb-ba53-cd032f088bb9.png) </br>


/var/log/ - kansio var on juuressa ja log löytyy var kansion alta. Tämä paikka on ilmiselvästi koti erilaisille lokitiedostoille. </br>
![Kuva13](https://user-images.githubusercontent.com/122887740/213863264-ec98c676-9ecd-4b67-9b38-81271cefd900.png) </br>

Avasin lokitiedoston nimeltä dpkg.log käyttäen less-komentoa. </br>
![Kuva14](https://user-images.githubusercontent.com/122887740/213863271-bfaeb0cf-2aa1-40af-93e2-61e947405cda.png) </br>


## GREP-komennon käyttö
Klo 12.06 </br>
Tätä tehtävää varten etsin aiheesta Internetin syövereistä SATHIYAMOORTHYn nimisen henkilön kirjoittaman artikkelin, jossa on 15 käytännöllistä Grep komentoa. 

Ensimmäisenä kokeilin oppitunnin aikana tehtyyn tiedostoon testi.md ajaa Grep komentoa "grep "tämä" testi.md", eli etsin tämä sanaa tiedostosta ja tuloksena tuli: </br>
![Kuva15](https://user-images.githubusercontent.com/122887740/213863279-3fe74576-1059-43a0-9921-a621ff5c9ad2.png) </br>


Tämä komento etsi vain pelkän tämä sanan ja sisällytti löydökseen myös koko lauseen, jossa tämä sana on.

Seuraavaksi ajoin /var/log kansiossa Grep komennon "grep -iw "configure" dpkg.log" ja sain seuraavat tulokset: </br>
![Kuva16](https://user-images.githubusercontent.com/122887740/213863283-57f8102d-7be6-4b28-b7fa-b51f821603ef.png) </br>


grep -iw komento rajoittaa haun pelkästään syötettyyn sanaan ja näyttää vain tarkasti osuneet rivit käyttäjälle kyseisestä tiedostosta.

Viimeisenä testinä käytin komentoa "grep -A 3 - i "configure" dpkg.log", kyseinen komento tulostaa osumat ja kolme riviä ekstraa: </br>
![Kuva17](https://user-images.githubusercontent.com/122887740/213863285-f437cd02-cfbc-4124-9208-401d8c8bb899.png) </br>


Grep vaikuttaa hyvältä työkalulta, mikäli haluaa tutkia isoja tiedostoja ja kaivaa haluttu data sieltä ulos.

## Lopetus
Kyseinen kotitehtävä avasi paljon komentokehotteen maailmaa Linuxissa. Sen avulla voi selvästi tehdä kaikki toimenpiteet, toki harjoitukset olivat vain pintaraapaisu, mutta kyllä niistä oli itselle ainakin hyötyä. Tehtäviin meni kokonaisuudessaan noin 1,5h.

## Lähteet:

Karvinen, Tero: Command Line Basics Revisited
(https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited)

Kesari, Varun: 8 Best Terminal Apps for Enhanced Linux Productivity
(https://www.makeuseof.com/best-linux-terminal/)

Wikipedia, Terminator (terminal emulator)
(https://en.wikipedia.org/wiki/Terminator_(terminal_emulator))

Enlightenment, Terminology
(https://www.enlightenment.org/about-terminology.md)

Wikipedia, GNOME Terminal
(https://en.wikipedia.org/wiki/GNOME_Terminal)

SATHIYAMOORTHY, 26.3.2009: 15 Practical Grep Command Examples In Linux / UNIX
(https://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/)
