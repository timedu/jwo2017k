---
layout: exercise_page
title: "Tehtävä 1.3: Piirakkaresepti (5p)"
exercise_template_name: W1E03.Piirakkaresepti
exercise_discussion_id: 77875
exercise_upload_id: 315275
---

Muokkaa tehtäväpohjassa olevia tiedostoja `index.html`, `recipe1.css` ja `recipe2.css` siten, että html-sivu näkyy selaimessa alla olevan kuvan mukaisena.

---

![Piirakka](../img/piirakka.jpg "Piirakka"){: style="display: block; margin: auto; margin-top: 10px;"}

---
<small>Kuva 1.</small>

Toteuta ratkaisu [spesifikaation][speksi] mukaan huomioiden kuitenkin, että tehtäväpohja sisältää jo reseptin perustekstin ja kaikki tarvittavat kuvat[^1]. Ratkaisu kannattanee laatia vaiheittain seuraavasti: 1) [HTML-merkkaus][vaihe1], 2) [perustyylit][vaihe2] (`recipe1.css`) ja 3) [lisäominaisuudet][vaihe3] (`recipe2.css` ja merkkauksen täydennys). 

[^1]: Spesifikaatiossa esiintyviä validaattorikuvia/-linkkejä ei tarvitse sisällyttää ratkaisuun.

[speksi]: https://moodle2.tut.fi/mod/resource/view.php?id=315259
[vaihe0]: https://moodle2.tut.fi/mod/resource/view.php?id=315260
[vaihe1]: https://moodle2.tut.fi/mod/resource/view.php?id=315261
[vaihe2]: https://moodle2.tut.fi/mod/resource/view.php?id=315262
[vaihe3]: https://moodle2.tut.fi/mod/resource/view.php?id=315263
[tsekki]: https://moodle2.tut.fi/mod/resource/view.php?id=315264


Piirakkasivu oletettavasti edellyttää seuraavien html-elementtien käyttöä[^2]:  [a][a], [abbr][abbr], [blockquote][blockquote], [br][br], [del], [h1][h1], [h2], [hr][hr], [img][img], [li][li], [link][link] ([rel][rel]="stylesheet", [rel][rel]="icon"), [ol][ol], [p], [pre], [span][span], [strong][strong] ja [ul][ul]. Myös copyright-[entiteettiä][ent] varmaankin tarvitaan. Tehtävän kannalta ainakin seuraavat lienevät keskeisiä css-ominaisuuksia: [background-attachment][background-attachment], [background-color][background-color], [background-image][background-image], [color][color], [font-family][font-family], [font-size][font-size], [font-style][font-style], [font-weight][font-weight], [letter-spacing][letter-spacing], [list-style-image][list-style-image], [text-align][text-align] ja [text-decoration][text-decoration].

[^2]: Linkit viittaavat [MDN][MDN]-sivuston käsikirja-aineistoon.

{% assign mdn = 'https://developer.mozilla.org/en-US/docs/Web' %}

{% capture html %}{{mdn}}/HTML/Element/{% endcapture %}
{% capture css  %}{{mdn}}/CSS/{% endcapture %}

[MDN]:        {{mdn}}

[a]:          {{html}}a
[abbr]:       {{html}}abbr
[blockquote]: {{html}}blockquote
[br]:         {{html}}br
[del]:        {{html}}del
[h1]:         {{html}}h1
[h2]:         {{html}}h2
[hr]:         {{html}}hr
[img]:        {{html}}img
[li]:         {{html}}li
[link]:       {{html}}link
[rel]:        {{mdn}}/HTML/Link_types
[ol]:         {{html}}ol
[p]:          {{html}}p
[pre]:        {{html}}pre
[span]:       {{html}}span
[strong]:     {{html}}strong
[ul]:         {{html}}ul

[ent]: https://dev.w3.org/html5/html-author/charref

[background-attachment]:  {{css}}background-attachment
[background-color]:       {{css}}background-color
[background-image]:       {{css}}background-image
[color]:                  {{css}}color
[font-family]:            {{css}}font-family
[font-size]:              {{css}}font-size
[font-style]:             {{css}}font-style
[font-weight]:            {{css}}font-weight
[letter-spacing]:         {{css}}letter-spacing
[list-style-image]:       {{css}}list-style-image
[text-align]:             {{css}}text-align
[text-decoration]:        {{css}}text-decoration


**Palauta** tehtävän ratkaisuna tiedostot `index.html`, `recipe1.css` ja `recipe2.css`. Käy [tarkistuslistan][tsekki] avulla vielä läpi, että ratkaisu sisältää kaikki halutut ominaisuudet.


<br/>

<small>
Tehtävän lähde: [Web Programming][cse154], University of Washington, 
Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[cse154]:https://courses.cs.washington.edu/courses/cse154/
