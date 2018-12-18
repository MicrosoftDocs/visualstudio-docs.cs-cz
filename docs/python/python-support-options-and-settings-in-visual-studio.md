---
title: Možnosti a nastavení pro Python
description: Referenční informace pro různá nastavení v sadě Visual Studio, které se týkají kódu v Pythonu a projekty.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: f5b8c6b3860641dafccac28b24a4be141d90eae5
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220053"
---
# <a name="options-for-python-in-visual-studio"></a>Možnosti pro Python v sadě Visual Studio

Chcete-li zobrazit možnosti Python, použijte **nástroje** > **možnosti** nabídce příkaz, ujistěte se, že **zobrazit všechna nastavení** je vybrána a potom přejděte na  **Nástroje Python Tools**:

![Dialogové okno Možnosti Python, obecné](media/options-general.png)

Existují také další možnosti specifické pro Python na **textový Editor** > **Python** > **Upřesnit** kartu a na  **Prostředí** > **písma a barvy** kartu v rámci **textový Editor** skupiny.

> [!Note]
> **Experimentální** skupina obsahuje možnosti pro funkce, které jsou stále ve vývoji a tady nejsou uvedené. Tyto jsou často popsány v příspěvcích na [engineering Python v blogu Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="general-options"></a>Obecné možnosti

(**Nástroje** > **možnosti** > **Python** tab.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Při vytváření virtuálních prostředí zobrazit okno výstupu**| On | Vymazat, aby se zabránilo **výstup** okno nezobrazovalo. |
| **Zobrazit okno výstupu při instalaci nebo odebrání balíčků** | On | Vymazat, aby se zabránilo **výstup** okno nezobrazovalo. |
| **Vždy spustit jako správce pip** | Off | Vždy ukládá `pip install` operace pro všechna prostředí. Při instalaci balíčků sady Visual Studio vyzve k zadání oprávnění správce, pokud se prostředí nachází v chráněné části systému souborů, jako *c:\Program Files*. V této výzvy můžete vždy zvýšit `pip install` pro právě jeden prostředí. Zobrazit [balíčky kartu](python-environments-window-tab-reference.md#packages-tab). |
| **Automatické generování databáze pro dokončování při prvním použití** | On | *Platí pro Visual Studio 2017 verze 15.5 a starší a novějších verzí při použití databáze IntelliSense.* Dokončení databáze pro knihovnu upřednostňuje při psaní kódu, která ji používá. Další informace najdete v tématu [kartu technologie Intellisense](python-environments-window-tab-reference.md#intellisense-tab). |
| **Ignorovat systémové proměnné PYTHONPATH** | On | PYTHONPATH ve výchozím nastavení se ignoruje, protože Visual Studio poskytuje přímější prostředky ke specifikaci cesty pro hledání v prostředí a projekty. Zobrazit [cesty hledání](search-paths.md) podrobnosti. |
| **Po přidání propojených souborů aktualizovat cesty pro hledání** | On | Při nastavení, přidávání [propojený soubor](managing-python-projects-in-visual-studio.md#linked-files) do projektu aktualizace [cesty hledání](search-paths.md) tak, aby IntelliSense můžete zahrnout obsah složky propojený soubor databáze pro dokončování. Zrušte zaškrtnutí tohoto políčka vyloučit takový obsah z databáze pro dokončování. |
| **Upozornění při importování modulu se nenašel.** | On | Zrušte tuto možnost, chcete-li potlačit upozornění, když víte, importovaného modulu není v současné době k dispozici, ale jinak nemá vliv na kód operace. |
| **Sestava nekonzistentní odsazení jako** | **Upozornění** | Protože interpret Pythonu závisí do značné míry na správné odsazení k určení oboru, Visual Studio ve výchozím nastavení vydá upozornění při zjištění nekonzistentní odsazení, které mohou uvádět chyb kódování. Nastavte na **chyby** jako ještě přísnější, což způsobí, že program ukončíte v takových případech. Chcete-li toto chování úplně zakázat, vyberte **není**. |
| **Kontrola zjišťování/zpráv** | **Jednou za týden** | Nastaví frekvenci, s jakou umožníte softwaru Visual Studio otevřete okno obsahující webovou stránku pomocí souvisejí s Pythonem zjišťování a příspěvky, pokud je k dispozici. Možnosti jsou **nikdy**, **jednou denně**, **jednou za týden**, a **jednou za měsíc**. |
| **Resetovat všechna trvale skrytá dialogová okna** tlačítko | není k dispozici | Různé dialogových oknech, jako poskytují možnosti **tento dialog již příště nezobrazovat**. Pomocí tohoto tlačítka můžete vymazat těchto možností a způsobit, že dialogových oknech se zase objeví. |

![Dialogové okno Možnosti Python, obecné](media/options-general.png)

## <a name="debugging-options"></a>Možnosti ladění

(**Nástroje** > **možnosti** > **Python** > **ladění** tab.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Dotázat se před spuštěním, když jsou chyby** | On | Pokud nastavíte, zobrazí výzvu k potvrzení, že chcete spustit kód, který obsahuje chyby. Zrušte zaškrtnutí tohoto políčka Zakázat upozornění. |
| **Při neobvyklém ukončení procesu počkat na vstup**<br/><br/>**Při procesu počkat na vstup** | Na (pro oba) | Python program spuštěn ze sady Visual Studio běží v samostatném okně konzoly. Ve výchozím okně čeká na stisknutím jakékoli klávesy před jeho uzavřením bez ohledu na to, jak program je ukončen. Pokud chcete odstranit tohoto řádku a zavřete okno automaticky, zrušte jeden nebo oba z těchto možností. |
| **TEE program výstup do okna výstup ladění** | On | V okně samostatné konzoly a sady Visual Studio se zobrazí výstup programu **výstup** okna. Zrušte zaškrtnutí tohoto políčka Zobrazit výstup pouze v okně samostatné konzoly. |
| **Pozastavte běh při výjimce SystemExit s ukončovacím kódem 0** | Off | Pokud nastavení, ladicí program se zastaví na tuto výjimku. Když je jasné, že ladicí program se ukončí bez přerušení. |
| **Povolit ladění standardní knihovny Pythonu** | Off | Umožňuje krokování s vnořením do standardní knihovny zdrojový kód při ladění, ale se prodlouží doba potřebná pro ladicí program ke spuštění.|

![Dialogové okno Možnosti Python, karta ladění](media/options-debugging.png)

## <a name="diagnostics-options"></a>Možnosti diagnostiky

(**Nástroje** > **možnosti** > **Python** > **diagnostiky** tab.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zahrnout protokoly analýzy** | On | Obsahuje podrobné protokoly týkající se analýza nainstalované prostředí Pythonu při ukládání diagnostiku do souboru nebo kopírování do schránky. pomocí tlačítka. Tato možnost může významně zvyšuje velikost generovaného souboru, ale je často nutné k diagnostice problémů technologie IntelliSense. |
| **Uložit diagnostické údaje do souboru** tlačítko | není k dispozici | Zobrazí výzvu k zadání názvu souboru a pak uloží do protokolu do textového souboru. |
| **Kopírovat diagnostické údaje do schránky** tlačítko | není k dispozici | Umístí celý protokol do schránky; Tato operace může trvat nějakou dobu v závislosti na velikosti souboru protokolu. |

![Dialogové okno Možnosti Python, karta Diagnostika](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Interaktivní možnosti Windows

(**Nástroje** > **možnosti** > **Python** > **interaktivní Windows** tab.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Skripty** | není k dispozici | Určuje obecné složku pro spouštěcí skripty vyrovnat **interaktivní** windows pro všechna prostředí. Zobrazit [spouštěcí skripty](python-environments-window-tab-reference.md#startup-scripts). Upozorňujeme však, že tato funkce aktuálně nefunguje. |
| **Šipky nahoru/dolů přejděte historie** | On | Procházení historie v pomocí kláves se šipkami **interaktivní** okna. Zrušte zaškrtnutí tohoto nastavení můžete pomocí kláves se šipkami, chcete-li procházet **interaktivní** místo toho výstupního okna. |
| **Režim dokončování** | **Jenom vyhodnotit výrazy bez volání funkcí** | Procesu, který určuje členy k dispozici na na výraz **interaktivní** okno může vyžadovat vyhodnocení aktuální nedokončené výraz, který může mít za následek vedlejší účinky nebo funkce volána více než jednou. Ve výchozím nastavení je **jenom vyhodnotit výrazy bez volání funkce** vyloučí výrazy, které se zobrazí volat funkci, ale vyhodnotí jiných výrazech. Například je vyhodnocen jako `a.b` , ale ne `a().b`.  **Nikdy vyhodnocujte výrazy** brání všechny vedlejší účinky pomocí jenom normální IntelliSense modulu pro návrhy. **Vyhodnotit všechny výrazy** vyhodnotí celý výraz získat návrhy, bez ohledu na to vedlejší účinky. |
| **Skrýt návrhy statické analýzy** | Off | Pokud nastavíte, zobrazí pouze návrhy, které jsou získány vyhodnocením výrazu. Pokud v kombinaci s **Doplňovacím režimem** hodnotu **nikdy vyhodnocujte výrazy**, žádné užitečnou funkci dokončování joinkind **interaktivní** okna. |

![Možnosti dialogového okna, interaktivní Windows kartu Pythonu](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Rozšířené možnosti editoru Pythonu

(**Nástroje** > **možnosti** > **textový Editor** > **Python**  >   **Pokročilé** tab.)

### <a name="completion-results"></a>Výsledky dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Dokončení členů zobrazí IK členů.** | Off | Pokud nastavíte, zobrazí pouze dokončování, které jsou podporovány všechny možné typy. |
| **Filtrovat seznam podle hledaného řetězce** | On | Platí při psaní filtrování dokončení návrhy (výchozí je zaškrtnuté políčko). |
| **Automaticky zobrazit dokončení pro všechny identifikátory** | On | Zrušte zaškrtnutí tohoto políčka zakážete dokončování v editor a **interaktivní** systému windows. |

### <a name="selection-in-completion-list"></a>Výběr v seznamu dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Potvrzen zadáním následujících znaků** | **{}\[\]().,:, +-* / % &&#124;^ ~ = <> #@\\** | Tyto znaky obvykle podle identifikátor, který jeden můžou vybrat ze seznamu dokončení, proto je vhodné potvrdit dokončení jednoduše zadáním znaku. Můžete odebrat nebo přidat zvláštní znaky do seznamu podle potřeby.  |
| **Zadejte aktuální dokončení potvrzení změn** | On | Při nastavení **Enter** klíč vybere a použije aktuálně vybraného dokončení stejně jako u výše uvedených znaků (ale samozřejmě není znak pro **Enter** proto ji nelze přímo přejít do tohoto seznamu!). |
| **Přidat nový řádek na konec plně napsaného slova** | Off | Ve výchozím nastavení, pokud zadáte celé slovo, které se zobrazí automaticky otevírané okno dokončení a stiskněte klávesu **Enter**, potvrdíte, že dokončení. Nastavením této možnosti můžete efektivně potvrdit dokončování napsání identifikátor, tak, aby **Enter** vloží nový řádek. |

### <a name="miscellaneous-options"></a>Ostatní možnosti

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Po otevření souborů vstoupit do režimu sbalování** | On | Automaticky zapněte funkci sbalování sady Visual Studio v editoru při otevírání souboru kódu Pythonu. |
| **Vložit odebrat REPL výzvy** | On | Odebere **>>>** a **...**  z vložený text povolení migrace kódu z profilu uživatele **interaktivní** okna editoru. Pokud potřebujete zachovat tyto znaky při vkládání z jiných zdrojů, zrušte zaškrtnutí tohoto políčka. |
| **Názvy barev podle typů** | On | Umožňuje barevné zvýrazňování syntaxe ve kódu Pythonu. |

![Python editor dialogové okno Možnosti, karta Upřesnit](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Možnosti písma a barvy

(**Prostředí** > **písma a barvy** kartu v rámci **textový Editor** skupiny.)

Názvy možností Python jsou předponu **Python** a není potřeba vysvětlovat. Výchozí písmo pro všechny barevných motivů Visual Studio je 10 b Consolas pravidelně (ne bold). Výchozí barvy se liší podle motiv. Obvykle můžete změnit písmo nebo barevné Pokud pro vás obtížné číst text s výchozím nastavením.

![Možnosti písma a barvy Pythonu](media/options-fonts-and-colors.png)
