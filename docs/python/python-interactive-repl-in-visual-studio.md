---
title: Interaktivní okno Python (REPL)
description: Použití interaktivního okna (REPL) pro rychlý vývoj kódu Python v sadě Visual Studio.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409978"
---
# <a name="work-with-the-python-interactive-window"></a>Práce s interaktivní okno Pythonu

Visual Studio poskytuje interaktivní okno pro čtení a vyhodnocení-tisk smyčky (REPL) pro každé prostředí Pythonu, které se vylepšuje na REPL, které získáte pomocí *Python. exe* na příkazovém řádku. **Interaktivní** okno (otevřené pomocí **zobrazení** > jiné prostředí **Windows** >  **&lt;&gt; interaktivní** příkazy nabídky) umožňuje zadat libovolný kód Pythonu a zobrazit okamžité výsledky. Tímto způsobem kódování pomáhá informace a experimentovat s rozhraním API a knihoven a interaktivně vyvíjet pracovní kód přikazující zahrnutí ve vašich projektech.

![Interaktivní okno Pythonu](media/interactive-window.png)

Visual Studio má několik režimů REPL Pythonu na výběr:

| REPL | Popis | Úprava | Ladění | Image |
| --- | --- | --- | --- | --- |
| Standard | Výchozí REPL, přednášky na Python přímo | Standardní editační (multiline atd.). | Ano, prostřednictvím `$attach` | Ne |
| Ladění | Výchozí REPL, přednášky na laděném procesu Pythonu | Standardní úpravy | Ladění | Ne |
| IPython | Přednášky REPL, IPython back-endu | Příkazy IPython, Pylab usnadnění | Ne | Ano, vložený v REPL |
| IPython bez Pylab | Přednášky REPL, IPython back-endu | Standardní IPython | Ne | Ano, oddělte okna |

Tento článek popisuje režimy **standardního** a **ladění** REPL. Podrobnosti o režimech IPython naleznete v tématu [use the IPYTHON REPL](interactive-repl-ipython.md).

