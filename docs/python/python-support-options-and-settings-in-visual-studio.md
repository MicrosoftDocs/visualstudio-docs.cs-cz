---
title: Možnosti a nastavení pro Python
description: Odkaz na různá nastavení v aplikaci Visual Studio, která se vztahují k kódu a projektům Python.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315132"
---
# <a name="options-for-python-in-visual-studio"></a>Možnosti pro Python v aplikaci Visual Studio

Pokud chcete zobrazit možnosti Pythonu, **Tools**použijte  >  příkaz nabídky**Možnosti** nástrojů, ujistěte se, že je vybraná možnost **Zobrazit všechna nastavení** a pak přejít na **Python**:

::: moniker range="vs-2017"
![Dialogové okno Možnosti Pythonu, karta Obecné](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno Možnosti Pythonu, karta Obecné](media/options-general-2019.png)
::: moniker-end

K dispozici jsou také další možnosti specifické pro Python na kartě Upřesnit v **textovém editoru**  >  **Python**  >  **Advanced** a na **Environment**  >  kartě**písma a barvy** prostředí v rámci skupiny **textový editor** .

> [!Note]
> **Experimentální** skupina obsahuje možnosti pro funkce, které jsou stále ve vývoji a nejsou zdokumentovány zde. Jsou často popsány v tématu příspěvky na [blogu Pythonu na blogu Microsoftu](https://devblogs.microsoft.com/python/).

## <a name="general-options"></a>Obecné možnosti

(**Nástroje**  >  **Možnosti**  >  Karta **Pythonu** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zobrazit okno Výstup při vytváření virtuálních prostředí**| Zapnout | Zrušte zaškrtnutí, aby se zabránilo zobrazování okna **výstup** . |
| **Zobrazit okno Výstup při instalaci nebo odebírání balíčků** | Zapnout | Zrušte zaškrtnutí, aby se zabránilo zobrazování okna **výstup** . |
| **Zobrazit panel oznámení pro vytváření prostředí** | Zapnout | *Pouze Visual Studio 2019.* Pokud je tato možnost nastavena a uživatel otevře projekt, který obsahuje soubor *requirements.txt* nebo *Environment. yml* , sada Visual Studio zobrazí informační panel s návrhy na vytvoření virtuálního prostředí nebo prostředí Conda, namísto použití výchozího globálního prostředí. |
| **Zobrazit panel oznámení pro instalaci balíčků** | Zapnout | *Pouze Visual Studio 2019.* Pokud je tato možnost nastavena a uživatel otevře projekt, který obsahuje soubor *requirements.txt* (a nepoužívá výchozí globální prostředí) Visual Studio porovná tyto požadavky s balíčky nainstalovanými v aktuálním prostředí. Pokud chybí nějaké balíčky, Visual Studio zobrazí výzvu k instalaci těchto závislostí. |
| **Vždy spouštět správce balíčků jako správce** | Vypnuto | Vždy zvyšuje úroveň `pip install` a podobné operace Správce balíčků pro všechna prostředí. Při instalaci balíčků se Visual Studio vyzve k zadání oprávnění správce, pokud se prostředí nachází v chráněné oblasti systému souborů, jako je například *C:\Program Files*. V této výzvě můžete zvolit, že se má vždycky zvýšit úroveň příkazu instalovat jenom pro jedno prostředí. Viz [karta balíčky](python-environments-window-tab-reference.md#packages-tab). |
| **Při prvním použití automaticky generovat databázi pro dokončování** | Zapnout | *Platí pro Visual Studio 2017 verze 15,5 a starší a novější verze při použití databáze IntelliSense.* Určí prioritu dokončení databáze pro knihovnu při psaní kódu, který ji používá. Další informace najdete na [kartě IntelliSense](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab). |
| **Ignorovat proměnné PYTHONPATH na úrovni systému** | Zapnout | PYTHONPATH se ve výchozím nastavení ignoruje, protože Visual Studio poskytuje lépe přímější způsob určení cest hledání v prostředích a projektech. Podrobnosti najdete v tématu [Vyhledání cest](search-paths.md) . |
| **Aktualizace cest hledání při přidávání propojených souborů** | Zapnout | Když je tato možnost nastavena, přidání [propojeného souboru](managing-python-projects-in-visual-studio.md#linked-files) do projektu aktualizuje [cesty hledání](search-paths.md) tak, aby technologie IntelliSense mohla do své databáze pro doplňování zahrnovat obsah složky propojeného souboru. Zrušením této možnosti vyloučíte takový obsah z databáze pro dokončování. |
| **Upozornit, když se importovaný modul nenajde** | Zapnout | Zrušením této možnosti potlačíte upozornění, když víte, že importovaný modul není momentálně k dispozici, ale nemá jinak vliv na operaci s kódem. |
| **Nahlásit nekonzistentní odsazení jako** | **Upozornění** | Vzhledem k tomu, že interpret Pythonu závisí silně na správném odsazení pro určení rozsahu, Visual Studio ve výchozím nastavení vystavuje upozornění, když detekuje nekonzistentní odsazení, která by mohla označovat chyby kódování. Nastavte, aby byly **chyby** ještě přísnější, což způsobí, že se program v takových případech ukončí. Pokud chcete toto chování úplně zakázat, vyberte **ne**. |
| **Vyhledat průzkum/novinky** | **Jednou týdně** | *Visual Studio 2017 a starší.* Nastaví četnost, s jakou umožníte, aby sada Visual Studio otevřela okno obsahující webovou stránku s použitím průzkumů a položek novinek v Pythonu, pokud jsou k dispozici. Možnosti nejsou **nikdy**, **jednou za den**, **jednou za týden**a **jednou za měsíc**. |
| Tlačítko **resetovat všechna trvale skrytá dialogová okna** | Není k dispozici | Jiná dialogová okna poskytují možnosti, jako již **Příště tuto zprávu nezobrazovat**. Pomocí tohoto tlačítka můžete tyto možnosti Vymazat a způsobit, že se dialogy znovu zobrazí. |

::: moniker range="vs-2017"
![Dialogové okno Možnosti Pythonu, karta Obecné](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno Možnosti Pythonu, karta Obecné](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda možnosti

(**Nástroje** > **Možnosti** > **Python** > Karta **conda** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Cesta ke spustitelnému souboru conda** | trhnout | Určuje přesnou cestu ke spustitelnému souboru *conda.exe* , ale nespoléhá se na výchozí instalaci Miniconda, která je součástí úlohy Pythonu. Pokud je zde uvedena jiná cesta, má přednost před výchozí instalací a dalšími conda.exe spustitelnými soubory zadanými v registru. Toto nastavení můžete změnit, pokud ručně nainstalujete novější verzi Anaconda nebo Miniconda, nebo chcete použít 32 distribuce, nikoli výchozí 64-bit distribuce. |

![Dialogové okno Možnosti Pythonu, karta jazykový Server](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Možnosti ladění

(**Nástroje**  >  **Možnosti**  >  **Python**  >  Karta **ladění** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Dotázat se před spuštěním, když jsou k dispozici chyby** | Zapnout | Při nastavení se zobrazí výzva k potvrzení, že chcete spustit kód, který obsahuje chyby. Zrušením této možnosti zakážete upozornění. |
| **Při neobvyklém ukončení procesu počkat na vstup**<br/><br/>**Při normálním ukončení procesu počkat na vstup** | Zapnuto (pro obě) | Program Pythonu spuštěný ze sady Visual Studio se spouští ve vlastním okně konzoly. Ve výchozím nastavení okno čeká na stisknutí klávesy před zavřením bez ohledu na to, jak se program ukončí. Chcete-li tuto výzvu odebrat a zavřít okno automaticky, zrušte zaškrtnutí jedné nebo obou možností. |
| **Výstup programu Tee do okna výstup ladění** | Zapnout | Zobrazí výstup programu v samostatném okně konzoly i v okně **výstup** aplikace Visual Studio. Zaškrtnutím této možnosti zobrazíte výstup pouze v samostatném okně konzoly. |
| **Přerušení při výjimce SystemExit s ukončovacím kódem nula** | Vypnuto | Pokud je nastaveno, zastaví ladicí program na této výjimce. Pokud je jasné, ladicí program se ukončí bez přerušení. |
| **Povolit ladění standardní knihovny Pythonu** | Vypnuto | Umožňuje při ladění krokovat zdrojový kód standardní knihovny, ale zvyšuje čas potřebný ke spuštění ladicího programu.|
| **Zobrazit návratovou hodnotu funkce** | Zapnout | *Pouze Visual Studio 2019.* Zobrazuje návratové hodnoty funkcí v okně **místní** hodnoty a rozkrokování volání funkce v ladicím programu (F10). |
| **Použít starší ladicí program** | Vypnuto | *Pouze Visual Studio 2019.* Instruuje aplikaci Visual Studio, aby ve výchozím nastavení používala starší verzi ladicího programu. Další informace naleznete v tématu [ladění – použití starší verze ladicího programu](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Dialogové okno Možnosti Pythonu, karta ladění](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dialogové okno Možnosti Pythonu, karta ladění](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Možnosti diagnostiky

(**Nástroje**  >  **Možnosti**  >  **Python**  >  Karta **Diagnostika** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zahrnout protokoly analýzy** | Zapnout | Obsahuje podrobné protokoly týkající se analýzy nainstalovaných prostředí Pythonu při ukládání diagnostiky do souboru nebo jejich kopírování do schránky pomocí tlačítek. Tato možnost může významně zvětšit velikost generovaného souboru, ale je často nutná k diagnostice problémů s technologií IntelliSense. |
| Tlačítko **Uložit diagnostiku do souboru** | Není k dispozici | Zobrazí výzvu k zadání názvu souboru a pak uloží protokol do textového souboru. |
| Tlačítko **Kopírovat diagnostiku na schránku** | Není k dispozici | Vloží celý protokol do schránky. Tato operace může v závislosti na velikosti protokolu nějakou dobu trvat. |

![Dialogové okno Možnosti Pythonu, karta Diagnostika](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Interaktivní možnosti Windows

(**Nástroje**  >  **Možnosti**  >  **Python**  >  **Interaktivní karta okna** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Skripty** | Není k dispozici | Určuje obecnou složku pro spouštěcí skripty, které se použijí pro **interaktivní** okna pro všechna prostředí. Viz [skripty při spuštění](python-environments-window-tab-reference.md#startup-scripts). Upozorňujeme však, že tato funkce aktuálně nefunguje. |
| **Šipky nahoru/dolů navigují historii** | Zapnout | Pomocí kláves se šipkami prochází historii v **interaktivním** okně. Zrušením tohoto nastavení můžete místo toho použít klávesy se šipkami k procházení výstupu **interaktivního** okna. |
| **Režim dokončení** | **Vyhodnotit jenom výrazy bez volání funkcí** | Proces určení dostupných členů výrazu v **interaktivním** okně může vyžadovat vyhodnocení aktuálního nedokončeného výrazu, který může vést k vedlejším účinkům nebo funkcím, které jsou volány vícekrát. Výchozí nastavení, **pouze vyhodnotit výrazy bez volání funkce** vyloučí výrazy, které se objeví pro volání funkce, ale vyhodnotí jiné výrazy. Například se vyhodnocuje, `a.b` ale ne `a().b` .  **Nikdy nevyhodnotit výrazy** zabraňují všem vedlejším účinkům, a to pouze pomocí normálního stroje IntelliSense pro návrhy. **Vyhodnotit všechny výrazy** vyhodnotí úplný výraz pro získání návrhů bez ohledu na vedlejší účinky. |
| **Skrýt návrhy statických analýz** | Vypnuto | Při nastavení zobrazí pouze návrhy, které jsou získány vyhodnocením výrazu. Pokud se v kombinaci s **režimem dokončování** **nikdy nevyhodnotí výrazy**, v **interaktivním** okně se nezobrazí žádná užitečná dokončení. |

![Dialogové okno Možnosti Pythonu, interaktivní karta Windows](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Možnosti jazykového serveru

(**Nástroje** > **Možnosti** > **Python** > Karta **jazykový Server** .)

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Zakázat dokončování z Typeshed** | Vypnuto | Visual Studio IntelliSense normálně používá sadu Typeshedch verzí (soubory *. pyi* ) k hledání rad typu pro standardní knihovnu a knihovny třetích stran pro Python 2 a Python 3. Nastavení této možnosti zakáže TypeShed chování sady. |
| **Vlastní cesta Typeshed** | trhnout | Pokud je nastaveno, sada Visual Studio používá soubory Typeshed na této cestě namísto jejich sady oddaných verzí. Ignorujte, pokud je nastavené **Zakázat dokončování z Typeshed** . |

![Dialogové okno Možnosti Pythonu, karta jazykový Server](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Pokročilé možnosti editoru Pythonu

(**Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Python**  >  Karta **Upřesnit** .)

### <a name="completion-results"></a>Výsledky dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Dokončení členů zobrazuje průnik členů.** | Vypnuto | Při nastavení se zobrazí pouze doplňování, které jsou podporovány všemi možnými typy. |
| **Filtrovat seznam podle hledaného řetězce** | Zapnout | Použije filtrování návrhů dokončení při psaní (výchozí je zaškrtnuté). |
| **Automaticky zobrazit dokončování pro všechny identifikátory** | Zapnout | Zrušením této možnosti zakážete dokončování v editoru i v **interaktivních** oknech. |

### <a name="selection-in-completion-list"></a>Výběr v seznamu dokončení

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Potvrzeno zadáním následujících znaků** | **{}\[\]().,:; +-*/% &&#124;^ ~ =<> #@\\** | Tyto znaky se obvykle řídí identifikátorem, který může jeden vybrat ze seznamu pro doplňování, takže je vhodné zapsat dokončování pouhým zadáním znaku. V seznamu můžete podle potřeby odebrat nebo přidat konkrétní znaky.  |
| **Zadejte potvrzení aktuální dokončení.** | Zapnout | Když je nastavena, klávesa **ENTER** vybere a použije aktuálně vybrané dokončování jako znaky uvedené výše (ale samozřejmě není znak pro **ENTER** , takže se do tohoto seznamu nedá přímo přejít!). |
| **Přidat nový řádek při zadání na konci plně zadaného slova** | Vypnuto | Ve výchozím nastavení, pokud zadáte celé slovo, které se zobrazí v místní nabídce dokončení, a stiskněte klávesu **ENTER**, toto dokončení potvrďte. Když nastavíte tuto možnost, efektivně dokončíte dokončování po zadání identifikátoru, například **ENTER** vloží nový řádek. |

### <a name="miscellaneous-options"></a>Různé možnosti

| Možnost | Výchozí | Popis |
| --- | --- | --- |
| **Po otevření souborů přejít do režimu sbalení** | Zapnout | Při otevírání souboru kódu Pythonu automaticky zapněte funkci osnovy sady Visual Studio v editoru. |
| **Vložení – výzvy k odebrání REPL** | Zapnout | Odstraní **>>>** a **...** z vloženého textu a umožňuje snadné přenos kódu z **interaktivního** okna do editoru. Tuto možnost zrušte, pokud při vkládání z jiných zdrojů potřebujete zachovat tyto znaky. |
| **Názvy barev založené na typech** | Zapnout | Povoluje barevné zvýrazňování syntaxe v kódu Pythonu. |

![Dialogové okno Možnosti editoru Pythonu, karta Upřesnit](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Možnosti písem a barev

(**Prostředí**  >  Karta **písma a barvy** v rámci skupiny **textový editor** .)

Názvy možností Pythonu jsou všechny s předponou **Pythonu** a jsou vysvětlivekné. Výchozím písmem u všech barevných motivů sady Visual Studio je 10 – 10 – Consolas (ne tučné). Výchozí barvy se liší podle motivu. V případě, že je obtížné číst text s výchozími nastaveními, je obvykle třeba změnit písmo nebo barvu.

![Možnosti písma a barvy Pythonu](media/options-fonts-and-colors.png)
