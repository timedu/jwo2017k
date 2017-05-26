---
layout: exercise_page
title: "Tehtävä 7.2: Tehtävälista, SQL (5p)"
exercise_template_name: 
exercise_discussion_id: 81426
exercise_upload_id: 320612
---

Laadi [oheista projektipohjaa][pohja] täydentämällä [edellisen tehtävän](../tehtava71) kanssa samanlainen tehtävälista-sovellus kuitenkin niin, että tehtävälistat talletetaan tiedostojen sijaan *relaatiotietokantaan*. Ratkaisussa tietokantaa käsitteleviä ja tässä rakennettavia moduuleja ovat `prepareTodolist.php`, `doInsert.php` ja `doDelete.php`. Moduulin `prepareStart.php` voi kopioida sellaisenaan edellisen tehtävän ratkaisusta.


[pohja]: https://moodle2.tut.fi/mod/resource/view.php?id=320579

#### Tietokannasta

Valmis *SQLite*-relaatiotietokanta sijaisee projektipohjan `data`-hakemistossa nimellä `todos.sqlite`. Hakemistossa on myös skripti `create_database.php`, josta selviää käytettävän taulun rakenne ja, jonka avulla tietokanta voidaan perustaa tarvittaessa uudelleen[^1]. 

Moduulissa `php/commonCode.php` on vakion `TODOLIST` määrittely, joka viittaa käytettävään tietokantaan[^2]. Laadittavien moduulien rungoissa on vakiot, joiden sisältönä on tässä tarvittavat SQL-komennot.

[^1]: Pyyntö osoitteeseen `http://localhost:8000/data/create_database.php`
[^2]: Vrt. `create_database.php`

**Palauta** tehtävän ratkaisuna tiedostot `prepareTodolist.php`, `doInsert.php` ja `doDelete.php`.


### Vihjeitä ja lisätietoja

#### Sovelluksen toimintaa sekvenssikaavioina

Seuraavissa *kuvissa 1* ja *2* on esitetty [sekvenssikaavioiden][Sequence_diagram] muodossa, miten etenee Todolist -sivusta web-palvelimelle tehty pyyntö ja, mitä tapahtuu klikattaessa uuden tehtävän lisäämiseen liittyvän lomakkeen submit -painiketta.


[Sequence_diagram]: https://en.wikipedia.org/wiki/Sequence_diagram


![Sekvenssikaavio](../img/ex72sequence-select.png "Sekvenssikaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"}

<small>Kuva 1. Todolist -sivun pyyntö palvelimelle</small>


Kehitysympäristössä Todolist -sivun pyyntö saadaan välitettyä palvelimelle kirjaamalla selaimen osoitekenttään `http://localhost:8000/todolist.php`, jonka seurauksena selain lähettää palvelimelle [`GET`][httpmethods]-tyyppisen pyynnön (*Kuva 1*). Palvelimella oleva `todolist.php` sisältää [`require`][require]/[`include`][include] -viittauksia toisiin php -moduuleihin, jotka otetaan osaksi palvelimen päässä käsiteltävää php -koodia. Moduulin alussa on viittaus moduuliin `prepareTodolist.php`:


[httpmethods]: https://www.w3schools.com/tags/ref_httpmethods.asp
[require]: http://php.net/manual/en/function.require.php
[include]: http://php.net/manual/en/function.include.php


{% highlight php %}

<?php require './php/prepareTodolist.php'; ?>
<!DOCTYPE html>
<html>
...


{% endhighlight %}

<small>Listaus 1.</small>


`prepareTodolist.php` sisältää tarvittavan tietokantakäsittelyn so. se kohdistaa tietokantaan `SELECT` -komennon, joka palauttaa aktiivisen käyttäjän tehtävät, ja asettaa tehtävät `$items` -muuttujan arvoksi. Tehtäväpohjassa muuttujan arvoksi asetetaan vakiotietoja:  


{% highlight php %}

<?php
   ...
   $items = [
      ['id' => 3, 'task' => 'Tehtävä 1'],
      ['id' => 6, 'task' => 'Tehtävä 2']
   ];
   ...
?>

{% endhighlight %}

<small>Listaus 2.</small>

Tehtävän ratkaisussa vakiotiedot korvataan tietokannasta luetuilla tiedoilla. Tehtäväpohjassa määritelty vakio `SELECT_ITEMS` sisältää tässä tarvittava SQL-komennon. 

Moduulissa `todolist.php` oleva koodi muodostaa sovelluksen käyttöliittymän. Seuravassa on moduulista ote, jossa käytetään tietokannasta luettuja tietoja sisältävää `$items` -muuttujaa:


{% highlight php %}

