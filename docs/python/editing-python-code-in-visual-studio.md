---
title: Úprava kódu v Pythonu
description: Pro Python visual studio poskytuje bohaté Funkce IntelliSense, fragmenty kódu a navigační funkce spolu s formátováním, lintingem a refaktoringem.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73024725"
---
# <a name="edit-python-code"></a>Úprava kódu v Pythonu

Vzhledem k tomu, že trávíte většinu času vývoje v editoru kódu, [podpora Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md) poskytuje funkce, které vám pomohou zvýšit produktivitu. Mezi funkce patří zvýraznění syntaxe technologie IntelliSense, automatické dokončování, nápověda k podpisu, přepsání metod, vyhledávání a navigace.

Editor je také integrován s **interaktivní** okno v sadě Visual Studio, takže je snadné vyměňovat kód mezi těmito dvěma. Viz [Krok výuky 3: Použijte interaktivní okno REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) a [podrobnosti naleznete v příkazu Interaktivní – odeslat do interaktivního.](python-interactive-repl-in-visual-studio.md#send-to-interactive-command)

Obecnou dokumentaci k úpravám kódu v sadě Visual Studio naleznete v [tématu Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md). Viz Také [osnova](../ide/outlining.md), která vám pomůže soustředit se na konkrétní části kódu.

Můžete také použít Visual Studio **Object Browser** **(View** > **Other Windows** > **Object Browser** nebo **Ctrl**+**W** > **J**) pro kontrolu Tříd Pythonu definovaných v každém modulu a funkcí definovaných v těchto třídách.

## <a name="intellisense"></a>IntelliSense

Technologie IntelliSense poskytuje [dokončování](#completions), [nápovědu k podpisu](#signature-help), [rychlé informace](#quick-info)a [zbarvení kódu](#code-coloring). Visual Studio 2017 verze 15.7 a novější také podporují [rady typu](#type-hints).

Chcete-li zvýšit výkon, technologie IntelliSense ve Visual Studiu 2017 verze 15.5 a starší závisí na databázi dokončení, která je generována pro každé prostředí Pythonu ve vašem projektu. Databáze může být nutné aktualizovat, pokud přidáte, odeberete nebo aktualizujete balíčky. Stav databáze se zobrazuje v okně **Prostředí Pythonu** (na stejné úrovni **jako Průzkumník řešení)** na kartě **IntelliSense** (viz [Odkaz na okno Prostředí).](python-environments-window-tab-reference.md)

Visual Studio 2017 verze 15.6 a novější používá jiný způsob poskytování intelliSense dokončení, které nejsou závislé na databázi.

### <a name="completions"></a>Completions

Dokončení se zobrazí jako příkazy, identifikátory a další slova, která mohou být vhodně zadána v aktuálním umístění v editoru. To, co je zobrazeno v seznamu, je založeno na kontextu a je filtrováno tak, aby vynechalo nesprávné nebo rušivé možnosti. Dokončení se často spouští zadáním různých `import`příkazů (například ) a operátorů (včetně tečky), ale můžete je nechat zobrazit kdykoli zadáním **kombinace kláves Ctrl**+**J** > **Space**.

![Dokončení členství v editoru Visual Studio](media/code-editing-completions-simple.png)

Je-li otevřen seznam dokončení, můžete vyhledat požadované dokončení pomocí kláves se šipkami, myši nebo pokračováním v psaní. Při psaní dalších písmen je seznam dále filtrován tak, aby zobrazoval pravděpodobné dokončení. Můžete také použít zástupce, jako jsou:

- Psaní písmen, která nejsou na začátku názvu, například "analyzovat" najít 'argparse'
- Zadáním pouze písmena, která jsou na začátku slova, například 'abc' najít 'AbstractBaseClass' nebo 'vzduch' najít 'as_integer_ratio'
- Přeskakování písmen, například "b64", aby bylo najděte "base64"

Několik příkladů:

![Dokončení členství s filtrováním v editoru sady Visual Studio](media/code-editing-completion-filtering.png)

Dokončení členů se zobrazí automaticky při zadání období za proměnnou nebo hodnotu spolu s metodami a atributy potenciálních typů. Pokud proměnná může být více než jeden typ, seznam obsahuje všechny možnosti ze všech typů, s další informace o označení, které typy podporují každé dokončení. Pokud je dokončení podporováno všemi možnými typy, zobrazí se bez poznámky.

![Dokončení člena na více typech v editoru Visual Studio](media/code-editing-completion-types.png)

Ve výchozím nastavení "dunder" členy (členy začínající a končící dvojité podtržítko) nejsou zobrazeny. Obecně by k těmto členům neměl být přímo přistupován. Pokud ji však potřebujete, zadáním úvodního dvojitého podtržítka přidáte do seznamu tyto dokončení:

![Dokončení soukromého člena v editoru Sady Visual Studio](media/code-editing-completion-dunder.png)

`import` Příkazy `from ... import` a zobrazují seznam modulů, které lze importovat. V `from ... import`aplikaci obsahuje seznam členy, které lze importovat ze zadaného modulu.

![Dokončení importu v editoru Sady Visual Studio](media/code-editing-completion-import.png)

`raise` Příkazy `except` a zobrazují seznamy tříd, které mohou být typy chyb. Seznam nemusí obsahovat všechny uživatelem definované výjimky, ale pomůže vám rychle najít vhodné integrované výjimky:

![Dokončení výjimky v editoru sady Visual Studio](media/code-editing-completion-exception.png)

Zadání @ spustí decorator a zobrazí potenciální decorators. Mnohé z těchto položek nejsou použitelné jako dekoratéři; v dokumentaci ke knihovně zjistěte, které mají být použity.

![Dokončení decorator v editoru Sady Visual Studio](media/code-editing-completion-decorator.png)

> [!Tip]
> Chování dokončení můžete nakonfigurovat **pomocí** > **Options** > **textového editoru textových editorů** > **pythonu** > **Upřesnit**. Mezi nimi **filtr seznam založený na vyhledávací řetězec** použije filtrování návrhů dokončení při psaní (výchozí je zaškrtnuto) a dokončení člen zobrazí **průsečík členů** zobrazuje pouze dokončení, které jsou podporovány všechny možné typy (výchozí je nezaškrtnuté). Viz [Možnosti - výsledky dokončení](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Rady pro psaní typů

*Visual Studio 2017 verze 15.7 a novější.*

"Typ nápovědy" v Pythonu 3.5 +[(PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org) je syntaxe poznámky pro funkce a třídy, které označují typy argumentů, vrácené hodnoty a atributy třídy. Technologie IntelliSense zobrazí rady při psaní typu, když najedete na volání funkcí, argumenty a proměnné, které mají tyto poznámky.

V níže uvedeném `Vector` příkladu `List[float]`je třída `scale` deklarována jako a funkce obsahuje rady při psaní typu pro argumenty i vrácenou hodnotu. Najetím na volání této funkce se zobrazí nápovědy k typu:

![Najetím na volání funkce zobrazíte rady pro psaní typu.](media/code-editing-type-hints1.png)

V následujícím příkladu uvidíte, jak se atributy `Employee` s poznámkami třídy zobrazují v místní části dokončení technologie IntelliSense pro atribut:

![Dokončení technologie IntelliSense zobrazující rady při psaní typu](media/code-editing-type-hints2.png)

Je také užitečné ověřit rady při psaní v celém projektu, protože chyby se obvykle nezobrazí až do běhu. Pro tento účel Visual Studio integruje standardní nástroj MyPy prostřednictvím příkazu kontextové nabídky **Python** > **Run Mypy** v **Průzkumníku řešení**:

![Spustit příkaz kontextové nabídky MyPy v Průzkumníku řešení](media/code-editing-type-hints-run-mypy.png)

Spuštění příkazových výzev k instalaci balíčku mypy, v případě potřeby. Visual Studio pak spustí mypy k ověření typu rady v každém souboru Pythonu v projektu. Chyby se zobrazí v okně **Seznam chyb** sady Visual Studio. Výběrem položky v okně přejde na příslušný řádek v kódu.

V jednoduchém příkladu následující definice funkce obsahuje nápovědu typu označující, že `input` argument je typ `str`, vzhledem k tomu, že volání této funkce se pokusí předat celé číslo:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Pomocí příkazu **Spustit mypy** v tomto kódu se vygeneruje následující chyba:

![Příklad výsledku mypy validujících textových rad](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Pro verze Pythonu před 3.5 Visual Studio také zobrazuje rady typu, které dodáváte prostřednictvím *souborů se zakázaným inzerováním* typeshed (*.pyi*). Soubory se zakázaným inzerováním můžete použít vždy, když nechcete zahrnout rady při psaní přímo do kódu, nebo když chcete vytvořit rady při psaní pro knihovnu, která je nepoužívá přímo. Další informace najdete v [tématu Vytváření zástupů procedur pro moduly Pythonu](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wiki projektu mypy.
>
> V současné době Visual Studio nepodporuje typ rady v komentářích.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Pro verze Pythonu před 3.5 Visual Studio také zobrazuje rady typu, které dodáváte prostřednictvím *souborů se zakázaným inzerováním* typeshed (*.pyi*). Soubory se zakázaným inzerováním můžete použít vždy, když nechcete zahrnout rady při psaní přímo do kódu, nebo když chcete vytvořit rady při psaní pro knihovnu, která je nepoužívá přímo. Další informace najdete v [tématu Vytváření zástupů procedur pro moduly Pythonu](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) na wiki projektu mypy.
>
> Visual Studio obsahuje sadu balíčků typeshed souborů pro Python 2 a 3, takže další stahování není nutné. Pokud však chcete použít jinou sadu souborů, můžete zadat cestu v možnostech jazykového > **serveru** **Možnosti** >  **nástroje** > **Pythonu.** Viz [Možnosti - Jazykový server](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> V současné době Visual Studio nepodporuje typ rady v komentářích.
::: moniker-end

### <a name="signature-help"></a>Nápověda k podpisu

Při psaní kódu, který volá funkci, se `(` při zadání otevření zobrazí nápověda k podpisu a zobrazí dostupné informace o dokumentaci a parametrech. Můžete také vytvořit zobrazení pomocí **ctrl**+**shift**+**mezery** uvnitř volání funkce. Zobrazené informace závisí na dokumentačních řetězcích ve zdrojovém kódu funkce, ale obsahují všechny výchozí hodnoty.

![Nápověda k podpisu v editoru sady Visual Studio](media/code-editing-signature-help.png)

> [!Tip]
> Chcete-li zakázat nápovědu k podpisu, přejděte na**textový** > **editor** > **editoru pythonu** > **obecné** **nástroje** > a zrušte zaškrtnutí na **výpisu informace** > **o parametru dokončení**.

### <a name="quick-info"></a>Rychlé informace

Když najedete ukazatelem myši na identifikátor, zobrazí se popisek Rychlých informací. V závislosti na identifikátoru mohou rychlé informace zobrazovat potenciální hodnoty nebo typy, všechny dostupné dokumenty, návratové typy a umístění definic:

![Rychlé informace v editoru Visual Studia](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Zbarvení kódu

Zbarvení kódu používá informace z analýzy kódu na barevné proměnné, příkazy a další části kódu. Například proměnné, které odkazují na moduly nebo třídy mohou být zobrazeny v jiné barvě než funkce nebo jiné hodnoty a názvy parametrů se zobrazí v jiné barvě než místní nebo globální proměnné. (Ve výchozím nastavení nejsou funkce zobrazeny tučně):

![Zbarvení kódu a syntaxe v editoru Visual Studia](media/code-editing-code-coloring.png)

Chcete-li přizpůsobit barvy, přejděte na**Environment** > **položky prostředí** **nástroje** > **Options** > a barvy a upravte položky **pythonu** v seznamu **Zobrazit položky:**

![Možnosti písma a barvy v sadě Visual Studio](media/code-editing-customize-colors.png)

> [!Tip]
> Chcete-li zakázat zbarvení kódu, přejděte na**možnosti** >  **nástrojů** > **Textový editor** > **Pythonu** > **Upřesnit** a **zrušte zaškrtnutí možnosti** > různé**barvy Názvy barev na základě typu**. Viz [Možnosti – různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou fragmenty kódu, které lze vložit do souborů zadáním zástupce a stisknutím **klávesy Tab**, nebo pomocí příkazů **Edit** > **IntelliSense** > **Insert Code Snippet** and **Surround With,** výběrem **Pythonu**a výběrem požadovaného úryvku.

Například `class` je zástupce pro fragment kódu, který vloží definici třídy. Při psaní `class`se výstřižek zobrazí v seznamu automatického dokončování :

![Fragment kódu pro zástupce třídy](media/code-editing-code-snippet-class.png)

Stisknutím **klávesy Tab** se vygeneruje zbytek třídy. Potom můžete zadat přes seznam název a základy, pohybující se mezi zvýrazněnými poli pomocí **tabulátoru**a stisknutím **klávesy Enter** začněte psát tělo.

![Zvýraznění oblastí fragmentu kódu, které můžete dokončit](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Příkazy nabídky

Když použijete příkaz Příkaz **Vložit** > fragment**kódu** **technologie IntelliSense,** > nejprve vyberete **Python**a pak vyberete úryvek:

![Výběr fragmentu kódu pomocí příkazu Vložit fragment kódu](media/code-editing-code-snippet-insert.png)

Příkaz **Upravit** > **prostředí IntelliSense** > Surround**With** podobně umístí aktuální výběr do textového editoru uvnitř vybraného konstrukčního prvku. Předpokládejme například, že jste měli trochu kódu, jako je následující:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Výběrem tohoto kódu a výběrem příkazu **Prostorovat se** zobrazí seznam dostupných výstřižků. **Výběrdef** ze seznamu umístí vybraný kód do definice funkce a můžete použít klávesu **Tab** pro navigaci mezi zvýrazněným názvem funkce a argumenty:

![Použití příkazu Prostorovat pomocí pro fragmenty kódu](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Prozkoumání dostupných úryvků

Dostupné fragmenty kódu můžete zobrazit ve **Správci výstřižků kódu**, který se otevře pomocí **příkazu Správce** > **výstřižků kódu** nástrojů a jako jazyk **vyberete Python:**

![Správce fragmentů kódu v sadě Visual Studio](media/code-editing-code-snippets-manager.png)

Pokud chcete vytvořit vlastní úryvky, [přečtěte si návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

Pokud napíšete skvělý fragment kódu, který byste chtěli sdílet, neváhejte a pošlete jej v podstatě a [dejte nám vědět](https://github.com/Microsoft/PTVS/issues). Můžeme být schopni zahrnout do budoucí verze sady Visual Studio.

## <a name="navigate-your-code"></a>Navigace v kódu

Podpora Pythonu v sadě Visual Studio poskytuje několik prostředků pro rychlou navigaci v rámci kódu, včetně knihoven, pro které je k dispozici zdrojový kód: [navigační panel](#navigation-bar), [**Přejít na definici**](#go-to-definition), [**Přejít na**](#navigate-to)a najít všechny [**odkazy**](#find-all-references). Můžete také použít [**prohlížeč objektů**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)sady Visual Studio .

### <a name="navigation-bar"></a>Navigační panel

Navigační panel se zobrazí v horní části každého okna editoru a obsahuje dvouúrovňový seznam definic. Levý rozevírací seznam obsahuje definice tříd nejvyšší úrovně a funkce v aktuálním souboru; v pravém rozevíracím seznamu se zobrazí seznam definic v rámci oboru zobrazeného vlevo. Při pohybu v editoru se seznamy aktualizují tak, aby zobrazovalo aktuální kontext, a můžete také vybrat položku z těchto seznamů, na kterou můžete přejít přímo.

![Navigační panel v editoru Visual Studio](media/code-editing-navigation-bar.png)

> [!Tip]
> Chcete-li navigační panel skrýt, přejděte na**Options** > **textový** **editor** > **pythonu** >  **nástrojů** > a zrušte zaškrtnutí**navigačního panelu** **nastavení** > .

### <a name="go-to-definition"></a>Přejít na definici

**Přejít na definici** rychle přeskočí z použití identifikátoru (například název funkce, třídy nebo proměnné), do zdrojového kódu, kde je definován. Vyvoláte jej kliknutím pravým tlačítkem myši na identifikátor a výběrem **možnosti Přejít na definici** nebo umístěním stříšky do identifikátoru a stisknutím **klávesy F12**. Funguje napříč kódem a externími knihovnami za předpokladu, že zdrojový kód je k dispozici. Pokud zdrojový kód knihovny není k dispozici, `import` **přejít na definici** přejde na příslušný příkaz pro odkaz na modul nebo zobrazí chybu.

![Příkaz Přejít na definici v sadě Visual Studio](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Přejít na

Příkaz **Upravit** > **přechod na** **(Ctrl**+, ) zobrazí vyhledávací pole v editoru, kde můžete zadat libovolný řetězec a zobrazit možné shody v kódu, který definuje funkci, třídu nebo proměnnou obsahující tento řetězec.**,** Tato funkce poskytuje podobnou funkci jako **Přejít na definici,** ale bez nutnosti vyhledání použití identifikátoru.

Poklepáním na libovolný název nebo výběrem kláves se šipkami a **Enter**přejdete na definici tohoto identifikátoru.

![Příkaz Přejít na v sadě Visual Studio](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Najít všechny odkazy

**Najít všechny odkazy** je užitečný způsob, jak zjistit, kde je daný identifikátor definován a používán, včetně importů a přiřazení. Vyvoláte jej kliknutím pravým tlačítkem myši na identifikátor a výběrem **možnosti Najít všechny odkazy**nebo umístěním stříšky do identifikátoru a stisknutím **klávesy Shift**+**F12**. Poklepáním na položku v seznamu přejdete na její umístění.

![Najít výsledky všech referencí](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Viz také

- [Formátování](formatting-python-code.md)
- [Refactoring](refactoring-python-code.md)
- [Použití linteru](linting-python-code.md)
