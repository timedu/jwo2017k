---
layout: exercise_page
title: "Tehtävä 5.3:  Elokuva-arvostelu, templates (4p)"
exercise_template_name: "W5E03.ElokuvaArvostelu-templates"
exercise_discussion_id: 80016
exercise_upload_id: 318824
---

[Edellisen tehtävän](../tehtava52) tiedosto `index.php` on tässä nimelä `show_movie.php`. Tiedoston alkuun on lisätty `include`-lause, jonka viittaaman tiedoston määrää pyynnölle annettu `film`-parametri:

{% highlight php %}

<!DOCTYPE html>
<?php include "./data/" . filter_input(INPUT_GET, 'film') . "/movie.php"; ?>
<html>
  ...
</html>

{% endhighlight %}

<small>Listaus 1.<small>

Jos pyyntö on `http://localhost:8000/show_movie.php?film=tmnt`, `include`-lause viittaa tiedostoon `./data/tmnt/movie.php`, joka sisältää muuttujan `$movie` määrittelyn seuraavasti:

{% highlight php %}


    <?php

$movie = [
    'id' => 'tmnt',
    //
    'name' => 'TMNT',
    'year' => 2007,
    'score' => 33,
    //
    'overview' => [
        'starring' => 'Patrick Stewart<br/>'
        . 'Mako<br/>'
        . 'Sarah Michelle Gellar<br/>'
        . 'Kevin Smith',
        'director' => 'Kevin Munroe',
        ...
    ],
    //
    'review_count'=> 8,
    'reviews' => [
        [
            'review' => "Ditching the cheeky, self-aware wink that helped to "
            . "excuse the concept's inherent corniness, the movie attempts "
            . "to look polished and 'cool,' but the been-there animation can't "
            . "compete with the then-cutting-edge puppetry of the 1990 "
            . "live-action movie.",
            'score' => 'ROTTEN',
            'critic' => 'Peter Debruge',
            'publication' => 'Variety'
        ],
        [
            'review' => "TMNT is a fun, action-filled adventure that will "
            . "satisfy longtime fans and generate a legion of new ones.",
            'score' => 'FRESH',
            'critic' => 'Todd Gilchrist',
            'publication' => 'IGN Movies'
        ],
        ...
    ]
];


{% endhighlight %}

<small>Listaus 3.<small>

Muokkaa [edellisessä tehtävässä](../tehtava52) laatimiasi tiedostoja siten, että ne eivät sisällä suoraan elokuva- ja arvostelutietoja vaan viittaavat muuttujaan `$movie`. Muutosten jälkeen selaimen esittämä näkymä on sama kuin edellisissä tehtävissä esillä ollut näkymä tehtäessä pyyntö osoitteeseen `http://localhost:8000/show_movie.php?film=tmnt`. Kun pyyntö tehdään parametrilla `princessbride`, näkymä vastaa [oheistettua kuvaa][vaihe4a2]. 

Sivun sisältöalueen bannerissa oleva kuva määräytyy elokuvan yleisarvion `$movie['score']` perusteella. Jos yleisarvio on vähintään 60, kuva on `freshlarge.png`, muutoin  `rottenlarge.png`. Vastaava koskee sivuun liittyvää ikonia (`fresh.png`/`rotten.png`)[^1]. 

[vaihe4a2]: https://moodle2.tut.fi/mod/resource/view.php?id=318754

[^1]: Ikonin määrää tiedostossa `tmpl/page_title.php` oleva koodi. 

**Palauta** tehtävän ratkaisuna zip-arkistoituna `tmpl`-kansio.


#### Vihjeitä ja lisätietoja

Tehtävän lähtökohdaksi kannattanee kopioida tehtäväpohjaan tiedosto `css/styles.css` [tehtävän 5.1](../tehtava51) ratkaisusta ja tiedostot `tmpl/*.php` [tehtävän 5.2](../tehtava52) ratkaisusta.

Käytä tulostukseen liittyviin muuttujaviittauksiin PHP:n lausekelohkoa (`<?= ... ?>`). Esim. seuraavassa on tiedostoon `content_footer.php` tuleva ratkaisu, jossa sovelletaan lausekelohkoa:

{% highlight php %}

<div class="footer">
    (1-<?=count($movie['reviews'])?>) of <?=$movie['review_count']?>
</div>

{% endhighlight %}

Elokuvan yleiskuvaukseen liittyvä kuva `overview.png` löytyy nyt `img`-kansion sijaan kansiosta `data/tmnt` (ja `data/princessbride`). 

Älä tulosta PHP:n lauseita käyttäen `HTML`-tageja. Esim. luvuista 0-9 muodostuvan luettelon rakentaminen sujuu seuraavaan tyyliin: 

{% highlight php %}

<ul>
    <?php for ($i = 0; $i < 10; $i++): ?>            
        <li><?= $i ?></li>                
    <?php endfor; ?>
</ul>

{% endhighlight %}

Edellisessä listauksessa `<li>`-tagia ei muodosteta PHP:n avulla. Listaus käyttää myös ohjausrakenteiden vaihtoehtoista syntaksia, jossa ohjausrakenteeseen liittyvää lohkoa ei merkitä aaltosuluilla vaan lohkon päättyminen ilmaistaan avainsanalla (tässä: `endfor`). Vaihtoehtoisen syntaksin käyttö lienee luontevaa erityisesti upotettaessa PHP -koodia HTML -merkkaukseen.


<br/>

<small>
Tehtävän lähtökohtainen aineisto: Homeworks Movie Review & Movie Review Part Deux.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[cse154]:https://courses.cs.washington.edu/courses/cse154/

<br/>