<?php foreach ($items as $item): ?>
    <li>
        <form action="php/doDelete.php" method="post">
            <input type="hidden" name="index" value="<?= $item['id'] ?>" />
            <input type="submit" value="Delete" />
        </form>
        <?= $item['task'] ?>
    </li>
<?php endforeach; ?>


{% endhighlight %}

<small>Listaus 3.</small>


*Listauksen 3* koodi muodostaa selaimelle palautettavalle sivulle käyttäjän tehtäväluetteloon liittyvät elementit, joihin sisältyy lomakkeet tehtävien poistoa varten. Jos sivulle modostetaan elementit *listauksen 2* esittävien vakiotietojen pohjalta, saadaan näiltä osin seuraavanlainen merkkaus:


{% highlight html %}

<li>
    <form action="php/doDelete.php" method="post">
        <input name="index" value="3" type="hidden">
        <input value="Delete" type="submit">
    </form>
    Tehtävä 1 
</li>
<li>
    <form action="php/doDelete.php" method="post">
        <input name="index" value="6" type ="hidden">
        <input value="Delete" type="submit">
    </form>
    Tehtävä 2 
</li>


{% endhighlight %}

<small>Listaus 4.</small>


Pyynnön seurauksena selaimelle palautuu siis html-dokumentti ilman php-koodia.

**Tehtävän lisäykseen** liittyvän pyynnön lähtökohtana on sivulla oleva ao. lomake:


{% highlight html %}

<form action="./php/doInsert.php" method="post">
    <input name="item" type="text" size="25" 
           autofocus="autofocus" />
    <input type="submit" value="Add" />
</form>

{% endhighlight %}

<small>Listaus 5.</small>


*Listauksen 5* esittämän lomakkeen submit -painikkeen klikkauksen seurauksena selain lähettää palvelimelle [`POST`][httpmethods] -tyyppisen pyynnön (*Kuva 2*), johon pakataan lomakkeen tekstikentän sisältämä data.  


![Sekvenssikaavio](../img/ex72sequence-insert.png "Sekvenssikaavio"){: style="display: block; margin: auto; margin-top: 10px; width: 500px;"} 

<small>Kuva 2. Tehtävän talletus tietokantaan</small>


Moduuli `doInsert.php` käsittelee pyynnön tallettaen vastaanottamansa datan tietokantaan, jonka jälkeen se välittää selaimelle ohjeen, että sen tulisi tehdä pyyntö osoitteeseen `/todolist.php`. Tämän jälkeen käsittely etenee samoin kuin *kuvassa 1*. 

Datan vastaanotto on pohjakoodissa valmiina:

{% highlight php %}

<?php 
...
$new_item = filter_input(INPUT_POST, 'item', FILTER_SANITIZE_SPECIAL_CHARS);
...
?>


{% endhighlight %}

<small>Listaus 6.</small>

*Listauksessa 6* käytetään [`filter-input`][filter-input] -funktiota, jolla voi suodattaa syötteestä haitallisia merkkejä. Jos suodatusta ei tapahdu, listauksen sijoitus on sama kun `$new_item = $_POST['item']`. Valmis, uuden tehtävän tietokantaan tallettava SQL-komento, on pohjakoodin määrittelemässä vakiossa `INSERT_ITEM`. Käsittely voidaan ohjata Todolist -sivulle käyttäen pohjakoodissa määriteltyä (`commonCode.php`) funktiota `redirect_to`.
 
[filter-input]: http://php.net/manual/en/function.filter-input.php


**Tehtävä poiston** käsittely tapahtuu lisäykseen verrattavalla tavalla.


#### Tietokantarajapinnasta

Tässä käytettävä tietokantarajapinta, PDO - [PHP Data Objects][pdoman], tarjoaa tietokantakäsittelylle kaksi luokkaa, [PDO][PDO] ja [PDOStatement][PDOStatement]. Näiden lisäksi käytettävissä on virhetilanteiden varalle luokka [PDOException][PDOException].

Tietokannan käsittelystä PDO-rajapinnalla on lyhyitä esimerkkejä esim. Ohjelmointiputkan [MySQL ja PHP][mjp] -oppaan luvussa [PHP ja PDO][pp]. Oppaan otsikossa mainitaan MySQL, mutta relaatiotietokannan käsittely on PDO:ta käyttäen samankaltaista esim. *SQLite*-tietokannan yhteydessä PDO-objektin muodostamisen jälkeen.

[mjp]: http://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=mysqlphp01
[pp]: http://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=mysqlphp02

Seuraavassa on Ohjelmointiputkan aineiston pohjalta joitakin lisäesimerkkejä.


#### Yhteys tietokantaan

~~~
$db = new PDO("sqlite:$kansio/$tietokanta");
~~~

*SQLite*-tietokannan yhteydessä yksinkertaisesti vain viitataan tietokantatiedostoon, joka muodostuu viittauksen myötä, jos tiedostoa ei vielä ole olemassa.

