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


### Vihjeitä ja lisätietoja

Seuraavassa on pelkistetty esimerkki siitä, millä eri tavoin JavaScript -toiminnallisuutta voidaan liittää web-sivulle. Esimerkin lähtökohtana on seuraava merkkaus:

{% highlight html %}

    <body>
        <button>Toggle Hello</button>          
        <p>Hello, World!</p> 
    </body>

{% endhighlight %}
<small>Listaus 3.</small>

Merkkauksessa on painike (`button`) ja tekstikappale (`p`). Sivun halutaan käyttäytyvän niin, että tekstikappale ei ole näkyvissä sivun latauduttua selaimeen ja niin, että klikattaessa painiketta tekstikappale tulee näkyviin, jos se ei ole näkyvissä (ja päinvastoin).

Toiminnallisuuden toteuttava JavaScript-koodi voidaan kirjoittaa merkkauksen oheen seuraavasti:

{% highlight html %}

    <body onload="document.querySelector('p').classList.add('hidden');">
        <button onclick="document.querySelector('p').classList.toggle('hidden');">
            Toggle Hello
        </button>        
        <p> 
            Hello, World!
        </p>            
    </body>

{% endhighlight %}
<small>Listaus 4.</small>

Tässä oletetaan, että ennalta on määritelty `hidden`-niminen tyyliluokka[^1]. Listauksessa viitattava tekstikappale paikannetaan  [`document`][document] -olion [`querySelector`][querySelector] -metodilla, joka palauttaa [`Element`][Element] -tyyppisen olion. *Element* -olioilla on taas [`classList`][classList] -ominaisuus, jonka metodeilla voidaan ylläpitää elementin tyyliluokkaluetteloa. Listauksessa käytetään metodeja [`add`][add] ja `toggle`.

[document]: https://developer.mozilla.org/en-US/docs/Web/API/Document
[querySelector]: https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector
[Element]: https://developer.mozilla.org/en-US/docs/Web/API/element
[classList]: https://developer.mozilla.org/en-US/docs/Web/API/Element/classList
[add]: https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/DOMTokenList.add()

[^1]: Ks. esim. kurssimateriaalin [kohta 4.6][kohta-4-6].

[kohta-4-6]: http://web-selainohjelmointi.github.io/#4.6-Case:-Tyylien-muuttaminen-JavaScriptillä


Seuraavassa listauksessa merkkauksen ohessa oleva JavaScript -koodi on typistetty yksinkertaisiksi funktiokutsuiksi:

{% highlight html %}

    <body onload="piilotaHello();">

        <button onclick="vaihdaHello();">
            Toggle Hello
        </button>  
        
        <p> 
            Hello, World!
        </p> 

        <script>
            function piilotaHello() {
                document.querySelector('p').classList.add('hidden');
            }
            function vaihdaHello() {
                document.querySelector('p').classList.toggle('hidden');
            }
        </script>

    </body>

{% endhighlight %}
<small>Listaus 5.</small>

*Listauksessa 5* merkkauksessa olevien funktioiden kutsuma toiminnallisuus on siirretty `script` -elementin sisällöksi[^2]. Seuraavassa myös funktiokutsut on poistettu merkkauksesta:

[^2]: Koodi olisi luontevampi kirjoittaa erilliseen tiedostoon, mutta tässä se yksinkertaisuuden vuoksi on osana html-tiedostoa. 


{% highlight html %}

    <body>

        <button>Toggle Hello</button>          
        <p>Hello, World!</p> 

        <script>
            function piilotaHello() {
                document.querySelector('p').classList.add('hidden');
            }
            function vaihdaHello() {
                document.querySelector('p').classList.toggle('hidden');
            }
            window.onload = piilotaHello;
            document.querySelector('button').onclick = vaihdaHello;
        </script>

    </body>

{% endhighlight %}
<small>Listaus 6.</small>

