---
title: Úprava kódu v Pythonu
description: Visual Studio pro Python, poskytuje bohaté možnosti technologie IntelliSense, fragmenty kódu a navigačním funkcím, formátování, linting, a refaktoringu.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15020111702d68c8c35fb09655018215e3a11d3b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062813"
---
# <a name="edit-python-code"></a>Úprava kódu v Pythonu

Protože jste tráví mnoho času vývoje v editoru kódu [podpora Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md) poskytuje funkce, aby vám pomohly zvýšit produktivitu práce. Funkce zahrnují IntelliSense zvýrazňování syntaxe, automatické dokončování, signaturám, přepsání metody, vyhledávání a navigace.

Editor je integrovaná taky s **interaktivní** okna v sadě Visual Studio, což usnadňuje exchange kód mezi těmito dvěma. V tématu [kurzu krok 3: použití okna interaktivní okno REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) a [použití interaktivního okna - Odeslat do interaktivního příkazu](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) podrobnosti.

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) ukázku úprav kódu Pythonu (2 miliony 30s).|

Obecná dokumentace o úpravách kódu v sadě Visual Studio, naleznete v tématu [funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md). Viz také [Osnova](../ide/outlining.md), který pomáhá zajistit zaměřené na konkrétní části kódu.

Můžete také použít Visual Studio **prohlížeče objektů** (**zobrazení** > **ostatní Windows** > **prohlížeče objektů**nebo **Ctrl**+**W** > **J**) pro kontrolu Python tříd definovaných v každém modulu a funkce definované v těch třídy.

## <a name="intellisense"></a>IntelliSense

