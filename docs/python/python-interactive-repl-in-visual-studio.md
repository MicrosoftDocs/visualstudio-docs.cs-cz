---
title: Interaktivní okno Python (REPL)
description: Použití interaktivního okna (REPL) pro rychlý vývoj kódu Python v sadě Visual Studio.
ms.date: 10/29/2018
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
ms.openlocfilehash: 3c3a3a6cd3694a0affa6ca1d5cfabac58b124ec9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055712"
---
# <a name="work-with-the-python-interactive-window"></a>Práce s interaktivní okno Pythonu

Visual Studio poskytuje oknem interaktivní čtení vyhodnocení print smyčky (REPL) pro každé prostředí Pythonu, které dále to vylepšuje REPL všechno získáte s *python.exe* na příkazovém řádku. **Interaktivní** okno (Otevřít **zobrazení** > **ostatní Windows** > **&lt;prostředí&gt; Interaktivní** příkazy nabídky) vám umožní zadat libovolný kód Pythonu a zobrazit výsledky okamžitě. Tímto způsobem kódování pomáhá informace a experimentovat s rozhraním API a knihoven a interaktivně vyvíjet pracovní kód přikazující zahrnutí ve vašich projektech.

![Interaktivní okno Pythonu](media/interactive-window.png)

Visual Studio má několik režimů REPL Pythonu na výběr:

| REPL | Popis | Úpravy | Ladění | Obrázky |
| --- | --- | --- | --- | --- |
| Standard | Výchozí REPL, přednášky na Python přímo | Standardní editační (multiline atd.). | Ano, prostřednictvím `$attach` | Ne |
| Ladit | Výchozí REPL, přednášky na laděném procesu Pythonu | Standardní úpravy | Ladění | Ne |
| IPython | Přednášky REPL, IPython back-endu | Příkazy IPython, Pylab usnadnění | Ne | Ano, vložený v REPL |
| IPython bez Pylab | Přednášky REPL, IPython back-endu | Standardní IPython | Ne | Ano, oddělte okna | 

Tento článek popisuje **standardní** a **ladění** REPL režimy. Informace o režimech IPython, naleznete v tématu [použití Ipythonu REPL](interactive-repl-ipython.md).

Podrobný návod s příklady, včetně interakcí s editoru **Ctrl**+**Enter**, naleznete v tématu [kurzu krok 3: použití okna interaktivní okno REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) na **interaktivní** okno (2 miliony 22s).|

## <a name="open-an-interactive-window"></a>Otevřít interaktivní okno

Existuje několik způsobů, jak otevřít **interaktivní** okno pro prostředí.

