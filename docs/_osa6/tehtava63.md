---
layout: exercise_page
title: "Tehtävä 6.3: Liukupalapeli, vaihe 1"
exercise_template_name: W6E03.LiukupalapeliVaihe1
exercise_discussion_id: 
exercise_upload_id: 
---

> The Fifteen Puzzle (also called the Sliding Puzzle) is a simple classic game consisting of a 4×4 grid of numbered squares with one square missing. The object of the game is to arrange the tiles into numerical order by repeatedly sliding a square that neighbors the missing square into its empty space.

Laadi selaimessa toimiva liukupalapeli täydentämällä oheistettua projektirunkoa.

![Peli alussa](../img/peli_alussa.png "Peli alussa"){: style="display: block;  margin-top: 10px; width: 400px;"}

<small>Kuva 1.</small>

Sovelluksen käynnistymisen yhteydessä koodi muodostaa pelin palat pelialueelle siten, että palat ovat pelialueella numerojärjestyksessä (*Kuva 1*). Alkutilateessa palaa 12 tai 15 voi siirtää pelialueella olevaan tyhjään paikkaan. Siirto tapahtuu palaa klikkaamalla. Kun hiiren kursori on siirrettävissä olevan palan yläpuolella, kursorin muoto on *pointer*, ja palan numero ja raami ovat punaisia.

![Peli sekoitettu](../img/peli_sekoitettu.png "Peli sekoitettu"){: style="display: block;  margin-top: 10px; width: 400px;"}

<small>Kuva 2.</small>

Palat voidaan sekoittaa klikkaamalla *Sekoita* -painiketta. *Kuvassa 2* on eräs mahdollinen tilanne pelialueella palojen sekoittamisen jälkeen. *Kuvan 2* pelitilanteessa voidaan siirtää palaa 2, 7, 10 tai 13.

Tehtäväpohjan tiedostossa `js/code.js` on kuvattu eräs, *Kuvan 3* kutsukaavion mukainen, design sovelluksen koodiksi. Tehtävän ratkaisussa voi noudattaa tätä periaatetta, mutta tarvittavan funktiokokonaisuuden voi muodostaa myös muulla tavalla. JavaScript koodin ohella myös tiedoston `css/styles.css` tyylistö kaipaa pientä täydennystä.

![Kutsukaavio](../img/kutsukaavio.png "Kutsukaavio"){: style="display: block; margin: auto; margin-top: 10px;"}

<small>Kuva 3.</small>

**Palauta** tehtävän ratkaisuna tiedostot `code.js` ja `styles.js`

### Vihjeitä ja lisätietoja

Pohjakoodin tiedostossa `index.html` on poiskommentoituna merkkaus, joka vastaa pelialueen tilaa sivun latauksen jälkeen. Kommentit voi avata, jos tarvittavan css-täydennyksen laatii ennen JavaScript-koodia.
 
Seuraavat [document][document] -objektin metodit saattavat olla ratkaisussa tarpeellisia: [createElement][createElement], [getElementById][getElementById] ja [querySelectorAll][querySelectorAll]. 
Myös [käyttöliittymäelementtien][Element] seuraavia metodeja ja ominaisuuksia voidaan tarvita: [appendChild][appendChild], [className][className], [firstElementChild][firstElementChild], [id][id], [nextElementSibling][nextElementSibling], [parentElement][parentElement], [style][style].left, [style][style].top ja [textContent][textContent].
Muita käyttökelpoisia apuneuvoja tässä voivat olla [parseInt][parseInt] sekä [Math][Math]-objektin [floor][floor] ja [random][random].

[document]: https://www.w3schools.com/jsref/dom_obj_document.asp
[createElement]: https://www.w3schools.com/jsref/met_document_createelement.asp
[getElementById]: https://www.w3schools.com/jsref/met_document_getelementbyid.asp
[querySelectorAll]: https://www.w3schools.com/jsref/met_document_queryselectorall.asp

[Element]: https://www.w3schools.com/jsref/dom_obj_all.asp
[appendChild]: https://www.w3schools.com/jsref/met_node_appendchild.asp
[className]: https://www.w3schools.com/jsref/prop_html_classname.asp
[firstElementChild]: https://www.w3schools.com/jsref/prop_element_firstelementchild.asp
[id]: https://www.w3schools.com/jsref/prop_html_id.asp
[nextElementSibling]: https://www.w3schools.com/jsref/prop_element_nextelementsibling.asp
[parentElement]: https://www.w3schools.com/jsref/prop_node_parentelement.asp
[style]: https://www.w3schools.com/jsref/prop_html_style.asp
[textContent]: https://www.w3schools.com/jsref/prop_node_textcontent.asp

[Math]: https://www.w3schools.com/jsref/jsref_obj_math.asp
[floor]: https://www.w3schools.com/jsref/jsref_floor.asp
[random]: https://www.w3schools.com/jsref/jsref_random.asp

[parseInt]: https://www.w3schools.com/jsref/jsref_parseint.asp


Tehtävän [lähteenä käytetty spesifikaatio][speksi] löytyy Moodlesta.

[speksi]: https://moodle2.tut.fi/mod/resource/view.php?id=319595


<br/><small>
Tehtävän lähde: Homework Assignment - Fifteen Puzzle.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

<br/>

[cse154]:https://courses.cs.washington.edu/courses/cse154/


