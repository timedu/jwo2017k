---
layout: exercise_page
title: "Tehtävä 6.1: Ascii-animaatio, vaihe 1"
exercise_template_name: W6E01.AsciiAnimaatioVaihe1
exercise_discussion_id: 80861
exercise_upload_id: 
---

Laadi selaimessa toimiva ascii-animaatioiden katselusovellus. Tehtäväpohjassa on sovelluksen html/css-käyttöliittymä, jota täydennnetään JavaScript-koodilla halutun toiminnallisuuden aikaansaamiseksi. Pohja sisältää myös joukon valmiita animaatioita.

![Pyöräilijä](../img/bike.png "Pyöräilijä"){: style="display: block; margin: auto; margin-top: 10px;"}

<small>Kuva 1.</small>

Sovelluksen käyttöliittymässä on tekstialue, joka sisältää animaatioon kuuluvat "freimit", kun animaatio ei ole käynnissä. Freimit on erotettu toisistaan viisi `=`-merkkiä käsittävillä tekstiriveillä. Esim. *kuvassa 1* on esillä eräästä animaatiosta sen neljä ensimmäistä freimiä. Animaation voi valita tekstialueelle kuvan alareunassa olevalla *Animaatio* -valinnalla. Tekstialueen sisältöä voi muokata, kun animaatio ei ole käynnissä.

Animaatio käynnistetään *Start*-paninikkeella, jolloin tekstialueelle ilmestyy animaation ensimmäinen freimi ja sitten pienen hetken kuluttua toinen jne. Viimeisen freimin jälkeen esitetään jälkeen ensimmäinen. Animaatio on käynnissä kunnes se pysäytetään *Stop*-näppäimellä. Tällöin tekstialue palaa tilaan, jossa se oli juuri ennen animaation käynnistämistä. Animaation ollessa käynnissä tekstialueen sisältöä ei voi muokata eikä alueelle voi valita toista animaatiota *Animaatio* -valinnalla (ko. valintakenttä ei ole ole aktiivinen). Myöskään animaation käynnistyspainike ei ota tällöin vastaan klikkauksia.

Tekstialueella esitettävän sisällön kokoa (fontin koko) voidaan säätää *Koko* -valinnalla. Valittavissa olevat koot ovat *XS, S, M, L, XL* ja *XXL*, jotka vastaavat lukuarvoja *7pt, 10pt, 12pt, 16pt, 24pt* ja *32pt*. Animaation nopeutta (viive freimien vaihdon välillä) voidaan muuttaa radionapeilla  *Turbo, Normaali* ja *Matelu*. Näitä vastaavat arvot *50ms, 250ms* ja *1500ms*. Sekä kokoa että nopeutta voidaan muuttaa myös animaation ollessa käynnissä.

Sovelluksen käynnistyksen yhteydessä animaatio *Blankko* on valittuna (tekstialue on tyhjä), koko on *M* ja nopeus *Normaali*. Animaatio ei ole käynnissä.


**Palauta** tehtävän ratkaisuna tiedosto `code.js`.

### Vihjeitä ja lisätietoja

#### Pohjakoodista

Valmiit animaatiot sijaitsevat tehtäväpohjan tiedostossa `anim/animaatiot.js` siten, että esim. *Kuvassa 1* esillä olevaan *Pyöräilijä* -animaatioon voidaan viitata seuraavasti: `ANIMATIONS['bike']`. Tehtävän ratkaisun muodostava koodi laaditaan tiedostoon `js/code.js`, joka sisältää käyttöliittymän elementtien tapahtumakäsittelijöiden rungot. Esim. animaation valintakentän osalta runko on seuraavanlainen:


{% highlight javascript %}

    document.getElementById('animaatio').onchange = function (e) {
        console.log('animaatioksi valittiin ' + e.target.value);        
    };

{% endhighlight %}

<small>Listaus 1.</small>