*Listauksessa 6* sivun alkutilaan asettava funktio `piilotaHello` on asetettu [`window`][window] -olion `onload`-ominaisuuden arvoksi ja tekstikappaleen näkyvyyden vaihtava funktio `vaihdaHello` painikkeen `onclick`-ominaisuuden arvoksi.

[window]: https://developer.mozilla.org/en-US/docs/Web/API/Window

JavaScriptissa funktot ovat tietyn tyyppisiä olioita, joita voidaan asettaa muiden olioiden tapaan muuttujien arvoksi. Täten *Listauksen 6* koodi voidaan kirjoittaa myös seuraavasti:

{% highlight html %}

    <body>

        <button>Toggle Hello</button>          
        <p>Hello, World!</p> 

        <script>
        
            var piilotaHello = function () {
                document.querySelector('p').classList.add('hidden');
            };
            var vaihdaHello = function () {
                document.querySelector('p').classList.toggle('hidden');
            };
            
            window.onload = piilotaHello;
            document.querySelector('button').onclick = vaihdaHello;
            
        </script>

    </body>

{% endhighlight %}
<small>Listaus 7.</small>

*Listauksessa 7* funktiot on asetettu muuttujiin `piilotaHello` ja `vaihdaHello`. Koska näihin funktioihin viitataan ainoastaan yhdessä kohdassa koodissa, erillisiä muuttujia ei välttämättä tarvita:

{% highlight html %}

    <body>

        <button>Toggle Hello</button>          
        <p>Hello, World!</p> 

        <script>

            window.onload = function () {
                document.querySelector('p').classList.add('hidden');
            };

            document.querySelector('button').onclick = function () {
                document.querySelector('p').classList.toggle('hidden');
            };
            
        </script>
        
    </body>

{% endhighlight %}
<small>Listaus 8.</small>

*Listauksessa 8* funktiot on sijoitettu suoraan `onload`- ja `onclick`-ominaisuuksien arvoiksi.


Erilaisiin tapahtumiin[^3] liittyviä funktioita voidaan asettaa myös [`addEventListener`][addEventListener] -metodilla[^4], jota on käytetty seuraavassa listauksessa:  

[^3]: Tässä esiintyviä tapahtumia ovat *dokumentin lataus selaimen ikkunaan* ja *painikkeen klikkaus*.
[^4]: Metodilla samaan tapahtumaan voidaan sitoa useita käsittelijöitä.


[addEventListener]: https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener


{% highlight html %}

    <body>

        <button>Toggle Hello</button>          
        <p> ello, World!</p> 

        <script>
            var piilotaHello = function () {
                document.querySelector('p').classList.add('hidden');
            };
            var vaihdaHello = function () {
                document.querySelector('p').classList.toggle('hidden');
            };
            window.addEventListener('load', piilotaHello);
            document.querySelector('button').addEventListener('click', vaihdaHello);
        </script>

    </body>

{% endhighlight %}
<small>Listaus 9.</small>

Funktio voidaan antaa suoraan parametriksi toiselle funktiolle ja siten edellisen listauksen koodi voidaan kirjoittaa samanarvoisesti myös seuraavasti:


{% highlight html %}

    <body>

        <button>Toggle Hello</button>          
        <p>Hello, World!</p> 

        <script>
            window.addEventListener('load', function () {
                document.querySelector('p').classList.add('hidden');
            });
            document.querySelector('button').addEventListener('click', function () {
                document.querySelector('p').classList.toggle('hidden');
            });
        </script>

    </body>

{% endhighlight %}
<small>Listaus 10.</small>


<br/>

<small>
Tehtävän lähde: [Web-selainohjelmointi][weso], Helsingin yliopisto, Tietojenkäsitelytieteen laitos.
Creative Commons BY-NC-SA. (alkuperäisiä tehtäviä muokattu)
</small>

[weso]: http://web-selainohjelmointi.github.io/

<br/>