Nejprve, přepněte do okna prostředí Pythonu (**zobrazení** > **ostatní Windows** > **prostředí Pythonu** nebo **Ctrl** + **K** > **Ctrl**+**`**) a vyberte **otevřít interaktivní Okno** příkazu nebo tlačítko pro zvolený prostředí.

![Interaktivní okno odkaz v okně prostředí Pythonu](media/interactive-window-opening.png)

Za druhé u dolního okraje **zobrazení** > **ostatní Windows** nabídky, je **interaktivním okně Pythonu** příkaz pro výchozí prostředí, stejně jako příkaz pro přepnutí na **prostředí** okno:

![Interaktivní okno položky v zobrazení > ostatní Windows](media/interactive-window-menu.png)

Třetí, můžete otevřít **interaktivní** na spouštěcí soubor ve vašem projektu, nebo pro samostatný soubor, tak, že vyberete okno **ladění** > **Execute \<projektu | Soubor > v Pythonu interaktivní** příkazu nabídky (**Shift**+**Alt**+**F5**):

![Provést projekt v nabídce interaktivní Python](media/interactive-execute-project.png)

Nakonec můžete vybrat kód v souboru a použít [ **zaslat do Interactive** příkaz](#send-to-interactive-command) je popsáno níže.

## <a name="interactive-window-options"></a>Interaktivní okno Možnosti

Můžete určit různé aspekty **interaktivní** okno prostřednictvím **nástroje** > **možnosti** > **nástroje Python Tools**  >  **Interaktivní Windows** (viz [možnosti](python-support-options-and-settings-in-visual-studio.md)):

![Možnosti interaktivního okna Pythonu](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Pomocí interaktivního okna

Jednou **interaktivní** je otevřeno okno, můžete začít zadávat kódu řádek po řádku na **\> \> \>** řádku. **Interaktivní** okno vykonává každý řádek tak, jak zadat, která zahrnuje importu modulů, definující proměnné a tak dále:

![Interaktivní okno Pythonu](media/interactive-window.png)

Výjimkou je další řádky kódu, které jsou potřebné k tomu úplný příkaz, třeba při `for` příkaz končí za dvojtečkou, jak je uvedeno výše. V těchto případech řádku příkazový řádek se změní **...**  označující, že budete muset zadat další řádky pro blok, jak je znázorněno na řádcích čtvrtý a pátý na obrázku výše. Když stisknete klávesu **Enter** na prázdný řádek, **interaktivní** okno zavře bloku a běží v překladač.

> [!Tip]
> **Interaktivní** okno dále to vylepšuje obvykle Python prostředí REPL příkazového řádku, které automaticky odsazení příkazy, které patří do rozsah obklopujícím rozsahem. Historii (třeba připomenout pomocí kláves Šipka nahoru) také nabízí Víceřádkový položky, že REPL příkazového řádku obsahuje pouze jeden řádek.

<a name="meta-commands"></a> **Interaktivní** okna podporuje také několik meta příkazů. Všechny příkazy meta začínat `$`, a zadáte `$help` zobrazíte seznam meta příkazů a `$help <command>` zobrazíte podrobnosti o použití ke konkrétnímu příkazu.

| Meta příkazu | Popis |
| --- | --- |
| `$$` | Vloží poznámku, což je užitečné komentáře kódu v průběhu relace. |
| `$attach` | Ladicí program sady Visual Studio připojí k procesu okno REPL pro povolení ladění. |
| `$cls`, `$clear` | Vymaže obsah okna editor uživatele zůstanou nedotčena historie a spuštění kontextu. |
| `$help` | Zobrazit seznam příkazů a nápovědy ke konkrétnímu příkazu. |
| `$load` | Načte příkazy ze souboru a spustí, až do dokončení. |
| `$mod` | Přepne aktuální obor na zadaný název modulu. |
| `$reset` | Obnoví prostředí pro spuštění do původního stavu, ale zachová historii. |
| `$wait` | Čeká na alespoň zadaný počet milisekund. |

Příkazy se také dají rozšířit pomocí rozšíření sady Visual Studio pomocí implementace a export `IInteractiveWindowCommand` ([příklad](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Přepnout obory

Ve výchozím nastavení **interaktivní** okno projektu působí na projektu po spuštění souboru, jako kdyby jste spustili z příkazového řádku. Pro soubor samostatné obory pro daný soubor. Kdykoli při relaci REPL, ale v rozevírací nabídce podél horního okraje **interaktivní** okna umožňuje změnit obor:

![Interaktivní okno obory](media/interactive-scopes.png)

Po importování modulu, například `import importlib`, možnosti se zobrazí rozevírací seznam pro přepnutí do žádný rozsah v tomto modulu. Zpráva v **interaktivní** okna také určuje nový obor, takže můžete sledovat, jak jste získali na a jejich určitého stavu během vaší relace.

Zadání `dir()` v oboru zobrazí platné identifikátory v tomto oboru, včetně názvy funkcí, tříd a proměnné. Například použití `import importlib` následovaný `dir()` zobrazuje následující:

![Interaktivní okno v rámci importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Odeslání do interaktivního příkazu

Kromě práci v rámci **interaktivní** okno přímo, vyberte kód v editoru klikněte pravým tlačítkem a zvolte **zaslat do Interactive** nebo stiskněte klávesu **Ctrl** + **Zadejte**.

![Poslat příkaz interaktivní nabídky](media/interactive-send-to.png)

Tento příkaz je užitečné pro vývoj iterativní nebo evoluční kódu, včetně testování kódu při vývoji. Například jednou odeslali jste část kódu, který **interaktivní** okno a zobrazit jeho výstup, stisknete šipku nahoru znovu zobrazit kód upravit a otestujte rychle stisknutím klávesy **Ctrl** + **Zadejte**. (Stisknutím klávesy **Enter** na konci vstupu spustí ho, ale klávesy **Enter** uprostřed vstup vloží nový řádek.) Jakmile budete mít kód, který chcete, můžete ho snadno zkopírovat zpět do souboru projektu.

> [!Tip]
> Ve výchozím nastavení, Visual Studio odebere **>>>** a **...** REPL zobrazí výzvu, při vkládání kódu z **interaktivní** okno do editoru. Toto chování můžete změnit na **nástroje** > **možnosti** > **textový Editor** > **Python**  >  **Upřesnit** kartu pomocí **vložit odebere REPL výzvy** možnost. Zobrazit [možnosti - různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

Používáte-li soubor kódu jako zápisník, mají často malého bloku kódu, který chcete odeslat všechny najednou. K seskupení kódu, označit kód jako *buňku kódu* tak, že přidáte komentář začíná `#%%` začátek buňku, která končí předchozí. Buňky kódu může být sbalené a rozšířená a pomocí **Ctrl**+**Enter** uvnitř kód odešle buňky celé buňky do **interaktivní** okna a přejde Další příkaz.

Visual Studio také detekuje buňky kódu počínaje komentáře jako `# In[1]:`, což je formát, který získáte při exportu Poznámkový blok Jupyter jako soubor Pythonu. Toto zjišťování umožňuje snadno spustit z poznámkového bloku [poznámkových bloků Azure](https://notebooks.azure.com/) stažením jako soubor Pythonu, otevřete v sadě Visual Studio a použitím **Ctrl**+**Enter**ke spuštění každého buňky.

![Interaktivní kód buňky](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Chování technologie IntelliSense

**Interaktivní** okno obsahuje rozšíření IntelliSense na základě živých objektů, na rozdíl od editor kódu, ve kterém je IntelliSense podle pouze analýzu zdrojového kódu. Doporučení jsou uvedená ve více správná **interaktivní** okna, zejména v případě dynamicky generovaného kódu. Nevýhodou je, že funkce s vedlejšími účinky (například protokolování zpráv) může mít vliv na vaše zkušenosti s vývojem.

Pokud toto chování je nějaký problém, změňte nastavení v části **nástroje** > **možnosti** > **nástroje Python Tools**  >   **Interaktivní Windows** v **Doplňovacím režimem** skupině, jak je popsáno na [možnosti - interaktivních oken](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
