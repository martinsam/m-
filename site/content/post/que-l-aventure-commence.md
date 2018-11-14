Title:  Simplifier le passage des moteurs de recherche sur le fil d'Ariane
Slug: le-site-propose-un-fil-dariane
Date: 2016-09-07 14:47:05
Tags: seo, ariane, breadcrumbs
Category: quality
Author: Samuel Martin
Lang: fr
Summary: D'après [la checklist Opquast V3 N°153](https://checklists.opquast.com/oqs-v3/criteria/chaque-page-affiche-une-information-permettant-de-connaitre-son-emplacement-dans-larborescence-du-site) on peut lire ceci : « Chaque page affiche une information permettant de connaître son emplacement dans l'arborescence du site.» Dans les trois objectifs mentionnés intéressons-nous à celui consacré au moteur de recherche et laissons volontairement l'utilisateur de côté.



Ci-dessous l'illustration de la bonne pratique Opquast V3 N°159 - Chaque page affiche une information permettant de connaître son emplacement dans l'arborescence du site. 


<img src="{filename}/images/bp159.png" alt="Bonne pratique Opquast V3 N°159" width="600" height="205" />

On retrouve également cette bonne pratique côté Opquast SEO N°80 

![Bonne pratique Opquast SEO N°80]({filename}/images/bpseo80.png)




# Exemples
Voici trois illustrations permettant de visualiser le fil d'ariane

Sur le site de Castorama
![Capture d'écran Castorama - Fil d'ariane]({filename}/images/fil_ariane_casto.png)


Sur le site de Röcssti.net
![Capture d'écran Röcssti.net - Fil d'ariane]({filename}/images/fil_ariane_rocssti.png)


Sur le site de LeroyMerlin

![Capture d'écran LeroyMerlin - Fil d'ariane]({filename}/images/fil_ariane.png)




Mise à part des différences de présentation, rien ne ressemble plus à un fil d'ariane qu'un autre fil d'ariane. 

Du point de vue de la bonne pratique on pourrait en rester là et se féliciter du travail accompli. Malheureusement le moteur de recherche (GoogleBot et autre) a besoin d'un peu aide.

Voyons dans le paragraphe suivant comment passer de l'objectif naïf « Simplifier le passage des moteurs de recherche » à « Structurer le contenu pour le passage des moteurs de recherche »

# Enrichissement sémantique

Inutile de tergiverser, tout se passe du côté de la source HTML. Côté Castorama, pas la peine de perdre de temps, rien ne présente d'intérêt pour un crawler (GoogleBot ou autre).

## Micro-données 

Coté Rocssti.net et notamment sur la page [Röcssti-Builder, to build your CSS](https://rocssti.net/en/builder-css) on peut extraire ceci:

    :::html
    <span xmlns="http://www.w3.org/1999/xhtml" itemprop="itemListElement" itemscope="itemscope" itemtype="http://schema.org/ListItem">
     <a href="./" itemprop="item"><span itemprop="name">Home</span></a>
     <meta itemprop="position" content="1" />
    </span> 
    &gt; 
    <span xmlns="http://www.w3.org/1999/xhtml" itemprop="itemListElement" itemscope="itemscope" itemtype="http://schema.org/ListItem">
     <span itemprop="item">
      <span itemprop="name">Röcssti-Builder</span>
     </span>
     <meta itemprop="position" content="2" />
    </span>


+ L'attribut itemscope identifie et annonce des blocs qui seront balisés.
+ L'attribut itemtype permet de spécifier le type d'élément
+ L'attribut itemprop permet de spécifier les propriétés de l'élément

Grossièrement comprenez que chaque bloc est défini comme un élément de type liste et que chaque item à une position précise (content="1" ...). Oui j'avoue c'est redondant avec l'utilisation classique (ul ol li)

Côté LeroyMerlin, on retrouve la même approche sémantique avec cependant l'absence de poids.

    :::html
    <ul class="breadcrumb">
        <li><a href="/">Accueil</a></li>
       <li itemtype="http://data-vocabulary.org/Breadcrumb" itemscope=""> &gt; <a itemprop="url" href="/v3/p/produits-l1308218734"><i itemprop="title">Produits</i></a></li>
       
       <li itemtype="http://data-vocabulary.org/Breadcrumb" itemscope=""> &gt; <a itemprop="url" href="/v3/p/produits/cuisine-l1308216917"><i itemprop="title">Cuisine</i></a></li>
       
       <li itemtype="http://data-vocabulary.org/Breadcrumb" itemscope=""> &gt; <a itemprop="url" href="/v3/p/produits/cuisine/poubelle-tabouret-et-accessoires-de-cuisine-l1308216961"><i itemprop="title">Poubelle, tabouret et accessoires de cuisine</i></a></li>
       
       <li itemtype="http://data-vocabulary.org/Breadcrumb" itemscope=""> &gt; <span itemprop="title">Accessoires muraux de crédence</span></li>
    </ul>


L'équipe technique semble avoir suivi cette [documentation](https://www.bing.com/webmaster/help/markup-breadcrumbs-72419f3f).


Voilà et pour montrer que tout cela n'est pas de l'enculage de mouche au vinaigre voyons le résultat du côté de chez Google

# Résultats chez Google

![Capture d'écran Google - Fil d'ariane Rocssti]({filename}/images/google_rocssti_ariane.png)

![Capture d'écran Google - Fil d'ariane Rocssti]({filename}/images/google_leroy_ariane.png)

Le fil d'ariane était trop important donc il a été tronqué.
On remarque au passage **qu'il est bien dommage de ne pas avoir le fil d'ariane cliquable depuis Google n'est ce pas ?**


Bon allez cadeau pour la route  voici un exemple avec Alinea qui utilise le même balisage sémantique que LeroyMerlin.

![Capture d'écran Google - Fil d'ariane Alinea]({filename}/images/google_alinea_ariane.png)

# Allez plus haut ♬♬♬

En regardant l'extrait de Röcssti.net il est intéressant de se pencher sur la ressource [http://schema.org/BreadcrumbList](http://schema.org/BreadcrumbList)
qui à mon sens apporte un peu plus de valeur sémantique  que http://schema.org/ListItem.




