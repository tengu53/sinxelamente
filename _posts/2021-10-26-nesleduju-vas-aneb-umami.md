---
layout: post
title: "Web bez cookies s trochou Umami"
Author: Edgar Walden
description: "Možná si někdo všiml, že na mém blogu chybí takové to otravné vyskakovací okno s hláškou, že máte odsouhlasit všechna cookies. Není to chyba, nýbrž vlastnost. Tento web vám totiž žádnou sušenku do prohlížeče neukládá."
categories: [Werkzeug, tech]
tags: [web, wekzeug, tech]
---

Možná si někdo všiml, že na mém blogu chybí takové to otravné vyskakovací okno s hláškou, že máte odsouhlasit všechna cookies. Není to chyba, nýbrž vlastnost. Tento web vám totiž žádnou "sušenku" do prohlížeče neukládá.

Povinnost informovat návštěvníka webu o uložení cookies je už tady s námi řadu let. A výsledkem jsou ty otravné hlášky, které musíte před čtením webu odsouhlasit. Legislativa ohledně cookies se ale nyní mění/zpřísňuje a zatímco dosud stačilo jen informování uživatele a jeho souhlas, že to prostě bere na vědomí, v budoucnu to tak jednoduché nebude. Návštěvník webu bude muset **nejdříve aktivně souhlasit** s použitím cookies a pak teprve se bude řešit, co akceptuje a co ne. A nakonec si teda bude moci prohlédnout navštívenou stránku. Zkrátka daleko větší **opruz**. No a to byl jeden z důvodů, proč zamyslet se nad tím, zda jsou vůbec cookies potřeba.

Pokud jde o běžný obsahový web, jako je blog, webový magazín nebo tak něco, největší potřeba ukládat cookies asi přichází s nástroji pro analýzu návštěvnosti. Pokud na web implementujete Google Analytics v základním nastavení, cookies se lidem ukládat budou a vy musíte také pořešit zmíněné okénko a v budoucnu i explicitní souhlas s jejich použitím. Anebo je zde cesta cookies návštěvníkům neukládat, kterou jsem zvolil já. Toto řešení má své výhody i nevýhody:

- Všechny zmíněné věci okolo ukládání cookies můžete pustit z hlavy.
- Web je pro návštěvníka méně komplikovaný
- Můžete mít lepší pocit, že více respektujete soukromí návštěvníků.
- No a nevýhody? Sledování návštěv nebude tak přesné, protože kvůli absenci cookies dobře nerozlišíte unikátní návštěvníky od těch, kteří se vrací. 

A jak tedy sledovat návštěvy webu bez cookies? Jednou z možností je modifikace skriptu Google Analytics tak, aby cookies neukládal. Jde o následjící modifikaci kódu skriptu (přidáte to "*storage: none*"):

```
ga('create', 'UA-XXXXX-Y', {
  'storage': 'none'
});
```

Více informací najdete **[třeba tady](https://developers.google.com/analytics/devguides/collection/analyticsjs/cookies-user-id#disabling_cookies)**.

## Chce to trochu Umami

Ale nebyl bych to já, abych si nezvolil trochu těžší ale zajímavější cestu a nezkusil nějaký jiný analytický nástroj. Těch je docela spousta - namátkou třeba **Plausible**, **Matomo**, **Fathom** nebo právě **Umami**. Většinou jde o placené nástroje (a ne zrovna levné), některé jsou ale zdarma, pokud si je implementujete na svůj server. Už dlouho mám na hraní malý server na **[Digitalocean.com](https://m.do.co/c/06f877040b93)**, takže se to přímo nabízelo. Vyzkoušel jsem Umami.

Instalace není složitá, využijete k tomu *Docker Compose*, webový server *Nginx* a *databázi*. A musíte mít také k dispozici nějakou doménu - třeba něco takového: *"umami.blabla.cz"*, která bude ukazovat na váš server. Návod na instalaci [Umami](https://umami.is/) na server na Digitaloceanu najdete **[tady](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)**. Pokud už vám na severu běží Docker, Docker Compose a Nginx, je to otázka cca půl hodiny.  

## Co umí Umami?

Samozřejmě,  Umami daleko jednodušší než mnohem komplexnější Google Analytics, ale pro základní metriky bohatě postačí. Nové návštěvníky od vracejících se rozlišuje pomocí hashe, který spočítá z jejich IP adresy, údajů o prohlížeči a bůhvíčeho dalšího. Je to asi méně přesné, než cookies, ale v podstatě to stačí. 

Jinak Umami nabízí všechny důležité základní metriky - počet návštěv, počet shlédnutých stránek, bouncerate, čas na stránce, zobrazený obsah, systém a prohlížeč, jednoduché geografické údaje + sloupcové grafy. Umožňuje také sledování různých *událostí*, jako je kliknutí na cokoli, stažení souborů, přehrání videí atd. Takže pokud do toho chcete zabřednout, můžete. 

Jak už jsem povídal, Umami neukládá cookies, je plně v souladu s GDPR, je rychlé a má příjemné uživatelské prostředí. 

Co mi trochu chybí je export dat do CSV (nebo jsem ho zatím nenašel), ale všechna data máte v databázi na serveru, takže by se s nimi dalo všemožně pracovat jinými nástroji. Také zde nenajdete demografické metriky, data není možné segmentovat a nelze je porovnávat s předchozím obdobím ani meziročně. Umami je ale podle všeho aktivně vyvíjeno, takže je možné, že se dalších funkcí v dohledné době dočkáme. Podle autora je hlavní záměrem kromě vetšího respektu k soukromí také přehlednost a jednoduchost, takže uvidíme.      