Kun valintakentän arvo muuttuu, selaimen konsolille tulostuu ao. teksti. Tapahtumakäsittelijöinä toimivat funktiot saavat parametrikseen [Event][Event]-objektin (funktion parametri `e`), jonka [target][target]-ominaisuus viittaa tapahtuman aiheuttaneeseen käyttöliittymäelementtiin - tässä siis valintakenttään, jonka `value`-ominaisuudesta löytyy animaation tunnus.

[Event]: https://developer.mozilla.org/en-US/docs/Web/API/Event
[target]: https://developer.mozilla.org/en-US/docs/Web/API/Event/target

Tehtäväpohjassa koodi on sisällytetty ns. JavaScript-moduuliin:

{% highlight javascript %}

(function () { //- moduuli alkaa -//

    // ...

})(); //- moduuli päättyy -//

{% endhighlight %}

<small>Listaus 2.</small>

Moduuli on käytännössä funktio, joka on asetettu sulkumerkkien sisään. Funktion sisällä `var`-lauseella määritellyt muuttujat eivät näy moduulin ulkopuolelle. Jos funktio on sulkeissa, se suoritetaan ilman erillistä kutsua.

#### setInterval-/clearInterval -funktiot

Animaation toteutuksessa voidaan käyttää [setInterval][setInterval] -funktiota:

[setInterval]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval


{% highlight javascript %}

var intervalID = window.setInterval(callback, delay);

{% endhighlight %}

<small>Listaus 3.</small>


*Listauksessa 3* `callback` on funktio, joka halutaan suorittaa toistuvasti, ja `delay` suorituskertojen välinen aika millisekunteina. Funktion toistuva suoritus voidaan keskeyttää [clearInterval][clearInterval]-funktiolla:

[clearInterval]: https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearInterval


{% highlight javascript %}

window.clearInterval(intervalID);

{% endhighlight %}

<small>Listaus 4.</small>


Seuraavassa on esimerkki *setInterval/clearInterval* -funktioiden käytöstä:


{% highlight javascript %}

var ajastin, numero;

document.getElementById('startti').onclick = function () {
    numero = 0;
    ajastin = window.setInterval(vaihdaNumero, 500);
};

document.getElementById('stoppi').onclick = function () {
    window.clearInterval(ajastin);
};

function vaihdaNumero() {
    if (numero >= 9) { numero = 1; } else { numero++; }
    document.getElementById('numero').value = numero;
}

{% endhighlight %}

<small>Listaus 5.</small>


*Listauksen 5* koodi askeltaa numeroita 1..9 tekstikentässä *startti*-painikkeen klikkauksen jälkeen. Numero vaihtuu 500ms välein. Askellus päättyy, kun klikataan *stoppi*-painiketta.


#### Muita apuneuvoja

Tässä tehtävässä [split][split]- ja [join][join] -metodit saattavat olla tarpeellisia animaatioiden käsittelyssä. Myös seuraavat käyttöliittymäelementtien ominaisuudet lienevät käyttökelpoisia: [checked][checked], [disabled][disabled], [readOnly][readOnly], [selectedIndex][selectedIndex] ja [style][style].fontSize.

Tehtävän [lähteenä käytetty spesifikaatio][speksi] löytyy Moodlesta.

[speksi]: https://moodle2.tut.fi/mod/resource/view.php?id=319586

[split]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split
[join]:  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join

[checked]: https://www.w3schools.com/jsref/prop_checkbox_checked.asp
[disabled]: https://www.w3schools.com/jsref/prop_pushbutton_disabled.asp
[readOnly]: https://www.w3schools.com/jsref/prop_text_readonly.asp
[selectedIndex]: https://www.w3schools.com/jsref/prop_select_selectedindex.asp
[style]: https://www.w3schools.com/jsref/prop_html_style.asp


<br/><small>
Tehtävän lähde: Homework Assignment - ASCIImation.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

<br/>

[cse154]:https://courses.cs.washington.edu/courses/cse154/

