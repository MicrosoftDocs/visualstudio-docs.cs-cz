---
title: Přizpůsobení sestavení ladění úloh pomocí souboru launch.vs.json tasks.vs.json
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca5a80c07cb64cfd638542da4e1deefe7e373b18
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342397"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Přizpůsobení sestavení a ladění úlohy pro vývoj "Otevřít složku"

Visual Studio ví, jak spustit mnoha různých jazycích a základů kódu, ale neví, jak spustit vše. Pokud jste [otevřít složku kód](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) v sadě Visual Studio a Visual Studio ví, jak spustit kód, můžete ji spustit okamžitě bez jakékoli dodatečné konfigurace.

Pokud základu kódu používá vlastní sestavovací nástroje, které Visual Studio nerozpozná, musíte zadat některé podrobnosti o konfiguraci ke spuštění a ladění kódu v sadě Visual Studio. Řekněte sady Visual Studio jak k sestavení vašeho kódu tak, že definujete *úlohy sestavení*. Můžete vytvořit jednu nebo více úloh zadat všechny položky, které jazyk je potřeba sestavit a spustit jeho kód sestavení. Můžete také vytvořit libovolné úlohy, které můžou provádět téměř všechno, co chcete. Můžete například vytvořit úkol pro vypsání obsahu složky nebo pokud chcete přejmenovat soubor.

Přizpůsobení vašeho projektu bez základu kódu s použitím následujících *.json* soubory:

|Název souboru|Účel|
|-|-|
|*tasks.vs.json*|Určení vlastního sestavení příkazy a přepínače kompilátoru a libovolného (bez sestavení související) úlohy.<br>K dispozici prostřednictvím **Průzkumník řešení** položky nabídky po kliknutí pravým tlačítkem myši **Konfigurovat úkoly**.|
|*launch.vs.json*|Zadejte argumenty příkazového řádku pro ladění.<br>K dispozici prostřednictvím **Průzkumník řešení** položky nabídky po kliknutí pravým tlačítkem myši na položku **nastavení ladění a spuštění**.|

Tyto *.json* soubory jsou umístěny ve skryté složce s názvem *.vs* v kořenové složce vašeho základu kódu. *Tasks.vs.json* a *souboru launch.vs.json* soubory jsou vytvořeny pomocí sady Visual Studio na základě potřeby, po výběru některé **nakonfigurovat úlohy** nebo **ladění Nastavení a spouštění** pro soubor nebo složku v **Průzkumníka řešení**. Tyto *.json* soubory jsou skryté, protože uživatelé zbytečné vrátit je do správy zdrojového kódu. Ale pokud chcete mít možnost zkontrolovat do správy zdrojového kódu, přetáhněte soubory v kořenové složce vašeho základu kódu, kde jsou viditelné.

> [!TIP]
> Chcete-li zobrazit skryté soubory v sadě Visual Studio, zvolte **zobrazit všechny soubory** tlačítko **Průzkumníka řešení** nástrojů.

## <a name="define-tasks-with-tasksvsjson"></a>Definovat úkoly pomocí tasks.vs.json

Můžete automatizovat skripty sestavení ani žádné jiné externí operace se soubory, které máte v aktuálním pracovním prostoru spuštěním jako úlohy přímo v integrovaném vývojovém prostředí. Vytvoření nového úkolu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a vyberete **nakonfigurovat úlohy**.

![Konfigurace nabídka úkoly](../ide/media/customize-configure-tasks-menu.png)

To vytvoří (nebo se otevře) *tasks.vs.json* ve *.vs* složky. V tomto souboru můžete definovat úlohu sestavení nebo libovolný úkol a potom ji vyvolat pomocí názvu, který jste zadali v nabídce **Průzkumník řešení** kliknutím pravým tlačítkem myši.

Vlastní úlohy se dají přidat pro jednotlivé soubory nebo pro všechny soubory určitého typu. Například soubory balíčku NuGet lze nakonfigurovat pro úkol "Packages obnovení", nebo všechny zdrojové soubory se dají konfigurovat mít statické analýzy úloh, jako je linter pro všechny *js* soubory.

### <a name="define-custom-build-tasks"></a>Definovat úkoly vlastního sestavení

Pokud vašeho základu kódu používá vlastní sestavovací nástroje, které Visual Studio nerozpozná, nelze spustit a ladit kód v sadě Visual Studio, dokud je provést některé kroky konfigurace. Visual Studio poskytuje *úlohy sestavení* poznáte sady Visual Studio, jak vytvářet, opětovné sestavení a vyčištění kódu. *Tasks.vs.json* sestavení souboru párům úloh vývoje vnitřní smyčky sady Visual Studio vlastního sestavení nástroje používané ve vašem základu kódu.

