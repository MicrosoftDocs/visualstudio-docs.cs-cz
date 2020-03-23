---
title: Definování příkazů vlastní nabídky pro projekty Pythonu
description: Úpravou souborů projektu a cílů můžete přidat vlastní příkazy do kontextové nabídky projektu Pythonu v sadě Visual Studio a vyvolat spustitelné programy, skripty, moduly, fragmenty vřádíkem vřádku a pip.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ec53a67980866ed6422fae5764bbf6a9313ef91e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957656"
---
# <a name="define-custom-commands-for-python-projects"></a>Definování vlastních příkazů pro projekty Pythonu

V procesu práce s projekty Pythonu se můžete ocitnout při přepnutí do příkazového okna pro spuštění konkrétních skriptů nebo modulů, spuštění příkazů pip nebo spuštění jiného libovolného nástroje. Chcete-li zlepšit svůj pracovní postup, můžete přidat vlastní příkazy do podnabídky **Pythonu** v kontextové nabídce projektu Pythonu. Tyto příkazy lze spustit v okně konzoly nebo v okně Visual Studio **Output.** Regulární výrazy můžete také použít k instruování sady Visual Studio, jak analyzovat chyby a upozornění z výstupu příkazu.

Ve výchozím nastavení tato nabídka obsahuje pouze jeden příkaz **Spustit PyLint:**

![Výchozí vzhled podnabídky Pythonu v kontextové nabídce projektu](media/custom-commands-default-menu.png)

Vlastní příkazy se zobrazí ve stejné místní nabídce. Vlastní příkazy jsou přidány do souboru projektu přímo, kde se vztahují na tento jednotlivý projekt. Můžete také definovat vlastní příkazy v souboru *.targets,* které lze snadno importovat do více souborů projektu.

Některé šablony projektů Pythonu v sadě Visual Studio již přidávají vlastní příkazy pomocí souboru *.targets.* Například šablony Bottle Web Project a Flask Web Project přidávají dva příkazy, **Start server** a **Start ladicí server**. Šablona webového projektu Django přidává stejné příkazy a několik dalších:

![Vzhled podnabídky Pythonu v kontextové nabídce projektu Django](media/custom-commands-django-menu.png)

Každý vlastní příkaz může odkazovat na soubor Pythonu, modul Pythonu, vřádkový kód Pythonu, libovolný spustitelný soubor nebo příkaz pip. Můžete také určit, jak a kde je příkaz spuštěn.

> [!Tip]
> Kdykoli provedete změny v souboru projektu v textovém editoru, je nutné znovu načíst projekt v sadě Visual Studio, abyste tyto změny použili. Například je nutné znovu načíst projekt po přidání vlastní chod příkazů pro tyto příkazy, které se zobrazí v kontextové nabídce projektu.
>
> Jak možná víte, Visual Studio poskytuje prostředky k úpravě souboru projektu přímo. Nejprve klepněte pravým tlačítkem myši na soubor projektu a vyberte **uvolnit projekt**, potom znovu klepněte pravým tlačítkem myši a vyberte **upravit \<název projektu>** otevřete projekt v editoru sady Visual Studio. Potom provedete a uložíte úpravy, znovu kliknete pravým tlačítkem myši na projekt a vyberete **znovu načíst projekt**, který vás také vyzve k potvrzení zavření souboru projektu v editoru.
>
> Při vývoji vlastního příkazu se však všechna tato kliknutí mohou stát zdlouhavá. Efektivnější pracovní postup načtěte projekt v sadě Visual Studio a také otevřete soubor *.pyproj* v samostatném editoru (například jinou instanci sady Visual Studio, kód sady Visual Studio, poznámkový blok atd.). Když uložíte změny v editoru a přepnete do sady Visual Studio, Visual Studio zjistí změny a zeptá se, zda chcete znovu načíst projekt (**Název \<projektu> byl změněn mimo prostředí.**). Vyberte **Znovu načíst** a změny se okamžitě použijí v jediném kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Návod: Přidání příkazu do souboru projektu

