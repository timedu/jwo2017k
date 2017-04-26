---
layout: exercise_page
title: "Tehtävä 7.1: Tehtävälista, Files"
exercise_template_name: 
exercise_discussion_id: 
exercise_upload_id: 
---

Rakenna tehtävälista-sovellus täydentämällä oheista [NetBeans-projektirunkoa][pohja][^1]. Seuraava kaavio esittää joukon sovelluksen moduuleista, joista tässä laaditaan `prepareStart.php`, `prepareTodolist.php`, `doInsert.php` ja `doDelete.php`. Muut moduulit ovat pohjassa valmiina. Keskeisiä tehtävässä esille tulevia asioita ovat *tiedostokäsittely*, *istunnot* ja *evästeet*.

[pohja]: https://moodle2.tut.fi/mod/resource/view.php?id=320530

[^1]: Tässä tehtävässä projektirunko on Moodlessa.


![Moduulikaavio](../img/part7-ex7.1.png "Moduulikaavio"){: style="display: block; margin: auto; margin-top: 10px;"}

<small>Kuva 1.</small>


Sovelluksen käyttöliittymä muodostuu kahdesta sivusta, [`start.php`][start] ja [`todolist.php`][todolist]. *Start*-sivulla kirjaudutaan sovellukseen ja *Todolist*-sivun kautta lisätään ja poistetaan tehtäviä. 

[start]: https://moodle2.tut.fi/mod/resource/view.php?id=320528
[todolist]: https://moodle2.tut.fi/mod/resource/view.php?id=320527


Käyttäjä suorittaa kirjautumisen syöttämällä käyttäjätunnuksen ja salasanan *Start*- sivulla oleviin tekstikenttiin, ja klikkaamalla sen jälkeen kenttien alapuolella olevaa painonappia. Jos annettu käyttäjätunnus on sovelluksen tiedossa, sovellus tuo käyttäjälle esiin *Todolist* -sivun, jos annettu salasana täsmää rekisteröityyn salasanaan. Jos käyttäjätunnus -kenttään syötettyä tunnusta ei ole vielä rekisteröity, rekisteröi sovellus uuden käyttäjän ja tuo esiin *Todolist* -sivun edellyttäen, että salasanakenttään syötetty merkkijono on oikeaa muotoa. Jos kirjautuminen ei onnistu, *Start*-sivulle ilmestyy ongelmaa kuvaava virheilmoitus.

*Todolist* -sivun kautta voidaan suorittaa uuden tehtävän lisääminen ja olemassa olevan tehtävän poistaminen sekä uloskirjautuminen sovelluksesta. Tehtävää ei lisätä, jos sille ei ole annettu tekstiä. 

#### Tiedostot sekä istuntoon ja evästeeseen talletettavat tiedot

Käyttäjätunnukset ja salasanat ovat tiedostossa `data/users.txt` ja käyttäjäkohtaiset tehtävälistat tiedostoissa `data/todo_<user>.txt`[^2]. Kirjautuneen käyttäjän tunnus on *istunnossa* avaimella `user`. Viimeisin kirjautumisaika on *evästeessä* avaimella `last_login`. Kirjautumiseen liittyvät virheilmoitukset välitetään *istunnossa* avaimella `message`.

[^2]: Tehtäväpohjassa on esimerkit tiedostoista. 

#### Laadittavista moduuleista

*Start*-sivu ottaa käyttöönsä moduulin `php/prepareStart.php`. Sivu viittaa muutuujiin `$last_login` ja `$message` (viimeinen kirjautumisaika ja mahdollinen virhelimoitus), jotka *prepareStart* asettaa.  *prepareStart* myös ohjaa käsittelyn suoraan *Todolist*-sivulle, jos käyttäjä on jo kirjautuneena, sekä poistaa istunnosta mahdollisen virheilmoituksen. 

*Todolist*-sivu ottaa käyttöönsä moduulin `php/prepareTodolist.php`. Sivu viittaa muutuujiin `$last_login`, `$user` ja `$items` (viimeinen kirjautumisaika, kirjautunut käyttäjä sekä käyttäjän tehtävälistan tehtävät), jotka *prepareTodolist* asettaa.  *prepareTodolist* myös ohjaa käsittelyn *Start*-sivulle, jos käyttäjää ei ole kirjautuneena. 

Moduuli `php/doInsert.php` lisää kirjautuneen käyttäjän tehtävälistaan *Todolist*-sivun välittämän uuden tehtävän sekä ohjaa käsittelyn takaisin *Todolist*-sivulle. Moduuli `php/doDelete.php` poistaa kirjautuneen käyttäjän tehtävälistasta  tehtävän, jonka indeksin *Todolist*-sivu välittää sekä ohjaa käsittelyn takaisin *Todolist*-sivulle. Jos näihin moduuleihin kohdistuu pyyntö siten, että käyttäjää ei ole kirjautuneena, moduulit ohjaavat käsittelyn *Start*-sivulle.


**Palauta** tehtävän ratkaisuna tiedostot `prepareStart.php`, `prepareTodolist.php`, `doInsert.php` ja `doDelete.php`.

### Vihjeitä ja lisätietoja

`php`-kansiossa olevat moduulit ottavat käyttöönsä moduulin `php/commonCode.php`, joka käynnistää istunnon. Moduuli sisältää myös funktiot `redirect_to`, jolla voidaa ohjata käsittely toiselle sivulle, sekä `debug`, jolla voidaan tulostaa tietoja NetBeansin *Output*-ikkunaan.

*Istunnoista* ja *evästeista* löytyy tiivis esitys esim. Ohjelmointiputkan [PHP-oppaasta][putka-1]. Tehtäväpohjan moduuli `php/doLogin.php` tallettaa arvoja istuntoon sekä asettaa evästeen.

Tarvittava tiedostokäsittely sujunee jouhevimmin käyttäen funktioita [file][file] ja
[file_put_contents][file_put_contents]. Funktiota [file_exists][file_exists] käyttämällä vältyttäneen tietyistä virheilmoituksista. Funkioiden käytöstä löytyy esimerkkejä esim. Ohjelmointiputkan [materiaalista][putka-2] ja tehtäväpohjan moduulista `php/doLogin.php`.


[file_exists]: http://php.net/manual/en/function.file-exists.php
[file]: http://php.net/manual/en/function.file.php
[file_put_contents]: http://php.net/manual/en/function.file-put-contents.php

[putka-1]: https://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=php_11
[putka-2]: https://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=php_09

<br/><small>
Tehtävän lähteet: Homeworks [To-Do List][todo] & [To-Do List Extra Features][extra].<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[todo]: https://moodle2.tut.fi/mod/resource/view.php?id=320576
[extra]: https://moodle2.tut.fi/mod/resource/view.php?id=320577

[cse154]:https://courses.cs.washington.edu/courses/cse154/



<br/>