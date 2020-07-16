---
title: Definování vlastních příkazů nabídky pro projekty v Pythonu
description: Úpravou souborů projektu a cílů můžete přidat vlastní příkazy do kontextové nabídky projektu Python v aplikaci Visual Studio k vyvolání spustitelných programů, skriptů, modulů, vložených fragmentů kódu a PIP.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e9e7fe418528bb888672b1b73d421d811b9e69e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386982"
---
# <a name="define-custom-commands-for-python-projects"></a>Definovat vlastní příkazy pro projekty v Pythonu

Při práci s projekty v Pythonu se můžete setkat s přepnutím do okna příkazového řádku, ve kterém můžete spouštět konkrétní skripty nebo moduly, spouštět příkazy PIP nebo spouštět jiný libovolný nástroj. Chcete-li vylepšit pracovní postup, můžete přidat vlastní příkazy do podnabídky **Python** v kontextové nabídce projektu Python. Tyto příkazy lze spustit v okně konzoly nebo v okně **výstup** aplikace Visual Studio. Můžete také použít regulární výrazy k tomu, abyste aplikaci Visual Studio pověřili, jak analyzovat chyby a upozornění z výstupu příkazu.

Ve výchozím nastavení tato nabídka obsahuje pouze jeden příkaz **Run Pylint** :

![Výchozí vzhled podnabídky Pythonu v kontextové nabídce projektu](media/custom-commands-default-menu.png)

Vlastní příkazy se zobrazí v této stejné místní nabídce. Vlastní příkazy jsou přidány do souboru projektu přímo, kde se vztahují na daný jednotlivý projekt. Můžete také definovat vlastní příkazy v souboru *. targets* , které lze snadno importovat do více souborů projektu.

Některé šablony projektů Pythonu v aplikaci Visual Studio již přidávají vlastní příkazy s použitím jejich souboru *. targets* . Například šablony webového projektu na láhvi a webové projekty v baňce přidejte dva příkazy, **spusťte server** a **spusťte ladicí Server**. Šablona webového projektu Django přidává tyto stejné příkazy a ještě několik dalších:

![Vzhled podnabídky Pythonu v místní nabídce projektu Django](media/custom-commands-django-menu.png)

Každý vlastní příkaz může odkazovat na soubor Pythonu, modul Pythonu, vložený kód Pythonu, libovolný spustitelný soubor nebo příkaz PIP. Můžete také určit, jak a kde se příkaz spustí.

> [!Tip]
> Pokaždé, když provedete změny v souboru projektu v textovém editoru, je nutné znovu načíst projekt v aplikaci Visual Studio, aby se změny projevily. Například je nutné znovu načíst projekt poté, co přidáte vlastní definice příkazů pro tyto příkazy, které se mají zobrazit v místní nabídce projektu.
>
> Jak budete možná znám, Visual Studio poskytuje způsob, jak přímo upravovat soubor projektu. Nejprve klikněte pravým tlačítkem myši na soubor projektu a vyberte **Uvolnit projekt**, potom klikněte pravým tlačítkem myši a **výběrem \<project-name> Upravit** otevřete projekt v editoru sady Visual Studio. Pak můžete upravit a uložit úpravy, kliknout pravým tlačítkem myši na projekt a vybrat možnost **znovu načíst projekt**, což vás také vyzve k potvrzení zavření souboru projektu v editoru.
>
> Při vývoji vlastního příkazu se ale všechna tato kliknutí můžou stát únavné. Pro efektivnější pracovní postup načtěte projekt v aplikaci Visual Studio a také otevřete soubor *. pyproj* v samostatném editoru (například jinou instanci sady Visual Studio, Visual Studio Code, Poznámkový blok atd.). Když uložíte změny v editoru a přepnete se do sady Visual Studio, Visual Studio zjistí změny a zeptá se, jestli se má projekt znovu načíst (**projekt \<name> byl upravený mimo prostředí**). Vyberte možnost **znovu načíst** a vaše změny se okamžitě uplatní jenom v jednom kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Návod: Přidání příkazu do souboru projektu

