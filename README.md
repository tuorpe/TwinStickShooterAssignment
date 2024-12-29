# TwinStick Shooter
## Tietoa
Tämä projekti on toteutettu Peliohjelmointi-kurssin toiseksi palautustyöksi. Kävimme tunneilla läpi tutoriaalin TwinStick Shooter-pelin prototyypin tekoon, josta sitten jatkoimme itsenäisesti projektin saattamisen täysin pelattavaksi paketiksi.

Pelissä on hahmo kuvattu yläviistosta. Hahmo asetetaan pelikentälle, jossa hahmo saa vastaansa robottimaisia puhelinliittymämyyjiä, jotka hyökkäävät pelaajaa kohti saaden vahinkoa aikaan pelaajassa. 

Hahmolla on toisin kuin oikeassa elämässä, useampia elämiä mahdollista antaa myyjille sitä mitä ne ansaitsevat....kasan lasersäteitä.

Kuten oikeassakin elämässä, valitettavasti myyjien määrä ei lopu, vaan niitä tulee aina vain enemmän ja pelin edetessä myyjiä ilmaantuu jatkuvalla tahdilla enemmän. 
## Asennus
* Lataa paketti
* Avaa Unreal v. 5.2.1.
* Klikkaamalla Browse-näppäintä, aukeaa tiedostonavauksen ikkuna, jolla voit avata Unreal projektitiedoston (TwinStickShooter.uproject).

## Kontrollit

* Peliä voidaan ohjata sekä näppäimistöllä että ohjaimella.
* Näppäimistöllä:
	* WASD ohjaa pelaajan katsomissuuntaa ja samalla ampumista.
	* Nuolinäppäimet liikuttavat hahmoa.
	* P- ja ESC-näppäintä käyttämällä saa pelin pysäytettyä.
	
* Ohjaimella:
	* Vasen tatti ohjaa pelihahmon liikettä.
	* Oikea tatti muuttaa pelaajan katseen suuntaa ja ampumista.
	* Valitettavasti ajanpuutteen ja osaamattomuuden vuoksi valikoihin ei pääse ohjaimella ja valikon napit reagoivat ainoastaan hiiren klikkauksiin.
## Projektin rakenne

* Projekti koostuu kolmesta tasosta: MainMenu, TwinstickArena ja GameOverMenu:sta.
### MainMenu

* Alkuvalikko, jossa pelaaja voi aloittaa pelin tai poistua pelistä.
### TwinStickArena

* Varsinainen pelitaso.
* Pelaaja asetetaan alkupaikalle
* Pelaajaa kohti lähtee tulemaan liittymämyyjärobotteja, joiden lahtaamisesta saa pisteitä.

### GameOverMenu

* Pelaajalta loppuessa elämät, päädytään loppuvalikkoon, jossa esitetään saavutetut pisteet.
* Pelaajalla on mahdollista yrittää pelata uudelleen tai palata takaisin päävalikkoon.

## Tekninen kuvaus

* Tämä projekti oli allekirjoittaneelle ensimmäinen "valmiiksi" saatettu Unreal-pelimoottorilla tehty projekti, jossa tuli itse kehitettyä ratkaisuja. Tästä syystä välttämättä kaikki ratkaisut eivät varmasti ole ylläpidon kannalta helposti tehtyjä, kun suurin ongelma itsellä oli ihan ylipäätänsä hahmottaminen mitä kaikkea voikaan tehdä ja miten.
* Pääosin pyrin pitämään toiminnallisuudet siellä, jossa ne oletin loogisesti sijaitsevan. Esimerkiksi valikon nappien ohjaukset ovat valikoiden blueprinteissä, poislukien Pause-valikkoa, joka piti tehdä TwinStickMode-blueprintissä. 
* Tasojen omissa blueprinteissä hoidetaan asiat, jotka UI-elementtien näyttäminen vaatii, eli UI-elementtien näyttäminen ja kontrollien siirtäminen joko hiirelle tai näppäimistölle.
* Tasojen siirto tapahtuu seuraamalla eliminoitujen vihollisten määrää. Kun 10 vihollista on eliminoitu, siirtyy taso seuraavaan, jolloin mahdollistuu yksi enemmän vihollista kentällä.
* Pisteitä kerätään myös tutkimalla eliminoitujen vihollisten määrää.
* Jos viholliset saavat tarpeeksi vahinkoa aikaiseksi sankariin. kuolee sankari, yksi elämä vähennetään ja jos elämiä oli vielä jäljellä, pelaaja palautetaan lähtöpisteeseen ja peli jatkuu siitä mihin kuollessa jäi. Elämien loputtua, siirrytään GameOverMenuun.
* Pelin pisteet siirretään TwinStickArena-tasosta GameOverMenu-tasoon käyttämällä BP_myGameInstancea (ja siellä Score-muuttujaa), joka ei katoa tasojen hyppimisien välillä. 

## Omat kokemukset projektista

Kuten yllä oli mainittu, oli tämä haastava projekti itselle, koska kokemusta Unreal-pelimoottorista ei ollut. Asiat editorissa ovat itselle totutusta poikkeavissa paikoissa, ohjeita etsiessä versioiden välillä voi ulkoasu olla suuresti muuttunut ja blueprint:n kautta ohjelmointi osoittautui hieman totuttelua vaativaksi. Toki itsellä on kokemusta node-tyylisestä ohjelmoinnista ennenkin, mutta selvittely millaisia asioita löytyy ja jossain määrin ymmärtäminen mitä vaaditaan esim. eri blueprint-ohjelmaosuuksien välillä komuunikoinnissa vaati hieman paneutumista.
Lisäksi koska käytimme melkoisen vanhaa tutoriaalia ja tahti siinä oli nopeaa, monet osa-alueet jäivät itselle hieman epäselviksi, miksi asioita tehdään niin kuin asiat tehtiin ja miten kannattaa asioita ehkä tehdä. Lopun viilauksien aikana opin monta uutta taitoa Unreal:n kanssa, mutta vielä osaaminen on hataralla tasolla. Uusia projekteja odotellessa.