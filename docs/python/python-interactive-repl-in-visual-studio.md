---
title: Interaktivní okno Pythonu (REPL)
description: Použijte interaktivní okno (REPL) pro rychlý vývoj kódu Pythonu v sadě Visual Studio.
ms.date: 02/11/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ceecffec577528484cd67fd13d3e04f368fb916
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302761"
---
# <a name="work-with-the-python-interactive-window"></a>Práce s interaktivním oknem Pythonu

Visual Studio poskytuje interaktivní okno smyčky repl (read-evaluate-print) pro každé prostředí Pythonu, které vylepšuje funkci REPL, kterou získáte pomocí *souboru python.exe* na příkazovém řádku. **Interaktivní** okno (otevřené pomocí příkazů nabídky **Zobrazit** > jiné**&lt;prostředí&gt; Windows)** **Other Windows** > umožňuje zadat libovolný kód Pythonu a zobrazit okamžité výsledky. Tento způsob kódování vám pomůže naučit se a experimentovat s api a knihovnami a interaktivně vyvíjet pracovní kód, který chcete zahrnout do vašich projektů.

![Interaktivní okno Pythonu](media/interactive-window.png)

Visual Studio má několik režimů Repl pythonu, ze kterých si můžete vybrat:

| Repl | Popis | Úprava | ladění | Image |
| --- | --- | --- | --- | --- |
| Standard | Výchozí REPL, mluví s Pythonem přímo | Standardní úpravy (multiline, atd.). | Ano, přes`$attach` | Ne |
| Ladění | Výchozí REPL, rozhovory s laděným procesem Pythonu | Standardní úpravy | Pouze ladění | Ne |
| IPython | REPL mluví s backendem IPython | Příkazy IPython, vymoženosti Pylab | Ne | Ano, inline v REPL |
| IPython s Pylabem | REPL mluví s backendem IPython | Standardní Ipython | Ne | Ano, samostatné okno |

Tento článek popisuje režimy **REPL Standard** a **Debug.** Podrobnosti o režimech IPython naleznete [v tématu Použití funkce IPython REPL](interactive-repl-ipython.md).

