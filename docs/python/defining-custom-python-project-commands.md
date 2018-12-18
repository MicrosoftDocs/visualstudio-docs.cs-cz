---
title: Definovat vlastní příkazy pro projekty v Pythonu
description: Podle úprav projektu a soubory cíle můžete přidat vlastní příkazy do kontextové nabídky projektu Pythonu v sadě Visual Studio, který má být vyvolán spustitelné programy, skripty, moduly, vložené fragmenty kódu a pip.
ms.date: 11/12/2018
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
ms.openlocfilehash: be8befcc549b76c8ac2b6435146c636b592b5494
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062868"
---
# <a name="define-custom-commands-for-python-projects"></a>Definovat vlastní příkazy pro projekty v Pythonu

Při práci s projekty v Pythonu, může být pro vás sami přepnutí na okno příkazového řádku spustit konkrétní skripty a moduly, spustit příkazy nástroje pip, nebo nějaký jiný libovolný nástroj. Cílem pracovního postupu můžete přidat vlastní příkazy **Python** podnabídce v kontextové nabídce projektu Pythonu. Tyto příkazy můžete spustit v okně konzoly nebo v sadě Visual Studio **výstup** okna. Regulární výrazy můžete použít také dáte pokyn, aby Visual Studio jak parsovat chyby a upozornění z výstupu příkazu.

Ve výchozím nastavení, této nabídky obsahuje pouze jeden **spustit Pylintu** příkaz:

![Výchozí vzhled podnabídky Python v místní nabídce projektu](media/custom-commands-default-menu.png)

Vlastní příkazy se zobrazují v tomto stejné místní nabídce. Vlastní příkazy jsou přidány do souboru projektu přímo, kde se vztahují na tento projekt. Můžete také definovat vlastní příkazy v *.targets* soubor, který lze snadno importovat do více souborech projektu.

Některé šablony projektů Python v sadě Visual Studio už přidat vlastní příkazy jejich vlastní použití jejich *.targets* souboru. Například šablony Bottle webový projekt a webový projekt Flask přidat dva příkazy **spustit server** a **spustit server pro ladění**. Šablona webového projektu Django přidá tyto stejné příkazy, a navíc několik dalších:

![Vzhled podnabídky Python v místní nabídce projektu Django](media/custom-commands-django-menu.png)

Každý vlastní příkaz mohou odkazovat na soubor Pythonu, modul Pythonu, vložený kód Pythonu, libovolný spustitelný soubor nebo příkazu pip. Můžete také určit, jak a kde se příkaz spustí.

> [!Tip]
> Pokaždé, když provedete změny do souboru projektu v textovém editoru, je nutné znovu načíst projekt v sadě Visual Studio, aby se tyto změny. Například je nutné znovu projektu po přidání vlastního příkazu definice pro tyto příkazy se zobrazí v místní nabídce projektu.
>
> Jak asi víte, Visual Studio poskytuje prostředky k přímo upravit soubor projektu. Nejprve klikněte pravým tlačítkem na soubor projektu a vyberte **uvolnit projekt**, pak znovu klikneme pravým tlačítkem a vyberte **upravit \<název projektu >** projekt otevřít v editoru sady Visual Studio. Můžete pak provádět a uložení úprav, ještě jednou klikněte pravým tlačítkem na projekt a vyberte **znovu načíst projekt**, což také vás vyzve k potvrzení zavření souboru projektu v editoru.
>
> Při vytváření vlastního příkazu, ale tyto kliknutí se může stát únavné. Pro efektivnější pracovní postupy, načtení projektu v sadě Visual Studio a také otevřít *.pyproj* souboru v samostatných editoru úplně (jako je například jiná instance sady Visual Studio, Visual Studio Code, Poznámkový blok, atd.). Při uložení změn v editoru a přepnete se do sady Visual Studio, Visual Studio zjistí změny a zeptá, jestli se má znovu načtěte projekt (**projektu \<name > byl změněn mimo prostředí.**). Vyberte **Reload** a provedené změny se okamžitě použijí v jednom kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Návod: Přidání příkazu do souboru projektu