Chcete-li se seznámit s vlastními příkazy, Tato část vás provede jednoduchým příkladem, který spouští spouštěcí soubor projektu přímo pomocí *python.exe*. (Takový příkaz je efektivně stejný jako při použití **ladění**  >  **Spustit bez ladění**.)

1. Pomocí šablony **aplikace Python** vytvořte nový projekt s názvem Python-CustomCommands. (Další informace najdete v tématu [rychlý Start: vytvoření projektu v Pythonu ze šablony](quickstart-02-python-in-visual-studio-project-from-template.md) pro pokyny, pokud už tento proces neznáte.)

1. Do *Python_CustomCommands. py*přidejte kód `print("Hello custom commands")` .

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt, vyberte **Python**a Všimněte si, že jediný příkaz, který se zobrazí v podnabídce, se **spustí Pylint**. Vlastní příkazy se zobrazí v této stejné podnabídce.

1. Jak je navrženo v úvodu, otevřete *Python-CustomCommands. pyproj* v samostatném textovém editoru. Pak na konec souboru přidejte následující řádky, které jsou právě uvnitř zavření `</Project>` a soubor uložte.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Přepněte zpět do sady Visual Studio a po výzvě k změně souboru vyberte **znovu načíst** . Pak znovu zkontrolujte nabídku **Pythonu** , abyste viděli, že **běh Pylint** je stále jediná zobrazená položka, protože řádky, které jste přidali, replikují pouze výchozí `<PythonCommands>` skupinu vlastností obsahující příkaz Pylint.

1. Přepněte do editoru se souborem projektu a přidejte následující `<Target>` definici za `<PropertyGroup>` . Jak je vysvětleno dále v tomto článku, tento `Target` prvek definuje vlastní příkaz pro spuštění spouštěcího souboru (identifikovaný vlastností "StartupFile") pomocí *python.exe* v okně konzoly. Atribut `ExecuteIn="consolepause"` používá konzolu, která čeká na stisknutí klávesy před zavřením.

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

1. Přidejte hodnotu `Name` atributu target do `<PythonCommands>` skupiny vlastností přidané dříve, aby element vypadal jako následující kód. Přidání názvu cíle do tohoto seznamu je to, co přidá do nabídky **Pythonu** .

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Pokud chcete, aby se Váš příkaz zobrazoval před tím, než je definované v `$(PythonCommands)` , umístěte je před tento token.

