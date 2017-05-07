---
layout: exercise_page
title: "Tehtävä 7.3: Tehtävälista, Ajax (5p)"
exercise_template_name: 
exercise_discussion_id: 81427
exercise_upload_id: 320614
---

Laadi [oheista projektipohjaa][pohja] täydentämällä [edellisen tehtävän](../tehtava72) kanssa samanlainen tehtävälista-sovellus kuitenkin niin, että *Todolist* -sivua ei ladata selaimeen uudelleen tehtävän lisäyksen ja poiston jälkeen. Ratkaisussa tieto tehtävälistan muutoksista välitetään palvelimelle JavaScriptin avulla. Tietokantaan tehdyn päivityksen jälkeen JavaScript myös muokkaa selaimessa olevaa dokumenttia vastaamaan tietokannan uutta tilaa. Seuraava kaavio esittää sovelluksen osaa, joka on erilainen verrattuna [tehtävään 7.2](../tehtava72).


[pohja]: https://moodle2.tut.fi/mod/resource/view.php?id=320608

![Moduulikaavio](../img/part7-ex7.3.png "Moduulikaavio"){: style="display: block; margin: auto; margin-top: 10px;"}

<small>Kuva 1.</small>

Ratkaisussa *Todolist*-sivu ottaa käyttöönsä moduulin `prepareTodolist.php` lisäksi JavaScript-moduulin `todolist.js`. *prepareTodolist* ei edellisten tehtävien ([7.1](../tehtava71) ja [7.2](../tehtava72)) tapaan välitä sivulle käsiteltävään tehtävälistaan sisältyviä tehtäviä, vaan asian hoitaa sivun latauksen jälkeen *todolist.js* -moduulin sisältämä funktio `doSelect`. Tietojen haun tietokannasta toteuttaa palvelu `doSelect.php`, jolle *doSelect*-funktio tekee pyynnön. Paluudatan saatuaan funktio rakentaa dataa vastaavat elementit osaksi selaimessa olevaa dokumenttia.

Tehtävän lisäyksen tehtävälistaan toteuttaa funktio `doInsert` palvelun `doInsert.php` tuella. Palvelu palauttaa funktiolle tietokantaan lisäämänsä tehtävän (ml. tietokantatunnus), jota vastaavat elementit funktio rakentaa selaimessa olevaan dokumenttiin. Tehtävän poiston tietokannasta toteuttaa funktio `doDelete` palvelun `doDelete.php` tuella. Funktio myös poistaa vastaavat elementit selaimessa olevasta dokumentista.

*Kuvassa 1* esiintyvä funktio `doLogout` ja palvelu `doLogout.php` ovat projektipohjassa valmiina. Tässä rakennettavista moduuleista pohja sisältää rungot siten, että sovellus toimii esittäen vakiotietoja. Edellissä tehtävässä laaditusta tietokantakäsittelystä on tässä paljon hyötyä.

**Palauta** tehtävän ratkaisuna tiedostot `doSelect.php`, `doInsert.php`, `doDelete.php` ja `todolist.js`.


### Vihjeitä ja lisätietoja


#### logout -toiminto


Tässä tietokantakäsittelyyn liittyvät toiminnot rakennetaan siten, pyynnöt välitetään palvelimelle JavaScriptilla käyttäen `XMLHttpRequest`-objektia. Tehtäväpohjassa on valmiina tällä periaatteella toteutettu logout -toiminto. 

Käyttäjä käynnistää logout -toiminnon klikkaamalla sivulla olevaa linkkiä:


{% highlight html %}

<a href="#"><strong>Log Out</strong></a>

{% endhighlight %}

<small>Listaus 1.</small>


Linkin klikkaukseen on sidottu funktio, joka välittää pyynnön palvelimelle (*Listaus 2*). Jos pyyntöön saatavassa vasteessa on ilmoitus toiminnon onnistuneesta suorituksesta, pyydetään selaimeen Start -sivu.


