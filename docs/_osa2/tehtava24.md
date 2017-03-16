---
layout: exercise_page
title: "Tehtävä 2.4: DOMWalker (1p)"
exercise_template_name: W2E04.DOMWalker
exercise_discussion_id: 78344
exercise_upload_id: 315778
---

Tehtäväpohjan tiedosto `index.html` sisältää [edelliseen tehtävään](../tehtava23) liittyvän merkkauksen `div`-elementin sisältönä (`id="perus-mooc"`). Elementin yläpuolella on painonappi sekä toinen `div`-elementti, jonka `id`attribuutin arvona on `dom-walker` (*Listaus 1*). 

{% highlight html %}
{% raw %}

    <body>
        <button onclick="walkDOM();">Walk DOM</button>        
        <div id="dom-walker"></div>
        <hr/>
        <div id="perus-mooc">
            <header>
                <h1>PerusMOOC &gt;&gt;</h1>
                <nav>
         ...
         <script src="./js/code.js"></script>
    </body>         
{% endraw %}
{% endhighlight %}
<small>Listaus 1.</small>

Laadi tiedostoon `js/code.js` funktio `walkDOM` siten, että painonappia klikkaamalla `div`-elementin (`id="dom-walker"`) sisällöksi muodostuu `p`-elementtejä seuraavasti:

{% highlight html %}
{% raw %}

  <div id="dom-walker">      
      <p>HEADER</p>
      <p>H1</p>
      <p>NAV</p>
      <p>UL</p>
      <p>LI</p>
      <p>A</p>
      ...
  </div>
{% endraw %}
{% endhighlight %}
<small>Listaus 2.</small>

*Listauksen 2* `p`-elementti rakentuu "*perus-mooc*" -elementin perusteella. `p`-elementin sisältönä on  "*perus-mooc*"-elementin nimi. `p`-elementtejä muodostuu yhteensä 23.

Tehtävän ratkaisussa ei ole tarkoitus soveltaa `textContent`- eikä `innerHTML` -ominaisuuksia. Elementin nimi löytyy attribuutista [`tagName`][tagName].

[tagName]: https://developer.mozilla.org/en-US/docs/Web/API/Element/tagName

**Palauta** tehtävän ratkaisuna tiedosto `code.js`. Varmista ennen palautusta, että tehtäväpohjassa oleva sivu `testaa.html` ei esitä virheilmoituksia. 

<br/>

<small>
Tehtävän lähde: [Web-selainohjelmointi][weso], Helsingin yliopisto, Tietojenkäsitelytieteen laitos.
Creative Commons BY-NC-SA. (alkuperäistä tehtävää muokattu)
</small>

[weso]: http://web-selainohjelmointi.github.io/