1. Uložte soubor projektu, přepněte do sady Visual Studio a po zobrazení výzvy znovu načtěte projekt. Pak klikněte pravým tlačítkem na projekt **Python-CustomCommands** a vyberte **Python**. V nabídce by se měla zobrazit položka **spustit spouštěcí soubor** . Pokud se položka nabídky nezobrazí, zkontrolujte, zda jste přidali název k `<PythonCommands>` elementu. Další informace najdete také v části [řešení potíží](#troubleshooting) dále v tomto článku.

    ![Vlastní příkaz se zobrazuje v podnabídce kontextu Pythonu.](media/custom-commands-walkthrough-menu-item.png)

1. Vyberte příkaz **spustit spouštěcí soubor** a měli byste vidět, že se zobrazí okno s textovým textem Hello, po kterém následují **vlastní příkazy** , a **pokračujte stisknutím libovolné klávesy**.  Stisknutím klávesy zavřete okno.

    ![Výstup vlastního příkazu v okně konzoly](media/custom-commands-walkthrough-console.png)

1. Vraťte se do editoru se souborem projektu a změňte hodnotu `ExecuteIn` atributu na `output` . Uložte soubor, přepněte do sady Visual Studio, znovu načtěte projekt a znovu spusťte příkaz. Tentokrát se zobrazí výstup programu v okně **výstupu** sady Visual Studio:

    ![Výstup vlastního příkazu v okně výstup](media/custom-commands-walkthrough-output-window.png)

1. Chcete-li přidat další příkazy, definujte vhodný `<Target>` prvek pro každý příkaz, přidejte název cíle do `<PythonCommands>` skupiny vlastností a znovu načtěte projekt v aplikaci Visual Studio.

>[!Tip]
> Pokud vyvoláte příkaz, který používá vlastnosti projektu, například `($StartupFile)` , a příkaz se nepovede, protože není definovaný token, Visual Studio zakáže příkaz, dokud projekt znovu nenačtete. Provádění změn v projektu, které by definovaly vlastnost, ale neaktualizuje stav těchto příkazů, takže v takových případech stále potřebujete znovu načíst projekt.

## <a name="command-target-structure"></a>Cílová struktura příkazu

Obecný tvar `<Target>` elementu je zobrazen v následujícím pseudo kódu:

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

Chcete-li odkazovat na vlastnosti projektu nebo proměnné prostředí v hodnotách atributu, použijte název v rámci `$()` tokenu, například `$(StartupFile)` a `$(MSBuildProjectDirectory)` . Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atributy cíle

| Atribut | Povinné | Popis |
| --- | --- | --- |
| Název | Yes | Identifikátor příkazu v rámci projektu sady Visual Studio. Tento název musí být přidán do `<PythonCommands>` skupiny vlastností pro příkaz, který se zobrazí v podnabídce Python. |
| Popisek | Yes | Zobrazované jméno uživatelského rozhraní, které se zobrazí v podnabídce Pythonu |
| Návraty | Yes | Musí obsahovat `@(Commands)` , který identifikuje cíl jako příkaz. |

### <a name="createpythoncommanditem-attributes"></a>Atributy CreatePythonCommandItem

U všech hodnot atributů se nerozlišují velká a malá písmena.

| Atribut | Povinné | Popis |
| --- | --- | --- |
| TargetType | Yes | Určuje, jaký cílový atribut obsahuje a jak se používá společně s atributem arguments:<ul><li>**spustitelný soubor**: Spusťte spustitelný soubor s názvem v cíli a připojením hodnoty v argumentech jako při zadání přímo na příkazovém řádku. Hodnota musí obsahovat pouze název programu bez argumentů.</li><li>**skript**: Spusťte *python.exe* s názvem souboru v cíli a potom s hodnotou v argumentech.</li><li>**modul**: spustit `python -m` následovaný názvem modulu v cíli a následovaný hodnotou v argumentech.</li><li>**kód**: Spusťte vložený kód obsažený v cíli. Hodnota argumentů je ignorována.</li><li>**PIP**: Spusťte `pip` příkaz s příkazem v cíli, následovaný argumenty. ExecuteIn je nastavená na "Output", ale příkaz PIP předpokládá `install` příkaz a jako název balíčku používá cíl.</li></ul> |
| Cíl | Yes | Název souboru, název modulu, kód nebo PIP, který se má použít, v závislosti na TargetType. |
| Arguments | Volitelné | Určuje řetězec argumentů (pokud existuje), který se má poskytnout cíli. Všimněte si, že pokud je TargetType `script` , argumenty jsou předány programu Python, nikoli *python.exe*. Ignorováno pro `code` TargetType. |
| ExecuteIn | Yes | Určuje prostředí, ve kterém se má příkaz spustit:<ul><li>**Konzola**: (výchozí) spustí cíl a argumenty, jako by byly zadány přímo na příkazovém řádku. Příkazové okno se zobrazí, když je cíl spuštěný, a pak se automaticky zavře.</li><li>**consolepause**: totéž jako konzola, ale před zavřením okna počká na stisknutí klávesy.</li><li>**výstup**: spustí cíl a zobrazí jeho výsledky v okně **výstup** v aplikaci Visual Studio. Pokud TargetType je "PIP", sada Visual Studio používá jako název balíčku cíl a připojuje argumenty.</li><li>**REPL**: cíl spuštění v [interaktivním okně Pythonu](python-interactive-repl-in-visual-studio.md) ; volitelné zobrazované jméno se používá pro název okna.</li><li>**žádné**: chová se stejně jako konzola.</li></ul>|
| WorkingDirectory | Volitelné | Složka, ve které se má příkaz Spustit |
| ErrorRegex<br>WarningRegEx | Volitelné | Používá se pouze v případě, že je ExecuteIn `output` . Obě hodnoty určují regulární výraz, se kterým Visual Studio analyzuje výstup příkazu, aby se zobrazily chyby a upozornění v okně **Seznam chyb** . Pokud není zadán, příkaz nemá vliv na okno **Seznam chyb** . Další informace o tom, co Visual Studio očekává, najdete v tématu [pojmenované skupiny zachycení](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Volitelné | Seznam požadavků balíčku pro příkaz ve stejném formátu jako [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (PIP.readthedocs.IO). Příkaz **Run Pylint** , například určuje `pylint>=1.0.0` . Před spuštěním příkazu kontroluje aplikace Visual Studio, zda jsou nainstalovány všechny balíčky v seznamu. Visual Studio pomocí PIP nainstaluje všechny chybějící balíčky. |
| Prostředí | Volitelné | Řetězec proměnných prostředí, které mají být definovány před spuštěním příkazu. Každá proměnná používá formulář \<NAME> = \<VALUE> s více proměnnými oddělenými středníky. Proměnná s více hodnotami musí být obsažená v jednoduchých nebo dvojitých uvozovkách, jako je název = HODNOTA1; HODNOTA2. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Pojmenované skupiny zachycení pro regulární výrazy

Při analýze chyb a upozornění z výstupu příkazu aplikace Visual Studio očekává, že regulární výrazy v `ErrorRegex` `WarningRegex` hodnotách a používají následující pojmenované skupiny:

- `(?<message>...)`: Text chyby
- `(?<code>...)`: Kód chyby
- `(?<filename>...)`: Název souboru, pro který je Nahlášená chyba
- `(?<line>...)`: Číslo řádku umístění v souboru, pro které byla chyba hlášena.
- `(?<column>...)`: Číslo sloupce umístění v souboru, pro které byla chyba hlášena.

Například PyLint generuje upozornění v následujícím tvaru:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Chcete-li, aby aplikace Visual Studio mohla z takových upozornění extrahovat správné informace a zobrazit je v okně **Seznam chyb** , `WarningRegex` je hodnota příkazu **Run Pylint** následující:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Všimněte si, že `msg_id` ve skutečnosti by měla být tato hodnota `code` , viz článek o [problému 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Vytvoření souboru. targets s vlastními příkazy

Definování vlastních příkazů v souboru projektu zpřístupňuje je pouze pro tento soubor projektu. Chcete-li použít příkazy ve více souborech projektu, můžete místo toho definovat `<PythonCommands>` skupinu vlastností a všechny `<Target>` prvky v souboru *. targets* . Pak tento soubor naimportujete do jednotlivých souborů projektu.

Soubor *. targets* je naformátován takto:

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

Chcete-li načíst soubor *. targets* do projektu, umístěte `<Import Project="(path)">` prvek kdekoli v rámci `<Project>` elementu. Například pokud máte soubor s názvem *CustomCommands. targets* v podsložce *cíle* v projektu, použijte následující kód:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Pokaždé, když změníte soubor *. targets* , je nutné znovu načíst *řešení* , které obsahuje projekt, nikoli pouze samotný projekt.

## <a name="example-commands"></a>Příklady příkazů

### <a name="run-pylint-module-target"></a>Spustit PyLint (cíl modulu)

V souboru *Microsoft. PythonTools. targets* se zobrazí následující kód:

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Spustit instalaci PIP s konkrétním balíčkem (cíl PIP)

Následující příkaz se spustí `pip install my-package` v okně **výstup** . Tento příkaz můžete použít při vývoji balíčku a testování jeho instalace. Všimněte si, že cíl obsahuje název balíčku `install` , a ne příkaz, který se předpokládá při použití `ExecuteIn="output"` .

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

### <a name="show-outdated-pip-packages-pip-target"></a>Zobrazit zastaralé balíčky PIP (cíl PIP)

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

Následující příkaz se jednoduše spustí `where` pro zobrazení souborů Pythonu, které začínají ve složce projektu:

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

### <a name="run-server-and-run-debug-server-commands"></a>Spustit příkazy serveru a spustit ladicí Server

Chcete-li prozkoumat, jak jsou definovány příkazy **spustit server** a **Spustit ladicí Server** pro webové projekty, prozkoumejte [Microsoft. PythonTools. Web. targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) používané s oprávněním.*

### <a name="generate-windows-installer"></a>Generovat instalační službu systému Windows

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) používané s oprávněním.*

### <a name="generate-wheel-package"></a>Generovat balíček kolečka

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) používané s oprávněním.*

## <a name="troubleshooting"></a>Řešení potíží

### <a name="message-the-project-file-could-not-be-loaded"></a>Zpráva: "soubor projektu nelze načíst"

Označuje, že v souboru projektu máte syntaktické chyby. Zpráva obsahuje konkrétní chybu s číslem řádku a pozicí znaků.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Okno konzoly se zavře hned po spuštění příkazu.

`ExecuteIn="consolepause"`Místo použijte `ExecuteIn="console"` .

### <a name="command-does-not-appear-on-the-menu"></a>Příkaz se nezobrazuje v nabídce

Ověřte, zda je příkaz součástí `<PythonCommands>` skupiny vlastností a zda název v seznamu příkazů odpovídá názvu zadanému v `<Target>` elementu.

Například v následujících prvcích se název "Příklad" ve skupině vlastností neshoduje s názvem "ExampleCommand" v cíli. Visual Studio nenalezne příkaz s názvem "example", takže se nezobrazí žádný příkaz. V seznamu příkazů buď použijte "ExampleCommand", nebo změňte název cíle na pouze "Příklad".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Zpráva: při běhu došlo k chybě \<command name> . Nepodařilo se získat příkaz \<target-name> z projektu. "

Indikuje, že obsah `<Target>` `<CreatePythonCommandItem>` elementů nebo není správný. Mezi možné příčiny patří:

- Požadovaný `Target` atribut je prázdný.
- Požadovaný `TargetType` atribut je prázdný nebo obsahuje nerozpoznanou hodnotu.
- Požadovaný `ExecuteIn` atribut je prázdný nebo obsahuje nerozpoznanou hodnotu.
- `ErrorRegex`nebo `WarningRegex` je zadáno bez nastavení `ExecuteIn="output"` .
- V elementu existují nerozpoznané atributy. Můžete například použít `Argumnets` (špatně napsaný) místo `Arguments` .

Pokud odkazujete na vlastnost, která není definována, hodnoty atributu můžou být prázdné. Například pokud použijete token `$(StartupFile)` , ale v projektu není definován spouštěcí soubor, token se přeloží na prázdný řetězec. V takových případech možná budete chtít definovat výchozí hodnotu. Například příkazy **spustit server** a **Spustit ladicí Server** , které jsou definovány v láhvích, baňce a šablonách projektů Django, se nastaví jako výchozí *Manage.py* , pokud jste jinak neurčili spouštěcí soubor serveru ve vlastnostech projektu.

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio přestane reagovat a dojde k chybě při spuštění příkazu

Pravděpodobně se pokoušíte spustit příkaz konzoly s `ExecuteIn="output"` , v takovém případě může Visual Studio selhat při pokusu o analýzu výstupu. Místo toho použijte `ExecuteIn="console"`. (Viz článek o [problému 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Spustitelný příkaz se nerozpoznal jako interní nebo externí příkaz, funkční program nebo dávkový soubor.

Při použití `TargetType="executable"` aplikace `Target` musí být hodnota v názvu programu *pouze* bez argumentů, například *Python* nebo *python.exe* . Přesuňte všechny argumenty na `Arguments` atribut.
