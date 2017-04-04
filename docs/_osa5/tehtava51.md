---
layout: exercise_page
title: "Tehtävä 5.1: Elokuva-arvostelu, css (6p)"
exercise_template_name: "W5E01.ElokuvaArvostelu-css"
exercise_discussion_id: 80014
exercise_upload_id: 318820
---

{% assign css = 'https://developer.mozilla.org/en-US/docs/Web/CSS' %}

[background-attachment]: {{css}}/background-attachment
[background-color]: {{css}}/background-color
[background-image]: {{css}}/background-image
[border]: {{css}}/border
[border-radius]: {{css}}/border-radius
[bottom]: {{css}}/bottom
[clear]: {{css}}/clear
[color]: {{css}}/color
[float]: {{css}}/float
[font-family]: {{css}}/font-family
[font-size]: {{css}}/font-size
[font-style]: {{css}}/font-style
[font-weight]: {{css}}/font-weight
[left]: {{css}}/left
[margin]: {{css}}/margin
[margin-bottom]: {{css}}/margin-bottom
[margin-left]: {{css}}/margin-left
[margin-right]: {{css}}/margin-right
[margin-top]: {{css}}/margin-top]
[overflow]: {{css}}/overflow
[padding]: {{css}}/padding
[position]: {{css}}/position
[text-align]: {{css}}/text-align
[text-shadow]: {{css}}/text-shadow
[top]: {{css}}/top
[vertical-align]: {{css}}/vertical-align
[width]: {{css}}/width



Tehtäväpohjassa on merkkaus, `index.html`, joka ilman tyylejä näyttää selaimessa [oheisen tiedoston][vaihe0] mukaiselta. Laadi merkkaukseen liittyvät tyylit siten, että sivu näyttää seuraavalta: sivu [ylös][vaihe4a] / [alas][vaihe4b]  skrollattuna. Merkkaukseen ei tehtä muutoksia.

[vaihe0]: https://moodle2.tut.fi/mod/resource/view.php?id=318437
[vaihe4a]: https://moodle2.tut.fi/mod/resource/view.php?id=318438
[vaihe4b]: https://moodle2.tut.fi/mod/resource/view.php?id=318439


**Palauta** tehtävän ratkaisuna tiedosto `styles.css`.

Kaikki tarvittavat kuvat löytyvät tehtäväpohjasta. Merkkauksen viittaamat kuvat ovat hakemistossa `img` ja tyyleihin liittyvät kuvat hakemistossa `css`. Tiedostossa `styles.css` on valmiina joukko valitsimia, joita voi hyödyntää oman ratkaisun osana. Tehtävän ratkaisua voi vaiheistaa esim. seuraavasti:


#### 1. Sivun yleiset ominaisuudet ("body")

Sivun normaalin tekstin fontti on `Verdana`, `Tahoma` tai  `sans-serif` (tässä ensisijaisuusjärjestyksessä) koon ollessa `8pt`. Sivulla on skrollattaessa paikallaan pysyvä tausta (`moviebg.png`).

Selainikkunan ylä- ja alaosassa on bannerit, jotka ovat näkyvissä riippumatta siitä, mihin kohtaan sivu on skrollattu. Banneri muodostuu keskitetyn kuvan (`rancidbanner.png`) sisältävästä `div`-elementistä, jolla on kuvaan sointuva tausta (`rancidbannerbg.png`). 

Sivun pääotsikko on keskitetty. Otsikko on esitetty vahvennetulla `24pt` kokoisella `Tahoma`-, `Verdana`- tai  `sans-serif`-fontilla  (tässä ensisijaisuusjärjestyksessä). Otsikolla on vaalean harmaa (`#999999`) varjostus.  

Otsikko on näkyvissä, jos sivu on skrollattu aivan ylös so. se ei jää yläbannerin taakse ja vastaavasti, jos sivu on skrollattu alas, sisältöä ei jää alabannerin taakse.

Edellisten ominaisuuksien aikaansaamiseksi saatetaan tarvita seuraavia css-ominaisuuksia[^1]: 
[background-attachment][background-attachment],
[background-image][background-image],
[bottom][bottom],
[font-family][font-family],
[font-size][font-size],
[font-weight][font-weight],
[left][left],
[margin][margin],
[position][position],
[text-align][text-align],
[text-shadow][text-shadow],
[top][top],
[width][width].

