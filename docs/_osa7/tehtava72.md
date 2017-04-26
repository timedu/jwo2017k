---
layout: exercise_page
title: "Tehtävä 7.2: Tehtävälista, SQL"
exercise_template_name: 
exercise_discussion_id: 
exercise_upload_id: 
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



<br/><small>
Tehtävän lähteet: Homeworks [To-Do List][todo] & [To-Do List Extra Features][extra].<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[todo]: https://moodle2.tut.fi/mod/resource/view.php?id=320576
[extra]: https://moodle2.tut.fi/mod/resource/view.php?id=320577

[cse154]:https://courses.cs.washington.edu/courses/cse154/


<br/>