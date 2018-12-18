---
title: Úpravy kódu R
description: Visual Studio poskytuje přizpůsobené možnosti úprav pro R a přitom zachovat všechny funkce a umožňuje používat rozšíření.
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: c1d44e6d316db2ddce799784169a11a06578fe7f
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220876"
---
# <a name="edit-r-code-in-visual-studio"></a>Upravit kód R v sadě Visual Studio

Nástroje R pro Visual Studio (RTVS) přizpůsobuje jim editační rozhraní speciálně pro R a přitom zachovat všechny funkce a umožňuje používat rozšíření sady Visual Studio. (Například pokud dáváte přednost VIM klávesové zkratky, můžete nainstalovat bezplatnou [VsVim rozšíření](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z webu Visual Studio Marketplace.)

Kromě funkcí v tomto článku, také naleznete v tématu [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [fragmenty kódu](code-snippets-for-r.md), a [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Zvýrazňování syntaxe

Kromě obarvení různé části kódu, jako jsou řetězce, komentáře a klíčová slova, RTVS také zvýrazní a povolí odkazů v komentářích:

![Pro kód R barevné zvýrazňování syntaxe](media/editing-syntax-colors.png)

Chcete-li přizpůsobit písma a barvy určité zvýraznit, vyberte **nástroje** > **možnosti** příkazu, přejděte na **prostředí**  >  **Písma a barvy**, změňte nastavení pro položky související s R **zobrazení položek** pole:

![Písma a barvy možnosti pro kód jazyka R](media/editing-syntax-colors-options.png)

Visual Studio také podtrhuje chyby syntaxe v editoru:

![Chyba syntaxe, zvýrazňování v kódu jazyka R](media/editing-syntax-error.png)

Chcete-li toto chování změnit, přečtěte si téma **Upřesnit** > **kontrola syntaxe** v nabídce [možnosti editoru](#editor-options).

## <a name="edit-and-organize-code"></a>Upravit a organizaci kódu

Při psaní kódu, RTVS poskytuje automatické dokončování, jak je popsáno na [IntelliSense](r-intellisense.md) stránky. Také provádí automatické formátování, jako je doplňování závorek a závorky: 

![Animace vložené formátování](media/editing-inline-formatting.gif)

Při zadávání volání funkcí, které mají velký počet parametrů se často budete chtít zarovnejte tyto parametry tak, aby byl kód lépe čitelný. RTVS si pamatuje odsazení vaši sadu parametrů a automaticky použije tento odsazení pro následné řádky:

![Animace Automatické odsazení](media/editing-auto-indentation.gif)

Chcete-li toto chování změnit, přečtěte si téma [možnosti editoru](#editor-options) pro **karty** skupiny.

Sbalitelné oblasti kódu umožňují dočasně skrýt části kódu v editoru. Visual Studio různých oblastech za vás automaticky vytvoří, jako u víceřádkových příkazech, není-li **Upřesnit** > **Osnova** > **sbalování kódu**  je možnost nastavená na vypnuto.

Chcete-li vytvořit oblasti Vlastní, obklopit požadovaný kód s komentáři, které končí `---`. Malé +/-ovládací prvky k levému okraji kódu umožňuje pak rozbalovat a sbalovat oblasti:

![Vytváření sbalitelná oblast s komentáři](media/editing-collapsible-regions.gif)

Ve výchozím nastavení, sada Visual Studio vloží mezery po stisknutí klávesy **kartu** klíč. Toto chování lze znovu změnit, jak je popsáno na [možnosti, textový Editor, karty](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navigace v kódu

Navigace v kódu umožňuje rychlý přístup ke zdrojovému kódu programu jazyka R a jeho knihoven. Tyto funkce můžete zadarmo i ve službě flow svou práci a ne museli ručně vyhledávání v kódu.

**Přejít k definici** rychle přejde do definice funkce nebo zobrazí zkrácené editoru vložené číst zdrojový kód funkce knihovny. Stačí pravým tlačítkem myši na funkci zájmu a vyberte **přejít k definici**, nebo umístěte kurzor do funkce a stiskněte klávesu **F12**.

Tento příkaz otevře nové okno editoru obsahující zdrojový kód pro funkci. Kurzor je jednoduše nastavený na začátku definice funkce.

**Náhled definice**, vyvolaná v místní nabídce nebo **Alt**+**F12**, vloží jen pro čtení, rolovací oblast, která obsahuje zdrojový kód funkce následujícím volání funkce:

![Animace pro funkce Náhled definice](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Poslat kód do interaktivního okna

Mnoho vývojářů preferuje napsání kódu v editoru a odešlete kódu [interaktivní okno](interactive-repl-for-r-in-visual-studio.md) pro okamžité testování (označované také jako čtení-vyhodnocení-Print-Loop nebo REPL). Stisknutím klávesy **Ctrl**+**Enter** v R editor odesílá aktuální řádek kódu do interaktivního okna a umístí kurzor na další řádek. S **Ctrl**+**Enter**, pak můžete efektivně krokovat kódu z editoru.

Můžete také vybrat kód a stiskněte klávesu **Ctrl**+**Enter** použít celý výběr. Alternativně klepněte výběr pravým tlačítkem a vyberte **provést v Interactive**.

## <a name="format-code"></a>Formátování kódu

Visual Studio automatické formátování udržuje kód, který píšete, a zároveň i kód, který vložíte do editoru formátované jako sada předvolby. Můžete také vytvořit výběr, klikněte pravým tlačítkem a vyberte **výběr formátu** (**Ctrl**+**K**,**F**) Chcete-li použít ty Předvolby. Například pokud máte definici funkce vše na jednom řádku:

```R
f<-function  (a){  return(a + 1) }
```

Formátování vyčistí ho na:

```R
f <- function(a) { return(a + 1) }
```

Chcete-li změnit formát souboru celý kód, vyberte **upravit** > **Upřesnit** > **formátovat dokument** (**Ctrl** + **E**,**D**).

Automatické formátování je samostatný operace, která lze vrátit zpět. Například, pokud kód vložte do editoru a formátování se vztahuje, pak výběrem **upravit** > **zpět** nebo stiskněte **Ctrl** + **Z** jednou obrátí formátování; sekundy **zpět** obrátí vložit samotné.

Možnosti formátování (včetně vypnutí formátování), se konfigurují pomocí **nástroje** > **možnosti** na **textový Editor**  >  **R** > **Upřesnit** kartu. Můžete přejít přímo na tuto stránku pomocí buď **nástroje R** > **možnosti editoru** příkazu nebo tím, že v editoru pravým tlačítkem myši a vyberete **možnostiformátování**. Zobrazit [možnosti editoru](#editor-options) podrobné informace.

## <a name="inserting-roxygen-comments"></a>Vkládání komentářů Roxygen

RTVS poskytuje zástupce pro generování [Roxygen](http://roxygen.org/) komentáře pomocí názvy parametrů funkce. Stačí zadat `###` na prázdný řádek výše definice funkce:

![Animace vložení komentář Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Možnosti editoru

Editor specifické možnosti, které se konfigurují pomocí **nástroje** > **možnosti** příkazu, že přejdete na **textový Editor** > **R**, nebo použijte příkaz místní **nástroje R** > **možnosti editoru**.

Možnosti **Obecné**, **posuvníky**, a **karty** karet nejsou specifická pro R, ale jsou spíše obecné nastavení sady Visual Studio k dispozici pro všechny jazyky, ale použité na základ podle jazyka. Podrobnosti najdete v následujících článcích:

- [Možnosti, Textový editor, Všechny jazyky](../ide/reference/options-text-editor-all-languages.md)
- [Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Možnosti, textový Editor, karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Možnosti **R** > **Upřesnit** jsou specifické pro RTVS kartu:

| Skupina | Možnost | Výchozí | Popis |
| --- | --- | --- | --- |
| Formátování | Automatické formátování | On | Přeformátuje kódu při psaní. Nemá vliv **výběr formátu** nebo **formátovat dokument** příkazy. |
| | Rozšířené závorky | Off | Umístí otevřenou {na nový řádek. |
| | Formátovat při vložení | On | Použije formátování při vložení. |
| | Formátovat rozsah při vložení} | On | Naformátuje rozsah po zadání uzavírací}. |
| | Mezera za čárkou | On | Vloží mezeru za čárky. |
| | Mezera za klíčovým slovem | On | Vloží mezeru po klíčová slova, jako jsou `if`, `while`, a `repeat`. |
| | Mezera před {} | On | Vloží mezeru před a otevírání {. |
| | Mezery kolem znaku = | On | Umístí mezery kolem znaménko rovná se. |
| IntelliSense | Potvrdit při stisknutí klávesy Enter | Off | Potvrzení automatického dokončování výběr při **Enter** stisknutí. |
| | Potvrdit při stisknutí mezerníku | Off | Potvrzení automatického dokončování výběr při **místo** stisknutí.|
| | Seznam pro doplňování při prvním znaku | On | Zobrazí seznam pro doplňování při prvním typy znaků. Při vypnutí, zobrazí se seznam pro doplňování s **upravit** > **IntelliSense** > **seznam členů** (**Ctrl** + **J**). |
| | Seznam pro doplňování **kartu** klíč | Off | Vyvolá seznam pro doplňování zadáním jednoho nebo více znaků a stisknutím klávesy **kartu**. |
| | Shoda částečně typy názvy argumentů | Off | Při zadávání názvy argumentů ve volání funkce se zobrazí nápovědu k signatuře popis argumentu, který nejlépe odpovídá. |
| Interaktivní okno | Kontrola syntaxe v konzole R | Off | Platí kontrolu syntaxe v interaktivním okně. Kontrola syntaxe nemusí fungovat správně s víceřádkových příkazech. | 
| Sbalování | Sbalování kódu | On | Automaticky vytvoří sbalitelné oblasti pro oblasti, jako je víceřádkových příkazech. |
| Kontrola syntaxe | Zobrazit syntaktické chyby | On | Povolí automatickou kontrolu kódu syntaxe. |
