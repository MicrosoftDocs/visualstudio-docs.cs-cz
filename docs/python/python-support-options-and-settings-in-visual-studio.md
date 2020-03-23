---
title: Možnosti a nastavení pro Python
description: Odkaz na různá nastavení v sadě Visual Studio, které se vztahují k kódu Pythonu a projekty.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302747"
---
# <a name="options-for-python-in-visual-studio"></a>Možnosti pro Python v sadě Visual Studio

Chcete-li zobrazit možnosti Pythonu, použijte příkaz**Příkaz Možnosti** **nástrojů,** > ujistěte se, že je **vybraná možnost Zobrazit všechna nastavení,** a přejděte do **Pythonu**:

::: moniker range="vs-2017"
![Dialogové okno volby Pythonu, karta Obecné](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno volby Pythonu, karta Obecné](media/options-general-2019.png)
::: moniker-end

K dispozici jsou také další možnosti specifické pro Python na kartě **Text Editor** > **Python** > **Upřesnit** a na kartě**Písma a barvy** **prostředí** > ve skupině **Textový editor.**

> [!Note]
> Experimentální **Experimental** skupina obsahuje možnosti pro funkce, které jsou stále ve vývoji a nejsou zde dokumentovány. Často jsou diskutovány v příspěvcích na [pythonském inženýrství na blogu společnosti Microsoft](https://devblogs.microsoft.com/python/).

## <a name="general-options"></a>Obecné možnosti

**(Nástroje** > **Možnosti** > **Python** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zobrazení výstupního okna při vytváření virtuálních prostředí**| Zapnuto | Zrušte zaškrtnutí, chcete-li zabránit zobrazení okna **Výstup.** |
| **Zobrazení výstupního okna při instalaci nebo odebírání balíčků** | Zapnuto | Zrušte zaškrtnutí, chcete-li zabránit zobrazení okna **Výstup.** |
| **Zobrazit panel oznámení pro vytvoření prostředí** | Zapnuto | *Pouze Visual Studio 2019.* Pokud je tato možnost nastavena a uživatel otevře projekt, který obsahuje soubor *requirements.txt* nebo *environment.yml,* visual studio zobrazí informační panel s návrhy na vytvoření virtuálního prostředí nebo prostředí conda, v uvedeném pořadí namísto použití výchozího globálního prostředí. |
| **Zobrazit panel oznámení pro instalaci balíčků** | Zapnuto | *Pouze Visual Studio 2019.* Pokud je tato možnost nastavena a uživatel otevře projekt, který obsahuje soubor *requirements.txt* (a nepoužívá výchozí globální prostředí), Visual Studio porovná tyto požadavky s balíčky nainstalovanými v aktuálním prostředí. Pokud některé balíčky chybí, Visual Studio zobrazí výzvu k instalaci těchto závislostí. |
| **Vždy spouštět správce balíčků jako správce** | Vypnuto | Vždy zvyšuje `pip install` a podobné operace správce balíčků pro všechna prostředí. Při instalaci balíčků visual studio zobrazí výzvu k zadání oprávnění správce, pokud je prostředí umístěno v chráněné oblasti systému souborů, například *c:\Program Files*. V této výzvě můžete vždy zvýšit instalační příkaz pouze pro jedno prostředí. Viz [karta Balíčky](python-environments-window-tab-reference.md#packages-tab). |
| **Automaticky generovat dokončení DB při prvním použití** | Zapnuto | *Platí pro Visual Studio 2017 verze 15.5 a starší a na novější verze při použití databáze IntelliSense.* Upřednostňuje dokončení databáze pro knihovnu při psaní kódu, který ji používá. Další informace naleznete [v záložce Intellisense](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab). |
| **Ignorovat systémové proměnné PYTHONPATH** | Zapnuto | PYTHONPATH je ve výchozím nastavení ignorován, protože Visual Studio poskytuje přímější prostředky k určení vyhledávacích cest v prostředích a projektech. Podrobnosti najdete [v tématu Hledání cest.](search-paths.md) |
| **Aktualizace vyhledávacích cest při přidávání propojených souborů** | Zapnuto | Při nastavení přidání [propojeného souboru](managing-python-projects-in-visual-studio.md#linked-files) do projektu aktualizuje [cesty hledání,](search-paths.md) aby technologie IntelliSense mohla zahrnout obsah složky propojeného souboru do databáze dokončení. Zrušte zaškrtnutí této možnosti, chcete-li takový obsah vyloučit z databáze dokončení. |
| **Upozornit, když importovaný modul nebyl nalezen** | Zapnuto | Zrušte zaškrtnutí této možnosti, chcete-li potlačit upozornění, když víte, že importovaný modul není v současné době k dispozici, ale jinak nemá vliv na operaci kódu. |
| **Nekonzistentní odsazení sestavy jako** | **Upozornění** | Vzhledem k tomu, že interpret Pythonu závisí do značné míry na správné odsazení k určení oboru, Visual Studio ve výchozím nastavení vydává upozornění, když zjistí nekonzistentní odsazení, které by mohly znamenat chyby kódování. Nastavte **chyby** být ještě přísnější, což způsobí, že program ukončit v takových případech. Chcete-li toto chování úplně zakázat, vyberte možnost **Nedělat**. |
| **Podívejte se na průzkum / novinky** | **Jednou týdně** | *Visual Studio 2017 a starší.* Nastaví frekvenci, s jakou povolíte aplikaci Visual Studio otevřít okno obsahující webovou stránku s průzkumy a diskusními položkami souvisejícími s Pythonem, pokud jsou k dispozici. Možnosti jsou **Nikdy**, **Jednou denně**, **Jednou týdně**a **Jednou za měsíc**. |
| **Tlačítko Obnovit všechna trvale skrytá dialogová okna** | neuvedeno | Různá dialogová okna poskytují možnosti, například **Nezobrazovat znovu**. Pomocí tohoto tlačítka můžete tyto možnosti vymazat a způsobit, že se dialogy znovu objeví. |

::: moniker range="vs-2017"
![Dialogové okno volby Pythonu, karta Obecné](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno volby Pythonu, karta Obecné](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Možnosti Conda

**(Nástroje** > **Možnosti** > **Python** > **Conda** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Cesta spustitelného souboru Conda** | (prázdné) | Určuje přesnou cestu k spustitelnému souboru *conda.exe,* nikoli na výchozí instalaci Miniconda, která je součástí úlohy Pythonu. Pokud je zde zadána jiná cesta, má přednost před výchozí instalací a všemi dalšími spustitelnými soubory conda.exe zadanými v registru. Toto nastavení můžete změnit ručně, pokud ručně nainstalujete novější verzi aplikace Anaconda nebo Miniconda nebo chcete použít 32bitovou distro místo výchozího 64bitového distro. |

![Dialogové okno možnosti Pythonu, karta Jazykový server](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Možnosti ladění

**(Nástroje** > **Možnosti** > **Python** > **ladění** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Před spuštěním se zobrazí výzva, pokud jsou přítomny chyby** | Zapnuto | Po nastavení zobrazívýzva k potvrzení, že chcete spustit kód, který obsahuje chyby. Zrušte zaškrtnutí této možnosti, chcete-li upozornění zakázat. |
| **Počkejte na vstup, když proces ukončí abnormálně**<br/><br/>**Počkejte na vstup, když proces ukončí normálně** | Zapnuto (pro oba) | Program Pythonu spuštěný z Visual Studia běží ve vlastním okně konzoly. Ve výchozím nastavení okno čeká, až stisknete klávesu před zavřením bez ohledu na to, jak program ukončí. Chcete-li tuto výzvu odebrat a okno automaticky zavřít, zrušte zaškrtnutí jedné z těchto možností nebo obou těchto možností. |
| **Výstup programu Tee do okna Ladění výstupu** | Zapnuto | Zobrazí výstup programu v samostatném okně konzoly i v okně Visual Studio **Output.** Zrušte zaškrtnutí této možnosti, chcete-li zobrazit výstup pouze v samostatném okně konzoly. |
| **Break na SystemExit výjimku s ukončovací kód nula** | Vypnuto | Pokud je nastavena, zastaví ladicí program na tuto výjimku. Pokud je zaškrtnuto, ladicí program se ukončí bez přerušení. |
| **Povolení ladění standardní knihovny Pythonu** | Vypnuto | Umožňuje krokovat do zdrojového kódu standardní knihovny při ladění, ale zvyšuje čas potřebný pro debugger ke spuštění.|
| **Zobrazit vrácenou hodnotu funkce** | Zapnuto | *Pouze Visual Studio 2019.* Zobrazí vrácené hodnoty funkce v okně **Locals** a poté krokování přes volání funkce v ladicím programu (F10) |
| **Použití staršího ladicího programu** | Vypnuto | *Pouze Visual Studio 2019.* Instruuje Visual Studio používat starší ladicí program ve výchozím nastavení. Další informace naleznete v tématu [Ladění – použití staršího ladicího programu](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Dialogové okno možnosti Pythonu, karta Ladění](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno možnosti Pythonu, karta Ladění](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Možnosti diagnostiky

**(Tools** > **Options** > **Python** > **Diagnostika** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zahrnout protokoly analýzy** | Zapnuto | Obsahuje podrobné protokoly týkající se analýzy nainstalovaných prostředí Pythonu při ukládání diagnostiky do souboru nebo jejich kopírování do schránky pomocí tlačítek. Tato možnost může výrazně zvětšit velikost generovaného souboru, ale je často vyžadována k diagnostice problémů technologie IntelliSense. |
| **Tlačítko Uložit diagnostiku do souboru** | neuvedeno | Zobrazí výzvu k zadání názvu souboru a potom protokol uloží do textového souboru. |
| **Tlačítko Kopírovat diagnostiku do** schránky | neuvedeno | Umístí celý protokol do schránky; Tato operace může trvat nějakou dobu v závislosti na velikosti protokolu. |

![Dialogové okno možnosti Pythonu, karta Diagnostika](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Možnosti interaktivního systému Windows

**(Nástroje** > **Možnosti** > **Python** > interaktivní**windows** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Skripty** | neuvedeno | Určuje obecnou složku pro spouštěcí skripty, která se má použít pro **interaktivní** okna pro všechna prostředí. Viz [Spouštěcí skripty](python-environments-window-tab-reference.md#startup-scripts). Všimněte si však, že tato funkce v současné době nefunguje. |
| **Šipky nahoru/dolů provigují historii** | Zapnuto | Pomocí kláves se šipkami můžete procházet historii v **interaktivním** okně. Zrušte zaškrtnutí tohoto nastavení, chcete-li místo toho procházet pomocí kláves se šipkami ve výstupu **interaktivního** okna. |
| **Režim dokončení** | **Vyhodnocovat pouze výrazy bez volání funkcí** | Proces určení dostupných členů na výraz v **interaktivním** okně může vyžadovat vyhodnocení aktuálního nedokončeného výrazu, což může mít za následek opakované volání vedlejších účinků nebo funkcí. Výchozí nastavení **Pouze vyhodnotit výrazy bez volání funkce** vylučuje výrazy, které se zobrazí volat funkci, ale vyhodnocuje jiné výrazy. Například vyhodnocuje, `a.b` ale ne `a().b`.  **Nikdy nevyhodnocovat výrazy** zabraňuje všechny vedlejší účinky, pomocí pouze normální IntelliSense modul pro návrhy. **Vyhodnotit všechny výrazy vyhodnotí** celý výraz získat návrhy, bez ohledu na vedlejší účinky. |
| **Skrytí návrhů statické analýzy** | Vypnuto | Pokud je nastavena, zobrazí pouze návrhy, které jsou získány vyhodnocením výrazu. V kombinaci s hodnotou **režimu dokončení** **Nikdy nevyhodnocovat výrazy**, žádné užitečné dokončení se zobrazí v **interaktivní** masce. |

![Dialogové okno možnosti Pythonu, karta Interaktivní windows](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Možnosti jazykového serveru

**(Tools** > **Options** > **Python** > Jazyk **server** kartu.)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zakázat dokončení z Typeshed** | Vypnuto | Visual Studio IntelliSense obvykle používá přibalenou verzi Typeshed (sada *souborů .pyi)* k vyhledání nápovědy k typu pro standardní knihovny a knihovny třetích stran pro Python 2 i Python 3. Nastavení této možnosti zakáže přibalené TypeShed chování. |
| **Vlastní cesta typeshed** | (prázdné) | Pokud je nastavena, Visual Studio používá Typeshed soubory na této cestě namísto jeho přibalené verze. Ignorovat, pokud **zakázat dokončení z Typeshed** je nastavena. |

![Dialogové okno možnosti Pythonu, karta Jazykový server](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Rozšířené možnosti editoru Pythonu

(Nástroje**Tools** > **Možnosti** > **Textový editor** > **Python** > **Advanced** kartu.)

### <a name="completion-results"></a>Výsledky dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Dokončení člena zobrazuje průsečík členů** | Vypnuto | Při nastavení zobrazí pouze dokončení, které jsou podporovány všechny možné typy. |
| **Seznam filtrů založený na vyhledávacím řetězci** | Zapnuto | Použije filtrování návrhů dokončení při psaní (výchozí nastavení je zaškrtnuto). |
| **Automaticky zobrazit dokončení pro všechny identifikátory** | Zapnuto | Zrušte zaškrtnutí této možnosti, chcete-li zakázat dokončení v editoru i **interaktivních** oknech. |

### <a name="selection-in-completion-list"></a>Výběr v seznamu dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Potvrzeno zadáním následujících znaků** | **{}\[\]().::;+-*/%&&#124;^~=<> #@\\** | Tyto znaky se obvykle řídí identifikátorem, který lze vybrat ze seznamu dokončení, takže je vhodné potvrdit dokončení jednoduše zadáním znaku. Podle potřeby můžete do seznamu odebrat nebo přidat určité znaky.  |
| **Zadejte aktuální dokončení potvrzení** | Zapnuto | Když je **nastavena,** klávesa Enter zvolí a použije aktuálně vybrané dokončení jako u výše uvedených znaků (ale samozřejmě pro **Enter** není znak, takže nemůže jít přímo do tohoto seznamu!). |
| **Přidání nového řádku na zadejte na konci plně zadaný word** | Vypnuto | Ve výchozím nastavení, pokud zadáte celé slovo, které se zobrazí v rozbalovacím okno dokončení a stiskněte **Enter**, potvrzení, že dokončení. Nastavením této možnosti efektivně potvrdíte dokončení po dokončení zadávání identifikátoru tak, aby **Enter** vložil nový řádek. |

### <a name="miscellaneous-options"></a>Různé možnosti

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zadání režimu osnovy při otevření souborů** | Zapnuto | Při otevírání souboru kódu Pythonu automaticky zapněte funkci osnovy visual studia v editoru. |
| **Vložit odstraněny výzvy REPL** | Zapnuto | Odstraňuje **>>>** a **...** z vloženého textu, což umožňuje snadný přenos kódu z **interaktivního** okna do editoru. Zrušte zaškrtnutí této možnosti, pokud potřebujete tyto znaky zachovat při vkládání z jiných zdrojů. |
| **Názvy barev založené na typech** | Zapnuto | Povolí vkódu Pythonu vybarvení syntaxe. |

![Dialogové okno možností editoru Pythonu, karta Upřesnit](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Písma a barvy, volby

( Karta**Písma a barvy** **prostředí** > ve skupině **Textový editor.)**

Názvy možností Pythonu jsou všechny předponou **pythonu** a jsou samozřejmé. Výchozí písmo pro všechny barevné motivy sady Visual Studio je 10 bodů Consolas regular (ne tučné). Výchozí barvy se liší podle motivu. Obvykle změníte písmo nebo barvu, pokud je pro vás obtížné číst text s výchozím nastavením.

![Možnosti písma a barev pythonu](media/options-fonts-and-colors.png)
