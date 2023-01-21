# Komentokehote
Tämän tehtävän tarkoituksena oli tehdä opettajan antamia harjoituksia komentokehotteessa

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
Aloitin tehtävän 20.1.2023 klo 17.33 syöttämällä komentoriville seuraavan pätkän: sudo apt-get install micro.
Tulos oli seuraavanlainen ![Add file: Upload](Kuva 1.png) </br>

Tämä johtuu siitä, että latasin Micro työkalun jo oppitunnin aikana.


## Rauta
17:35
Seuraavaksi tiedossa oli raudan läpikäynti virtuaalikoneella. Kokeilin komentoa sudo lshw -short -sanitize, mutta komentokehote palautti seuraavan tiedon: "sudo: lshw: command not found". Tämä johtuu siis siitä, että jouduin ensin asentamaan kyseisen työkalun koneelle käyttämällä komentoa: sudo apt-get install lshw.
Asennuksen jälkeen koitin uudelleen edellä mainittua komentoa sudo lshw -short -sanitize ja sain seuraavat tulokset: ![Add file: Upload](Kuva 2.png) </br>

Listaus pitää sisällään virtuaalikoneeseen syötetyt tiedot, jotka määriteltiin konetta luotaessa, pois lukien prosessoria, joka on sama kuin fyysisessä raudassa.
- system: toimii järjestelmän luokkana / päätasona.
- bus: seuraava taso päätasosta.
- memory: tämä luokka pitää sisällään muistiin liittyvät tiedot, kuten koneelle asetetun määrän.
- processor: prosessori, jota kone käyttää, tässä tapauksessa se on sama kuin mitä isäntä koneessa on käytössä.
- system: näyttää siihen koneeseen kiinnitetyt PnP (plug&play) laitteet.
- storage: tämä luokka toimii pääkategoriana sekä virtuaaliselle kiintolevylle, partitioille ja liikutettaville medioille.
- disk: joko virtuaalinen levyasema, cd/dvd-asema tai muistitikku/kortti
- network: kytketty verkkokortti


## Kolme uutta komentoriviohjelmaa apt komennolla
17:51
Kävin aluksi etsimässä komentoriviohjelmia ja törmäsin artikkeliin Varun Kesarin kirjoittamaan artikkeliin otsikolla "Best Terminal Apps for Enhanced Linux Productivity", päädyin käyttämään sitä lähteenä kolmen eri komentoriviohjelman testaukseen. Valitsin seuraavat:
- Terminator
- Terminology
- GNOME Terminal

Käytin komentoa "sudo apt-get install terminator terminology gnome-terminal -y" asentaakseni kaikki ohjelmat kerralla. Hommat jäivät tällä erää tähän 18.00, jatkuu huomenna.

Homma jatkui seuraavana aamuna 11.15.
Ensimmäisenä kokeilin Terminator ohjelmaa, käynnistin ohjelman ja kirjoitin ensimmäisenä komentona help.
![Add file: Upload](Kuva 3.png) </br>

Ohjeiden perusteella terminator toimii komentoriviemulaattorina. Tutkiessani tätä enemmän paljastui Wikipedian artikkelista lisätietoa ja vaikuttaa siltä, että ohjelma on ohjelmoitu käyttäen Javakieltä. Ulkoasu ohjelmalla on hyvin yksinkertainen ja samannäköinen kuin Debianin sisäänrakennetulla komentokehotteella.

Toinen ohjelma oli nimeltään Terminology, tein samat testit tässä ja ajoin aivan aluksi komennon help.
![Add file: Upload](Kuva 4.png) </br>

Tämä ohjelma osoittautuikin hiukan monipuolisemmaksi, sillä kyseisellä ohjelmalla pystyy tekstin lisäksi käsittelemään myös ääntä, kuvaa ja animoituja gifejä.
Ulkoasukin on myös monipuolisempi ohjelman salliessa eri värejä. Mielenkiintoinen ohjelmisto kokonaisuudessaan.

Viimeisenä oli kokeilussa GNOME Terminal ja se osoittautuikin hyvin perinteisen oloiseksi komentokehotteeksi.
![Add file: Upload](Kuva 5.png) </br>

