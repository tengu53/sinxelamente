---
layout: post
title: "Nové psací a blogové workflow?"
date: 2020-09-22 00:19:23
author: Edgar Walden
categories: [Werkzeug]
image: /assets/img/type.jpg
---

To vám bylo tak, prostě jsem celý blog přepracoval do statických stránek a nepoužívám už Wordpress. Web teď generuju pomocí generátoru Jekyll. A co je nejlepší, docela mě to baví.

Nové statické stránky jsou teď hodně rychlé. Samozřejmě něco mi tu chybí  - třeba zobrazování obrázků v lightboxu. Ale to se dá dodělat. Každopádně web teď běží v cloudu v sytému Netlify, který je pro malé nenáročné projekty zdarma. Jako vzhled jsem použil mírně upravenou šablonu [Lagrange](https://github.com/LeNPaul/Lagrange).

Docela radikálně se mi ale změnilo i celkové psací workflow ze schématu *Textový editor->Administrace Wodpressu ->Publikování* na *Textový editor -> Commit a push na Github*. Ačkoli to tak nevypadá, celkově je správa malého obsahového webu takto daleko jednodušší a má i několik dalších výhod.

## Od markdownu po cloud  

Už nějaký čas si píšu deník (neveřejný, takže tady není:-). Píšu ho v textovém formátu označkovaném **markdownem**. Postupem času mi markdown přešel nějak do krve a začal jsem ho používat taky třeba pro poznámky, krátké texty atd.

Pro psaní a značkování jsem používal editor s názvem **Ghostwriter**. Ten mi dobře běžel v Ubuntu, ale poté co jsem z pracovních důvodů přešel zpět na Windows 10, to nefungovalo tak dobře. Autor navíc Ghostwriter přestal pro Windows vyvíjet, takže jsem hledal náhradu a našel editor [**Typora**](https://typora.io/).

 ![typora](/assets/img/typora.jpg)

Ten má krásné minimalistické rozhraní a co je hlavní, umožňuje otevřít složku s texty, takže máte v bočním okně přehled o všech textech ve složce a můžete do ní přidávat další.

No a od toho už byl jen krůček předělat blog do statických stránek pomocí nástroje Jekyll. Ten je docela intuitivní a ve spojení s dalšími nástroji a službami může provoz malého webu s Jekyllem fungovat naprosto plynule - a bez CMS.:-).

S nějakým webovým tutoriálem se dá jednoduchý web s Jekyllem rozchodit odhadem za dvacet minut. Prakticky si musíte si do počítače jen nainstalovat jazyk Ruby a pak už je to pár příkazů v terminálu. Pokud se budete trochu vrtat v nastavení (což stejně budete muset:-) a použít nějakou jinou než výchozí šablonu , tak je rozchození malého obsahového projektu v Jekyllu se základními funkcemi otázkou jednoho večera. Třeba se o tom někdy rozepíšu víc.

### V praxi může příprava malého statického blogu vypadat třeba takto

1. Pomocí Jekyllu připravíme web (jsou na to [tutoriály](https://jekyllrb.com/docs/))
2. Uděláme repositář na Githubu s webem
3. Web publikujeme třeba na [Netlify](https://www.netlify.com/), který umožňuje automatickou aktualizaci z Githubu a spuštění Jekyllu (na Netlify jsou už jen hotové stránky, zdrojový kód zůstává v repozitáři)
4. V Typoře si pak na lokálním disku otevřeme složku s posty a zvesela sem přidáváme další texty
5. Pak už je potřeba to všechno comitnout a pushnout do repositáře a post postupně probublá až na web na Netlify. Samozřejmostí je provoz na vlastní doméně a na https...
6. Vtip je v tom, že na první tři body pak můžete zapomenout - děje se to automaticky.
7. Pokud uděláte jakékoli úpravy webu – třeba něco předěláte v šabloně, doplníte do Jekyllu další pluginy atd. – vše se automaticky aktualizuje taky. Jekyll má vlastní vývojový server, takže všechny úpravy si uděláte a prohlédnete nejdřív na lokále a jakmile jste spokojeni, všechno comitnete a nahrajete do repositáře.  Ke comitnutí a nahrání do repositáře můžete použít třeba aplikaci [Github Desktop](https://desktop.github.com/). Typora ukládá text sama a vy se jen musíte místo to postarat o tohle. Takže už žádné "ukládání dokumentu", ale jeho "comitnutí". Mimo jiné to zní víc cool. :-). Samozřejmě pokud děláte víc změn na webu, tak všechno comitnete najednou.  
8. No a je to zadarmo .-) Netlify má ve verzi zdarma nejspíš nějaká omezení, ale to vás asi při provozu malého blogu nemusí zajímat...
9. Na lokálním počítači a na GitHubu máte celou zálohu webu, takže když se někde něco pokazí, prostě ho publikujete jinde. Třeba na Cloudcanonu nebo na svém hostingu u nějaké lokální firmy, u kámoše na serveru atd...

### Typora má ale i další vychytávky

Typora umí mimo jiné hezky formátovat takzvaný *front matter* - údaje o textu a základní proměnné pro Jekyll.

Pokud do textu zkopírujete obrázek, nahraje se automaticky do vámi zvolené složky - třeba tam, kde ho najde Jekyll :-)

Dobře se v ní dělají odkazy - automaticky doplní URL ve schránce.
