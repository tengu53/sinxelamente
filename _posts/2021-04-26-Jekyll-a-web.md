---
layout: post
title: Seznamte se s Jekyllem
date: 2021-04-26 00:00:23
author: Edgar Walden
tags: [Werkzeug]
image: /assets/img/typewriter.jpg
---
O generátorech statických webů jsem se poprvé dočetl nejspíš na webu Maxiorel.cz. Honza Polzer takto udělal jeden web pomocí generátoru [Hugo](https://gohugo.io/), a prý to s drobnými obtížemi pro malý projekt funguje. Tvořit přímo statické webové stránky bez nutnosti dalších technologií na serveru (PHP, MySQL) mi už tehdy přišlo docela cool. Mám totiž rád jednoduché věci, které dělají právě to co mají.  Nic méně ale i nic více. Třeba proto tento post píšu v [editoru Typora](https://typora.io/) a ne třeba ve Wordu. Právě proto mě myšlenka generovat statické stránky docela zaujala. Takovýto web je také super rychlý a taky nehacknutelný (no aspoň myslím).

Obecně si myslím, že jde o trend, a v podstatě si nedovedu představit třeba produktovou mikrosite nebo malý osobní web, který by byl udělán jinak, než pomocí generátoru. Generátor statických stránek prostě pro tyto případy ideální a používat v tomto případě Wordpress asi nemá smysl. I když je možné to udělat tak, že se Wordpress použije jenom jako backend a statické stránky se vygenerují nějakým pluginem. Někde na webu jsem na to viděl pěknou případovku a možná to někdy jen tak z legrace zkusím.  

Generátorů statických webů je spousta. Ty, které jsem jen tak letmo viděl, pracují přibližně na podobném principu:

1. Nainstalujete potřebný generátor
2. Někde něco nakonfigurujete, aby systém věděl, jak se bude web jmenovat atd.
3. Někam připravíte obsah - většinou v nějak formátovaném textu + obrázky.
4. Uděláte šablonu nebo použijete už hotovou
5. Spustíte generátor
6. V nějakém výstupním adresáři pak najdete vygenerovaný web, který pak někde publikujete.

Mezi nejpoužívanější generátory statických webů patří [Jekyll](https://jekyllrb.com/), napsaný v jazyce Ruby a využívá systém knihoven kódu - gems. Pokud se budete chtít s Jekyllem kamarádit trochu víc, chtě nechtě do toho trochu zabřednete, ale není to na škodu. Každopádně práce s Jekyllem je docela jednoduchá. Musíte nejdřív nainstalovat jazyk Ruby. V Ubuntu zadáte:

    sudo apt-get install ruby-full build-essential zlib1g-dev

A pak ještě v souboru .bashrc nastavíte cestu k adresáři, do něhož se budou přidávat jednotlivé gems:

    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

Ve Windows na to existuje instalátor, kde vše probehne +- samo. Pak už v terminálu zadáte:

    gem install jekyll bundler

A můžete se do toho pustit.

Ale cílem textu není ani tak poskytovat návod k Jekyllu. Na webu je spousta tutoriálů a běžně zručný člověk to bez problémů zvládne. Spíš mě zajímají výhody této technologie a pracovní workflow.

## Wordpress je mnohdy zbytečný

Nedávno jsem se nachomýtl k přípravě malého webu pro jednu instituci. Šlo o jednoduchý jednostránkový web s pár informacemi, trochou textů a obrázky. Ani se nepočítalo s tím, že by obsah na webu nějak závratně přibýval, a když už, šlo by spíš jen o drobné updaty typu *změny kontaktních údajů* atd. 

Web byl řešen na Wordpressu s jakýmsi docela komplikovaným pluginem, který udělal ten jednostránkový web. Výsledkem byl sice funkční, ale značně pomalý web, přičemž jsme nevyužili hlavních výhod Wordpressu (správa autorů, správa obsahu, diskuse atd.). Právě naopak jsme (teda my ne, vývojář :-)) web zatížili nevýhodami Wordpressu, jako je dlouhé načítání stránek, hacknutelnost, potřeba updatů atd. V době, kdy vyhledávače značně preferují rychlost načítání webu, to rozhodně není nejlepší řešení.

Naopak dobrý generátor statických webů by zde byl mnohem vhodnější. Vytvoří totiž samotné stránky, které pak server zobrazuje, bez nutnosti dotazů do databáze, šablonovacího systému atd. Stránky je pak možné hostovat třeba na nějaká CDN, jako je Netlify, přičemž pro jejich deployment na CDN slouží třeba GitHub. Pro netechnicky orientovaného čtenáře to možná zní složitě, ale průměrný foxteriér se to naučí za odpoledne. Fakt.

Velkou výhodou takového řešení je také dobrá škálovatelnost. Třeba na [Netlify](https://www.netlify.com/) je možné začít s verzí zdarma, pak při ostrém nasazení jít do nějakého základního tarifu a ten pak případně podle rostoucího provozu zvyšovat. Netlify umí pořešit i sběr dat z kontaktních formulářů na stránkách a jejich export do CSV, což je dobré. 

Při diskusi v naší agentuře, jsme ale přišli na některé další nevýhody. Web samozřejmě potřebuje grafiku a kodéři jsou zvyklí spíš na ten Wordpress. Takže může být těžší sehnat na takový projekt vhodné pracovní síly. I tak ale může jít o zajímavé a praktické řešení. Ostatně na Jekyllu a CDN Netlify běží i tento blog a plánuju takto i další malý obsahový projekt.   