Vezměte v úvahu základu kódu, který se skládá z jedné C# soubor s názvem *hello.cs*. *Makefile* pro takové codebase může vypadat třeba takto:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Pro tento *makefile* , který obsahuje sestavení, vyčištění a znovu sestavte cíle, můžete definovat následující *tasks.vs.json* souboru. Obsahuje tři úlohy sestavení pro vytváření, opětovného sestavování a čištění základu kódu pomocí NMAKE jako nástroj pro sestavení.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Po definování úloh sestavení v *Tasks. vs. JSON*jsou do odpovídajících souborů v **Průzkumník řešení**přidány další nabídky pravým tlačítkem myši (kontextová nabídka) položek. V tomto příkladu "sestavení", "sestavení" a "Vyčištění" možnosti jsou přidány do kontextové nabídky žádné *makefile* soubory.

![místní nabídka souboru pravidel se sestavením, opětovné sestavení a vyčištění](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Příkazy se zobrazí v místní nabídce v části **nakonfigurovat úlohy** příkaz z důvodu jejich `contextType` nastavení. "sestavení", "sestavení" a "Vyčištění" jsou příkazy sestavení, takže se budou zobrazovat v části sestavení uprostřed v místní nabídce.

Když vyberete některou z těchto možností, spustí příslušný úkol. Výstup se zobrazí v **výstup** okno a chyby sestavení se zobrazí v **seznam chyb**.

### <a name="define-arbitrary-tasks"></a>Definujte libovolné úlohy

Můžete definovat libovolné úlohy v *tasks.vs.json* souboru prakticky cokoliv, které chcete provést. Například můžete definovat úkol, který zobrazí název aktuálně vybraného souboru v **výstup** okna, nebo seznam souborů v zadaném adresáři.

Následující příklad ukazuje *tasks.vs.json* soubor, který definuje jeden úkol. Při vyvolání, úloha zobrazuje název souboru z aktuálně vybraného *js* souboru.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` určuje název, který se zobrazí v nabídce kliknutím pravým tlačítkem myši.
- `appliesTo` Určuje soubory, které lze příkaz provést na.
- `command` Vlastnost určuje příkaz, který má být vyvolán. V tomto příkladu `COMSPEC` proměnné prostředí se používá k identifikaci překladač příkazového řádku, obvykle *cmd.exe*.
- `args` Vlastnost určuje argumenty, které mají být předány je volaný příkaz.
- `${file}` Makra obnoví na vybraný soubor na **Průzkumníka řešení**.

Po uložení *tasks.vs.json*, kliknete pravým tlačítkem na žádném *js* souboru ve složce a zvolte **Echo filename**. Zobrazí se v názvu souboru **výstup** okna.

> [!NOTE]
> Pokud neobsahuje vašeho základu kódu *tasks.vs.json* soubor, můžete vytvořit jednu bránu výběrem **nakonfigurovat úlohy** z klikněte pravým tlačítkem nebo místní nabídky souboru v **Průzkumníka řešení**.

Následující příklad definuje úlohu, která obsahuje soubory a podsložky *bin* adresáře.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` je definován vlastní makro, které je první před `tasks` bloku. Potom je volána `args` vlastnost.

Tato úloha se vztahuje na všechny soubory. Když otevřete místní nabídku na jakýkoli soubor v **Průzkumníka řešení**, název úkolu **seznamu výstupy** se zobrazí v dolní části nabídky. Při výběru **seznamu výstupy**, obsah *bin* adresáře jsou uvedeny v **výstup** okna v sadě Visual Studio.

![Libovolné úlohy v kontextové nabídce](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Nastavení oboru

Více *tasks.vs.json* soubory mohou existovat v kořenové a podadresářů základ kódu. Tento návrh umožňuje flexibilitu pro různé chování v různých podadresáře základu kódu. Visual Studio agreguje nebo přepíše nastavení v celém základu kódu, určování priority soubory v následujícím pořadí:

- Soubory nastavení v kořenové složce *.vs* adresáře.
- Adresář, ve kterém se počítá nastavení.
- Nadřazený adresář aktuálního adresáře, až do kořenového adresáře.
- Soubory nastavení v kořenovém adresáři.

Tato pravidla agregace platí pro *Tasks. vs. JSON*. Informace o tom, jak se agregují nastavení v jiném souboru naleznete v části odpovídající pro tento soubor v tomto článku.

### <a name="properties-for-tasksvsjson"></a>Vlastnosti pro tasks.vs.json

Tato část popisuje některé z vlastností můžete zadat v *tasks.vs.json*.

#### <a name="appliesto"></a>AppliesTo –

Můžete vytvářet úkoly pro kterýkoli soubor nebo složku tak, že zadáte jeho název `appliesTo` pole, například `"appliesTo": "hello.js"`. Následující masky souboru můžete použít jako hodnoty:

|||
|-|-|
|`"*"`| Úloha je k dispozici pro všechny soubory a složky v pracovním prostoru|
|`"*/"`| Úloha je dostupná pro všechny složky v pracovním prostoru|
|`"*.js"`| Úloha je dostupná pro všechny soubory s příponou *js* v pracovním prostoru|
|`"/*.js"`| Úloha je dostupná pro všechny soubory s příponou *js* v kořenu pracovního prostoru|
|`"src/*/"`| Úloha je k dispozici pro všechny podsložky *src* složky|
|`"makefile"`| Úloha je k dispozici všem *makefile* souborům v pracovním prostoru|
|`"/makefile"`| Úloha je k dispozici pouze *makefile* v kořenu pracovního prostoru|

#### <a name="macros-for-tasksvsjson"></a>Makra pro tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Určuje všechny proměnné prostředí (např. ${env. PATH}, ${env.COMSPEC} a tak dále), která je nastavena pro příkazový řádek pro vývojáře. Další informace najdete v tématu [příkazový řádek pro vývojáře pro sadu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru (například *C:\sources\hello*)|
|`${file}`| Úplná cesta k souboru nebo složky vybrané ke spuštění této úlohy před (například *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Relativní cesta k souboru nebo složky (například *src\hello.js*)|
|`${fileBasename}`| Název souboru bez cesty a přípony (například *hello*)|
|`${fileDirname}`| Úplná cesta k souboru, s výjimkou názvu souboru (například *C:\sources\hello\src*)|
|`${fileExtname}`| Rozšíření na vybraný soubor (například *js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurovat ladění pomocí launch.vs.json

1. Ke konfiguraci vašeho základu kódu pro ladění, v **Průzkumníka řešení** zvolte **nastavení ladění a spouštění** položky nabídky v nabídce klepněte pravým tlačítkem nebo kontextu spustitelný soubor.

   ![Kontextové nabídky nastavení ladění a spouštění](media/customize-debug-launch-menu.png)

1. V **vyberte ladicí program** dialogové okno, vyberte možnost a klikněte na tlačítko **vyberte** tlačítko.

   ![Vyberte dialogového okna ladicího programu](media/customize-select-a-debugger.png)

   Pokud *souboru launch.vs.json* soubor již neexistuje, vytvoří se.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Pak klikněte pravým tlačítkem na spustitelný soubor ve **Průzkumníka řešení**a zvolte **nastavit jako položku při spuštění**.

   Spustitelný soubor je určený jako položku při spuštění vašeho základu kódu a ladění **Start** změny názvu tlačítka tak, aby odrážely název spustitelný soubor.

   ![Vlastní tlačítka Start](media/customize-start-button.png)

   Pokud zvolíte **F5**, ladicí program se spustí a zastaví na zarážce, všechny možná jste už nastavili. Všechny známé ladicí program systému windows jsou dostupné a funkční.

   > [!IMPORTANT]
   > Další podrobnosti o vlastních úkolech sestavení a ladění v C++ projektech otevřených složek naleznete v tématu [Podpora otevřených složek C++ pro systémy sestavení v aplikaci Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Zadejte argumenty pro ladění

Můžete zadat argumenty příkazového řádku a zajistěte tak předání pro ladění *souboru launch.vs.json* souboru. Přidání argumentů `args` pole, jak je znázorněno v následujícím příkladu:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Při ukládání tohoto souboru se zobrazí název nové konfigurace v rozevíracím seznamu cíl ladění a vyberte spuštění ladicího programu. Můžete vytvořit mnoho konfiguraci ladění, kolik chcete.

![Ladění konfigurace rozevíracího seznamu](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` Pole vlastnosti v *souboru launch.vs.json* číst ze dvou umístění souboru&mdash;kořenový adresář pro základ kódu a *.vs* adresáře. Pokud dojde ke konfliktu, Priorita se určuje na hodnotu v *.vs\launch.vs.json*.

## <a name="additional-settings-files"></a>Další nastavení soubory

Kromě tři *.json* soubory popsané v tomto tématu, Visual Studio také načte nastavení z některé další soubory, pokud existují ve vašem základu kódu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio načte omezená nastavení ze souboru s názvem *settings.json*, pokud se nachází v adresáři s názvem *.vscode*. Tato funkce je poskytována pro základů kódu, které dřív byly vyvinuty ve Visual Studio Code. V současné době jediným nastavením, který je čten *.vscode\settings.json* je `files.exclude`, který filtruje soubory vizuálně v Průzkumníku řešení a z některé vyhledávací nástroje.

Můžete mít libovolný počet *.vscode\settings.json* soubory ve vašem základu kódu. Čtení z tohoto souboru nastavení se použijí pro nadřazený adresář složky *.vscode* a všech jeho podadresářích.

### <a name="gitignore"></a>.gitignore

*.gitignore* soubory se používají k řekněte Git soubory, které se mají ignorovat; to znamená, které soubory a adresáře nechcete k vrácení se změnami. *.gitignore* soubory jsou obvykle součástí základ kódu tak, aby všichni vývojáři základu kódu můžou sdílet nastavení. Visual Studio načte vzory v *.gitignore* soubory pro filtrování položek vizuálně a z některé vyhledávací nástroje.

Čtení nastavení z *.gitignore* souboru se použijí u svého nadřazeného adresáře a všech podadresářích.

## <a name="see-also"></a>Viz také:

- [Vývoj kódu bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Otevřete složku projekty jazyka C++](/cpp/build/open-folder-projects-cpp)
- [Projekty CMake proC++](/cpp/build/cmake-projects-in-visual-studio)
- [NMake – odkaz](/cpp/build/reference/nmake-reference)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