Podrobný návod s příklady, včetně interakcí s editorem, jako je **Ctrl**+**Enter**, naleznete [v tématu Krok výuky 3: Použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otevření interaktivního okna

Existuje několik způsobů, jak otevřít **interaktivní** okno pro prostředí.

Nejprve přepněte do okna Prostředí Pythonu **(Zobrazit** > **jiná prostředí Windows** > **Pythonu** nebo **Ctrl**+**K** > **Ctrl)**+**`** a vyberte příkaz nebo tlačítko Otevřít interaktivní **okno** pro zvolené prostředí.

![Odkaz interaktivní okno v okně Prostředí Pythonu](media/interactive-window-opening.png)

Za druhé, v dolní části nabídky **Zobrazit** > **další Windows** je příkaz Interaktivní okno **Pythonu** pro výchozí prostředí a také příkaz pro přepnutí do okna **Prostředí:**

![Položky nabídky Interaktivní okno v zobrazení > jiným windows](media/interactive-window-menu.png)

Za třetí, můžete otevřít **interaktivní** okno na spouštěcí soubor v projektu nebo pro samostatný soubor výběrem **ladění** > **spustit \<projekt | Soubor> v interaktivní mase pythonu** příkaz **(Shift**+**Alt**+**F5**):

![Spustit projekt v interaktivní nabídce Pythonu](media/interactive-execute-project.png)

Nakonec můžete vybrat kód v souboru a použít příkaz [ **Odeslat do interaktivního** ](#send-to-interactive-command) popsaného níže.

## <a name="interactive-window-options"></a>Možnosti interaktivního okna

Můžete ovládat různé aspekty **interaktivního** okna prostřednictvím **interaktivního okna Tools** > **Options** > **Python** > **Interactive Windows** (viz [Možnosti](python-support-options-and-settings-in-visual-studio.md)):

![Možnosti interaktivního okna Pythonu](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Použití interaktivního okna

Po otevření **interaktivního** okna můžete začít zadávat kód řádek ** \> \> ** po řádku na výzvu. Interaktivní **Interactive** okno provede každý řádek při jeho zadání, který zahrnuje import modulů, definování proměnných a tak dále:

![Interaktivní okno Pythonu](media/interactive-window.png)

Výjimkou je, když další řádky kódu jsou potřebné k vytvoření `for` úplné prohlášení, například když příkaz končí dvojtečkou, jak je znázorněno výše. V těchto případech se výzva řádku změní na **...** což znamená, že je třeba zadat další řádky pro blok, jak je znázorněno na čtvrtém a pátém řádku na obrázku výše. Když stisknete **enter** na prázdném řádku, **interaktivní** okno zavře blok a spustí jej v interpretu.

> [!Tip]
> **Interaktivní** okno vylepšuje obvyklé prostředí REPL příkazového řádku Pythonu automatickým odsazením příkazů, které patří do okolního oboru. Jeho historie (připomenout šipkou nahoru) také poskytuje víceřádkové položky, zatímco příkazový řádek REPL poskytuje pouze jeden řádek.

<a name="meta-commands"></a>**Interaktivní** okno také podporuje několik metapříkazů. Všechny metapříkazy začínají `$`písmenem a `$help` můžete zadat seznam metapříkazů a `$help <command>` získat podrobnosti o použití konkrétního příkazu.

| Meta-příkaz | Popis |
| --- | --- |
| `$$` | Vloží komentář, který je užitečný pro komentář kódu v průběhu relace. |
| `$attach` | Připojí ladicí program sady Visual Studio k procesu okna REPL, aby bylo možné ladění. |
| `$cls`, `$clear` | Vymaže obsah okna editoru a ponechá historii a kontext spuštění beze změny. |
| `$help` | Zobrazení seznamu příkazů nebo nápovědy k určitému příkazu |
| `$load` | Načte příkazy ze souboru a provede až do dokončení. |
| `$mod` | Přepne aktuální obor na zadaný název modulu. |
| `$reset` | Obnoví prostředí spuštění do počátečního stavu, ale zachová historii. |
| `$wait` | Čeká alespoň zadaný počet milisekund. |

Příkazy jsou také rozšiřitelné rozšířením sady Visual `IInteractiveWindowCommand` Studio implementací a exportem ([příklad](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Přepnutí oborů

Ve výchozím nastavení je **interaktivní** okno projektu vymezeno na spouštěcí soubor projektu, jako byste jej spustili z příkazového řádku. Pro samostatný soubor obory k tomuto souboru. Kdykoli během relace REPL však rozevírací nabídka v horní části **interaktivního** okna umožňuje změnit rozsah:

![Interaktivní okenní obory](media/interactive-scopes.png)

Po importu modulu, například psaní `import importlib`, se v rozevíracím souboru zobrazí možnosti pro přepnutí do libovolného oboru v daném modulu. Zpráva v **interaktivním** okně také označuje nový obor, takže můžete sledovat, jak jste se během relace dostali do určitého stavu.

Zadáním `dir()` oboru se v tomto oboru zobrazí platné identifikátory, včetně názvů funkcí, tříd a proměnných. Například pomocí `import importlib` následuje `dir()` ukazuje následující:

![Interaktivní okno v oboru importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Příkaz Odeslat do interaktivního příkazu

Kromě přímé práce **v interaktivním** okně můžete vybrat kód v editoru, klepnout pravým tlačítkem myši a zvolit **Odeslat do interaktivní** nebo stisknout **klávesu Ctrl**+**Enter**.

![Příkaz Odeslat do interaktivní nabídky](media/interactive-send-to.png)

Tento příkaz je užitečný pro vývoj iterativního nebo evolučního kódu, včetně testování kódu při jeho vývoji. Například po odeslání části kódu do **interaktivního** okna a zobrazení jeho výstupu můžete stisknutím šipky nahoru kód znovu zobrazit, upravit a rychle jej otestovat stisknutím **klávesctrl**+**enter**. (Stisknutím klávesy **Enter** na konci vstupu se spustí, ale stisknutím **klávesy Enter** uprostřed vstupu se vloží nový řádek.) Jakmile budete mít požadovaný kód, můžete jej snadno zkopírovat zpět do souboru projektu.

> [!Tip]
> Ve výchozím nastavení Visual **>>>** Studio odebere a **...** REPL vyzve při vkládání kódu z **interaktivního** okna do editoru. Toto chování můžete změnit na kartě > **Možnosti** >  **nástroje****Textový editor** > **Pythonu** > **Upřesnit** pomocí **možnosti Vložit odstraní výzvy REPL.** Viz [Možnosti – různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Práce s buňkami kódu

Buňky kódu lze použít při analýze dat a jsou podporovány různými textovými editory.

Například při použití souboru kódu jako scratchpad, často máte malý blok kódu, který chcete odeslat všechny najednou. Chcete-li kód seskupit, označte kód `#%%` jako *buňku kódu* přidáním komentáře začínajícího na začátek buňky, která končí předchozí buňkou. Buňky kódu lze sbalit a rozbalit a pomocí **klávesy Ctrl**+**Enter** uvnitř buňky kódu odešle celou buňku do **interaktivního** okna a přesune se na další.

Visual Studio také detekuje buňky `# In[1]:`kódu počínaje komentáři, jako je , což je formát, který získáte při exportu poznámkového bloku Jupyter jako soubor u Pythonu. Tato detekce usnadňuje spuštění poznámkového bloku z [poznámkových bloků Azure](https://notebooks.azure.com/) stažením jako soubor u Pythonu, otevřením v Sadě Visual Studio a spuštěním jednotlivých buněk pomocí **klávesCtrl**+**Enter.**

![Interaktivní buňky kódu](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Chování technologie IntelliSense

**Interaktivní** okno obsahuje technologie IntelliSense založenou na živých objektech, na rozdíl od editoru kódu, ve kterém je technologie IntelliSense založena pouze na analýze zdrojového kódu. Tyto návrhy jsou správnější v **interaktivní** masce, zejména s dynamicky generovaným kódem. Nevýhodou je, že funkce s vedlejšími účinky (například protokolování zpráv) může mít vliv na vaše vývojové prostředí.

Pokud se jedná o toto chování, změňte nastavení v části > **Možnosti** > **nástroje interaktivního** > **okna Python** ve skupině **Režim dokončení,** jak je popsáno v části [Možnosti – Interaktivní možnosti systému windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options). **Tools**
