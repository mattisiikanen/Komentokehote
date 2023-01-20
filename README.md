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
Tulos oli seuraavanlainen (kuva1)

Tämä johtuu siitä, että latasin Micro työkalun jo oppitunnin aikana.




## Rauta
17:35
Seuraavaksi tiedossa oli raudan läpikäynti virtuaalikoneella. Kokeilin komentoa sudo lshw -short -sanitize, mutta komentokehote palautti seuraavan tiedon: "sudo: lshw: command not found". Tämä johtuu siis siitä, että jouduin ensin asentamaan kyseisen työkalun koneelle käyttämällä komentoa: sudo apt-get install lshw.
Asennuksen jälkeen koitin uudelleen edellä mainittua komentoa sudo lshw -short -sanitize ja sain seuraavat tulokset: (kuva2)

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

Käytin komentoa "sudo apt-get install terminator terminology gonme-terminal -y" asentaakseni kaikki ohjelmat kerralla.


## Kansioiden esittely FHS:llä
Kokonaisuudessaan asennukseen meni sähellyksineen noin 38 min. Hyper-V virtuaalikoneongelman lisäksi asennuksessa ei ilmennyt muita ongelmia.
Harjoitus oli mielenkiintoinen ja uusi/vanha kokemus, koska en ole koskaan asentanut Debiania, mutta muita Linuxeja kyllä.


## GREP-komennon käyttö

## Lähteet:

Karvinen, Tero: Command Line Basics Revisited
(https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited)

Kesari, Varun: 8 Best Terminal Apps for Enhanced Linux Productivity
https://www.makeuseof.com/best-linux-terminal/