Seznamte se s vlastní příkazy, tato část vás provede jednoduchý příklad, který spouští projektu po spuštění souboru přímo pomocí *python.exe*. (Takové příkaz je v podstatě totéž jako použití **ladění** > **spustit bez ladění**.)

1. Vytvoření nového projektu s názvem "Python-CustomCommands" pomocí **aplikace v Pythonu** šablony. (Viz [rychlý start: vytvoření projektu Pythonu ze šablony](quickstart-02-python-in-visual-studio-project-from-template.md) pokyny, pokud ještě nejste obeznámeni s procesem.)

1. V *Python_CustomCommands.py*, přidejte kód `print("Hello custom commands")`.

1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**vyberte **Python**a Všimněte si, že je jediný příkaz, který se zobrazí v podnabídce **spustit Pylintu**. Vlastní příkazy se zobrazí v podnabídce Tento stejný.

1. Jak je navrženo v úvodu, otevřete *Python CustomCommands.pyproj* v samostatném textovém editoru. Pak přidejte následující řádky na konci souboru pouze uvnitř uzavírací `</Project>` a soubor uložte.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Přepněte zpět do sady Visual Studio a vyberte **Reload** při zobrazování výzvy o změně souboru. Zkontrolujte **Python** nabídky znovu, abyste viděli, která **spustit Pylintu** je stále pouze položky, které je znázorněno, protože jste přidali pouze řádky replikovat výchozí `<PythonCommands>` vlastnosti skupiny obsahující Pylintu příkaz.

1. Přejděte k editoru do souboru projektu a přidejte následující `<Target>` definici po `<PropertyGroup>`. Jak je popsáno dále v tomto článku se to `Target` element definuje vlastní příkaz pro spuštění po spuštění souboru (identifikovaný podle vlastnosti "StartupFile") pomocí *python.exe* v okně konzoly. Atribut `ExecuteIn="consolepause"` používá konzolu, která čeká na stisknutím jakékoli klávesy před zavřením.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Přidejte hodnotu cíle `Name` atribut `<PythonCommands>` skupiny vlastností přidali dříve, tak, že element bude vypadat jako následující kód. Název cíle přidání do tohoto seznamu je co přidá jej do **Python** nabídky.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Pokud chcete, aby před těmi definovanými ve svých rukou `$(PythonCommands)`, je umístit před tento token.

