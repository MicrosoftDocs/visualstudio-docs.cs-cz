---
title: Úprava kódu v Pythonu
description: Pro Python poskytuje Visual Studio bohatou technologii IntelliSense, fragmenty kódu a navigační funkce společně s formátováním, linting a refaktoringem.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eb3e3ca5d18429c60894c42bda12328836dc6fc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73024725"
---
# <a name="edit-python-code"></a>Úprava kódu v Pythonu

Vzhledem k tomu, že strávíte spoustu času vývoje v editoru kódu, nabízí [Podpora Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md) funkce, které vám pomůžou zvýšit produktivitu. K funkcím patří zvýrazňování syntaxe IntelliSense, automatické dokončování, podepisování, potlačení metod, hledání a navigace.

Editor je také integrovaný do **interaktivního** okna v aplikaci Visual Studio, což usnadňuje výměnu kódu mezi těmito dvěma. Podrobnosti najdete v [kurzu krok 3: použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) a interaktivního [příkazu pro odeslání do interaktivního okna](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) .

Obecnou dokumentaci k úpravám kódu v sadě Visual Studio naleznete v tématu [funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md). Viz také [Osnova](../ide/outlining.md), která vám pomůže udržet si fokus na konkrétní části kódu.

Můžete také použít **Prohlížeč objektů** sady Visual Studio (**Zobrazit**  >  **Další**  >  **Prohlížeč objektů** Windows nebo **CTRL +** + **W**  >  **J**) pro kontrolu tříd Pythonu definovaných v jednotlivých modulech a funkcích definovaných v těchto třídách.

## <a name="intellisense"></a>IntelliSense

