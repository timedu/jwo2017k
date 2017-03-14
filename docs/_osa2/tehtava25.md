---
layout: exercise_page
title: "Tehtävä 2.5: Yleiskone (3p)"
exercise_template_name: W2E05.Yleiskone
exercise_discussion_id: 78345
exercise_upload_id: 315779
---

Yleiskone on erilaisissa toiminnoissa auttava sivusto, jonka kautta käyttäjä voi käydä etsimässä apua arkisiin ongelmiin. Toteuta yleiskone, jossa on kolme toiminnallisuutta: Lämpötilamuunnin,  Pituusmuunnin ja Julkaisupistelaskuri. 

**Lämpötilamuunnin**. Sivusto tarjoaa laskurin, jonka avulla käyttäjä voi syöttää kenttään Celsius- ja Fahrenheit -asteet, ja muuntaa ne yhdestä muodosta toiseen (ks. [kuva][ui1]). Ohjeita muunnnoksen tekemiseen löytyy [webistä](http://lmgtfy.com/?q=how+to+calculate+celsius+from+fahrenheit+javascript).

[ui1]: https://moodle2.tut.fi/mod/resource/view.php?id=315960

**Pituusmuunnin**. Sivusto tarjoaa myös laskurin, jonka avulla käyttäjä voi syöttää kenttään jalkojen lukumäärän (engl. feet) sekä metriluvun, ja muuntaa ne yhdestä muodosta toiseen (ks. [kuva][ui2]).

[ui2]: https://moodle2.tut.fi/mod/resource/view.php?id=315961

**Julkaisulaskuri**. Julkaisut voidaan jakaa neljään luokkaan: luokka 0, luokka 1, luokka 2, ja luokka 3. Luokan 0 julkaisujen painoarvo on 1, luokan 1 julkaisujen painoarvo on 1.5, luokan 2 julkaisujen painoarvo on 3, ja luokan 3 julkaisujen painoarvo on 3. Toteuta laskuri, johon tutkija voi kirjoittaa kuhunkin luokkaan kuuluvien julkaisujen määrän, ja joka laskee julkaisujen yhteispainomäärän (ks. [kuva][ui3]). 

[ui3]: https://moodle2.tut.fi/mod/resource/view.php?id=315962

Edellisten toimintojen lisäksi Yleiskone -sivustolla on **"tykkää"-teksti**, jota klikkaamalla tykkää-tekstin viereinen luku kasvaa yhdellä. 

Sivuston merkkaus `index.html` on tehtäväpohjassa valmiina. Perustyylit ja valikon toiminnot voi kopioida [tehtävän 2.3](../tehtava23) ratkaisusta nimille `css/style-perus-mooc.css` ja `js/code-perus-mooc.js`[^1]. Laadi yleiskoneen varsinainen toiminnallisuus tiedostoon `js/code.js`.

[^1]: Tehtävän ratkaisu ei edellytä näitä.

**Palauta** tehtävän ratkaisuna tiedosto `code.js`. Varmista ennen palautusta, että tehtäväpohjassa oleva sivu `testaa.html` ei esitä virheilmoituksia. 

<br/>

<small>
Tehtävän lähde: [Web-selainohjelmointi][weso], Helsingin yliopisto, Tietojenkäsitelytieteen laitos.
Creative Commons BY-NC-SA. (alkuperäistä tehtävää muokattu)
</small>

[weso]: http://web-selainohjelmointi.github.io/