Poskytuje IntelliSense [dokončování](#completions), [signaturám](#signature-help), [rychlé informace](#quick-info), a [barevné zvýraznění kódu](#code-coloring). Visual Studio 2017 verze 15.7 nebo novější podporují také [zadání pomocných parametrů](#type-hints).

Kvůli zvýšení výkonu, technologie IntelliSense v **Visual Studio 2017 verze 15.5** a dříve závisí na dokončení databáze, který je generován pro každé prostředí Pythonu ve vašem projektu. Databáze může být nutné aktualizovat, je-li přidat, odebrat nebo aktualizovat balíčky. Stav databáze je zobrazena ve **prostředí Pythonu** okno (na stejné úrovni **Průzkumníka řešení**) na **IntelliSense** kartu (naleznete v tématu [okno prostředí referenční dokumentace](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017 verze 15.6** a později použije jiný způsob zajištění dokončování IntelliSense, které nejsou závislé na databázi.

### <a name="completions"></a>Dokončování

Dokončení se zobrazí jako příkazy, identifikátory a jiná slova, které může správně zadány na aktuální pozici v editoru. Co se zobrazí v seznamu je na základě kontextu a je filtrováno, aby byly vynechány možnosti nesprávné nebo rušivě. Dokončení se často spouštějí zadáním jiné příkazy (například `import`) a operátory (včetně tečky), ale můžete ho kdykoli zobrazit na zadáním **Ctrl**+**J**  >  **Místo**.

![Dokončování členů v editoru sady Visual Studio](media/code-editing-completions-simple.png)

Při otevření seznamu dokončení můžete vyhledat dokončení můžete určit pomocí kláves se šipkami, myši, nebo když budete pokračovat, zadejte. Při psaní nebo několik písmen. v seznamu další filtr, který zobrazuje pravděpodobné dokončení. Klávesové zkratky můžete také použít jako:

- V psaní písmen, které nejsou na začátku názvu, například 'parse' najít 'argparse.
- Zadáním pouze písmena, které jsou na začátku slova, jako jsou "abc" najít "AbstractBaseClass" nebo "vzduchem" najít "as_integer_ratio.
- Přeskakuje se písmena, například "b64' najít 've formátu base64.

Příklady:

![Dokončování členů s filtrováním v editoru sady Visual Studio](media/code-editing-completion-filtering.png)

Dokončování členů se automaticky zobrazit, když zadáte tečku po proměnné nebo hodnotu společně s metodami a atributy možných typů. Pokud proměnná může být více než jeden typ, seznam obsahuje všechny možnosti ze všech typů, další informace, které označují, typy, které podporují každou doplňování. Tam, kde všechny možné typy podporuje dokončování, zobrazí se bez poznámek.

![Dokončování členů o více typech v editoru sady Visual Studio](media/code-editing-completion-types.png)

Ve výchozím nastavení se nezobrazují "dunder" členy (počáteční a koncové s dvojitým podtržítkem členů). Obecně platí tito členové by neměl být k nim přistupuje přímo. Pokud budete potřebovat, ale zadáte počáteční dvojitým podtržítkem přidá tyto dokončování do seznamu:

![Dokončování soukromých členů v editoru sady Visual Studio](media/code-editing-completion-dunder.png)

`import` a `from ... import` příkazy zobrazení seznamu modulů, které mohou být naimportovány. S `from ... import`, seznam obsahuje členy, které lze importovat z zadaný modul.

![Importovat dokončení v editoru sady Visual Studio](media/code-editing-completion-import.png)

`raise` a `except` příkazů zobrazit seznam tříd, které mohou být typy chyb. V seznamu nemusí obsahovat všechny uživatelem definované výjimky, ale vám pomůže rychle najít vhodnou předdefinované výjimky:

![Dokončení výjimky v editoru sady Visual Studio](media/code-editing-completion-exception.png)

Zadáním spustí dekoratér a ukazuje potenciální dekorátory. Mnoho z těchto položek nejsou použitelné jako dekoratéry; v dokumentaci knihovny k určení, které chcete použít.

![Dokončení dekoratéru v editoru sady Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Můžete provádět konfiguraci chování dokončování prostřednictvím **nástroje** > **možnosti** > **textový Editor**  >   **Python** > **Advanced**. Mezi tyto **filtrovat seznam podle hledaného řetězce** platí filtrování průběžně zobrazovanými návrhy dokončení (výchozí je zaškrtnuté políčko), a **dokončování členů zobrazí IK členů** se zobrazí pouze dokončování, které jsou podporovány všechny možné typy (výchozí nastavení je zaškrtnuté políčko). Zobrazit [možnosti - výsledky dokončení](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Pomocné parametry typu

*Visual Studio 2017 verze 15.7 nebo novější.*

"Zadejte pomocných parametrů" v jazyce Python 3.5 + ([období 484](https://www.python.org/dev/peps/pep-0484/) (python.org) je syntaxe poznámky pro funkce a třídy, které zahrnovaly typy argumentů, návratové hodnoty a tříd atributů. Technologie IntelliSense zobrazí pomocné parametry typu při najetí myší volání funkce, argumentů a proměnné, které mají tyto poznámky.

V následujícím příkladu `Vector` třída je deklarována jako `List[float]`a `scale` funkce obsahuje typ pomocné parametry pro její argumenty a návratové hodnoty. Pomocné parametry typu ukazatel myši volání této funkce ukazuje:

![Volání funkce zobrazíte typu ukazatel myši](media/code-editing-type-hints1.png)

V následujícím příkladu je vidět způsob, jakým označena atributy `Employee` třídy se zobrazí v místní nabídce doplňování technologie IntelliSense pro atribut:

![Technologie IntelliSense pomocné parametry typu znázorňující dokončení](media/code-editing-type-hints2.png)

Je také užitečné pro ověření pomocných parametrů typu v celém projektu, protože chyby se obvykle nezobrazí až do spuštění. Pro tento účel, Visual Studio se integruje oborový standardní MyPy nástroj pomocí příkazu kontextové nabídky **Python** > **spustit Mypy** v **Průzkumníka řešení**:

![Spusťte příkaz MyPy místní nabídky v Průzkumníku řešení](media/code-editing-type-hints-run-mypy.png)

Spuštění příkazového řádku k instalaci balíčku mypy, pokud potřebné. Visual Studio pak spustí mypy ověření pomocných parametrů typu v každém souboru Python v projektu. V sadě Visual Studio se zobrazí chyby **seznam chyb** okna. Výběrem položky v okně přejde na odpovídající řádek v kódu.

Jako jednoduchý příklad následující definice funkce obsahuje typ nápovědu k označení, že `input` argument je typu `str`, že volání této funkce se pokusí předat celé číslo:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Použití **spustit Mypy** příkazu pro tento kód generuje následující chybu:

![Příklad výsledku ověřování typu mypy](media/code-editing-type-hints-validation-error.png)

> [!Tip]
> Pro verze Pythonu, než 3.5, zobrazí Visual Studio také pomocné parametry typu, které zadáte pomocí *soubory zástupných procedur* (*.pyi*). Pokaždé, když nechcete zahrnout pomocné parametry typu přímo v kódu nebo pokud chcete vytvořit pomocných parametrů typu pro knihovnu, která nepoužívá je přímo, můžete použít soubory zástupných procedur. Další informace najdete v tématu [vytvoření zástupné procedury pro moduly Pythonu](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) Wiki mypy projektu.
>
> V současné době nepodporuje sady Visual Studio pomocných parametrů typu v komentářích.

### <a name="signature-help"></a>Nápověda k podpisu

Při psaní kódu, který volá funkci, signaturám se zobrazí, když zadáte otevírání `(` a zobrazí dostupné informace o dokumentaci a parametrů. Můžete provést také zobrazí s **Ctrl**+**Shift**+**místo** uvnitř funkce volání. Informace zobrazené závisí na dokumentaci řetězce ve zdrojovém kódu funkce, ale zahrnuje všechny výchozí hodnoty.

![Nápovědu k signatuře v editoru sady Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Chcete-li zakázat signaturám, přejděte na **nástroje** > **možnosti** > **textový Editor** > **Python**  >  **Obecné** a zrušte zaškrtnutí **dokončování** > **informace o parametrech**.

### <a name="quick-info"></a>Rychlé informace

Ukazatel myši přesunout ukazatel myši identifikátor zobrazí popisek rychlé informace. V závislosti na identifikátor může zobrazit rychlé informace možných hodnot nebo typy, všechny dostupné dokumentaci, návratové typy a umístění definice:

![Rychlé informace v editoru sady Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Barevné zvýraznění kódu

Barevné zvýraznění kódu na základě informací z analýzy kódu na barvu proměnné, příkazy a jiných částí kódu. Například proměnné, které odkazují na moduly nebo třídy se může zobrazit jinou barvou, než funkce nebo jiné hodnoty a názvy parametrů se zobrazí v jinou barvou, než místní nebo globální proměnné. (Ve výchozím nastavení, nejsou zobrazeny funkce tučně):

![Kódu a barevné zvýrazňování syntaxe ve Visual Studiu](media/code-editing-code-coloring.png)

Chcete-li přizpůsobit barvy, přejděte na **nástroje** > **možnosti** > **prostředí** > **písma a barvy** a upravit **Python** položky **zobrazení položek** seznamu:

![Možnosti písma a barev v sadě Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Pokud chcete zakázat barevného zvýraznění kódu, přejděte na **nástroje** > **možnosti** > **textový Editor** > **Python**  >  **Upřesnit** a zrušte zaškrtnutí **různé možnosti** > **barva názvy na základě typu**. Zobrazit [možnosti - různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou fragmenty kódu, který lze vložit do souborů zadáním zástupce a stisknutím klávesy **kartu**, nebo pomocí **upravit** > **IntelliSense**  >  **Vložit fragment kódu** a **obklopit fragmentem** příkazy, že vyberete **Python**, poté vyberete požadovaný fragment.

Například `class` je zkratka pro fragment kódu, který se vkládá definici třídy. Najdete v tomto fragmentu kódu se zobrazí v seznamu automatického dokončování, když zadáte `class`:

![Fragment kódu pro místní třídy](media/code-editing-code-snippet-class.png)

Stisknutím klávesy **kartu** generuje rest třídy. Potom zadáte v seznamu název a základních tříd přesouvání mezi zvýrazněná pole s **kartu**, stiskněte klávesu **Enter** k začněte zadávat text.

![Vybraná vystoupení na oblasti fragment kódu pro dokončení](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Příkazy nabídky

Při použití **upravit** > **IntelliSense** > **Vložit fragment kódu** příkaz nabídky, můžete nejprve vybrat **Python**, pak vyberte fragment kódu:

![Výběr fragmentu kódu pomocí příkazu Vložit fragment kódu](media/code-editing-code-snippet-insert.png)

**Upravit** > **IntelliSense** > **obklopit fragmentem** příkazu podobně umístí aktuální výběr v textovém editoru uvnitř vybraného strukturální elementu. Předpokládejme například, že máte hodně kód podobný tomuto:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Výběrem tento kód a klepnutím **obklopit fragmentem** příkaz zobrazí seznam dostupných fragmentů. Výběr **def** odjinud seznamu vybraný kód uvnitř definice funkce kde můžete použít **kartu** klíč přecházet mezi název funkce zvýrazněné a argumenty:

![Použití příkazu obklopit fragmentem pro fragmenty kódu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Zkontrolujte dostupné fragmenty

Můžete zobrazit fragmenty kódu k dispozici v **Správce fragmentů kódů**otevřené pomocí **nástroje** > **Správce fragmentů kódů** příkaz nabídky a výběr **Python** jako jazyk:

![Správce fragmentů kódů v sadě Visual Studio](media/code-editing-code-snippets-manager.png)

Vytvoření vlastní fragmenty kódu najdete v tématu [návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

Pokud píšete skvělého kódu fragmentu kódu, který chcete sdílet, neváhejte přidat v gist a [dejte nám vědět](https://github.com/Microsoft/PTVS/issues). Jsme možné zahrnout do budoucí verze sady Visual Studio.

## <a name="navigate-your-code"></a>Navigace v kódu

Podpora Pythonu v sadě Visual Studio obsahuje několik způsob, jak rychle navigace v kódu, včetně knihoven pro zdroj, který kód je k dispozici: [navigační panel](#navigation-bar), [ **přejít k definici** ](#go-to-definition), [ **Přejděte do**](#navigate-to), a [ **najít všechny odkazy**](#find-all-references). Můžete také použít Visual Studio [ **prohlížeče objektů**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser).

### <a name="navigation-bar"></a>Navigační panel

Na navigačním panelu se zobrazí v horní části okna editoru a zahrnuje dvě úrovně seznam definic. Vlevo rozevírací seznam obsahuje třídy nejvyšší úrovně a definice funkcí v aktuálním souboru. správné rozevíracího seznamu zobrazí seznam definic v rámci oboru, zobrazí na levé straně. Při pohybu v editoru seznamu aktualizuje a zobrazí aktuální kontext a můžete také vybrat položku z těchto seznamů můžete přejít přímo k.

! [Navigační panel] v sadě Visual Studio editor(media/code-editing-navigation-bar.png)

> [!Tip]
> Chcete-li skrýt navigační panel, přejděte na **nástroje** > **možnosti** > **textový Editor** > **Python**  >  **Obecné** a zrušte zaškrtnutí **nastavení** > **navigační panel**.

### <a name="go-to-definition"></a>Přejít k definici

**Přejít k definici** rychle přejde z použití identifikátoru (jako je název funkce, třídy nebo proměnná), ke zdrojovému kódu níž byl definován. Vyvolání identifikátor pravým tlačítkem a výběrem **přejít k definici** nebo tím, že blikající kurzor umístíte identifikátor a stisknutím klávesy **F12**. Funguje na kód a externí knihovny za předpokladu, že zdrojový kód je k dispozici. Pokud není k dispozici, zdrojový kód knihovny **přejít k definici** přejde do příslušné `import` příkaz pro odkaz na modul, nebo zobrazí chybu.

![Příkaz Přejít k definici v sadě Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Přejděte na

**Upravit** > **přejít na** příkazu (**Ctrl**+**,**) zobrazí vyhledávací pole v editoru ve kterém můžete můžete zadat libovolný řetězec a zobrazit možných shod v kódu, který definuje funkci, třídy nebo proměnné obsahující tento řetězec. Tato funkce poskytuje podobné funkce jako **přejít k definici** , ale bez nutnosti vyhledejte použití identifikátoru.

Poklepáním na libovolný název, nebo jeho výběru pomocí šipkových kláves a **Enter**, přejde k definici identifikátoru.

![Přejděte na příkaz v sadě Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Najít všechny odkazy

**Najít všechny odkazy** užitečný způsob, jak zjistit, kde všechny daným identifikátorem je definovaná a použitá, včetně importy a přiřazení. Vyvolání identifikátor pravým tlačítkem a výběrem **najít všechny odkazy**, nebo tím, že blikající kurzor umístíte identifikátor a stisknutím klávesy **Shift**+**F12**. Dvojitým kliknutím na položku v seznamu přejde do jeho umístění.

![Najít všechny odkazy na výsledky](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Viz také:

- [Formátování](formatting-python-code.md)
- [Refactoring](refactoring-python-code.md)
- [Použít linter](linting-python-code.md)
