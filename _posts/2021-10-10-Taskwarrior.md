---
layout: post
title: "Taskwarrior — minimalistický To-Do list"
date: 2021-10-10 00:19:23 +0100
author: Edgar Walden
categories: [Werkzeug]
---

Nedávno se mi podařilo díky blogu Maxiorel.cz objevit To-Do aplikaci pro příkazovou řádku **Taskwarrior**. Na svém domácím počítači používám Linux, takže nebyl problém s jejím vyzkoušením. A líbí se mi tak moc, že že jsem ji poměrně snadno implementoval do svého pracovního života. Ačkoli se jedná o CLI aplikaci, kterou musíte spustit v Terminálu, práce s ní je překvapivě jednoduchá a intuitivní.

![Image for post](https://miro.medium.com/max/701/1*yC7U8gZ07l-n9DDW5TEl5g.jpeg)

Zobrazení úkolů v projektu

Obecně mám rád minimalistické věci a raději využívám jednoduché jednoúčelové nástroje. V tom mi obecně Linux vyhovuje. **Taskwarrior** jde v tomto na dřeň. Prostě jedním příkazem úkol zadáte i se všemi parametry a je to. Nemám rád vyplňování formulářů a neustálé klikání do různých vstupních polí, takže v tomto směru je to pro mě ok.

Taskwarrior nainstalujete běžným způsobem (v Ubuntu Linuxu třeba *sudo apt install task*) a pak už jen můžete v terminálu přidávat a upravovat úkoly. Základní příkaz je *task* — vypíše vám seznam úkolů v jednotlivých projektech, jejich deadliny, popisky a prioritu.

Přidání úkolu uděláte příkazem *task add*, přičemž příkaz vypadá nejčastěji nějak takto:

>task add Nový úkol project:Názevprojektu due:datum

Pokud jste název projektu ještě nepoužili, projekt se založí. Datum se nejspíš musí použít v nějakém formátu — asi YYYY-MM-DD. Osobně ale datum nezadávám a používám *due:eod* (splnění dnes) *due:eow* (do konce týdne) a *due:eom* (do konce měsíce). Tyto zkratky jsou dostatečně signifikantní, aby si je jeden zapamatoval.

**Moje workflow s taskwarriorem vypadá nějak takhle:**

1. Přidám úkol pomocí *task add*
2. Zobrazím seznam úkolů pomocí *task*
3. Případně modifikuju úkoly pomocí *task X modify* — X je ID úkolu, které vidíte ve výpisu příkazu *task*
4. Pokud je úkol splněn, zadám *task x done*
5. Občas se dívám, jak se vše daří pomocí příkazu *task burndown.daily* — zobrazí graf s množství splněných a neplněných věcí
6. Jakmile vím, že úkolníček chvíli nebudu používat, zadám *task sync*, aby se vše synchronizovalo se serverem — viz dále.

Taskwarrior toho samozřejmě umí daleko víc. Umí třeba zobrazit kalendář (příkaz *task calendar*), v němž vidíte termíny různých úkolů. Zobrazení seznamů můžete různě filtrovat — třeba podle projektů nebo data. Dá se nějak trackovat čas (*task X start*) a vůbec dělat další fůra věcí.

Pro tento nástroj navíc existuje spousta pluginů a frontendů. Obecně mi ale zatím stačí jen tak, jak je v základní instalaci. Co je ale důležitější, je možné ho synchronizovat se serverem. Spousta lidí totiž samozřejmě pracuje na více počítačích — typicky doma v práci. A je asi dobré mít všude to-do list synchronizován.

Možností, jak na to, je víc. Je možné někde rozjet něco, co se jmenuje Taskwarrior Server, možná je i synchronizace přes služby typu Dropbox. Podařilo se mi ale najít službu **Freecinc.com**, která umožňuje Taskwarrior snadno a kupodivu zdarma synchronizovat. Nastavení je jednoduché a aplikace Freecinc.com vám poskytne personalizovaný a dostatečně blbovzdorný návod. Vše spočívá v nakopírování pár souborů s certifikáty do adresáře *~/.taskrc* a provedení pěti příkazů. Stránku s návodem si ale pak musíte uložit pro provedení téhož na všech vašich dalších počítačích. A pak nesmíte zapomenout na příkaz *task sync*. Ale pokud uděláte trochu víc změn v úkolech, program vás na nutnost synchronizace upozorní. No a služba je zdarma, takže samozřejmě bez záruky.

**Pár dalších tipů:**

Zadávejte úkoly včetně *due* a *project* a případně *priority*. Čím víc Taskwarrior o úkolu “ví”, tím lépe je prioritizuje a funguje jako takový inteligentní připomínač.

Práce s nástrojem je překvapivě rychlá. Čas od času si sednu a hážu sem úkoly, co mě napadnou. Vše kontroluju příkazem *task*.

Taskwarrior je jen pro Linux (aspoň si to myslím), ve Windows ho používám pomocí WSL — mám tam nainstalované Ubuntu a puštěný Terminál. Vše funguje bez problémů.

Všechna data jsou uložena v adresáři *.taskrc* v textovém formátu, takže pokud chcete, můžete do toho různě vrtat.

Úkolníček v Terminálu je navíc docela cool.:-). A že nejde jednoduše synchronizovat s mobilem? Uff, ještě že tak…
