---
layout: site_page
title: Yhteenveto
permalink: /yhteenveto/index.html 
---

Tällä kurssilla on käsitelty perustason tekniikoita, joilla voidaan tuottaa web-sovelluksia. Karkealla tasolla tällaisten sovellusten käyttöympäristöä voidaan esittää alla olevalla kaaviolla.


![kuva-1]({{site.baseurl}}/img/summary-1.png "kuva-1"){: style="max-width: 400px; height: auto; display: block; margin: auto;"}

<small>Kuva 1.</small> 


[Web-sovellusten][application] käyttöliittymänä toimii [selain][browser], joka tekee [HTTP][HTTP]-muotoisia pyyntöjä [web-palvelimelle][palvelin]. Pyynnön lähtökohtana voi olla esim. se, että käyttäjä kirjoittaa selaimen osoitekenttään web-sivun [URL][URL]-osoitteen. Käyttöympäristössä selain ja palvelin sijaitsevat tyylillisesti eri laitteissa, mutta sovelluksia kehitettäessä näitä ajetaan usein samassa laitteessa.

Kurssin tehtäviin liittyen web-sovellus käynnistettiin useimmiten [NetBeans][NetBeans]-kehitysympäristöstä käsin. Tällön NetBeans käynnisti sisältämänsä, kehitystyöhön tarkoitetun, web-palvelimen ja asetusten osoittaman web-selaimen (esim. [Firefox][Firefox]) sekä ohjasi selainta tekemään palvelimelle sovellukseen liittyvä pyyntö. 


[application]: https://en.wikipedia.org/wiki/Web_application
[browser]: https://en.wikipedia.org/wiki/Web_browser
[HTTP]: https://fi.wikipedia.org/wiki/HTTP
[palvelin]: https://fi.wikipedia.org/wiki/WWW-palvelin
[URL]: https://fi.wikipedia.org/wiki/URI
[Firefox]: https://www.mozilla.org/fi/
[NetBeans]: https://netbeans.org/


#### Selainpäässä tulkittava koodi: HTLM, CSS, JS


Tyypillinen vaste palvelimelle tehtävään pyyntöön on [HTML][HTML]-dokumentti. HTML on merkkauskieli, jolla määritellään selaimessa esitettävän web-sivun *rakenne* ja *sisältö*. Vastaanottaessaan palvelimelta HTML-dokumentin selain hahmontaa siitä selaimen ikkunassa esitettävän näkymän. HTML-elementteillä on tietty oletusarvoinen *ulkoasu*, mutta se on myös täysin määriteltävissä erillisellä tyylien kuvauskielellä: [CSS][CSS]. Tyylikuvauksia voidaan laatia osaksi HTML-dokumenttia ja erillisiin tyylitiedostoihin.


[HTML]: https://fi.wikipedia.org/wiki/HTML
[CSS]: https://fi.wikipedia.org/wiki/CSS


HTML-merkkauksen ja tyylimääreiden lisäksi selain tulkitsee [JavaScript][JavaScript] -ohjelmakoodia, jota CSS:n tapaan voidaan kirjoittaa HTML-dokumentiin tai erillisiin kooditiedostoihin. Koodia suoritetaan yleensä reagointina erilaisiin tapahtumiin. Esimerkki usein esiintyvästä tapahtumasta on klikkaus hiirellä selaimen esittämässä näkymässä olevaa elementtiä. JavaScriptin avulla voi myös muokata selaimessa olevaa dokumenttia erityisen [DOM][DOM]-rajapinnan kautta. JavaScript muistuttaa syntaksiltaan suuresti Javaa, mutta näiden kielten olioperiaatteet poikkeavat suhteellisen paljon toisistaan. 


[JavaScript]: https://fi.wikipedia.org/wiki/JavaScript
[DOM]: https://fi.wikipedia.org/wiki/Document_Object_Model


#### Palvelinpään ohjelmoinnista


Web-sovellusten ohjelmakoodia suoritetaan selaimen ohella myös palvelimella. Tällä kurssilla palvelinpään ohjelmontikielenä on ollut [PHP][PHP], joka on yksi yleisimmistä web-ohjelmoinnissa käytetyistä kielistä. Kun selaimella kohdistetaan pyyntö palvelimella olevaan PHP-kieliseen ohjelmaan, palvelin ei palauta vasteena tuota ohjelmatiedostoa vaan suorittaa ohjelman ja palauttaa selaimelle ohjelman aikaansaaman tulosteen.

