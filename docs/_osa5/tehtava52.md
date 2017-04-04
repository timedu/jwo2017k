---
layout: exercise_page
title: "Tehtävä 5.2:  Elokuva-arvostelu, includes (1p)"
exercise_template_name: "W5E02.ElokuvaArvostelu-includes"
exercise_discussion_id: 80015
exercise_upload_id: 318823
---

Tehtäväpohjassa on [edellisen tehtävän](../tehtava51) merkkausta vastaava tiedosto `_index.html` sekä seuraavanlainen tiedosto `index.php`:

{% highlight php %}

<!DOCTYPE html>
<html>

  <head>
  
    <?php include './tmpl/page_title.php'; ?>
    
    <meta name="description" content="Rancid Tomatoes movie reviews"/>
    <meta name="keywords" content="movie review"/>
    <meta charset="UTF-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <link rel="stylesheet" type="text/css" href="./css/styles.css"/>
    
  </head>

  <body>

    <?php
    include './tmpl/page_banner.php';
    include './tmpl/page_heading.php';
    ?>
    
    <div id="content"> 
    
      <?php
      include './tmpl/content_banner.php';
      include './tmpl/movie_overview.php';
      include './tmpl/movie_reviews.php';
      include './tmpl/content_footer.php';
      include './tmpl/content_banner.php';
      ?>
    
    </div>
    
    <?php include './tmpl/page_banner.php'; ?>
    
  </body>

</html>

{% endhighlight %}

Jaa tiedoston `_index.html` sisältöä kansiossa `tmpl` oleviin tiedostoihin `page_title.php`, `page_banner.php`,  `page_heading.php` jne. siten, että tiedostoon `index.php` kohdistuva pyyntö tuottaa selaimeen saman näkymän kuin pyyntö tiedostoon `_index.html`. (Voit halutessasi kopioida [edellisen tehtävän](../tehtava51) ratkaisusi `css`-kansioon, jolloin näkymä lienee hieman tyylikkäämpi).


**Palauta** tehtävän ratkaisuna zip-arkistoituna `tmpl`-kansio.


Ratkaisussa tiedosto `page_title.php` sisältää `title`-elementin ja ikoniin viittaavan `link`-elementin. Tiedostossa `page_heading.php` on `h1` -elementti. Muissa tiedostoissa on sisältöineen yksi `div`-elementti.

<br/>

<small>
Tehtävän lähtökohtainen aineisto: Homeworks Movie Review & Movie Review Part Deux.<br/> 
[Web Programming][cse154], University of Washington, Computer Science & Engineering.<br/>
Copyright © Marty Stepp / Jessica Miller, licensed under Creative Commons Attribution 2.5 License.
</small>

[cse154]:https://courses.cs.washington.edu/courses/cse154/