Wikipedian mukaan kyseessä on GNOME Terminal on kehitetty GNOME työpöydän rinnalle ja se tarjoaa samat perusmahdollisuudet kuin esimerkiksi Debianin komentokehote.



## Kansioiden esittely (Important Directories)
11.45
Aloitin tämän tehtävän menemällä ensin root kansioon käyttämällä cd .. komentoa niin kauan kunnes kehotteessa luki /$

/ (root) - kansiossa käytin komentoja pwd ja ls, sain seuraavat tulokset:
![Add file: Upload](Kuva 6.png) </br>

Root kansio on kaikkien alikansioiden päätaso, josta pääsee tarvittaessa navigoimaan koneen kaikkiin tiedostoihin. Sen alta löytyy myös tulevien kansiorakenteiden kansiot.

/home/ - navigoin kyseiseen kansioon root kansiosta kirjoittamalla cd home. Kansiossa ajoin jälleen komennot pwd ja ls.
![Add file: Upload](Kuva 7.png) </br>

Tämä kansio ei tarjonnut paljon tuloksia.

/home/mattis/ - kansio on jatkoa home-kansiolle ja tämä sisältää käyttäjäprofiilin / asetukset. Navigoin tänne käyttämällä jälleen cd komentoa.
![Add file: Upload](Kuva 8.png) </br>

Kansiosta löytyi oppitunnin aikana tehty tiedosto testi.md, jonka sisältöä kävin tutkimassa käyttämällä komentoa less testi.md
![Add file: Upload](Kuva 9.png) </br>

/etc/ - kansio löytyy suoraan root kansion alta. ![Add file: Upload](Kuva 10.png) </br>

Kansiosta löytyy paljon erilaisia tiedostoja eri tiedostopäätteillä sekä kansioita. Testasin avata yhden tiedostoista käyttäen less komentoa.
![Add file: Upload](Kuva 11.png) </br>

Kyseinen tiedosto xattr.conf viittaa ainakin tiedostopäätteen perusteella johonkin konfiguraatioon. Tätä muokkaamalla saa asiaa x konfiguroitua.
Kansio vaikuttaa olevan koti kaikille ohjelmille ja eri asetuksille.

/media/ - kansio on suoraan root kansion juuressa ja tänne tulee kaikki irroitettavat mediat, kuten USB-muistitikut, muistikortit, CD/DVD-levyt.
![Add file: Upload](Kuva 12.png) </br>

/var/log/ - kansio var on juuressa ja log löytyy var kansion alta. Tämä paikka on ilmiselvästi koti erilaisille lokitiedostoille
![Add file: Upload](Kuva 13.png) </br>

Avasin lokitiedoston nimeltä dpkg.log käyttäen less-komentoa.

![Add file: Upload](Kuva 14.png) </br>



## GREP-komennon käyttö
12.06
Tätä tehtävää varten etsin aiheesta Internetin syövereistä SATHIYAMOORTHYn nimisen henkilön kirjoittaman artikkelin, jossa on 15 käytännöllistä Grep komentoa. 

Ensimmäisenä kokeilin oppitunnin aikana tehtyyn tiedostoon testi.md ajaa Grep komentoa "grep "tämä" testi.md", eli etsin tämä sanaa tiedostosta ja tuloksena tuli:
![Add file: Upload](Kuva 15.png) </br>

Tämä komento etsi vain pelkän tämä sanan ja sisällytti löydökseen myös koko lauseen, jossa tämä sana on.

Seuraavaksi ajoin /var/log kansiossa Grep komennon "grep -iw "configure" dpkg.log" ja sain seuraavat tulokset:
![Add file: Upload](Kuva 16.png) </br>

grep -iw komento rajoittaa haun pelkästään syötettyyn sanaan ja näyttää vain tarkasti osuneet rivit käyttäjälle kyseisestä tiedostosta.

Viimeisenä testinä käytin komentoa "grep -A 3 - i "configure" dpkg.log", kyseinen komento tulostaa osumat ja kolme riviä ekstraa:
![Add file: Upload](Kuva 17.png) </br>

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