1. Uložte soubor projektu, přepněte do aplikace Visual Studio a znovu načtěte projekt po zobrazení výzvy. Klepněte pravým tlačítkem myši **Python CustomCommands** projektu a vyberte **Python**. Měli byste vidět **spuštění spouštěcího souboru** položky v nabídce. Pokud se nezobrazí položka nabídky, zkontrolujte, že jste přidali název, který má `<PythonCommands>` elementu. Viz také [Poradce při potížích s](#troubleshooting) dále v tomto článku.

    ![Vlastní příkaz povolí, v kontextu podnabídky Pythonu](media/custom-commands-walkthrough-menu-item.png)

1. Vyberte **spuštění spouštěcího souboru** příkazu a měli byste vidět okno příkazového řádku se zobrazí s textem **Hello vlastní příkazy** následovaný **stisknutím libovolné klávesy pokračovat**.  Stisknutím jakékoli klávesy zavřete okno.

    ![Výstup vlastního příkazu v okně konzoly](media/custom-commands-walkthrough-console.png)

1. Vraťte se do editoru do souboru projektu a změňte hodnotu `ExecuteIn` atribut `output`. Uložte soubor, přepněte do aplikace Visual Studio, znovu načtěte projekt a znovu vyvolat příkaz. Tentokrát uvidíte výstup programu v sadě Visual Studio se zobrazí **výstup** okno:

    ![Výstup vlastního příkazu v okně Výstup](media/custom-commands-walkthrough-output-window.png)

1. Chcete-li přidat další příkazy, definujte vhodný `<Target>` – element pro každý příkaz, přidejte název cíle do `<PythonCommands>` skupiny vlastností a znovu načtěte projekt v sadě Visual Studio.

>[!Tip]
> Pokud spuštění příkazu, použití vlastnosti projektu, jako například `($StartupFile)`a příkaz se nezdaří, protože token, který není definován, Visual Studio zakáže příkaz, dokud znovu načíst projekt. Provádění změn pro projekt, který by definovat vlastnost, ale neaktualizuje stavu těchto příkazů, je stále potřeba znovu načíst projekt v takových případech.

## <a name="command-target-structure"></a>Příkaz cílová struktura

Obecný tvar `<Target>` elementu se zobrazí v následujícím kódu pseudo:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

K odkazování na vlastnosti projektu a proměnných prostředí v hodnoty atributů, použijte název v rámci `$()` token jako `$(StartupFile)` a `$(MSBuildProjectDirectory)`. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Cílové atributy.

| Atribut | Požadováno | Popis |
| --- | --- | --- |
| Název | Ano | Identifikátor příkazu v rámci projektu sady Visual Studio. Tento název musí být přidán do `<PythonCommands>` skupiny vlastností příkazu se zobrazí v podnabídce Python. |
| Popisek | Ano | Zobrazovaný název uživatelského rozhraní, který se zobrazí dílčí nabídky Python. |
| Vrací | Ano | Musí obsahovat `@(Commands)`, který identifikuje cíl jako příkaz. |

### <a name="createpythoncommanditem-attributes"></a>Atributy CreatePythonCommandItem

Všechny hodnoty atributů jsou malá a velká písmena.

| Atribut | Požadováno | Popis |
| --- | --- | --- |
| TargetType | Ano | Určuje, co obsahuje atribut Target a způsobu jejich použití spolu s argumenty atributu:<ul><li>**spustitelný soubor**: spuštění spustitelného souboru s názvem v cíli, připojením hodnoty v argumentech, jako kdyby zadali přímo na příkazovém řádku. Hodnota musí obsahovat pouze název programu bez argumentů.</li><li>**skript**: Spusťte *python.exe* s názvem souboru v cíli, a potom s hodnotou v argumentech.</li><li>**modul**: Spusťte `python -m` za nímž následuje název modulu v cíli, a potom s hodnotou v argumentech.</li><li>**kód**: spuštění kódu vložené obsažených v cíli. Hodnota argumenty se ignoruje.</li><li>**PIP**: Spusťte `pip` pomocí příkazu v cíli, za nímž následuje argumenty; je ExecuteIn nastavená na "výstupní", ale předpokládá pip `install` příkazů a používá cíl jako název balíčku.</li></ul> |
| Cíl | Ano | Název souboru, název modulu, kód nebo příkazu pip používat, v závislosti na TargetType. |
| Arguments | volitelná, | Určuje řetězec argumentů (pokud existuje) pro cíl. Všimněte si, že pokud TargetType je `script`, argumenty uvedeny v programu Python, ne *python.exe*. Ignorovat `code` TargetType. |
| ExecuteIn | Ano | Určuje prostředí, ve kterém chcete spustit příkaz:<ul><li>**Konzola**: (výchozí) spustí cíl a argumenty jako v případě, že se zadají přímo na příkazovém řádku. Okno příkazového řádku se zobrazí, zatímco cílem běží, pak je automaticky uzavřeny.</li><li>**consolepause**: stejné jako konzoly, ale čeká keypress před zavřením okna.</li><li>**výstup**: cíl spuštění a zobrazuje výsledky v **výstup** okna v sadě Visual Studio. Pokud TargetType je "pip", Visual Studio používá cíl jako název balíčku a připojí argumenty.</li><li>**REPL**: cíl spuštění [interaktivní Python](python-interactive-repl-in-visual-studio.md) okno; volitelný zobrazovaný název se používá pro záhlaví okna.</li><li>**žádný**: chová se stejně jako konzola.</li></ul>|
| WorkingDirectory | volitelná, | Složka, ve kterém chcete spustit příkaz. |
| ErrorRegex<br>WarningRegEx | volitelná, | Použít pouze, když je ExecuteIn `output`. Regulární výraz, pomocí které sady Visual Studio analyzuje výstup zobrazíte chyby a upozornění v příkazu zadat obě hodnoty jeho **seznam chyb** okna. Pokud není zadán, příkaz nemá vliv **seznam chyb** okna. Očekává, že další informace o jaké Visual Studio, najdete v části [skupin zachycení pojmenované](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | volitelná, | Seznam všech požadavků balíčku pro příkaz ve stejném formátu jako [ *souboru requirements.txt* ](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). **Spustit Pylintu** příkazu, například určuje `pylint>=1.0.0`. Před spuštěním příkazu, Visual Studio kontroluje, zda jsou nainstalovány všechny balíčky v seznamu. Visual Studio používá k instalaci všechny chybějící balíčky pip. |
| Prostředí | volitelná, | Řetězec proměnné prostředí k definování před spuštěním příkazu. Každou proměnnou používá formulář \<NAME > =\<hodnota > v případě více proměnných oddělených středníky. Proměnná s více hodnotami musí být obsažen v jednoduché nebo dvojité uvozovky, stejně jako v "NAME = VALUE1; HODNOTA2 ". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Skupiny pojmenované sběr dat pro regulární výrazy

Při analýze kódu chyby a varování z výstupu příkazu, Visual Studio, která očekává regulární výrazy v `ErrorRegex` a `WarningRegex` hodnot použít následující pojmenované skupiny:

- `(?<message>...)`: Text chyby
- `(?<code>...)`: Kód chyby
- `(?<filename>...)`: Název souboru, pro kterou je chyba Hlášená
- `(?<line>...)`: Číslo řádku umístění v souboru, pro který ohlásil chybu.
- `(?<column>...)`: Číslo sloupce umístění v souboru, pro který ohlásil chybu.

Například Pylintu vytvoří upozornění v následujícím formátu:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Umožňuje sadě Visual Studio k extrahování správné informace z těchto upozornění a zobrazit je v **seznam chyb** okně `WarningRegex` hodnotu pro **spustit Pylintu** příkaz vypadá takto:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Všimněte si, že `msg_id` v hodnotě by měl být ve skutečnosti `code`, naleznete v tématu [problém 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Vytvoření souboru .targets pomocí vlastních příkazů

Definování vlastní příkazy v souboru projektu je k dispozici pouze tento soubor projektu. Použití příkazů ve více souborech projektu, můžete místo toho definujte `<PythonCommands>` vlastnost skupinu a všechny vaše `<Target>` prvků v *.targets* souboru. Tento soubor pak importovat do jednotlivé soubory projektu.

*.Targets* je ve formátu souboru následujícím způsobem:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Načíst *.targets* soubor do projektu, umístěte `<Import Project="(path)">` prvek kdekoli v rámci `<Project>` elementu. Například, pokud máte soubor s názvem *CustomCommands.targets* v *cíle* podsložky ve vašem projektu, použijte následující kód:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Vždy, když změníte *.targets* souboru, je potřeba znovu načíst *řešení* , který obsahuje projekt, ne jenom projektu.

## <a name="example-commands"></a>Příklady příkazů

### <a name="run-pylint-module-target"></a>Spustit PyLint (cíl modulu)

Následující kód se zobrazí v *Microsoft.PythonTools.targets* souboru:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Spuštění instalace pip s konkrétním balíčku (cíl pip).

Následující příkaz spustí `pip install my-package` v **výstup** okna. Můžete použít tyto příkaz při vývoji balíček a jeho instalace testování. Všimněte si, že cíl obsahuje název balíčku místo `install` příkaz, který se předpokládá, že při použití `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Zobrazit zastaralé balíčky pip (cíl pip).

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Spuštění spustitelného souboru s consolepause

Následující příkaz spustí jednoduše `where` zobrazíte soubory Pythonu, spouští se ve složce projektu:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Spusťte server a spusťte ladění příkazy serveru

Prozkoumat jak **spustit server** a **spustit server pro ladění** příkazy pro webové projekty jsou definovány, zkontrolujte [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Instalace balíčku pro vývoj

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), použít s oprávněním.*

### <a name="generate-windows-installer"></a>Generovat Instalační služby systému Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), použít s oprávněním.*

### <a name="generate-wheel-package"></a>Generovat balíček wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), použít s oprávněním.*

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="message-the-project-file-could-not-be-loaded"></a>Zpráva: "soubor projektu nelze načíst"

Označuje, že máte chyby syntaxe v souboru projektu. Zpráva obsahuje konkrétní chyba s číslem řádku a pozici znaku.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Zavře okno konzoly hned po spuštění příkazu

Použití `ExecuteIn="consolepause"` místo `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Příkaz v nabídce nezobrazí.

Zkontrolujte, že příkaz je součástí `<PythonCommands>` skupiny vlastností a že název v seznamu příkazu odpovídá názvu zadanému v `<Target>` elementu.

Například následující elementy název "Vzorový" ve skupině vlastností neodpovídá názvu "ExampleCommand" v cílové. Visual Studio nenajde příkaz s názvem "Vzorový", takže se zobrazí žádný příkaz. Použijte "ExampleCommand" v seznamu příkazu, nebo změňte název cílového pouze na "Vzorový".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Zpráva: "došlo k chybě při spouštění \<název příkazu >. Nepovedlo se získat příkaz \<target-name > z projektu. "

Označuje, že obsah `<Target>` nebo `<CreatePythonCommandItem>` prvky jsou nesprávné. Mezi možné důvody patří:

- Požadované `Target` atributu je prázdný.
- Požadované `TargetType` atributu je prázdný nebo obsahuje nerozpoznanou hodnotu.
- Požadované `ExecuteIn` atributu je prázdný nebo obsahuje nerozpoznanou hodnotu.
- `ErrorRegex` nebo `WarningRegex` je zadán bez nastavení `ExecuteIn="output"`.
- Nerozpoznaný atributy neexistují v elementu. Například jste mohli použít `Argumnets` (chybně) namísto `Arguments`.

Hodnoty atributů může být prázdný, pokud budete odkazovat na vlastnost, která není definovaná. Například, pokud použijete token `$(StartupFile)` , ale v projektu nebyl definován žádný spouštěcí soubor a potom token, který se přeloží na prázdný řetězec. V takových případech můžete definovat výchozí hodnotu. Například **spuštění serveru** a **server pro spuštění ladění** příkazy definované v Bottle, Flask, a výchozí šablony projektu Django *souboru manage.py* Pokud jste tak dosud jinak Zadaný spouštěcí soubor, který server ve vlastnostech projektu.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio přestane reagovat a dojde k chybě při spuštění příkazu

Pravděpodobně se pokoušíte spustit příkaz konzoly s `ExecuteIn="output"`, v takovém případě sady Visual Studio dojít k chybě při pokusu o parsování výstupu. Místo nich se používá `ExecuteIn="console"`. (Viz [vydat 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Spustitelný příkaz "nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru"

Při použití `TargetType="executable"`, hodnota v `Target` musí být *pouze* program název bez argumentů, jako například *python* nebo *python.exe* pouze. Přesunout argumentů `Arguments` atribut.
