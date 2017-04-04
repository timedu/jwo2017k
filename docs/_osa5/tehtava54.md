---
layout: exercise_page
title: "Tehtävä 5.4:  Elokuva-arvostelu, files (4p)"
exercise_template_name: "W5E04.ElokuvaArvostelu-files"
exercise_discussion_id: 80017
exercise_upload_id: 318825
---

[Tehtävässä 5.3](../tehtava53) elokuvaan liittyvät tiedot oli asetettu valmiiksi muuttujan `$movie` arvoksi. Tässä tehtävässä tiedot ovat tiedostoissa, joista ne on luettava `$movie`- muuttujaan tulostusta varten.

Tiedostot löytyvät elokuvittain tehtäväpohjan `data`-hakemistosta. Elokuvan nimi, julkaisuvuosi ja yleisarvio on talletettu tiedostoon `info.txt`. Elokuvan yleiskuvaukseen liittyvät tiedot löytyvät tiedostosta `overview.txt`. Jokainen arvostelu on omassa tiedostossaan (`review*.txt`). 

Laadi tarvittava PHP-koodi tiedostoon `data/get_movie.php`, jonka `show_movie.php` ottaa käyttöönsä `include`-lauseella. `film`-parametrin lisäksi `show_movie.php`-skriptille voidaan tässä antaa parametri `reviews`, joka määrää, kuinka monta arviota elokuvasta  esitetään. Jos parametria ei anneta, parametri on nolla tai sen arvo ylittää arvioiden kokonaismäärän, sivulla esitetään kaikki arviot.

Kun tehtäväpohjaan kopioidaan tehtävien [5.1](../tehtava51) ja [5.3](../tehtava53) ratkaisut (`css/styles.css`, `tmpl/*.php`) pyynnön osoiteeseen `http://localhost:8000/show_movie.php?film=tmnt` tulisi tuottaa selaimeen edellisiä tehtäviä vastaava näkymä. Tehtäväpohjassa on sivu `index.html`, jossa on linkkejä `show_movie.php`-tiedostoon erilaisilla parametreilla.

**Palauta** tehtävän ratkaisuna tiedosto `get_movie.php`.

Seuraavat PHP-elementit saattavat antaa tukea ratkaisulle:
[array_push][array_push],
[count][count],
[explode][explode],
[file][file],
[foreach][foreach],
[glob][glob],
[list][list],
[min][min].


[array_push]: http://php.net/manual/en/function.array-push.php
[count]: http://php.net/manual/en/function.count.php
[explode]: http://php.net/manual/en/function.explode.php
[file]: http://php.net/manual/en/function.file.php
[foreach]: http://php.net/manual/en/control-structures.foreach.php
[glob]: http://php.net/manual/en/function.glob.php
[list]: http://php.net/manual/en/function.list.php
[min]: http://php.net/manual/en/function.min.php


<br/><small>
Tehtävän lähtökohtainen aineisto: Homeworks Movie Review & Movie Review Part Deux.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

<br/>

[cse154]:https://courses.cs.washington.edu/courses/cse154/