[^1]: Linkit viittaavat MDN:n [CSS-aineistoon]({{css}}). Myös esim. W3Schools -sivustolta löytyy [CSS-käsikirja](https://www.w3schools.com/cssref/).

Vaiheen tyyliasetusten laatimisen jälkeen sivun pitäisi näyttää selaimessa seuraavalta:  sivu [ylös][vaihe1a] / [alas][vaihe1b]  skrollattuna.

[vaihe1a]: https://moodle2.tut.fi/mod/resource/view.php?id=318454
[vaihe1b]: https://moodle2.tut.fi/mod/resource/view.php?id=318455


#### 2. Sisältöalue ("#content")

Sisältö on vaakasuunnassa keskitetyllä `800px` levyisellä alueella, joka on kehystetty yhtenäisellä harmaalla `4px` raamilla. Raamin kulmat on pyöristetty (pyöristyksen säde: `20px`) siten, että sisältöä ei ole näkyvissä raamin ulkopuolella pyöristyksen kohdalla. Sisältöalueella on sama tausta kuin koko sivulla, mutta tässä tausta skrollaa sisällön mukana.

Sisältöalueella on ylä- ja alabannerit, joiden grafiikka muodostuu merkkauksen viittaamasta kuvasta (`rottenlarge.png`) ja tyyliasetusten määräämästä taustasta (`rottenlargebg.png`). 

Bannerin teksti on valkoisella sivun yleisasetusten mukaisella fontilla. Bannerin esittämä luku *33* on kuitenkin esitetty punaisella vahvennetulla `48pt` kokoisella tekstillä. Bannerin kuva on asemoitu tekstiin nähden alas (`bottom`). 

Alabannerin yläpuolella on taustaltaan vihreä (`#A2B964`) alatunniste ("footer"), jossa oleva teksti on keskitetty. Tekstin etäisyys alatunnisteen ylä- ja alareunasta on `5px`.

Edellisten ominaisuuksien aikaansaamiseksi saatetaan tarvita seuraavia css-ominaisuuksia[^1]: 
[background-color][background-color],
[background-image][background-image],
[border][border],
[border-radius][border-radius],
[color][color],
[font-size][font-size],
[font-weight][font-weight],
[margin-left][margin-left],
[margin-right][margin-right],
[overflow][overflow],
[padding][padding],
[text-align][text-align],
[vertical-align][vertical-align],
[width][width].


Vaiheen tyyliasetusten laatimisen jälkeen sivun pitäisi näyttää selaimessa seuraavalta:  sivu [ylös][vaihe2a] / [alas][vaihe2b] skrollattuna.

[vaihe2a]: https://moodle2.tut.fi/mod/resource/view.php?id=318466
[vaihe2b]: https://moodle2.tut.fi/mod/resource/view.php?id=318467


#### 3. Elokuvan yleiskuvaus ("#overview")

Sisältöalueen oikeassa reunassa `250px` levyisellä alueella esitetään elokuvan yleiskuvaus, joka muodostuu kuvan sisältämästä `div`-elementistä sekä `dl`-elementin sisältämistä tekstimuotoisista tiedoista. Alueella on vihreä (`#A2B964`) tausta. 

Yleiskuvauksen teksti on `8pt` kokoista `Arial`- tai `sans-serif`-fonttia (tässä ensisijaisuusjärjestyksessä). Otsikkona oleva `dt`-elementtien teksti on vahvennettu. Teksti on `10px` etäisyydellä alueen reunasta. Samoin otsikon ja sitä edeltävän tekstin välinen etäisyys on `10px`.

Sisältöalueen alatunniste (footer) asettuu yleiskuvaukselle varatun alueen alapuolelle. 

Varteenotettavia css-ominaisuuksia[^1] käytettäväksi tässä ovat
[background-color][background-color], 
[clear][clear], 
[float][float], 
[font-family][font-family], 
[font-size][font-size], 
[font-weight][font-weight], 
[margin][margin], 
[margin-top][margin-top], 
[width][width].

Vaiheen tyyliasetusten laatimisen jälkeen sivun pitäisi näyttää selaimessa seuraavalta:  sivu [ylös][vaihe3a] / [alas][vaihe3b] skrollattuna.

[vaihe3a]: https://moodle2.tut.fi/mod/resource/view.php?id=318648
[vaihe3b]: https://moodle2.tut.fi/mod/resource/view.php?id=318649


#### 4. Elokuvan arvostelut ("#reviews")

Elokuva-arvostelut tulevat kahteen sarakkeeseen sisältöalueen vasempaan reunaan `550px` levyiselle alueelle. Sarakkeen leveys on `47%` arvosteluille varatun alueen leveydestä. Sarakkeet on asemoitu siten, että niiden ympärille jää tilaa `2%` (550px:sta).

Kukin arvostelu on esitetty vahvennetulla tekstillä taustaväriltään `#E8DC9B` olevassa laatikossa, jossa on `2px` levyinen harmaa raami. Laatikon reunat on pyöristetty (säde: `10px`). Teksti on `8px` etäisyydellä laatikon reunoista ja vaakasuunnassa `5px` etäisyydellä laatikossa olevasta kuvasta. Yhtä useampi tekstirivi on kuvan rinnalla.

Arvostelun alapuolelle on tiedot arvion laatineesta kriitikosta. Kriitikon tietojen ja niiden alapuolelle olevan seuraavan arvostelun välinen etäisyys on `25px`. Kriitikon nimen ja sen vieressä olevan kuvan välinen etäisyys on `5px`. Kriitikon edustama julkaisu on esitetty kursivoituna.

Tässä seuraavat css-ominaisuudet[^1] saattavat osoittautua tarpeelliseksi:
[background-color][background-color],
[border][border],
[border-radius][border-radius],
[float][float],
[font-style][font-style],
[font-weight][font-weight],
[margin-bottom][margin-bottom],
[margin-left][margin-left],
[margin-right][margin-right],
[overflow][overflow],
[padding][padding],
[width][width].

Vaiheen tyyliasetusten laatimisen jälkeen sivun pitäisi näyttää selaimessa seuraavalta:  sivu [ylös][vaihe4a] / [alas][vaihe4b] skrollattuna.

<br/><small>
Tehtävän lähtökohtainen aineisto: Homeworks Movie Review & Movie Review Part Deux.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

<br/>

[cse154]:https://courses.cs.washington.edu/courses/cse154/