{% highlight javascript %}

var logoutLink = document.querySelector('body>div a[href="#"]');
logoutLink.onclick = doLogout;
...
function doLogout(e) {

    e.preventDefault();

    var xhr = new XMLHttpRequest();
    xhr.open("POST", './php/doLogout.php', true);

    xhr.onload = function () {
        var response = JSON.parse(xhr.responseText);
        if (response.ok) {
            location.href = './start.php';
        } else {
            console.log(response.message);
        }
    };
    xhr.send();
}


{% endhighlight %}

<small>Listaus 2. Ote moduulista *todolist.js*</small>


Pyyntöä varten muodostetaan `XMLHttpRequest` -objekti, jonka `open` -metodilla määritellään pyynnön tyyppi ja osoite sekä se, tapahtuuko pyyntö asykronisesti (`true`) vai synkronisesti. Objektin `onload`-ominaisuuden[^1] arvoksi asetetaan funktio, joka suoritetaan, kun palvelimelta saadaan pyyntöön vaste. Pyyntö lähetetään `XMLHttpRequest` -objektin `send`-metodilla, jolla tässä ei ole parametria, koska pyyntöön ei liity palvelimelle välitettävää dataa. 


[^1]: `onload` -ominaisuuden sijaan voi käyttää myös `onreadystatechange` -ominaisuutta, mutta tällöin on huomioitava pyynnön käsittelyn tila ja status (ks. esim. [ao. kohta][sec72] Web-selainohjelmointi -materiaalista).

[sec72]: http://web-selainohjelmointi.github.io/#7.2-Datan-hakeminen-palvelimelta


Palvelimelta pyyntöön saatava vaste löytyy `XMLHttpRequest` -objektin `responseText` -ominaisuudesta. Tässä vaste on JSON -muodossa[^2] oleva merkkijono, jonka muunnetaan JavaScript -objektiksi `JSON` -olion `parse` -metodilla. Pyynnön käsittelevän palvelun palauttama vaste on sellainen, että sen `ok` -ominaisuudessa on totuusarvo (`true`/`false`), joka ilmoittaa, onko käsittely palvelimella tapahtunut onnistuneesti. 


[^2]: Ks. esim. kohta [JSON][sec71] Web-selainohjelmointi -materiaalista.

[sec71]: http://web-selainohjelmointi.github.io/#7.1-JSON


*Listauksessa 3* on *listauksen 2* esittämän `doLogout` -funktion tekemän pyynnön käsittelijä, `doLogout.php`, joka poistaa kaikki istuntoon liittyvän datan ja tulostaa json-muotoisen merkkijonon `'{"ok": true}'`.  Merkkijonon lähtökohta on tässä PHP:ssä tyypillinen merkkijonoilla indeksoitu taulukko, joka muunnetaan JSON -muotoon funktiolla [json_encode][json_encode] (*listaus  4*).

[json_encode]: http://php.net/manual/en/function.json-encode.php


{% highlight php %}

<?php

include './commonCode.php';

session_destroy();

reply(['ok' => TRUE]);

?>

{% endhighlight %}

<small>Listaus 3. *doLogout.php*</small>



{% highlight php %}

<?php

function reply($data) {
    echo json_encode($data);
    die();
}

?>

{% endhighlight %}

<small>Listaus 4. *reply* -funktio moduulissa *commonCode.php*</small>



#### Tehtäväluettelon luku tietokannnasta


Tietokannasta luettu tehtäväluettelo esitetään *Todolist*  -sivulla. [Tehtävässä 7.2](../tehtava72) data on valmiina palvelimelta saatavassa html-dokumentissa, mutta tässä data haetaan erillisellä pyynnöllä, kun html-dokumentti on ladattu selaimeen (*Kuva 1*).


![Sekvenssikaavio](../img/ex73sequence-select.png "Sekvenssikaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"}