Chcete-li se seznámit s vlastními příkazy, tato část prochází jednoduchým příkladem, který spouští spouštěcí soubor projektu přímo pomocí *python.exe*. (Takový příkaz je v podstatě stejný jako pomocí **ladění** > **Start bez ladění**.)

1. Vytvořte nový projekt s názvem "Python-CustomCommands" pomocí šablony **aplikace Python.** (Viz [Úvodní příručka: Vytvoření projektu Pythonu ze šablony](quickstart-02-python-in-visual-studio-project-from-template.md) pro pokyny, pokud ještě nejste obeznámeni s procesem.)

1. V *Python_CustomCommands.py*přidejte `print("Hello custom commands")`kód .

1. Klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení**, vyberte **Python**a všimněte si, že jediný příkaz, který se zobrazí v podnabídce, je **Spustit PyLint**. Vlastní příkazy se zobrazí ve stejné podnabídce.

1. Jak je navrženo v úvodu, otevřete *Python-CustomCommands.pyproj* v samostatném textovém editoru. Potom přidejte následující řádky na konec souboru `</Project>` přímo uvnitř uzávěrky a uložte soubor.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Přepněte zpět do sady Visual Studio a vyberte **Znovu načíst,** když se zobrazí výzva ke změně souboru. Pak znovu zkontrolujte nabídku **Pythonu,** abyste viděli, že **Spustit PyLint** je `<PythonCommands>` stále jedinou položkou, která je zde zobrazena, protože řádky, které jste přidali, replikují pouze výchozí skupinu vlastností obsahující příkaz PyLint.

1. Přepněte do editoru se souborem `<Target>` projektu `<PropertyGroup>`a za soubor přidejte následující definici. Jak je vysvětleno dále `Target` v tomto článku, tento prvek definuje vlastní příkaz pro spuštění spouštěcího souboru (identifikovaný vlastností "StartupFile") pomocí *python.exe* v okně konzoly. Atribut `ExecuteIn="consolepause"` používá konzolu, která čeká na stisknutí klávesy před zavřením.

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

1. Přidejte hodnotu `Name` atributu Target `<PythonCommands>` do skupiny vlastností přidané dříve, aby prvek vypadal jako níže uvedený kód. Přidání názvu cíle do tohoto seznamu je to, co jej přidá do nabídky **Pythonu.**

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Pokud chcete, aby se příkaz `$(PythonCommands)`zobrazil před příkazy definovanými v aplikaci , umístěte je před tento token.

