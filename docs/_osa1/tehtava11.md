---
layout: exercise_page
title: "Tehtävä 1.1: Ascii-artisti (1p)"
exercise_template_name: W1E01.AsciiArtisti
exercise_discussion_id: 77873
exercise_upload_id: 315272
---


Tehtäväpohjassa olevassa `Site Root` -kansiossa[^1] on dokumentti `index.html`. Muokkaa dokumenttia siten, että sen katsominen selaimessa näyttää seuraavannäköisen ASCII-taideteoksen:

[^1]: NetBeansin *Files* -ikkunassa kansio näkyy nimellä `public_html`.

---

![Ascii-artisti](../img/ascii-artist.png "Ascii-artisti")

---
<small>Kuva 1.</small>

Vinkki tarvittaville muutoksille on yllä olevassa kuvassa. 

**Palauta** tehtävästä tiedosto `index.html`. Varmista ennen palautusta, että tehtäväpohjassa oleva sivu `testaa.html` ei esitä virheilmoituksia. 

### Vihjeitä ja lisätietoja

Sivun yläosassa on neljä linkkiä. Tehtävään liittyvän pohjakoodin voi ladata klikkaamalla [Tehtäväpohja][pohja]-linkkiä. Pohja on zip-arkistoiu NetBeans-projekti. Purettuna paketti on kansio, jonka NetBeans tulkitsee "HTML/JavaScript"- projektiksi[^2].

[pohja]: {{site.baseurl}}/pohjat/W1E01.AsciiArtisti.zip

[^2]: NetBeansista tulisi olla paketti, johon sisältyy "HTML5/JavaScript" ja "PHP" (esim. "Java SE"-paketissa näitä ei ole mukana). Tarvittavan paketin voi ladata [NetBeansin sivustolta][downloads].

[downloads]: https://netbeans.org/downloads/


![NetBeans-projekti](../img/nb-project.png "NetBeans-projekti"){: style="max-width: 400px; height: auto; display:block;"}
<small>Kuva 2.</small>


Kun projektin avaa NetBeansiin, näkymä on *Kuvan 2* kaltainen. Tehtävä ratkaistaan täydentämällä tiedostoa `index.html`. Sivun voi "ajaa" klikkaamalla sitä hiiren oikealla näppäimellä ja valitsemalla sitten esiin ilmestyvästä valikosta valinnan *Run File*[^3]. Ennen ajoa on kuitenkin varmistettava, että käytössä on haluttu selain. Käytettävän selaimen (Firefox) voi asettaa NetBeansin työkalupalkista löytyvän ao. pikanäppäimen kautta.

[^3]: `index.html`-sivu tulee esiin myös "ajamalla" projektin, koska index on asetettu projektin käynnistysivuksi.

*Run File* käynnistää NetBeansiin integroidun web-palvelimen ja valitun selaimen sekä ohjaa selainta lataamaan sivu osoitteesta `http://localhost:8383/W1E01/index.html`. 

NetBeansin -projektissa on mukana myös tiedosto `testaa.html`, jota ajamalla (*Run File*)[^4] voi testata, onko laadittu ratkaisu oikean suuntainen. Testien tulokset tulevat selaimeen. Projektin *qunit*-kansio sisältöineen liittyy testeihin. Testien ajo edellyttää verkkoyhteyttä.

[^4]: Projektin *Test* -valinta ei aja tässä testejä.

Jos esim. testäväkuvauksessa on epäselvyyksiä tai kaipaa tuekseen yleisen tason ratkaisuvihjeitä, voi käyttää Moodlessa olevaan tehtäväkohtaista keskustelua, johon ohjaa sivun alussa oleva [Keskustelu][keskustelu]-linkki. Tämän tehtävän [keskustelussa][keskustelu] on jo hyviä esimerkkejä keskustelualueen viesteistä.

[keskustelu]: https://moodle2.tut.fi/mod/forum/discuss.php?d=77873

Tehtävän ratkaisun voi palauttaa sivun yläosan [Palautus][palautus]-linkin kautta. Linkki ohjaa Moodlessa olevaan ao. palautustyökaluun, jonka kautta ratkaisuun liittyvät tiedostot voi palauttaa (tässä: index.html).

[palautus]: https://moodle2.tut.fi/mod/vpl/view.php?id=315272

Jos tehtävän ratkaisussa tulee vastaan sellaisia ylipääsemättömiä ongelmia, joita ei ole luonteva käsitellä [keskustelussa][keskustelu], voi lähettää kurssin vetäjälle katselmointipyynnön palauttamalla ratkaisuun liittyvät tiedostot ja kirjaamalla ongelmakuvauksen vetäjälle lähetettävään sähköpostiviestiin. Sivun yläosan [Katselmointipyyntö][katselmointi]-linkki osoitaa Moodlessa olevaan "mailto"-linkkiin, jonka tarkoitus on tuoda esiin osin valmiiksi täytetty viestin kirjoitus -ikkuna.[^5]

[katselmointi]: https://moodle2.tut.fi/mod/url/view.php?id=314337

[^5]: Ei toimi kaikissa ympäristöissä näin varsinkaan, jos Moodleen ei ole ennalta kirjauduttu, mutta sähköpostiviestin voi lähettää myös suoraan ilman ko. linkin apua.

<br/>

<small>
Tehtävän lähde: [Web-selainohjelmointi][weso], Helsingin yliopisto, Tietojenkäsitelytieteen laitos.
Creative Commons BY-NC-SA.
</small>

[weso]: http://web-selainohjelmointi.github.io/