Ohjelmakoodin suoritaminen palvelinpäässä edellyttää tähän kykenevää web-palvelinta. PHP-tulkin uudemmat versiot sisältävät kehitystyöhön soveltuvan web-palvelimen, jota myös hyödynnettiin tämän kurssin tehtäviä ratkaistaessa. NetBeansin PHP-projektit asetettiin siten, että sovellusta käynnistettäessä NetBeans käynnisti PHP:n ja selaimen sekä ohjasi selainta tekemään sovellukseen liittyvän pyynnön web-palvelimena toimivalle PHP-tulkille.


[PHP]: https://fi.wikipedia.org/wiki/PHP


Selain voi välittää tietoja palvelinpäässä ajettavalle ohjelmalle [pyynnön parametrien][query_string] avulla. HTML sisältää datan välittämiseen myös lomake -elementin, [form][tag_form], jonka attribuutilla voidaan määritellä [metodi][http-method], jolla pyyntö välitetään palvelimelle. Jos käytetään *GET* -metodia, data välittyy pyynnön parametreina, mutta *POST*-metodia käytettäessä data on sanoman sisältönä. Yleinen sääntö on, että *GET* -metodilla viitatut palvelut eivät tee muutoksia palvelimella ylläpidettäviin tietoihin. 

Monet palvelimelta tietoja lukevat PHP-ohjelmat sisältävät enimmäkseen HTML-koodia. Hyvä käytäntö on, että HTML-koodia ei tulosteta PHP-lauseilla vaan (mahdollisuuksien mukaan) kaikki HTML-koodi on PHP-tagien ulkopuolella (ks. *Listaus 1*).


{% highlight php %}

<?php foreach ($items as $item): ?>
    <li>
        <form action="php/doDelete.php" method="post">
            <input type="hidden" name="index" value="<?= $item['id'] ?>" />
            <input type="submit" value="Delete" />
        </form>
        <?= $item['task'] ?>
    </li>
<?php endforeach; ?>

{% endhighlight %}

<small>Listaus 1.</small>


*Listauksen 1* esimerkissä ainoastaan silmukkarkenne (`foreach`) ja viittaukset silmukkamuuttujaan (`$item`) on ilmaistu PHP:llä. HTML-koodi on PHP-tagien ulkopuolella, jolloin esim. editori pystyy ohjaamaan kelvollisen HTML-syntaksin käyttöön.

Kurssin tehtävissä tietoja ylläpitävien PHP-ohjelmien osalta hahmoteltiin seuraavanlaista [periaatetta][post-redirect-get]: 


[post-redirect-get]: https://en.wikipedia.org/wiki/Post/Redirect/Get


![kuva-2]({{site.baseurl}}/img/summary-3.png "kuva-2"){: style="max-width: 400px; height: auto; display: block; margin: auto;"}

<small>Kuva 2.</small> 


*Kuvassa 2* POST-pyynnön seurauksena toteutettava palvelu ei palauta selaimelle seuraavaksi selaimessa esitettävää dokumenttia vaan ohjeen, mihin osoitteeseen selaimen tulisi tehdä GET-pyyntö dokumentin saamiseksi. 


[query_string]: https://en.wikipedia.org/wiki/Query_string
[tag_form]: https://www.w3schools.com/tags/tag_form.asp
[http-method]: https://www.w3schools.com/tags/ref_httpmethods.asp


#### Evästeet ja istunnot


Selaimen palvelimelle tekemät pyynnöt ovat toisistaan erillisiä. Pyynnöstä toiseen voidaan kuitenkin välittää tietoja käyttäen [evästeitä][evaste] (cookie), jotka ovat selaipäähän talletettavia avain-arvopareja. *Kuvassa 3* palvelimella suoritettava ohjelma asettaa evästeen, joka siirtyy vasteen mukana selaimelle. Kun selain tekee uuden pyynnön samalle sivustolle, eväste kulkeutuu pyynnön mukana palvelimelle.


[evaste]: https://fi.wikipedia.org/wiki/Eväste


![Cookie]({{site.baseurl}}/img/summary-cookie.png "Cookie"){: style="max-width: 400px; height: auto; display: block; margin: auto;"}

<small>Kuva 3.</small> 


Pyynnöstä toiseen voidaa välittää tietoja myös hyödyntämällä [istuntoja][session] (session), joihin liittyvä data talletetaan palvelimelle. Tällöin istunnon tunnus välittyy selaimelle evästeen avulla. Kurssin tehtävissä esiintyi tilanne, jossa sovellukseen kirjautuneen käyttäjän tunnus tallennettiin istuntoon ja viimeisin kirjautumisajankohta evästeeseen.