Jos SQLite:n PDO-ajuri ei ole aktivoitu, sen voi tehdä (yksinkertaisessa tapauksessa) Windows-ympäristössä poistamalla kommenttimerkit kahdelta `php.ini`-tiedoston riviltä:

~~~
...
extension_dir = "ext"
...
extension=php_pdo_sqlite.dll
...
~~~


#### Kyselyt

Välitön kysely ilman parametreja:

~~~
$query = $db->query(
           'SELECT * '
         . 'FROM tuote '
         . 'ORDER BY nimi');         
  
~~~

Kyselyn tulos muuttujaan oletusmuodossa:

~~~
$tuotteet = $query->fetchAll(); 
~~~

Kyselyn tulos muuttujaan parametrin määrittelemässä muodossa:

~~~
$tuotteet = $query->fetchAll(PDO::FETCH_ASSOC); 
~~~

Kyselyn suoritus kahdessa vaiheessa:

~~~
$query = $db->prepare(
           'SELECT * '
         . 'FROM tuote '
         . 'ORDER BY nimi');         

$query->execute();  
~~~

Parametrin sisältävä kysely:

~~~
$query = $db->prepare(
           'SELECT * '
         . 'FROM tuote '
         . 'WHERE nimi = :nimi');         

$query->execute([':nimi'=>'vasara']);  
~~~

Yhden rivin luku kyselyn palauttamasta tulosjoukosta:

~~~
$tuote = $query->fetch(PDO::FETCH_ASSOC); 
~~~

Tuloksen palautus tiettynä objektina:

~~~
...
$query->setFetchMode(PDO::FETCH_CLASS, Tuote::class);
$query->execute([':nimi'=>'vasara']);
$tuote = $query->fetch(PDO::FETCH_CLASS);   
~~~

#### Tietojen ylläpito

Rivin lisäys tauluun:

~~~
$stmt = $db->prepare(
          "INSERT INTO tuote (nimi, hinta) "
        . "VALUES (:nimi, :hinta)");

$stmt->execute([':nimi' => 'saha',':hinta' => 10]);
~~~

Lisätylle riville muodostuneen avaimen selvittäminen:

~~~
$id = $db->lastInsertId();
~~~

Rivin muutos:

~~~
$stmt = $db->prepare(
           'UPDATE tuote  '
         . 'SET hinta = :hinta '
         . 'WHERE id = :id');
 
$stmt->execute([':id' => $id, ':hinta' => 11]);
~~~

Rivin poisto:

~~~
$stmt = $db->prepare(
           'DELETE FROM tuote  '
         . 'WHERE id = :id');
 
$stmt->execute([':id' => $id]);
~~~


Esimerkkejä löytyy myös PHP:n [PDO-käsikirjasta][pdoman] eri metodien käsittelyn yhteydessä. Seuraavassa on joitakin keskeisiä [PDO][PDO]- ja [PDOStatement][PDOStatement]-luokkien metodeja: [PDO-objektin muodostin][construct], [query][query], [lastInsertId][lastInsertId], [prepare][prepare], [execute][execute], [fetch][fetch], [fetchAll][fetchAll] ja [setFetchMode][setFetchMode].

[pdoman]: http://php.net/manual/en/book.pdo.php
[construct]: http://php.net/manual/en/pdo.construct.php
[query]: http://php.net/manual/en/pdo.query.php
[lastInsertId]: http://php.net/manual/en/pdo.lastinsertid.php
[prepare]: http://php.net/manual/en/pdo.prepare.php
[execute]: http://php.net/manual/en/pdostatement.execute.php
[fetch]: http://php.net/manual/en/pdostatement.fetch.php
[fetchAll]: http://php.net/manual/en/pdostatement.fetchall.php
[setFetchMode]: http://php.net/manual/en/pdostatement.setfetchmode.php

[PDO]: http://php.net/manual/en/class.pdo.php
[PDOStatement]: http://php.net/manual/en/class.pdostatement.php
[PDOException]: http://php.net/manual/en/class.pdoexception.php


*SQLite*-tietokantaa voidaan käsitellä sovellusohjelmien ohella erilaisilla hallintatyökaluilla. Eräs tällainen työkalu on Firefoxin lisäosa [SQLite Manager](https://addons.mozilla.org/fi/firefox/addon/sqlite-manager/).



<br/><small>
Tehtävän lähteet: Homeworks [To-Do List][todo] & [To-Do List Extra Features][extra].<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[todo]: https://moodle2.tut.fi/mod/resource/view.php?id=320576
[extra]: https://moodle2.tut.fi/mod/resource/view.php?id=320577

[cse154]:https://courses.cs.washington.edu/courses/cse154/


<br/>