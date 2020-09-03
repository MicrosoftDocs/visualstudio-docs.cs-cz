---
title: Interaktivní okno Pythonu (REPL)
description: Použijte interaktivní okno (REPL) pro rychlý vývoj kódu v Pythonu v aplikaci Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9608f273683865be767a44dd8f1d66106b97b7e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533546"
---
# <a name="work-with-the-python-interactive-window"></a>Práce s interaktivním oknem Pythonu

Visual Studio poskytuje interaktivní okno pro čtení a vyhodnocení-tisk smyčky (REPL) pro každé prostředí Pythonu, které se zlepšuje na REPL, které získáte pomocí *python.exe* na příkazovém řádku. **Interaktivní** okno (otevřené pomocí příkazu **Zobrazit**  >  jiné**Other Windows**  >  ** &lt; &gt; interaktivní nabídky prostředí** systému Windows) umožňuje zadat libovolný kód Pythonu a zobrazit okamžité výsledky. Tento způsob psaní kódu pomáhá naučit a experimentovat s rozhraními API a knihovnami a interaktivně vyvíjet pracovní kód pro zahrnutí do vašich projektů.

![Interaktivní okno Pythonu](media/interactive-window.png)

Visual Studio má řadu REPL režimů Pythonu, ze kterých si můžete vybrat:

| REPL | Popis | Probíhají úpravy | Ladění | Image |
| --- | --- | --- | --- | --- |
| Standard | Výchozí REPL, přednášky přímo v Pythonu | Standardní úpravy (víceřádkové atd.). | Ano, přes `$attach` | Ne |
| Ladění | Výchozí REPL, přednášky k ladění procesu v Pythonu | Standardní úpravy | Pouze ladění | Ne |
| IPython | REPL rozhovory do back-endu IPython | IPython příkazy, Pylab pohodlí | Ne | Ano, vloženo v REPL |
| IPython, Pylab | REPL rozhovory do back-endu IPython | IPython úrovně Standard | Ne | Ano, samostatné okno |

Tento článek popisuje režimy **standardního** a **ladění** REPL. Podrobnosti o režimech IPython naleznete v tématu [use the IPYTHON REPL](interactive-repl-ipython.md).

