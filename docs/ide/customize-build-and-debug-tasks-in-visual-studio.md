---
title: Přizpůsobení úloh ladění sestavení pomocí souborů JSON
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 795fbb099654c8b947c1c8e2941fad015a574717
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046227"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Přizpůsobení úloh sestavení a ladění pro vývoj "otevřít složku"

Visual Studio ví, jak spustit mnoho různých jazyků a základů kódu, ale neví, jak spustit vše. Pokud jste [otevřeli složku kódu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) v aplikaci Visual Studio a Visual Studio ví, jak váš kód spustit, můžete jej spustit hned bez jakékoli další konfigurace.

Pokud základ kódu používá vlastní nástroje sestavení, které Visual Studio nerozpozná, je nutné zadat některé podrobnosti o konfiguraci pro spuštění a ladění kódu v aplikaci Visual Studio. Aplikaci Visual Studio určíte, jak sestavit kód definováním *úloh sestavení* . Můžete vytvořit jednu nebo více úloh sestavení pro určení všech položek, které jazyk potřebuje k sestavení a spuštění kódu. Můžete také vytvořit libovolný úkol, který může dělat téměř cokoli, co potřebujete. Můžete například vytvořit úlohu pro vypsání obsahu složky nebo přejmenování souboru.

Přizpůsobte základ kódu bez projektu pomocí následujících souborů *. JSON* :

|Název souboru|Účel|
|-|-|
|*tasks.vs.jsna*|Zadejte vlastní příkazy sestavení a přepínače kompilátoru a libovolné úlohy (které nejsou související s sestavením).<br>K dispozici prostřednictvím **Průzkumník řešení** položky nabídky po kliknutí pravým tlačítkem myši **Konfigurovat úkoly** .|
|*launch.vs.jsna*|Zadejte argumenty příkazového řádku pro ladění.<br>K dispozici prostřednictvím **Průzkumník řešení** položky nabídky po kliknutí pravým tlačítkem myši na položku **nastavení ladění a spuštění** .|

Tyto soubory *. JSON* se nacházejí ve skryté složce s názvem *. vs* v kořenové složce vašeho základu kódu. *tasks.vs.js* a *launch.vs.jsna* soubory jsou vytvořeny v aplikaci Visual Studio podle potřeby, když zvolíte buď **konfiguraci úloh** , nebo **nastavení ladění a spouštění** pro soubor nebo složku v **Průzkumník řešení** . Tyto soubory *. JSON* jsou skryté, protože uživatelé je obvykle nechtějí kontrolovat do správy zdrojového kódu. Pokud však chcete být schopni je vrátit do správy zdrojového kódu, přetáhněte soubory do kořenového adresáře základů kódu, kde jsou viditelné.

> [!TIP]
> Chcete-li zobrazit skryté soubory v sadě Visual Studio, klikněte na tlačítko **Zobrazit všechny soubory** na panelu nástrojů **Průzkumník řešení** .

## <a name="define-tasks-with-tasksvsjson"></a>Definovat úkoly s tasks.vs.jsna

Můžete automatizovat skripty sestavení nebo jiné externí operace se soubory, které máte v aktuálním pracovním prostoru, a to tak, že je spustíte jako úkoly přímo v integrovaném vývojovém prostředí. Novou úlohu můžete nakonfigurovat tak, že kliknete pravým tlačítkem na soubor nebo složku a vyberete **Konfigurovat úlohy** .

![Nabídka konfigurovat úlohy](../ide/media/customize-configure-tasks-menu.png)

Tím se vytvoří (nebo otevře) *tasks.vs.js* v souboru ve složce *. vs* . V tomto souboru můžete definovat úlohu sestavení nebo libovolný úkol a potom ji vyvolat pomocí názvu, který jste zadali v nabídce **Průzkumník řešení** kliknutím pravým tlačítkem myši.

Vlastní úkoly lze přidat do jednotlivých souborů nebo do všech souborů určitého typu. Například soubory balíčku NuGet lze nakonfigurovat tak, aby měly úlohu obnovit balíčky, nebo všechny zdrojové soubory lze nakonfigurovat tak, aby měly úlohu statické analýzy, jako je například linter pro všechny soubory *. js* .

