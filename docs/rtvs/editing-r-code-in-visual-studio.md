---
title: Upravit kód R
description: Visual Studio poskytuje přizpůsobené prostředí pro úpravy jazyka R a zachovává všechny funkce a možnost používat rozšíření.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4aea7f5371dc425a77e10b64a9389571b06f80b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885856"
---
# <a name="edit-r-code-in-visual-studio"></a>Úprava kódu R v aplikaci Visual Studio

Nástroje R pro Visual Studio (RTVS) jsou zakončené prostředím pro úpravy sady Visual Studio, které je specifické pro jazyk R při zachování všech funkcí a možnosti používat rozšíření. (Pokud například dáváte přednost vazbám klíčů VIM, můžete nainstalovat bezplatné [rozšíření VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z Visual Studio Marketplace.)

Kromě funkcí v tomto článku viz také [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [fragmenty kódu](code-snippets-for-r.md)a [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Zvýrazňování syntaxe

Kromě vybarvení různých částí kódu, jako jsou například řetězce, komentáře a klíčová slova, RTVS také zvýrazní a povoluje odkazy v komentářích:

![Barevné zvýrazňování syntaxe kódu R](media/editing-syntax-colors.png)

Chcete-li přizpůsobit písma a určité barvy zvýraznění, vyberte  >  příkaz **Možnosti** nástrojů, přejděte do části   >  **písma a barvy** prostředí a pak změňte nastavení položek souvisejících s R v poli **zobrazované položky** :

![Písma a možnosti barev pro kód R](media/editing-syntax-colors-options.png)

Visual Studio také v editoru podtržené chyby syntaxe:

![Zvýrazňování chyb syntaxe v kódu R](media/editing-syntax-error.png)

Chcete-li toto chování změnit, přečtěte si téma nastavení **Rozšířené**  >  **kontroly syntaxe** v části [Možnosti editoru](#editor-options).

## <a name="edit-and-organize-code"></a>Upravit a uspořádat kód

Při psaní kódu RTVS poskytuje automatické dokončování, jak je popsáno na stránce [IntelliSense](r-intellisense.md) . Automatické formátování, jako je například dokončování složených závorek a závorek:

![Animace vloženého formátování](media/editing-inline-formatting.gif)

Když zadáváte volání funkcí, které mají mnoho parametrů, často, že chcete nastavovat parametry, aby bylo snazší číst kód. RTVS pamatuje odsazení vaší sady pro parametry a automaticky použije toto odsazení pro následné řádky:

![Animace automatického odsazení](media/editing-auto-indentation.gif)

Chcete-li toto chování změnit, přečtěte si téma [Možnosti editoru](#editor-options) pro skupinu **karet** .

Sbalitelná oblast kódu vám umožní dočasně skrýt část kódu v editoru. Sada Visual Studio vytváří různé oblasti automaticky, jako pro víceřádkové příkazy, pokud není možnost **pokročilého**  >  **sbalení**  >  **kódu** nastavená na hodnotu Vypnuto.

Chcete-li vytvořit vlastní oblast, uzavřete požadovaný kód s komentáři, které končí na `---` . Malé +/-ovládací prvky nalevo od kódu umožňují rozbalení a sbalení oblastí:

![Vytvoření sbalitelné oblasti s komentáři](media/editing-collapsible-regions.gif)

Ve výchozím nastavení vloží Visual Studio po stisknutí klávesy **tabulátoru** mezery. Toto chování můžete znovu změnit, jak je popsáno v tématu [Možnosti, textový editor, karty](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navigace v kódu

Navigace v kódu vám umožní rychlý přístup ke zdrojovému kódu vašeho programu R a jeho knihoven. Tyto funkce zabrání v toku práce, ale nemusíte ručně prohledávat kód.

**Přejít k definici rychlé přechodu** na definici funkce nebo nastavování vloženého zkráceného editoru pro čtení zdrojového kódu funkce knihovny. Stačí kliknout pravým tlačítkem myši na funkci zájmu a vybrat **Přejít k definici** nebo umístit kurzor do funkce a stisknout klávesu **F12**.

Tento příkaz otevře nové okno editoru obsahující zdrojový kód funkce. Kurzor je pohodlně umístěný na začátku definice funkce.

**Náhled definice**, vyvolaná v nabídce pravého tlačítka myši nebo **ALT** + **F12**, vloží oblast, která je jen pro čtení, která obsahuje zdrojový kód funkce pod voláním funkce:

![Animace pro náhled definice](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Odeslat kód do interaktivního okna

Mnoho vývojářů chce napsat nějaký kód v editoru a potom tento kód odeslat do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md) pro okamžité testování (označované také jako Read-Evaluate-Print-Loop nebo REPL). Stisknutí klávesy **CTRL** + **ENTER** v editoru R pošle aktuální řádek kódu do interaktivního okna a pak umístí kurzor na další řádek. Pomocí **klávesy CTRL** + **ENTER** a pak můžete efektivně krokovat kód z editoru.

Můžete také vybrat kód a stisknutím klávesy **CTRL** + **ENTER** použít celý výběr. Případně klikněte pravým tlačítkem myši na výběr a vyberte možnost **Spustit v Interactive**.

## <a name="format-code"></a>Formátování kódu

Automatické formátování sady Visual Studio udržuje kód, který píšete, i kód, který vložíte do editoru, formátovaný jako nastavený podle vašich požadavků. Můžete také provést výběr, kliknout pravým tlačítkem myši a vybrat **formát výběru** (**CTRL** + **K**,**F**) a tyto předvolby použít. Například pokud jste měli definici funkce na jednom řádku:

```R
f<-function  (a){  return(a + 1) }
```

Použití formátování vyčistí:

```R
f <- function(a) { return(a + 1) }
```

Chcete-li znovu zformátovat celý soubor kódu, vyberte možnost **Upravit**  >  **Rozšířené**  >  **formátování dokumentu** (**CTRL** + **E**,**D**).

Automatické formátování je samostatná operace, kterou je možné vrátit zpět. Pokud například vložíte kód do editoru a použijete ho formátování, vyberte možnost **Upravit**  >  **zpět** nebo stisknout **klávesovou zkratku CTRL +**, +  Jakmile se změní formátování; druhá **Akce** vrátí samotné vložení.

Možnosti formátování (včetně vypnutí formátování) se nastavují prostřednictvím  >  **možností** nástroje na kartě Upřesnit v **textovém editoru**  >  **R**  >   . Přímo na tuto stránku můžete přejít přímo pomocí   >  příkazu **Možnosti editoru** jazyka R nebo kliknutím pravým tlačítkem v editoru a výběrem **možností formátování**. Podrobnosti najdete v části [Možnosti editoru](#editor-options) .

## <a name="inserting-roxygen-comments"></a>Vkládání komentářů Roxygen

RTVS poskytuje zástupce pro generování komentářů [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) pomocí názvů parametrů funkce. Stačí zadat `###` prázdný řádek nad rámec definice funkce:

![Animace vložení Roxygen komentáře](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Možnosti editoru

Možnosti specifické pro Editor se nastavují pomocí  >  příkazu **Možnosti** nástrojů, přechodem na **textový editor**  >  **r** nebo pomocí klávesových zkratek pro Editor nástrojů příkazu **R**  >  .

Možnosti na kartách **Obecné**, **posuvníky** a **tabulátory** nejsou specifické pro jazyk R, ale místo toho jsou k dispozici obecná nastavení sady Visual Studio pro všechny jazyky, ale používá se na jednotlivých jazycích. Podrobnosti najdete v následujících článcích:

- [Možnosti, textový editor, všechny jazyky](../ide/reference/options-text-editor-all-languages.md)
- [Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Možnosti, textový editor, karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Možnosti na kartě   >  **Upřesnit** v R jsou specifické pro RTVS:

| Group (Skupina) | Možnost | Výchozí | Description |
| --- | --- | --- | --- |
| Formátování | Automatické formátování | Zapnout | Přeformátuje kód při psaní. Nemá vliv na příkazy pro **Výběr formátu** nebo **formátování dokumentu** . |
| | Rozšířené složené závorky | Vypnout | Umístí otevřené místo na nový řádek. |
| | Formátovat při vložení | Zapnout | Použije formátování při vložení. |
| | Rozsah formátu zapnuto} | Zapnout | Formátuje rozsah po zadání uzavíracího}. |
| | Mezera za čárkou | Zapnout | Umístí mezeru za čárky. |
| | Mezera za klíčovým slovem | Zapnout | Umístí mezeru za klíčová slova jako `if` , `while` a `repeat` . |
| | Mezera před { | Zapnout | Umístí mezeru před a otevře se {. |
| | Mezery kolem = | Zapnout | Umístí mezery kolem rovnítko. |
| IntelliSense | Potvrdit při zadání klávesy ENTER | Vypnout | Potvrdí výběr automatického dokončování při stisknutí klávesy **ENTER** . |
| | Potvrdit na klíč místo | Vypnout | Potvrdí výběr automatického dokončení při stisknutí **mezerníku** .|
| | Seznam pro doplňování při prvním znaku | Zapnout | Zobrazuje seznam pro doplňování u prvních typů znaků. Pokud je vypnutý, zobrazí se seznam dokončení s **úpravami**  >    >  **Členové seznamu** IntelliSense (**CTRL** + **J**). |
| | Seznam pro doplňování na klávesu **TAB** | Vypnout | Vyvolá seznam pro doplňování zadáním jednoho nebo více znaků a stisknutím klávesy **TAB**. |
| | Porovnává částečně typy názvů argumentů | Vypnout | Při zadávání názvů argumentů ve volání funkce Help help zobrazí popis argumentu, který je nejlepší shodou. |
| Okno Interactive | Kontrolu syntaxe v konzole R | Vypnout | Aplikuje kontrolu syntaxe v interaktivním okně. Kontrola syntaxe nemusí fungovat správně s víceřádkovými příkazy. |
| Sbalování | Osnova kódu | Zapnout | Automaticky vytvoří sbalitelné oblasti pro oblasti, jako jsou víceřádkové příkazy. |
| Kontroly syntaxe | Zobrazit syntaktické chyby | Zapnout | Povolí automatickou kontrolu syntaxe kódu. |