Technologie IntelliSense nabízí [dokončování](#completions), [podpisové](#signature-help)informace, [rychlé informace](#quick-info)a [barvy kódu](#code-coloring). Visual Studio 2017 verze 15,7 a novější také podporují [pomocné parametry typu](#type-hints).

Pro zlepšení výkonu závisí technologie IntelliSense v aplikaci Visual Studio 2017 verze 15,5 a starší na databázi pro dokončování, která je generována pro každé prostředí Pythonu v projektu. Pokud přidáte, odeberete nebo aktualizujete balíčky, mohou být databáze nutné aktualizovat. Stav databáze se zobrazí v okně **prostředí Pythonu** (na stejné úrovni **Průzkumník řešení**) na kartě **IntelliSense** (viz [Referenční dokumentace okna prostředí](python-environments-window-tab-reference.md)).

Visual Studio 2017 verze 15,6 a novější používá jiný způsob, jak zajistit dokončování IntelliSense, které nejsou závislé na databázi.

### <a name="completions"></a>Completions

Doplňování se zobrazí jako příkazy, identifikátory a další slova, která lze vhodně zadat v aktuálním umístění v editoru. Obsah zobrazený v seznamu je založený na kontextu a je filtrovaný pro vynechání nesprávných nebo rušivých možností. Dokončování jsou často spouštěny zadáním různých příkazů (například `import` ) a operátorů (včetně tečky), ale můžete je kdykoli zobrazit zadáním **CTRL +** + **J**  >  **MEZERNÍK**.

![Dokončování členů v editoru sady Visual Studio](media/code-editing-completions-simple.png)

Když je seznam dokončení otevřený, můžete vyhledat požadované dokončení pomocí kláves se šipkami, myši nebo pokračováním typu. Při psaní více písmen je seznam dále filtrován tak, aby zobrazoval pravděpodobná dokončení. Můžete také použít zkratky jako:

- Zadáním písmen, která nejsou na začátku názvu, jako je například ' Parse ' pro hledání ' argparse '.
- Psaním jenom písmen, která jsou na začátku slov, jako je například ABC, najděte ' AbstractBaseClass ' nebo ' Air ' a vyhledejte ' as_integer_ratio '.
- Vynechávání písmen, jako je například ' B64 ' k vyhledání ' Base64 '

Několik příkladů:

![Dokončení členů s filtrováním v editoru sady Visual Studio](media/code-editing-completion-filtering.png)

Dokončení členů se zobrazí automaticky při zadání tečky za proměnnou nebo hodnotou, spolu s metodami a atributy potenciálních typů. Pokud by proměnná mohla být více než jeden typ, obsahuje seznam všechny možnosti všech typů s dalšími informacemi, které určují, které typy podporují jednotlivé dokončování. V případě, že je dokončení podporováno všemi možnými typy, je zobrazen bez anotace.

![Dokončování členů na více typech v editoru sady Visual Studio](media/code-editing-completion-types.png)

Ve výchozím nastavení se nezobrazují členové "dunder" (členové začínající a končící dvojitým podtržítkem). Obecně by tito členové neměli mít přímý přímý odkaz. Pokud ale budete ho potřebovat, stačí zadat počáteční Dvojité podtržení, které se dokončí do seznamu:

![Dokončování soukromých členů v editoru sady Visual Studio](media/code-editing-completion-dunder.png)

`import`Příkazy a `from ... import` zobrazují seznam modulů, které lze importovat. `from ... import`Seznam obsahuje členy, které mohou být importovány ze zadaného modulu.

![Dokončení importu v editoru sady Visual Studio](media/code-editing-completion-import.png)

`raise`Příkazy a `except` zobrazují seznam tříd, které mohou být typy chyb. Seznam nesmí zahrnovat všechny uživatelsky definované výjimky, ale pomůže rychle najít vhodné vestavěné výjimky:

![Dokončení výjimky v editoru sady Visual Studio](media/code-editing-completion-exception.png)

Zadáním @ spustíte dekoratér a zobrazí se potenciální dekoratéry. Mnohé z těchto položek není možné použít jako dekoratéry; Podívejte se do dokumentace knihovny a určete, která z nich se má použít.

![Dekoratér dokončení v editoru sady Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Chování dokončování můžete nakonfigurovat prostřednictvím možností **nástroje**  >  **Options**  >  **textový editor**  >  **Python**  >  **Upřesnit**. **V seznamu filtru založeném na hledaném řetězci** se při psaní použijí filtrování návrhů dokončení (výchozí je zaškrtnuté) a **dokončení členů zobrazuje průnik členů** obsahuje jenom doplňování podporovaná všemi možnými typy (ve výchozím nastavení není zaškrtnuté). Viz [Možnosti – výsledky dokončování](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Pomocné parametry typu

*Visual Studio 2017 verze 15,7 a novější.*

"Pomocný parametr typu" v Pythonu 3.5 + ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (Python.org) je syntaxe poznámky pro funkce a třídy, které určují typy argumentů, návratových hodnot a atributů třídy. IntelliSense zobrazí pomocné parametry typu, když najedete myší na volání funkcí, argumenty a proměnné, které mají tyto poznámky.

V následujícím příkladu `Vector` je třída deklarována jako `List[float]` a `scale` funkce obsahuje pomocný parametr typu pro své argumenty a návratovou hodnotu. Najetí myší na volání této funkce zobrazuje pomocné parametry typu:

![Najetí myší na volání funkce, které odhalí pomocné parametry typu](media/code-editing-type-hints1.png)

V následujícím příkladu vidíte, jak se v `Employee` místní nabídce dokončování technologie IntelliSense zobrazí atributy s poznámkou pro atribut:

![Dokončování IntelliSense zobrazující pomocné parametry typu](media/code-editing-type-hints2.png)

Je také užitečné ověřit pomocný parametr typu v celém projektu, protože chyby se obvykle neprojeví až do doby běhu. Pro účely tohoto účelu Visual Studio integruje nástroj MyPy Industry Standard pomocí místní nabídky příkazu **Python**  >  **Run MyPy** v **Průzkumník řešení**:

![Spustit příkaz místní nabídky MyPy v Průzkumník řešení](media/code-editing-type-hints-run-mypy.png)

Po spuštění příkazu se zobrazí výzva k instalaci balíčku mypy, pokud je to potřeba. Visual Studio potom spustí mypy k ověření pomocných parametrů typu v každém souboru Pythonu v projektu. Chyby se zobrazí v okně **Seznam chyb** sady Visual Studio. Výběr položky v okně naviguje na příslušný řádek v kódu.

V jednoduchém příkladu následující definice funkce obsahuje pomocný parametr typu, který označuje, že `input` argument je typu `str` , zatímco volání této funkce se pokouší předat celé číslo:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Pomocí příkazu **Spustit Mypy** na tomto kódu se vygeneruje následující chyba:

![Příklad výsledku mypy ověřování pomocných parametrů typu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Pro verze Pythonu před 3,5 se v aplikaci Visual Studio zobrazí také pomocný parametr typu, který zadáte prostřednictvím *souborů zástupných procedur* Typeshed (*. pyi*). Můžete použít zástupné soubory vždy, když nechcete zahrnout parametry typu přímo do kódu, nebo když chcete vytvořit pomocné parametry pro knihovnu, která je nepoužívá přímo. Další informace najdete v tématu Vytvoření zástupných [procedur pro moduly Pythonu](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wikiwebu projektu mypy.
>
> V současné době Visual Studio nepodporuje v komentářích parametry typu.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Pro verze Pythonu před 3,5 se v aplikaci Visual Studio zobrazí také pomocný parametr typu, který zadáte prostřednictvím *souborů zástupných procedur* Typeshed (*. pyi*). Můžete použít zástupné soubory vždy, když nechcete zahrnout parametry typu přímo do kódu, nebo když chcete vytvořit pomocné parametry pro knihovnu, která je nepoužívá přímo. Další informace najdete v tématu Vytvoření zástupných [procedur pro moduly Pythonu](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wikiwebu projektu mypy.
>
> Sada Visual Studio obsahuje sadu Typeshed souborů pro Python 2 a 3, takže další soubory ke stažení nejsou nutné. Pokud ale chcete použít jinou sadu souborů, můžete cestu zadat v možnostech **nástrojů**  >  **Možnosti**  >  **Python**  >  **serveru jazyka** Python. Viz [Možnosti-jazykový Server](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> V současné době Visual Studio nepodporuje v komentářích parametry typu.
::: moniker-end

### <a name="signature-help"></a>Podpis – Help

Při psaní kódu, který volá funkci, se při zadání otevřeného `(` a zobrazení dostupné dokumentace a informací o parametrech zobrazí zpráva s podpisem. Můžete ji také zobrazit s **Ctrl** + **Shift** + **mezerou** CTRL SHIFT uvnitř volání funkce. Zobrazené informace závisí na řetězcích v dokumentaci ve zdrojovém kódu funkce, ale obsahuje všechny výchozí hodnoty.

![Help signatura v editoru sady Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Pokud chcete zakázat pojmenování v nápovědě, použijte možnosti **nástroje**  >  **Options**  >  **textový editor**  >  **Python**  >  **Obecné** a vymazat informace o parametrech **dokončování příkazů**  >  **Parameter information**.

### <a name="quick-info"></a>Rychlé informace

Když najedete ukazatel myši na identifikátor, zobrazí se Rychlé informace. V závislosti na identifikátoru můžou rychlé informace zobrazovat potenciální hodnoty nebo typy, všechny dostupné dokumentace, návratové typy a umístění definic:

![Rychlé informace v editoru sady Visual Studio](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Barvy kódu

Barevné zvýrazňování kódu používá informace z analýzy kódu k barevným proměnným, příkazům a dalším částem kódu. Například proměnné, které odkazují na moduly nebo třídy, mohou být zobrazeny v jiné barvě než funkce nebo jiné hodnoty a názvy parametrů se zobrazí v jiné barvě než místní nebo globální proměnné. (Ve výchozím nastavení se funkce nezobrazují tučně):

![Barevné zvýrazňování kódu a syntaxe v editoru sady Visual Studio](media/code-editing-code-coloring.png)

Chcete-li přizpůsobit barvy, použijte **Tools**  >  **možnost Nástroje možnosti**  >  **prostředí**  >  **písma a barvy** a upravte položky **Pythonu** v seznamu **zobrazení položek** :

![Možnosti písem a barev v aplikaci Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Chcete-li zakázat barevné zvýraznění kódu, přejít na možnosti **nástroje**  >  **Options**  >  **textový editor**  >  **Python**  >  **Upřesnit** a vymazat **různé možnosti**  >  **názvy barev založené na typu**. Viz [Možnosti – různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou fragmenty kódu, které mohou být vloženy do souborů zadáním zástupce a stiskem klávesy **TAB**nebo pomocí **Edit**  >  příkazu Upravit kód pro**IntelliSense**  >  **vložení kódu** IntelliSense a **obklopit** příkazy, výběrem **Pythonu**a následným výběrem požadovaného fragmentu.

Například `class` je zkratka pro fragment kódu, který vkládá definici třídy. V seznamu automatického dokončování se zobrazí fragment kódu, když zadáte `class` :

![Fragment kódu pro zástupce třídy](media/code-editing-code-snippet-class.png)

Stisknutí klávesy **TAB** vygeneruje zbytek třídy. Pak můžete napsat seznam názvů a základů, přesun mezi zvýrazněnými poli a pomocí **tabulátoru**a stisknutím klávesy **ENTER** začít psát text.

![Zvýrazní oblasti fragmentu kódu, které vám dokončí.](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Příkazy nabídky

Když použijete příkaz **Upravit**  >  **IntelliSense**  >  **kód nabídky Vložit fragment kódu** technologie IntelliSense, nejprve vyberte **Python**a pak vyberte fragment:

![Výběr fragmentu kódu pomocí příkazu Vložit fragment kódu](media/code-editing-code-snippet-insert.png)

Příkaz **Upravit**funkce  >  **IntelliSense**  >  **obklopující pomocí** příkazu, podobně umístí aktuální výběr v textovém editoru do vybraného strukturálního prvku. Předpokládejme například, že máte bit kódu podobný následujícímu:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Když vyberete tento kód a zvolíte-li příkaz **ohraničit pomocí** , zobrazí se seznam dostupných fragmentů. Zvolením možnosti **def** v seznamu umístíte vybraný kód do definice funkce a pomocí klávesy **TAB** můžete přecházet mezi zvýrazněným názvem funkce a argumenty:

![Použití příkazu obklopit s pro fragmenty kódu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Prozkoumávat dostupné fragmenty

Dostupné fragmenty kódu můžete zobrazit ve **Správci fragmentů kódu**, který jste otevřeli pomocí **Tools**  >  příkazu nabídky**Správce fragmentů kódu** nástroje a vybrali **Python** jako jazyk:

![Správce fragmentů kódů v aplikaci Visual Studio](media/code-editing-code-snippets-manager.png)

Chcete-li vytvořit vlastní fragmenty kódu, přečtěte si [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

Pokud píšete skvělý fragment kódu, který byste chtěli sdílet, můžete ho zveřejnit v registru a [dejte nám prosím o tom](https://github.com/Microsoft/PTVS/issues)nějaký. Můžeme být schopni ho zahrnout do budoucí verze sady Visual Studio.

## <a name="navigate-your-code"></a>Navigace v kódu

Podpora Pythonu v sadě Visual Studio poskytuje několik způsobů, jak rychle procházet v rámci kódu, včetně knihoven, pro které je k dispozici zdrojový kód: [navigační panel](#navigation-bar), [**Přejít k definici**](#go-to-definition), [**Přejít na**](#navigate-to)a [**vyhledat všechny odkazy**](#find-all-references). Můžete také použít [**Prohlížeč objektů**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)sady Visual Studio.

### <a name="navigation-bar"></a>Navigační panel

Navigační panel se zobrazí v horní části každého okna editoru a obsahuje seznam definic se dvěma úrovněmi. Rozevírací seznam vlevo obsahuje definice třídy a funkce nejvyšší úrovně v aktuálním souboru; v rozevíracím seznamu vpravo se zobrazí seznam definic v rámci oboru zobrazeného vlevo. Při přesunu v editoru se seznamy aktualizují, aby zobrazovaly aktuální kontext, a můžete také vybrat položku z těchto seznamů a přejít přímo na.

![Navigační panel v editoru sady Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Chcete-li skrýt navigační panel, v nabídce **nástroje**klikněte na  >  **možnost**nástroje  >  **textový editor**  >  **Python**  >  **Obecné** a zrušte zaškrtnutí políčka **Nastavení**  >  **navigační panel**.

### <a name="go-to-definition"></a>Přejít k definici

**Přejít k definici** rychle přeskočí z použití identifikátoru (například název funkce, třídy nebo proměnné) na zdrojový kód, kde je definován. Můžete ji vyvolat kliknutím pravým tlačítkem myši na identifikátor a vybráním možnosti **Přejít k definici** nebo vložením blikajícího kurzoru do identifikátoru stisknutím klávesy **F12**. Funguje napříč vaším kódem a externími knihovnami za předpokladu, že je zdrojový kód k dispozici. Pokud zdrojový kód knihovny není k dispozici, **přejdete k odkazu definice** na příslušný `import` příkaz pro odkaz na modul nebo zobrazíte chybu.

![Přejít na definice – příkaz v aplikaci Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Přejít na

Příkaz **Upravit**  >  **navigaci na** (**CTRL** + **,**) zobrazí vyhledávací pole v editoru, kde můžete zadat libovolný řetězec a zobrazit možné shody v kódu, které definují funkci, třídu nebo proměnnou obsahující tento řetězec. Tato funkce poskytuje podobnou funkci jako **Přejít k definici** , ale bez nutnosti najít použití identifikátoru.

Poklikejte na libovolný název, nebo vyberte pomocí kláves se **šipkami a přejít na definici**identifikátoru.

![Přejít k příkazu v aplikaci Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Najít všechny odkazy

**Najít všechny odkazy** je užitečný způsob, jak zjistit, kde je daný identifikátor definován a použit, včetně importů a přiřazení. Můžete ji vyvolat kliknutím pravým tlačítkem myši na identifikátor a vybráním možnosti **Najít všechny odkazy**nebo vložením blikajícího kurzoru do identifikátoru stisknutím **klávesy SHIFT** + **F12**. Dvojitým kliknutím na položku v seznamu přejdete do jejího umístění.

![Najít všechny odkazy – výsledky](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Viz také

- [Formátování](formatting-python-code.md)
- [Refactoring](refactoring-python-code.md)
- [Použití linter](linting-python-code.md)