### <a name="define-custom-build-tasks"></a>Definovat vlastní úkoly sestavení

Pokud váš základ kódu používá nástroje pro vlastní sestavení, které Visual Studio nerozpozná, nemůžete spustit a ladit kód v aplikaci Visual Studio, dokud nedokončíte některé kroky konfigurace. Visual Studio poskytuje *úkoly sestavení* , kde můžete říct, jak Visual Studio sestavovat, znovu sestavit a vyčistit váš kód. *tasks.vs.jsv* souboru úlohy sestavení Couples smyčku vnitřního vývoje sady Visual Studio do vlastních nástrojů sestavení používaných vaším základem kódu.

Vezměte v úvahu základ kódu, který se skládá z jednoho souboru C# s názvem *Hello.cs* . *Soubor pravidel* pro takový základ kódu by mohl vypadat takto:

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

Pro takový soubor *pravidel* , který obsahuje cíle sestavení, vyčištění a opětovného sestavení, můžete v souboru definovat následující *tasks.vs.js* . Obsahuje tři úlohy sestavení pro sestavování, opětovné sestavení a mazání základu kódu pomocí nástroje NMAKE jako nástroj sestavení.

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

Po definování úloh sestavení v *tasks.vs.jszapnuta* se další položky nabídky po kliknutí pravým tlačítkem myši (kontextová nabídka) přidají do odpovídajících souborů v **Průzkumník řešení** . V tomto příkladu jsou možnosti "sestavení", "znovu sestavit" a "vyčistit" přidány do kontextové nabídky všech souborů *pravidel* .