<small>Kuva 1. Todolist -sivun pyyntö palvelimelle</small>



{% highlight javascript %}

window.onload = doSelect;
...
function doSelect() {
    // palvelusta saatava data (json-muodossa oleva merkkijono), esim.
    var items = '[{"id": 3, "task": "Tehtävä 1"},{"id": 6, "task": "Tehtävä 2"}]';

    // datan muunnos objekteja sisältäväksi taulukoksi
    items = JSON.parse(items);

    // createTodoElement on apufunktio, joka löytyy moduulin lopusta
    items.forEach(createTodoElement);
}

{% endhighlight %}

<small>Listaus 5. Ote pohjakoodin moduulista *todolist.js*</small>



{% highlight php %}

<?php
include './commonCode.php';

reply([
    'ok' => TRUE,
    'items' => [
        ['id' => 3, 'task' => 'Tehtävä 1'],
        ['id' => 6, 'task' => 'Tehtävä 2']
    ]
]);

// muita mahdollisia pyyntöön annettavia vasteita:
// reply([
//    'message' => 'not logged in',
//    'ok' => FALSE
// ]);
// reply([
//    'message' => 'db error',
//    'ok' => FALSE
// ]);
?>

{% endhighlight %}

<small>Listaus 6. Pohjakoodin *doSelect.php*</small>








#### Uuden tehtävän talletus käyttäjän tehtäväluetteloon


![Sekvenssikaavio](../img/ex73sequence-insert.png "Sekvenssikaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"}


<small>Kuva 2. Tehtävän talletus tietokantaan</small>




{% highlight javascript %}

var addButton = document.querySelector('#new-item input[type="button"]');
addButton.onclick = doInsert;
...
function doInsert() {
    var addInput = document.querySelector('#new-item input[type="text"]');
    // palvelusta saatava data  esim.
    var item = '{"id": 9, "task": "Tehtävä 99"}';
    // esimerkkidata sivulle ja syötekentän tyhjennys
    createTodoElement(JSON.parse(item));
    addInput.value = '';
}

{% endhighlight %}

<small>Listaus 7. Ote pohjakoodin moduulista *todolist.js*</small>


{% highlight php %}

<?php
include './commonCode.php';

reply([
    'ok' => TRUE,
    'items' => ['id' => 9, 'task' => 'Tehtävä 99']
    ]
);

// muita mahdollisia pyyntöön annettavia vasteita:
// reply([
//    'message' => 'not logged in',
//    'ok' => FALSE
// ]);
// reply([
//    'message' => 'db error',
//    'ok' => FALSE
// ]);
//reply([
//    'message' => 'nothing to insert',
//    'ok' => FALSE
//]);
?>

{% endhighlight %}

<small>Listaus 8. Pohjakoodin *doInsert.php*</small>


#### Esimerkkeja XMLHttpRequest -objektin käytöstä


Sivulla <http://timedu.github.io/weo2016k/form2xhr/> on esimerkki, miten JavaScriptin `XMLHttpRequest`-objektin avulla välitetään tietoa palvelimelle. Tässä tehtävässä tiedot kannattanee välittää siinä muodossa, missä POST-metodilla lähetetyn lomakeenkin data välittyy palvelimelle (`application/x-www-form-urlencoded`).  Web-selainohjelmointi -materiaalissa aihetta käsitellään luvussa [7. Keskustelu palvelimen kanssa](http://web-selainohjelmointi.github.io/#7-Keskustelu-palvelimen-kanssa).




<br/><small>
Tehtävän lähteet: Homeworks [To-Do List][todo] & [To-Do List Extra Features][extra].<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[todo]: https://moodle2.tut.fi/mod/resource/view.php?id=320576
[extra]: https://moodle2.tut.fi/mod/resource/view.php?id=320577

[cse154]:https://courses.cs.washington.edu/courses/cse154/


<br/>