1. Uložte soubor projektu, přepněte do sady Visual Studio a po zobrazení výzvy projekt znovu načtěte. Potom klepněte pravým tlačítkem myši na projekt **Python-CustomCommands** a vyberte **Python**. V nabídce by se měla zobrazit položka **spouštěcího souboru.** Pokud položku nabídky nevidíte, zkontrolujte, zda jste `<PythonCommands>` do prvku přidali název. Viz také [řešení potíží](#troubleshooting) dále v tomto článku.

    ![Vlastní příkaz zobrazený v podnabídce kontextu Pythonu](media/custom-commands-walkthrough-menu-item.png)

1. Vyberte příkaz **Spustit spouštěcí soubor** a mělo by se zobrazit příkazové okno s textem Další vlastní příkazy následované **pokračováním stisknutím libovolné** **klávesy** .  Zavřete okno stisknutím klávesy.

    ![Vlastní výstup příkazu v okně konzoly](media/custom-commands-walkthrough-console.png)

1. Vraťte se do editoru se souborem `ExecuteIn` projektu `output`a změňte hodnotu atributu na . Uložte soubor, přepněte do sady Visual Studio, znovu načtěte projekt a příkaz znovu vyvoláte. Tentokrát se výstup programu zobrazí v okně **Výstup** sady Visual Studio:

    ![Vlastní výstup příkazu ve výstupním okně](media/custom-commands-walkthrough-output-window.png)

1. Chcete-li přidat další příkazy, definujte vhodný `<Target>` prvek pro každý `<PythonCommands>` příkaz, přidejte název cíle do skupiny vlastností a znovu načtěte projekt v sadě Visual Studio.

>[!Tip]
> Pokud vyvoláte příkaz, který používá `($StartupFile)`vlastnosti projektu, například , a příkaz se nezdaří, protože token není definován, Visual Studio zakáže příkaz, dokud projekt znovu nenačtete. Provádění změn v projektu, který by definoval vlastnost, však neaktualizuje stav těchto příkazů, takže v takových případech je stále nutné znovu načíst projekt.

## <a name="command-target-structure"></a>Cílová struktura příkazu

Obecná forma `<Target>` prvku je uvedena v následujícím pseudokódu:

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

Chcete-li odkazovat na vlastnosti projektu nebo proměnné `$()` prostředí v `$(StartupFile)` hodnotách atributů, použijte název v tokenu, například a `$(MSBuildProjectDirectory)`. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Cílové atributy

| Atribut | Požaduje se | Popis |
| --- | --- | --- |
| Name (Název) | Ano | Identifikátor pro příkaz v rámci projektu sady Visual Studio. Tento název musí být `<PythonCommands>` přidán do skupiny vlastností, aby se příkaz zobrazil v podnabídce Pythonu. |
| Popisek | Ano | Zobrazovaný název uživatelského prostředí, který se zobrazí v podnabídce Pythonu. |
| Vrací | Ano | Musí `@(Commands)`obsahovat , který identifikuje cíl jako příkaz. |

### <a name="createpythoncommanditem-attributes"></a>Atributy CreatePythonCommandItem

Všechny hodnoty atributů nerozlišují malá a velká písmena.

| Atribut | Požaduje se | Popis |
| --- | --- | --- |
| Targettype | Ano | Určuje, co atribut Target obsahuje a jak se používá spolu s atributem Arguments:<ul><li>**spustitelný soubor**: Spusťte spustitelný soubor pojmenovaný v targetu a připojujte hodnotu v argumentech, jako by byl zadán přímo na příkazovém řádku. Hodnota musí obsahovat pouze název programu bez argumentů.</li><li>**skript**: Spusťte *python.exe* s názvem souboru v Target, následovaný hodnotou v Arguments.</li><li>**modul**: `python -m` Spustit následovaný názvem modulu v Target, následovaný hodnotou v Arguments.</li><li>**kód**: Spusťte vložkový kód obsažený v targetu. Hodnota Arguments je ignorována.</li><li>**pip**: `pip` Spustit s příkazem v targetu, následovaným Argumenty; is ExecuteIn je nastavena na "výstup", `install` ale pip převezme příkaz a používá Target jako název balíčku.</li></ul> |
| Cíl | Ano | Název souboru, název modulu, kód nebo pip příkaz použít, v závislosti na TargetType. |
| Argumenty | Nepovinné | Určuje řetězec argumentů (pokud existuje) dát cíl. Všimněte si, `script`že když TargetType je , argumenty jsou uvedeny v programu Python, nikoli *python.exe*. Ignorováno pro `code` TargetType. |
| ExecuteIn | Ano | Určuje prostředí, ve kterém má být příkaz spuštěn:<ul><li>**konzole**: (Výchozí) Spustí cíl a argumenty, jako by byly zadány přímo na příkazovém řádku. Příkazové okno se zobrazí, když je cíl spuštěn, a pak se automaticky zavře.</li><li>**consolepause**: Stejné jako konzole, ale čeká na stisknutí klávesy před zavřením okna.</li><li>**výstup**: Spustí cíl a zobrazí jeho výsledky v okně **Výstup** v sadě Visual Studio. Pokud TargetType je "pip", Visual Studio používá Target jako název balíčku a připojí Arguments.</li><li>**repl**: Spustí cíl v interaktivním okně [Pythonu;](python-interactive-repl-in-visual-studio.md) pro název okna se používá volitelný zobrazovaný název.</li><li>**žádný**: chová se stejně jako konzole.</li></ul>|
| WorkingDirectory | Nepovinné | Složka, ve které chcete spustit příkaz. |
| Chybový kód<br>UpozorněníRegEx | Nepovinné | Používá se pouze `output`v případě, že executeIn je . Obě hodnoty určují regulární výraz, se kterým visual studio analyzuje výstup příkazu pro zobrazení chyb a upozornění v okně **seznamu chyb.** Pokud není zadán, příkaz nemá vliv na okno **Seznam chyb.** Další informace o tom, co Visual Studio očekává, naleznete [v tématu Pojmenované skupiny sběru](#named-capture-groups-for-regular-expressions). |
| Povinné balíčky | Nepovinné | Seznam požadavků na balíček pro příkaz ve stejném formátu jako [*requirements.txt*](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). Příkaz **Spustit PyLint,** například `pylint>=1.0.0`určuje . Před spuštěním příkazu visual studio zkontroluje, že jsou nainstalovány všechny balíčky v seznamu. Visual Studio používá pip k instalaci všech chybějících balíčků. |
| Prostředí | Nepovinné | Řetězec proměnných prostředí, které chcete definovat před spuštěním příkazu. Každá proměnná \<používá formulář\<NÁZEV>= HODNOTA> s více proměnnými oddělenými středníky. Proměnná s více hodnotami musí být obsažena v jednoduchých nebo dvojitých uvozovkách, jako v 'NAME=VALUE1; HODNOTA2". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Pojmenované skupiny sběru pro regulární výrazy

Při analýzě chyby a upozornění z výstupu příkazu visual studio očekává, `ErrorRegex` `WarningRegex` že regulární výrazy v hodnotách a používají následující pojmenované skupiny:

- `(?<message>...)`: Text chyby
- `(?<code>...)`: Kód chyby
- `(?<filename>...)`: Název souboru, pro který je chyba hlášena
- `(?<line>...)`: Číslo řádku umístění v souboru, pro které byla chyba hlášena.
- `(?<column>...)`: Číslo sloupce umístění v souboru, pro které byla chyba hlášena.

Například PyLint vytváří upozornění následujícího formuláře:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Chcete-li aplikaci Visual Studio povolit extrahovat správné informace `WarningRegex` z těchto upozornění a zobrazit je v okně **Seznam chyb,** je hodnota příkazu Spustit **pylint** následující:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Všimněte `msg_id` si, že `code`v hodnotě by měla být ve skutečnosti naleznete [v tématu Problém 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Vytvoření souboru .targets s vlastními příkazy

Definování vlastních příkazů v souboru projektu je zpřístupní pouze tomuto souboru projektu. Chcete-li použít příkazy ve více `<PythonCommands>` souborech projektu, `<Target>` definujte místo toho skupinu vlastností a všechny prvky v souboru *.targets.* Potom importovat tento soubor do jednotlivých souborů projektu.

Soubor *.targets* je formátován takto:

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

Chcete-li načíst soubor *.targets* `<Import Project="(path)">` do projektu, `<Project>` umístěte prvek kdekoli v rámci prvku. Pokud máte například soubor s názvem *CustomCommands.targets* v podsložce *cílů* v projektu, použijte následující kód:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Při každé změně souboru *.targets* je třeba znovu načíst *řešení,* které obsahuje projekt, nikoli pouze samotný projekt.

## <a name="example-commands"></a>Příklady příkazů

### <a name="run-pylint-module-target"></a>Spustit PyLint (cíl modulu)

V souboru *Microsoft.PythonTools.targets* se zobrazí následující kód:

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Spustit instalaci pipu s konkrétním balíčkem (pip target)

Následující příkaz `pip install my-package` běží v okně **Výstup.** Takový příkaz můžete použít při vývoji balíčku a testování jeho instalace. Všimněte si, že Target `install` obsahuje název balíčku spíše `ExecuteIn="output"`než příkaz, který se předpokládá při použití .

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

### <a name="show-outdated-pip-packages-pip-target"></a>Zobrazit zastaralé pip balíčky (pip cíl)

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

Následující příkaz jednoduše `where` spustí zobrazení souborů Pythonu začínajících ve složce projektu:

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

### <a name="run-server-and-run-debug-server-commands"></a>Spuštění serveru a spuštění příkazů ladicího serveru

Chcete-li **prozkoumat,** jak jsou definovány příkazy serveru Start a **Start pro** webové projekty, zkontrolujte [cíle Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Nainstalovat balíček pro vývoj

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), používá se svolením.*

### <a name="generate-windows-installer"></a>Generovat instalační program systému Windows

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), používá se svolením.*

### <a name="generate-wheel-package"></a>Generovat balíček kol

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), používá se svolením.*

## <a name="troubleshooting"></a>Řešení potíží

### <a name="message-the-project-file-could-not-be-loaded"></a>Zpráva " Soubor projektu nelze načíst"

Označuje, že máte v souboru projektu syntaktické chyby. Zpráva obsahuje konkrétní chybu s číslem řádku a pozicí znaku.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Okno konzoly se zavře ihned po spuštění příkazu

Místo `ExecuteIn="consolepause"` použít `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Příkaz se v nabídce nezobrazí

Zkontrolujte, zda je `<PythonCommands>` příkaz zahrnut do skupiny vlastností a zda název `<Target>` v seznamu příkazů odpovídá názvu zadanému v prvku.

Například v následujících prvcích název "Příklad" ve skupině vlastností neodpovídá názvu "ExampleCommand" v cíli. Visual Studio nenajde příkaz s názvem "Příklad", takže se nezobrazí žádný příkaz. Buď použijte "ExampleCommand" v seznamu příkazů, nebo změňte název cíle pouze na "Příklad".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Zpráva " Při spuštění \<názvu příkazu> došlo k chybě. Nepodařilo se \<získat> názvu cíle příkazu z projektu."

Označuje, že obsah `<Target>` `<CreatePythonCommandItem>` nebo prvky jsou nesprávné. Možné důvody zahrnují:

- Požadovaný `Target` atribut je prázdný.
- Požadovaný `TargetType` atribut je prázdný nebo obsahuje nerozpoznanou hodnotu.
- Požadovaný `ExecuteIn` atribut je prázdný nebo obsahuje nerozpoznanou hodnotu.
- `ErrorRegex`nebo `WarningRegex` je zadán `ExecuteIn="output"`bez nastavení .
- V prvku existují nerozpoznané atributy. Je například možné, `Argumnets` že jste místo toho `Arguments`použili (chybně napsané).

Hodnoty atributů mohou být prázdné, pokud odkazujete na vlastnost, která není definována. Pokud například použijete `$(StartupFile)` token, ale v projektu nebyl definován žádný spouštěcí soubor, pak se token překládá na prázdný řetězec. V takových případech můžete definovat výchozí hodnotu. Například **příkazy Spustit server** a **Spustit ladicí server** definované v šablonách projektu Bottle, Flask a Django jsou ve výchozím nastavení *manage.py* pokud jste jinak nezadali spouštěcí soubor serveru ve vlastnostech projektu.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio přestane reagovat a dojde k chybě při spuštění příkazu

Pravděpodobně se pokoušíte spustit příkaz konzoly s `ExecuteIn="output"`, v takovém případě visual studio může dojít k chybě při pokusu o analýzu výstupu. Místo toho použijte `ExecuteIn="console"`. (Viz [vydání 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Spustitelný příkaz "není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor"

Při `TargetType="executable"`použití musí `Target` být hodnota v *pouze* název programu bez jakýchkoli argumentů, například *pouze python* nebo *python.exe.* Přesuňte všechny argumenty do atributu. `Arguments`