[session]: https://www.w3schools.com/php/php_sessions.asp


#### Tietokanta 

Selaimen ja web-palvelimen ohella web-sovelluksissa esiintyy usein myös kolmas komponentti, tietokanta (*Kuva 4*). Tällöin esimerkiksi web-sivulla esitettävät tiedot luetaan tietokannasta ja sivuilla olevien lomakkeiden avulla kerättävät tiedot talletetaan tietokantaan. Tietokanta voi sijaita samassa laiteessa web-palvelimen kanssa tai erillisessä tietokantapalvelimessa.


![Tietokanta]({{site.baseurl}}/img/summary-db.png "Tietokanta"){: style="max-width: 600px; height: auto; display: block; margin: auto;"}

<small>Kuva 4.</small> 


Tällä kurssilla esimerkkinä oli [SQLite][SQLite]-relaatiotietokanta, johon ei liity erillistä palvelinohjelmistoa. Tietokannan käyttö tapahtui PHP:n [PDO][PDO]-rajapinnan (PHP Data Objects) kautta, minkä yhteydessä oli esillä myös hieman kielen tarjoamia oliopiirteitä.


[SQLite]: https://www.sqlite.org
[PDO]: http://php.net/manual/en/class.pdo.php


#### Ajax


Lyhenteellä [Ajax][Ajax] viitataan JavaScript-ohjelman ja palvelimen väliseen asynkroniseen kommunikointiin, missä tietojen välitys tapahtuu [XML][XML] -muodossa (*Asynchronous JavaScript and XML*). Ajax voidaa toteuttaa 
[XMLHttpRequest][XMLHttpRequest]-objektin avulla. Tällöin selaimessa olevaa sivua ei tarvitse ladata palvelimelta kokonaisuudessaan uudelleen, kun sivun esittämä data muuttuu. Palvelimelta haetaan ainoastaan muuttunut tieto, jonka jälkeen muokataan selaimessa olevaa dokumenttia muutoksen edellyttämällä tavalla.


[Ajax]: https://fi.wikipedia.org/wiki/Ajax_%28ohjelmointi%29
[XML]: https://fi.wikipedia.org/wiki/XML
[XMLHttpRequest]: https://www.w3schools.com/xml/xml_http.asp


XML:n ohella tietojen välityksessä voidaan käytää muitakin muotoja. Esimerkiksi kurssin tehtävissä dataa toimitettiin palvelimelle muodossa, jota käytetään välitettäessä HTML-lomakkeen data palvelimelle. Tietoja vastaanotettiin taas [JSON][JSON]-muotoisina merkkijonoina, jotka muunnettiin JavaScript -objekteiksi datan tulkinnan helpottamiseksi.   


[JSON]: https://www.w3schools.com/js/js_json_intro.asp


#### Muut aihepiiriä sivuavat kurssit tutkinto-ohjelmassa


Edellä oleva *kuva 4* esittää web-ympäristössä toimivan sovelluksen karkeaa arkkitehtuuria. Kaavio jäsentää samalla tutkinto-ohjelmassa olevat aihepiiriä käsittelvät muut opintojaksot:  [Web-selainohjelmointi][wso], Web-palvelinohjelmointi ja [Tietokantajärjestelmät][tkj].  


[wso]: https://timedu.github.io/wso/
[wpo]: http://web-palvelinohjelmointi.github.io
[tkj]: https://timedu.github.io/tkj2017k/


Lukuvuonna 2017/18 *Web-selainohjelmointi* -kurssin korvaa edelleenkin selainpäähän keskittyvä *Web-järjestelmät*. Kaikki mainnitut kolme kurssia täydentyvät 5 op laajuisiksi. *Tietokantajärjestelmät* järjestetään lukuvuoden ensimmäisellä periodilla ja *Web-järjestelmät* viimeisellä. Kursseille osallistuminen ei edellytä läsnäoloa. Kontaktitilaisuuksien ohjelma määräytyy osallistujien preferenssien mukaan. [Web-palvelinohjelmointi][wpo] perustuu suoraan Helsingin yliopiston samannimiseen verkkokurssiin. Tällä kurssilla ei ole lukuvuoden aikana lainkaan kontaktiopetusta ja sen voi suorittaa melko pitkälle oman aikataulun mukaan.