![místní nabídka souboru pravidel pomocí sestavení, opětovného sestavení a vyčištění](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Příkazy se zobrazí v kontextové nabídce v příkazu **Konfigurovat úlohy** z důvodu jejich `contextType` nastavení. příkazy "Build", "znovu sestavit" a "vyčistit" jsou příkazy sestavení, takže se zobrazí v části Build uprostřed místní nabídky.

Když vyberete jednu z těchto možností, úloha se spustí. Výstup se zobrazí v okně **výstup** a chyby sestavení se zobrazí v **Seznam chyb** .

### <a name="define-arbitrary-tasks"></a>Definovat libovolné úlohy

Můžete definovat libovolné úkoly v *tasks.vs.js* souboru, abyste mohli přesně dělat cokoli, co potřebujete. Můžete například definovat úkol pro zobrazení názvu aktuálně vybraného souboru v okně **výstup** nebo zobrazit seznam souborů v zadaném adresáři.

Následující příklad ukazuje *tasks.vs.jsv* souboru, který definuje jeden úkol. Při vyvolání úlohy se zobrazí název souboru aktuálně vybraného souboru *. js* .

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

- `taskName` Určuje název, který se zobrazí v nabídce kliknutím pravým tlačítkem myši.
- `appliesTo` Určuje, na kterých souborech lze příkaz provést.
- `command`Vlastnost určuje příkaz, který se má vyvolat. V tomto příkladu `COMSPEC` je proměnná prostředí používána k identifikaci překladače příkazového řádku, obvykle *cmd.exe* .
- `args`Vlastnost určuje argumenty, které mají být předány vyvolanému příkazu.
- `${file}`Makro načte vybraný soubor v **Průzkumník řešení** .

Po uložení *tasks.vs.js* můžete kliknout pravým tlačítkem na libovolný soubor *. js* ve složce a zvolit příkaz **echo název_souboru** . Název souboru se zobrazí v okně **výstup** .

> [!NOTE]
> Pokud váš základ kódu neobsahuje *tasks.vs.jspro* soubor, můžete ho vytvořit kliknutím na možnost **Konfigurovat úlohy** v místní nabídce nebo v místní nabídce souboru v **Průzkumník řešení** .

V následujícím příkladu je definován úkol, který obsahuje seznam souborů a podsložek adresáře *bin* .

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

- `${outDir}` je vlastní makro, které je nejprve definováno před `tasks` blokem. Pak je volána ve `args` Vlastnosti.

Tato úloha se vztahuje na všechny soubory. Když otevřete kontextovou nabídku libovolného souboru v **Průzkumník řešení** , zobrazí se v dolní části nabídky **výstupy v seznamu** název úkolu. Když zvolíte **výstupy seznamu** , obsah adresáře *bin* je uveden v okně **výstup** v aplikaci Visual Studio.

![Libovolný úkol v místní nabídce](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Rozsah nastavení

V kořenu a podadresáři základu kódu může existovat více *tasks.vs.js* souborů. Tento návrh umožňuje, aby flexibilita měla různé chování v různých podadresářích základu kódu. Visual Studio agreguje nebo přepisuje nastavení v celém základu kódu a určuje prioritu souborů v následujícím pořadí:

- Soubory nastavení v adresáři *. vs* kořenové složky.
- Adresář, ve kterém se počítá nastavení
- Nadřazený adresář aktuálního adresáře, a to až do kořenového adresáře.
- Soubory nastavení v kořenovém adresáři.

Tato pravidla agregace platí pro *tasks.vs.jsna* . Informace o tom, jak jsou nastavení v jiném souboru agregovaná, najdete v odpovídající části tohoto souboru v tomto článku.

### <a name="properties-for-tasksvsjson"></a>Vlastnosti pro tasks.vs.jsv

V této části jsou popsány některé vlastnosti, které lze zadat v *tasks.vs.js* .

#### <a name="appliesto"></a>appliesTo

Můžete vytvořit úkoly pro libovolný soubor nebo složku zadáním jejího názvu do `appliesTo` pole, například `"appliesTo": "hello.js"` . Následující masky souborů lze použít jako hodnoty:

|Maska souboru|Description|
|-|-|
|`"*"`| úloha je dostupná pro všechny soubory a složky v pracovním prostoru.|
|`"*/"`| úloha je dostupná pro všechny složky v pracovním prostoru.|
|`"*.js"`| úloha je dostupná pro všechny soubory s příponou *. js* v pracovním prostoru.|
|`"/*.js"`| úloha je dostupná pro všechny soubory s příponou *. js* v kořenu pracovního prostoru.|
|`"src/*/"`| úloha je k dispozici pro všechny podsložky složky *Src* .|
|`"makefile"`| úloha je k dispozici pro všechny soubory souborů *pravidel* v pracovním prostoru.|
|`"/makefile"`| úloha je k dispozici pouze pro *soubor pravidel* v kořenovém adresáři pracovního prostoru.|

#### <a name="macros-for-tasksvsjson"></a>Makra pro tasks.vs.jsv

|Podokně|Description|
|-|-|
|`${env.<VARIABLE>}`| Určuje libovolnou proměnnou prostředí (například $ {env. CESTA}, $ {env. COMSPEC} atd.), která je nastavena pro příkazový řádek vývojáře. Další informace naleznete v tématu [Developer Command Prompt for Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru (například *C:\sources\hello* )|
|`${file}`| Úplná cesta k souboru nebo složce vybrané ke spuštění této úlohy (například *C:\sources\hello\src\hello.js* )|
|`${relativeFile}`| Relativní cesta k souboru nebo složce (například *src\hello.js* )|
|`${fileBasename}`| Název souboru bez cesty nebo přípony (například *Hello* )|
|`${fileDirname}`| Úplná cesta k souboru s výjimkou názvu souboru (například *C:\sources\hello\src* )|
|`${fileExtname}`| Přípona vybraného souboru (například  *. js* )|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurace ladění pomocí launch.vs.js

Informace o konfiguraci projektů CMake pro ladění najdete v tématu [Konfigurace relací ladění cmake](/cpp/build/configure-cmake-debugging-sessions).

1. Chcete-li konfigurovat základ pro ladění, v **Průzkumník řešení** vyberte položku nabídky **nastavení ladění a spuštění** v místní nabídce nebo v místní nabídce spustitelného souboru.

   ![Místní nabídka nastavení ladění a spuštění](media/customize-debug-launch-menu.png)

1. V dialogovém okně **Vybrat ladicí program** zvolte možnost a pak klikněte na tlačítko **Vybrat** .

   ![Dialogové okno pro výběr ladicího programu](media/customize-select-a-debugger.png)

   Pokud *launch.vs.jsv* souboru ještě neexistuje, vytvoří se.

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

1. Potom klikněte pravým tlačítkem na spustitelný soubor v **Průzkumník řešení** a vyberte **nastavit jako položku po spuštění** .

   Spustitelný soubor je určen jako spouštěcí položka pro základ kódu a název tlačítka **Spustit** ladění se změní tak, aby odrážel název spustitelného souboru.

   ![Přizpůsobené tlačítko Start](media/customize-start-button.png)

   Když zvolíte **F5** , ladicí program se spustí a zastaví na jakékoli zarážce, kterou jste už mohli nastavit. Všechna známá okna ladicího programu jsou k dispozici a funkční.

   > [!IMPORTANT]
   > Další podrobnosti o vlastních úkolech sestavení a ladění v projektech otevřených složek C++ naleznete v tématu [Podpora otevření složky pro systémy sestavení c++ v aplikaci Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Zadat argumenty pro ladění

Můžete zadat argumenty příkazového řádku, které se mají předat pro ladění v *launch.vs.js* souboru. Přidejte argumenty v poli `args` , jak je znázorněno v následujícím příkladu:

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

Při uložení tohoto souboru se název nové konfigurace zobrazí v rozevíracím seznamu cíl ladění a můžete ho vybrat ke spuštění ladicího programu. Můžete vytvořit tolik konfigurací ladění, kolik budete chtít.

![Rozevírací seznam konfigurace ladění](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations`Vlastnost Array v *launch.vs.jszapnutá* je čtena ze dvou umístění souboru &mdash; kořenovým adresářem pro základ kódu a adresářem *. vs* . Pokud dojde ke konfliktu, je hodnota priorita dána hodnotě v *.vs\launch.vs.js* .

## <a name="additional-settings-files"></a>Další soubory nastavení

Kromě tří souborů *. JSON* popsaných v tomto tématu Visual Studio také přečte nastavení z některých dalších souborů, pokud existují ve vašem základu kódu.

### <a name="vscodesettingsjson"></a>.vscode\settings.jsna

Visual Studio čte omezené nastavení ze souboru s názvem *settings.jsv* , pokud se nachází v adresáři s názvem *. VSCode* . Tato funkce je k dispozici pro základy kódu, které byly dříve vyvinuty v Visual Studio Code. V současné době jediné nastavení, které je čteno z *.vscode\settings.js* `files.exclude` , je, které filtruje soubory vizuálně v Průzkumník řešení a z některých nástrojů pro hledání.

Ve vašem základu kódu můžete mít libovolný počet *.vscode\settings.js* souborů. Nastavení číst z tohoto souboru se aplikují na nadřazený adresář *. VSCode* a všechny jeho podadresáře.

### <a name="gitignore"></a>.gitignore

soubory *. gitignore* slouží k oznámení Gitu, které soubory se mají ignorovat; To znamená, které soubory a adresáře nechcete vrátit se změnami. soubory *. gitignore* jsou obvykle zahrnuty jako součást základu kódu, aby bylo možné sdílet nastavení se všemi vývojáři základního kódu. Visual Studio čte vzory v souborech *. gitignore* , aby bylo možné filtrovat položky vizuálně a z některých nástrojů pro hledání.

Nastavení číst ze souboru *. gitignore* se aplikují na svůj nadřazený adresář a všechny podadresáře.

## <a name="see-also"></a>Viz také

- [Vývoj kódu bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Projekty Otevřít složku pro C++](/cpp/build/open-folder-projects-cpp)
- [Projekty CMake pro C++](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE – referenční zdroje](/cpp/build/reference/nmake-reference)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
