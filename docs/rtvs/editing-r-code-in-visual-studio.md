---
title: Upravit kód R
description: Visual Studio poskytuje přizpůsobené prostředí pro úpravy pro R při zachování všech funkcí a možnost používat rozšíření.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302712"
---
# <a name="edit-r-code-in-visual-studio"></a>Upravit kód R v sadě Visual Studio

Nástroje R pro visual studio (RTVS) přizpůsobuje prostředí pro úpravy sady Visual Studio speciálně pro R při zachování všech funkcí a možnosti používat rozšíření. (Například pokud dáváte přednost vazby klíče VIM, můžete nainstalovat bezplatné [rozšíření VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z webu Visual Studio Marketplace.)

Kromě funkcí v tomto článku viz také [Technologie IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [fragmenty kódu](code-snippets-for-r.md)a [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Zvýraznění syntaxe

Kromě barvení různých částí kódu, jako jsou řetězce, komentáře a klíčová slova, RTVS také zdůrazňuje a umožňuje odkazy v komentářích:

![Zbarvení syntaxe pro kód R](media/editing-syntax-colors.png)

Chcete-li přizpůsobit písma a určité barvy zvýraznění, **Environment** > vyberte příkaz**Možnosti** **nástroje,** > přejděte na**prostředí Písma a barvy**a změňte nastavení položek souvisejících s r v poli Zobrazit **položky:**

![Písma a volby barev pro kód R](media/editing-syntax-colors-options.png)

Visual Studio také zdůrazňuje chyby syntaxe v editoru:

![Zvýraznění chyb syntaxe v kódu R](media/editing-syntax-error.png)

Chcete-li toto chování změnit, přečtěte si téma **Upřesnit** > **nastavení kontroly syntaxe** v části [možnosti editoru](#editor-options).

## <a name="edit-and-organize-code"></a>Úprava a uspořádání kódu

Při psaní kódu poskytuje rtvs automatické dokončování, jak je popsáno na stránce [IntelliSense.](r-intellisense.md) Provádí také automatické formátování, například dokončení závorek a závorek:

![Animace vřádkového formátování](media/editing-inline-formatting.gif)

Při zadávání volání funkcí, které mají mnoho parametrů, častokrát chcete zaokřovat parametry, aby byl kód čitelnější. RTVS si pamatuje odsazení nastavit pro parametry a automaticky použije, že odsazení pro následující řádky:

![Animace automatického odsazení](media/editing-auto-indentation.gif)

Chcete-li toto chování změnit, přečtěte [si téma možnosti editoru](#editor-options) pro skupinu **Tabs.**

Sbalitelné oblasti kódu umožňují dočasně skrýt část kódu v editoru. Visual Studio vytvoří různé oblasti pro vás automaticky, jako pro víceřádkové příkazy, pokud **rozšířené** > **osnovy** > **kódu nastínit** možnost je nastavena na Vypnuto.

Chcete-li vytvořit vlastní oblast, obklopte požadovaný `---`kód komentáři, které končí písmenem . Malé ovládací prvky +/- nalevo od kódu umožňují rozbalení a sbalení oblastí:

![Vytvoření sbalitelné oblasti s komentáři](media/editing-collapsible-regions.gif)

Ve výchozím nastavení aplikace Visual Studio vloží mezery, když stisknete klávesu **Tab.** Toto chování můžete znovu změnit, jak je popsáno v [části Možnosti, Textový editor, Karty](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Navigace kódu

Navigace kódu umožňuje rychlý přístup ke zdrojovému kódu programu R a jeho knihoven. Tyto funkce vás udrží v toku vaší práce, místo abyste museli ručně prohledávat kód.

**Přejít na definici** rychle přeskočí na definici funkce nebo se objeví vřádkový minieditor, který si přečte zdrojový kód funkce knihovny. Stačí kliknout pravým tlačítkem myši na funkci zájmu a vybrat **přejít na definici**, nebo umístit kurzor do funkce a stiskněte **klávesu F12**.

Tento příkaz otevře nové okno editoru obsahující zdrojový kód funkce. Kurzor je pohodlně umístěn na začátku definice funkce.

**Náhled definice**, vyvolána z nabídky pravým tlačítkem myši nebo **Alt**+**F12**, vloží jen pro čtení, rolovací oblast obsahující zdrojový kód funkce pod volání funkce:

![Animace pro definici náhledu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Odeslat kód do interaktivního okna

Mnoho vývojářů chtěli napsat nějaký kód v editoru a pak odeslat tento kód do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md) pro okamžité testování (také známý jako Read-Evaluate-Print-Loop nebo REPL). Stisknutím **klávesy Ctrl**+**Enter** v editoru R odešlete aktuální řádek kódu do interaktivního okna a umístíkurzor na další řádek. S **Ctrl**+**Enter**, pak můžete efektivně krokovat kód z editoru.

Můžete také vybrat kód a stisknutím **klávesy Ctrl**+**Enter** použít celý výběr. Případně klepněte pravým tlačítkem myši na výběr a vyberte **příkaz Execute in Interactive**.

## <a name="format-code"></a>Formátování kódu

Automatické formátování sady Visual Studio zachová kód, který píšete, stejně jako kód, který vložíte do editoru, formátovaný podle vašich předvoleb. Můžete také provést výběr, klepnout pravým tlačítkem myši a vybrat **možnost Formát výběru** **(Ctrl**+**K**,**F),** chcete-li tyto předvolby použít. Například pokud jste měli definici funkce vše na jednom řádku:

```R
f<-function  (a){  return(a + 1) }
```

Použití formátování jej vyčistí takto:

```R
f <- function(a) { return(a + 1) }
```

Chcete-li přeformátovat celý soubor kódu, vyberte **Upravit** > **dokument s rozšířeným** > **formátem** (**Ctrl**+**E**,**D**).

Automatické formátování je samostatná operace, kterou lze vrátit zpět. Pokud například vložíte kód do editoru a použije se jeho formátování, vyberte volbu **Upravit** > **zpět** nebo stisknutím **klávesy Ctrl**+**Z,** jakmile obrátíte formátování; druhý **Zpět** obrátí pastu sám.

Možnosti formátování (včetně vypnutí formátování) jsou **nastaveny** > pomocí**možností** nástroje na kartě **Text Editor** > **R** > **Upřesnit.** Na tuto stránku můžete přejít přímo pomocí příkazu**Možnosti editoru** **nástrojů** > R nebo klepnutím pravým tlačítkem myši do editoru a výběrem **možností formátování**. Podrobnosti najdete v části [možnosti editoru.](#editor-options)

## <a name="inserting-roxygen-comments"></a>Vkládání roxygen komentáře

RTVS poskytuje zástupce pro generování [roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) komentáře pomocí názvů parametrů funkce. Stačí `###` zadat prázdný řádek nad definicí funkce:

![Animace vložení komentáře Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Možnosti editoru

Možnosti specifické pro editor jsou nastaveny pomocí příkazu**Možnosti** **nástroje,** > přechodu do **textového editoru** > **R**nebo pomocí příkazu zástupce **R Tools** > **Editor Options**.

Možnosti na kartách **Obecné**, **Posuvníky**a **Tabulátory** nejsou specifické pro R, ale jsou spíše obecné nastavení sady Visual Studio, které je k dispozici pro všechny jazyky, ale platí pro jednotlivé jazyky. Podrobnosti naleznete v následujících článcích:

- [Možnosti, textový editor, všechny jazyky](../ide/reference/options-text-editor-all-languages.md)
- [Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Možnosti, Textový editor, tabulátory](../ide/reference/options-text-editor-all-languages-tabs.md)

Možnosti na kartě **R** > **Upřesnit** jsou specifické pro RTVS:

| Skupina | Možnost | Výchozí | Popis |
| --- | --- | --- | --- |
| Formátování | Automatické formátování | Zapnuto | Přeformátuje kód při psaní. Nemá vliv na příkazy **Výběr formátu** nebo **Formát dokumentu.** |
| | Rozbalené závorky | Vypnuto | Umístí otevřenou { na nový řádek. |
| | Formát při vložení | Zapnuto | Použije formátování při vložení. |
| | Formát oboru na } | Zapnuto | Po zadání uzávěrky }. |
| | Mezera za čárkou | Zapnuto | Umístí mezeru za čárky. |
| | Mezera za klíčovým slovem | Zapnuto | Umístí mezeru za `if`klíčová `while`slova `repeat`, jako jsou , a . |
| | Prostor před { | Zapnuto | Umístí mezeru před a otevření {. |
| | Mezery kolem = | Zapnuto | Umístí mezery kolem znaménko rovná se. |
| IntelliSense | Potvrdit klíč Enter | Vypnuto | Potvrdí výběr automatického dokončování při stisknutí klávesy **Enter.** |
| | Klíč Potvrzení v prostoru | Vypnuto | Potvrdí výběr automatického dokončování, když je **stisknuto mezera.**|
| | Seznam dokončení prvního znaku | Zapnuto | Zobrazí seznam dokončení na prvních typech znaků. Když je vypnuto, zobrazí se seznam dokončení s **funkcemi Edit** > **IntelliSense** > **List Members** **(Ctrl**+**J).** |
| | Seznam dokončení na **klávesové matné klávese** | Vypnuto | Vyvolá seznam dokončení zadáním jednoho nebo více znaků a stisknutím **klávesy Tab**. |
| | Shoda částečně zadá názvy argumentů | Vypnuto | WHen psaní argument názvy ve volání funkce, podpis nápověda ukazuje popis argument, který je nejlepší shoda. |
| Interaktivní okno | Změna syntaxe v konzoli R | Vypnuto | Použije kontrolu syntaxe v interaktivním okně. Kontrola syntaxe nemusí fungovat správně s víceřádkovými příkazy. |
| Sbalování | Osnova kódu | Zapnuto | Automaticky vytvoří sbalitelné oblasti pro oblasti, jako jsou víceřádkové příkazy. |
| Kontrola syntaxe | Zobrazit syntaktické chyby | Zapnuto | Umožňuje automatickou kontrolu syntaxe kódu. |
