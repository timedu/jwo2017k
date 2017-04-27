---
layout: exercise_page
title: "Tehtävä 7.3: Tehtävälista, Ajax"
exercise_template_name: 
exercise_discussion_id: 
exercise_upload_id: 
kesken: 1
julkaisu: 27.5.2017
---

Laadi [oheista projektipohjaa][pohja] täydentämällä [edellisen tehtävän](../tehtava72) kanssa samanlainen tehtävälista-sovellus kuitenkin niin, että *Todolist* -sivua ei ladata selaimeen uudelleen tehtävän lisäyksen ja poiston jälkeen. Ratkaisussa tieto tehtävälistan muutoksista välitetään palvelimelle JavaScriptin avulla. Tietokantaan tehdyn päivityksen jälkeen JavaScript myös muokkaa selaimessa olevaa dokumenttia vastaamaan tietokannan uutta tilaa. Seuraava kaavio esittää sovelluksen osaa, joka on erilainen verrattuna [tehtävään 7.2](../tehtava72).


[pohja]: https://moodle2.tut.fi/mod/resource/view.php?id=320608

![Moduulikaavio](../img/part7-ex7.3.png "Moduulikaavio"){: style="display: block; margin: auto; margin-top: 10px;"}

<small>Kuva 1.</small>

Ratkaisussa *Todolist*-sivu ottaa käyttöönsä moduulin `prepareTodolist.php` lisäksi JavaScript-moduulin `todolist.js`. *prepareTodolist* ei edellisten tehtävien ([7.1](../tehtava71) ja [7.2](../tehtava72)) tapaan välitä sivulle käsiteltävään tehtävälistaan sisältyviä tehtäviä, vaan asian hoitaa sivun latauksen jälkeen *todolist.js* -moduulin sisältämä funktio `doSelect`. Tietojen haun tietokannasta toteuttaa palvelu `doSelect.php`, jolle *doSelect*-funktio tekee pyynnön. Paluudatan saatuaan funktio rakentaa dataa vastaavat elementit osaksi selaimessa olevaa dokumenttia.

Tehtävän lisäyksen tehtävälistaan toteuttaa funktio `doInsert` palvelun `doInsert.php` tuella. Palvelu palauttaa funktiolle tietokantaan lisäämänsä tehtävän (ml. tietokantatunnus), jota vastaavat elementit funktio rakentaa selaimessa olevaan dokumenttiin. Tehtävän poiston tietokannasta toteuttaa funktio `doDelete` palvelun `doDelete.php` tuella. Funktio myös poistaa vastaavat elementit selaimessa olevasta dokumentista.

*Kuvassa 1* esiintyvä funktio `doLogout` ja palvelu `doLogout.php` ovat projektipohjassa valmiina.

**Palauta** tehtävän ratkaisuna tiedostot `doSelect.php`, `doInsert.php`, `doDelete.php` ja `todolist.js`.


### Vihjeitä ja lisätietoja


<br/><small>
Tehtävän lähteet: Homeworks [To-Do List][todo] & [To-Do List Extra Features][extra].<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[todo]: https://moodle2.tut.fi/mod/resource/view.php?id=320576
[extra]: https://moodle2.tut.fi/mod/resource/view.php?id=320577

[cse154]:https://courses.cs.washington.edu/courses/cse154/


<br/>