Podrobný návod s příklady, včetně interakcí s editorem, jako je **klávesa CTRL** + **ENTER**, najdete v [kurzu krok 3: použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otevřít interaktivní okno

Existuje několik způsobů, jak otevřít **interaktivní** okno pro prostředí.

Nejdřív přepněte do okna prostředí Pythonu (**Zobrazit**  >  **Další**  >  **prostředí Windows Python** nebo **CTRL +** + **K**  >  **CTRL** + **`** ) a vyberte příkaz **otevřít interaktivní okno** nebo tlačítko pro zvolené prostředí.

![Odkaz interaktivního okna v okně prostředí Pythonu](media/interactive-window-opening.png)

V dolní části nabídky **Zobrazit**  >  **Další Windows** je k dispozici **interaktivní okno Pythonu** pro vaše výchozí prostředí a příkaz pro přepnutí do okna **prostředí** :

![Interaktivní položky nabídky okna v zobrazení > jiných oknech](media/interactive-window-menu.png)

Třetí, můžete otevřít **interaktivní** okno na spouštěcím souboru v projektu nebo pro samostatný soubor tak, že vyberete **ladění**  >  **Spustit \<Project | File> v Pythonu interaktivní** nabídka (**SHIFT** + **ALT** + **F5**):

![Spustit projekt v interaktivní nabídce Pythonu](media/interactive-execute-project.png)

Nakonec můžete vybrat kód v souboru a použít [příkaz **Odeslat do interaktivního** příkazu](#send-to-interactive-command) , který je popsaný níže.

## <a name="interactive-window-options"></a>Možnosti interaktivního okna

Můžete ovládat různé aspekty **interaktivního** okna prostřednictvím **nástrojů**  >  **Možnosti**  >  interaktivní okna**Pythonu**  >  **Interactive Windows** (viz [Možnosti](python-support-options-and-settings-in-visual-studio.md)):

![Možnosti interaktivního okna Pythonu](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Použití interaktivního okna

Po otevření **interaktivního** okna můžete na příkazovém řádku začít zadávat kód řádek po řádku **\>\>\>** . **Interaktivní** okno provede každý řádek při jeho zadávání, což zahrnuje importování modulů, definování proměnných a tak dále:

![Interaktivní okno Pythonu](media/interactive-window.png)

Výjimkou je, když je nutné další řádky kódu pro vytvoření příkazu Complete, například když `for` příkaz končí dvojtečkou, jak je uvedeno výše. V těchto případech se řádek řádku změní na **...** značí, že je nutné zadat další řádky pro blok, jak je znázorněno na čtvrtém a pátém řádku na obrázku výše. Když stisknete klávesu **ENTER** na prázdném řádku, **interaktivní** okno ukončí blok a spustí ho v překladači.

> [!Tip]
> **Interaktivní** okno se zlepšuje na obvyklém prostředí REPL příkazového řádku Pythonu automatickým odrážkami příkazů, které patří do okolního rozsahu. Jeho historie (volána pomocí šipky nahoru) poskytuje také víceřádkové položky, zatímco REPL příkazového řádku poskytuje pouze jeden řádek.

<a name="meta-commands"></a>**Interaktivní** okno také podporuje několik meta příkazů. Všechny meta-příkazy začínají `$` na a můžete zadat a `$help` získat tak seznam meta příkazů a `$help <command>` získat podrobnosti o využití určitého příkazu.

| Meta – příkaz | Popis |
| --- | --- |
| `$$` | Vloží komentář, který je užitečný pro komentáře kódu v rámci vaší relace. |
| `$attach` | Připojí ladicí program sady Visual Studio k procesu okna REPL pro povolení ladění. |
| `$cls`, `$clear` | Vymaže obsah okna editoru, historii a kontext spuštění zůstane beze změny. |
| `$help` | Zobrazení seznamu příkazů nebo podrobnější informace o konkrétním příkazu. |
| `$load` | Načte příkazy ze souboru a provede až do dokončení. |
| `$mod` | Přepne aktuální obor na zadaný název modulu. |
| `$reset` | Obnoví spouštěcí prostředí do počátečního stavu, ale uchová historii. |
| `$wait` | Počká alespoň zadaný počet milisekund. |

Příkazy jsou také rozšiřitelné pomocí rozšíření sady Visual Studio implementací a export `IInteractiveWindowCommand` ([příklad](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Přepnout rozsahy

Ve výchozím nastavení je **interaktivní** okno pro projekt vymezeno na spouštěcí soubor projektu, jako kdybyste ho spustili z příkazového řádku. V případě samostatného souboru je tento soubor oborem IT. Při každé relaci REPL ale rozevírací nabídka v horní části **interaktivního** okna umožňuje změnit rozsah:

![Interaktivní rozsahy oken](media/interactive-scopes.png)

Po importu modulu, jako je například psaní `import importlib` , se v rozevíracím seznamu zobrazí možnosti přepnutí do libovolného oboru v tomto modulu. Zpráva v **interaktivním** okně také indikuje nový obor, takže můžete sledovat, jak jste během vaší relace získali určitý stav.

`dir()`Při zadání v oboru se zobrazí platné identifikátory v daném oboru, včetně názvů funkcí, tříd a proměnných. Například po použití `import importlib` následujícího příkladu se `dir()` zobrazí následující:

![Interaktivní okno v oboru importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Odeslat do interaktivního příkazu

Kromě možnosti pracovat přímo v **interaktivním** okně můžete vybrat kód v editoru, kliknout pravým tlačítkem myši a vybrat **Odeslat do interaktivního** režimu nebo stisknout klávesu **CTRL** + **ENTER**.

![Odeslat do interaktivní nabídky – příkaz](media/interactive-send-to.png)

Tento příkaz je vhodný pro iterativní nebo Evolutionary vývoj kódu, včetně testování kódu při jeho vývoji. Například po odeslání části kódu do **interaktivního** okna a zobrazení jeho výstupu můžete stisknutím šipky nahoru zobrazit kód znovu, upravit ho a rychle ho otestovat stisknutím **klávesy CTRL** + **ENTER**. (Stisknutím klávesy **ENTER** na konci vstupu se spustí, ale stisknutím klávesy **ENTER** uprostřed vstupu vložíte nový řádek.) Jakmile budete mít kód, který budete chtít, můžete ho snadno zkopírovat zpátky do souboru projektu.

> [!Tip]
> Ve výchozím nastavení Visual Studio odebere **>>>** a **...** REPL vyzve k vložení kódu z **interaktivního** okna do editoru. Toto chování můžete změnit na kartě možnosti **nástrojů**  >  **Options**  >  **textový editor**  >  **Python**  >  **Upřesnit** pomocí možnosti **vložení odebrat REPL výzvy** . Viz [Možnosti – různé možnosti](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Práce s buňkami kódu

Buňky kódu se dají použít při analýze dat a podporují se v různých textových editorech.

Například při použití souboru s kódem jako scratchpad, často máte malý blok kódu, který chcete odeslat najednou. Chcete-li seskupit kód dohromady, označte kód jako *buňku kódu* přidáním komentáře začínajícího `#%%` na začátek buňky, který ukončí předchozí. Buňky kódu lze sbalit a rozbalit a pomocí **klávesy CTRL** + **ENTER** v rámci buňky kódu Odeslat celou buňku do **interaktivního** okna a přejít na další.

Visual Studio také detekuje buňky kódu počínaje komentáři `# In[1]:` , jako je formát, který získáte při exportu Jupyter poznámkového bloku jako souboru Pythonu. Tato detekce usnadňuje spuštění poznámkového bloku z [Azure Notebooks](https://notebooks.azure.com/) stažením jako souboru Pythonu, otevřením v aplikaci Visual Studio a použitím **klávesy CTRL** + **ENTER** pro spuštění jednotlivých buněk.

![Buňky s interaktivním kódem](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Chování IntelliSense

**Interaktivní** okno obsahuje technologii IntelliSense na základě živých objektů na rozdíl od editoru kódu, ve kterém je technologie IntelliSense založena pouze na analýze zdrojového kódu. Tyto návrhy jsou v **interaktivním** okně lépe správné, zejména pomocí dynamicky generovaného kódu. Nevýhodou je, že funkce s vedlejšími účinky (například protokolování zpráv) můžou mít vliv na vývojové prostředí.

Pokud se jedná o problém, změňte nastavení **v nabídce**  >  **Možnosti možností**  >  **Python**  >  **interaktivní okna** Pythonu ve skupině **režim dokončení** , jak je popsáno v možnosti [interaktivní možnosti Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