Podrobný návod s příklady, včetně interakcí s editorem, jako je například **Ctrl**+**ENTER**, najdete v [kurzu krok 3: použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otevřít interaktivní okno

Existuje několik způsobů, jak otevřít **interaktivní** okno pro prostředí.

Nejdřív přepněte do okna prostředí Pythonu (**zobrazení** > **jiných prostředí Windows** > **Pythonu** nebo **CTRL**+**K** > **CTRL**+ **`** ) a vyberte příkaz **otevřít interaktivní okno** nebo tlačítko pro zvolené prostředí.

![Interaktivní okno odkaz v okně prostředí Pythonu](media/interactive-window-opening.png)

V dolní části **zobrazení** > **jiné nabídce systému Windows** je k dispozici **interaktivní okno Pythonu** pro vaše výchozí prostředí a příkaz pro přepnutí do okna **prostředí** :

![Interaktivní okno položky v zobrazení > ostatní Windows](media/interactive-window-menu.png)

Třetí, můžete otevřít **interaktivní** okno na spouštěcím souboru v projektu nebo pro samostatný soubor tak, že vyberete **ladění** > **Spustit \<projektu | Soubor > v interaktivní nabídce Pythonu** (**SHIFT**+**ALT**+**F5**):

![Provést projekt v nabídce interaktivní Python](media/interactive-execute-project.png)

Nakonec můžete vybrat kód v souboru a použít [příkaz **Odeslat do interaktivního** příkazu](#send-to-interactive-command) , který je popsaný níže.

## <a name="interactive-window-options"></a>Interaktivní okno Možnosti

Můžete ovládat různé aspekty **interaktivního** okna prostřednictvím **nástrojů** > **možností** > **Python** > **Interactive Windows** (viz [Možnosti](python-support-options-and-settings-in-visual-studio.md)):

![Možnosti interaktivního okna Pythonu](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Pomocí interaktivního okna

Po otevření **interaktivního** okna můžete začít zadávat kód na řádku **\>\>\>** příkazovém řádku. **Interaktivní** okno provede každý řádek při jeho zadávání, což zahrnuje importování modulů, definování proměnných a tak dále:

![Interaktivní okno Pythonu](media/interactive-window.png)

Výjimkou je, když je nutné další řádky kódu pro vytvoření příkazu Complete, například když příkaz `for` končí dvojtečkou, jak je uvedeno výše. V těchto případech se řádek řádku změní na **...** značí, že je nutné zadat další řádky pro blok, jak je znázorněno na čtvrtém a pátém řádku na obrázku výše. Když stisknete klávesu **ENTER** na prázdném řádku, **interaktivní** okno ukončí blok a spustí ho v překladači.

> [!Tip]
> **Interaktivní** okno se zlepšuje na obvyklém prostředí REPL příkazového řádku Pythonu automatickým odrážkami příkazů, které patří do okolního rozsahu. Historii (třeba připomenout pomocí kláves Šipka nahoru) také nabízí Víceřádkový položky, že REPL příkazového řádku obsahuje pouze jeden řádek.

<a name="meta-commands"></a>**Interaktivní** okno také podporuje několik meta příkazů. Všechny meta-příkazy začínají na `$`a můžete zadat `$help` a získat tak seznam meta-příkazů a `$help <command>`, abyste získali podrobnosti o využití určitého příkazu.

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

Příkazy jsou také rozšiřitelné pomocí rozšíření sady Visual Studio implementací a exportem `IInteractiveWindowCommand` ([příklad](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Přepnout obory

Ve výchozím nastavení je **interaktivní** okno pro projekt vymezeno na spouštěcí soubor projektu, jako kdybyste ho spustili z příkazového řádku. Pro soubor samostatné obory pro daný soubor. Při každé relaci REPL ale rozevírací nabídka v horní části **interaktivního** okna umožňuje změnit rozsah:

![Interaktivní okno obory](media/interactive-scopes.png)

Po importu modulu, jako je například zadání `import importlib`, se v rozevíracím seznamu zobrazí možnosti, které se v tomto modulu přepínají do libovolného oboru. Zpráva v **interaktivním** okně také indikuje nový obor, takže můžete sledovat, jak jste během vaší relace získali určitý stav.

Při zadání `dir()` v oboru se zobrazí platné identifikátory v daném oboru, včetně názvů funkcí, tříd a proměnných. Například použití `import importlib` následovaných `dir()` zobrazí následující:

![Interaktivní okno v rámci importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Odeslání do interaktivního příkazu

Kromě možnosti pracovat přímo v **interaktivním** okně můžete vybrat kód v editoru, kliknout pravým tlačítkem myši a vybrat **Odeslat do interaktivního** režimu nebo stisknout klávesu **CTRL**+**ENTER**.

![Poslat příkaz interaktivní nabídky](media/interactive-send-to.png)

Tento příkaz je užitečné pro vývoj iterativní nebo evoluční kódu, včetně testování kódu při vývoji. Například po odeslání nějakého kódu do **interaktivního** okna a zobrazení jeho výstupu můžete stisknutím šipky nahoru zobrazit kód znovu, upravit ho a rychle ho otestovat stisknutím **kombinace kláves CTRL**+**ENTER**. (Stisknutím klávesy **ENTER** na konci vstupu se spustí, ale stisknutím klávesy **ENTER** uprostřed vstupu vložíte nový řádek.) Jakmile budete mít kód, který budete chtít, můžete ho snadno zkopírovat zpátky do souboru projektu.

> [!Tip]
> Ve výchozím nastavení Visual Studio odebere **>>>** a **...** REPL vyzve k vložení kódu z **interaktivního** okna do editoru. Toto chování můžete změnit v nabídce **nástroje** > **Možnosti** > **textový editor** > kartě **Upřesnit** > **Pythonu** pomocí možnosti **Vložit odebrat REPL výzvy** . Viz [Možnosti – různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Práce s buňkami kódu

Buňky kódu se dají použít při analýze dat a podporují se v různých textových editorech.

Například při použití souboru s kódem jako scratchpad, často máte malý blok kódu, který chcete odeslat najednou. Chcete-li seskupit kód dohromady, označte kód jako *buňku kódu* přidáním komentáře začínajícího `#%%` na začátek buňky, který ukončí předchozí. Buňky kódu je možné sbalit a rozbalit a pomocí **kláves Ctrl**+**ENTER** uvnitř buňky kódu pošle celou buňku do **interaktivního** okna a přejde na další.

Visual Studio také detekuje buňky kódu počínaje komentáři, jako je `# In[1]:`, což je formát, který získáte při exportu poznámkového bloku Jupyter jako souboru Pythonu. Tato detekce usnadňuje spuštění poznámkového bloku z [Azure Notebooks](https://notebooks.azure.com/) stažením jako souboru Pythonu, otevřením v aplikaci Visual Studio a použitím **kombinace kláves CTRL**+**ENTER** pro spuštění jednotlivých buněk.

![Interaktivní kód buňky](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Chování technologie IntelliSense

**Interaktivní** okno obsahuje technologii IntelliSense na základě živých objektů na rozdíl od editoru kódu, ve kterém je technologie IntelliSense založena pouze na analýze zdrojového kódu. Tyto návrhy jsou v **interaktivním** okně lépe správné, zejména pomocí dynamicky generovaného kódu. Nevýhodou je, že funkce s vedlejšími účinky (například protokolování zpráv) může mít vliv na vaše zkušenosti s vývojem.

Pokud se jedná o problém, změňte nastavení v nabídce **nástroje** > **možnosti** > **Python** > **Interactive Windows** ve skupině **režim dokončení** , jak je popsáno v [Možnosti interaktivní možnosti Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
