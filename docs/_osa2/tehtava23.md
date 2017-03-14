---
layout: exercise_page
title: "Tehtävä 2.3: PerusMOOC (4p)"
exercise_template_name: W2E03.PerusMOOC
exercise_discussion_id: 78342
exercise_upload_id: 315777
---

Tehtäväpohjan tiedostossa `index.html` on erään sivuston merkkaus, jonka ulkoasu selaimessa on viitteenä olevan [kuvan 1][vaihe0] mukainen. Kehitä sivustoa eteenpäin alla kuvatulla tavalla.

[vaihe0]: https://moodle2.tut.fi/mod/resource/view.php?id=315852


#### Vaihe 1

Laadi tyylitiedosto `css/style.css` ja ota se käyttöön sivulla `index.html`. Näiden toimenpiteiden jälkeen sivun ulkoasun selaimessa tulisi olla viitteenä olevan [kuvan 2][vaihe1] mukainen.

[vaihe1]: https://moodle2.tut.fi/mod/resource/view.php?id=315853

Käytä seuraavia värejä `rgb(233, 229, 217)`, `rgb(73, 69, 69)` ja
`rgb(66, 126, 120)`. Fonttien määrittely on muotoa `font-family: 'Trebuchet MS', Trebuchet, Arial, sans-serif;`. Huomioi myös esim. tilanne, jossa hiiren kursori viedään valikon linkin yläpuolelle: tällöin linkin tekstin ja taustan värit muuttuvat.

#### Vaihe 2

Lisää sivulle toiminnallisuus, jossa vain ensimmäinen osio (`section`) näkyy ensin. valikon linkkejä klikkaamalla sivulla vaihdetaan osiosta toiseen. Viitteenä olevassa [kuvassa 3] [vaihe2] valintaa *Materiaali* on juuri klikattu.

[vaihe2]: https://moodle2.tut.fi/mod/resource/view.php?id=315854

Toteuta toiminnallisuus laatimalla tiedostoon `js/code.js` funktio `displaySection`. Ota JavaScript -tiedosto käyttöön sivulla `index.html`, jossa on jo valmiina em. funktion kutsut (*Listaus 1*).

{% highlight html %}
{% raw %}

    <body onload="displaySection(0);">
        <header>
            <h1>PerusMOOC &gt;&gt;</h1>
            <nav>
                <ul>
                    <li><a href="#" onclick="displaySection(0);">PerusMOOC?</a></li>
                    <li><a href="#" onclick="displaySection(1);">Materiaali</a></li>
                    <li><a href="#" onclick="displaySection(2);">Oma etenemiseni</a></li>
                </ul>
            </nav>
        </header>

{% endraw %}
{% endhighlight %}
<small>Listaus 1.</small>


#### Vaihe 3

Poista tiedostosta `index.html` kaikki JavaScript-koodi (*Listaus 2*) ja muokkaa tiedostoa `js/code.js` siten, että sivuston vaiheissa 1 ja 2 kuvattu toiminnallisuus ei muutu.

{% highlight html %}
{% raw %}

    <body>
        <header>
            <h1>PerusMOOC &gt;&gt;</h1>
            <nav>
                <ul>
                    <li><a href="#">PerusMOOC?</a></li>
                    <li><a href="#">Materiaali</a></li>
                    <li><a href="#">Oma etenemiseni</a></li>
                </ul>
            </nav>
        </header>

{% endraw %}
{% endhighlight %}
<small>Listaus 2.</small>

#### Palautettava aineisto

**Palauta** tehtävän ratkaisuna tiedostot `style.css` ja `code.js`. Varmista ennen palautusta, että sivuston ulkoasu ja toiminnallisuus on tehtäväkuvauksen mukainen.  Tehtäväpohjassa ei ole mukana testejä.

<br/>

<small>
Tehtävän lähde: [Web-selainohjelmointi][weso], Helsingin yliopisto, Tietojenkäsitelytieteen laitos.
Creative Commons BY-NC-SA. (alkuperäisiä tehtäviä muokattu)
</small>

[weso]: http://web-selainohjelmointi.github.io/





