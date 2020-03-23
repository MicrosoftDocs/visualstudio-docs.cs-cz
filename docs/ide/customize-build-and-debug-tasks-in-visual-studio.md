---
title: Přizpůsobení úloh ladění sestavení pomocí tasks.vs.json launch.vs.json
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
ms.openlocfilehash: e912459f45086b1bf5f96a9458f006354e982ffd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542682"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Přizpůsobení úloh sestavení a ladění pro vývoj "Otevřít složku"

Visual Studio ví, jak spustit mnoho různých jazyků a základy kódu, ale neví, jak spustit všechno. Pokud jste [otevřeli složku kódu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) v sadě Visual Studio a Visual Studio ví, jak spustit kód, můžete jej spustit ihned bez jakékoli další konfigurace.

Pokud základ kódu používá vlastní nástroje sestavení, které Visual Studio nerozpozná, je třeba zadat některé podrobnosti konfigurace ke spuštění a ladění kódu v sadě Visual Studio. Pokyn Visual Studio, jak vytvořit kód definováním *úlohsestavení*. Můžete vytvořit jeden nebo více úloh sestavení k určení všech položek, které jazyk potřebuje k sestavení a spuštění kódu. Můžete také vytvořit libovolné úkoly, které mohou dělat téměř cokoliv chcete. Můžete například vytvořit úkol, který zobrazí seznam obsahu složky nebo přejmenuje soubor.

Přizpůsobte si základ kódu bez projektu pomocí následujících souborů *JSON:*

|Název souboru|Účel|
|-|-|
|*tasks.vs.json*|Zadejte vlastní příkazy sestavení a přepínače kompilátoru a libovolné (nesouvisející) úkoly.<br>Přístup prostřednictvím **Průzkumníka řešení** klepněte pravým tlačítkem myši na položku nabídky **Konfigurovat úkoly**.|
|*launch.vs.json*|Zadejte argumenty příkazového řádku pro ladění.<br>Přístup prostřednictvím **Průzkumníka řešení** klepněte pravým tlačítkem myši na položku **nabídky Ladění a Nastavení spouštění**.|

Tyto soubory *JSON* jsou umístěny ve skryté složce s názvem *.vs* v kořenové složce základu kódu. Soubory *tasks.vs.json* a *launch.vs.json* jsou vytvořeny aplikací Visual Studio podle potřeby, když zvolíte **možnost Konfigurovat úlohy** nebo Ladění a nastavení **spuštění** v souboru nebo složce v **Průzkumníku řešení**. Tyto *soubory JSON* jsou skryté, protože uživatelé je obecně nechtějí zařazovat do správy zdrojového kódu. Pokud je však chcete mít možnost zkontrolovat do správy zdrojového kódu, přetáhněte soubory do kořenového adresáře základu kódu, kde jsou viditelné.

> [!TIP]
> Chcete-li zobrazit skryté soubory v sadě Visual Studio, zvolte tlačítko **Zobrazit všechny soubory** na panelu nástrojů **Průzkumníka řešení.**

## <a name="define-tasks-with-tasksvsjson"></a>Definování úkolů pomocí souboru tasks.vs.json

Můžete automatizovat vytvářet skripty nebo jiné externí operace na soubory, které máte v aktuálním pracovním prostoru spuštěním je jako úlohy přímo v ide. Nový úkol můžete nakonfigurovat tak, že kliknete pravým tlačítkem myši na soubor nebo složku a vyberete **konfigurovat úkoly**.

![Nabídka Konfigurovat úkoly](../ide/media/customize-configure-tasks-menu.png)

Tím se vytvoří (nebo otevře) soubor *tasks.vs.json* ve složce *.vs.* V tomto souboru můžete definovat úlohu sestavení nebo libovolnou úlohu a potom ji vyvolat pomocí názvu, který jste mu přiřadili z nabídky pravým tlačítkem myši **Průzkumníka řešení.**

Vlastní úkoly lze přidat do jednotlivých souborů nebo do všech souborů určitého typu. Například soubory balíčků NuGet mohou být nakonfigurovány tak, aby měly úlohu "Obnovit balíčky", nebo všechny zdrojové soubory mohou být nakonfigurovány tak, aby měly úlohu statické analýzy, například linter pro všechny soubory *JS.*

### <a name="define-custom-build-tasks"></a>Definování vlastních úloh sestavení

Pokud váš základ kódu používá vlastní nástroje sestavení, které Visual Studio nerozpozná, pak nelze spustit a ladit kód v sadě Visual Studio, dokud nedokončíte některé kroky konfigurace. Visual Studio poskytuje *úlohy sestavení,* kde můžete aplikaci Visual Studio sdělit, jak vytvořit, znovu sestavit a vyčistit kód. *Task.vs.json* sestavení soubor úlohy páry Visual Studio vnitřní vývoj smyčky vlastní sestavení nástroje používané codebase.

Zvažte základ kódu, který se skládá z jednoho souboru Jazyka C# s názvem *hello.cs*. *Makefile* pro takový základ kódu může vypadat takto:

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

Pro takový *makefile,* který obsahuje cíle sestavení, čištění a opětovné sestavení, můžete definovat následující *soubor tasks.vs.json.* Obsahuje tři úlohy sestavení pro vytváření, opětovné sestavení a čištění základu kódu pomocí NMAKE jako nástroj sestavení.

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

Po definování úloh sestavení v *tasks.vs.json*budou další položky nabídky (kontextová nabídka) přidány do odpovídajících souborů v **Průzkumníku řešení**. V tomto příkladu "sestavení", "znovu sestavit" a "čisté" možnosti jsou přidány do kontextové nabídky všech souborů *makefile.*

![vytvořit kontextovou nabídku souboru pomocí sestavení, opětovného sestavení a čištění](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Příkazy se zobrazí v místní nabídce pod `contextType` příkazem **Konfigurovat úkoly** z důvodu jejich nastavení. "sestavení", "znovu sestavit" a "čisté" jsou příkazy sestavení, takže se zobrazí v části sestavení uprostřed kontextové nabídky.

Když vyberete jednu z těchto možností, úloha se provede. Výstup se zobrazí v okně **Výstup** a chyby sestavení se zobrazí v **seznamu chyb**.

### <a name="define-arbitrary-tasks"></a>Definování libovolných úkolů

Můžete definovat libovolné úkoly v souboru *tasks.vs.json,* abyste mohli dělat cokoli, co chcete. Můžete například definovat úkol, který zobrazí název aktuálně vybraného souboru v okně **Výstup** nebo zobrazí soubory v zadaném adresáři.

Následující příklad ukazuje soubor *tasks.vs.json,* který definuje jeden úkol. Při vyvolání se na úkolu zobrazí název souboru aktuálně vybraného souboru *JS.*

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

- `taskName`určuje název, který se zobrazí v nabídce po kliknutí pravým tlačítkem myši.
- `appliesTo`určuje, ve kterých souborech lze příkaz provádět.
- Vlastnost `command` určuje příkaz, který má být vyvolán. V tomto příkladu `COMSPEC` se proměnná prostředí používá k identifikaci interpretu příkazového řádku, obvykle *cmd.exe*.
- Vlastnost `args` určuje argumenty, které mají být předány příkazu vyvolána.
- Makro `${file}` načte vybraný soubor v **Průzkumníku řešení**.

Po uložení *souboru tasks.vs.json*můžete klepnout pravým tlačítkem myši na libovolný soubor *js* ve složce a zvolit **název souboru Echo**. Název souboru se zobrazí v okně **Výstup.**

> [!NOTE]
> Pokud váš základ kódu neobsahuje soubor *tasks.vs.json,* můžete jej vytvořit tak, že v **Průzkumníku řešení**zvolíte Konfigurovat **úkoly** klepnutím pravým tlačítkem nebo kontextovou nabídkou souboru .

V dalším příkladu je definován úkol, který obsahuje seznam souborů a podsložek adresáře *přihrádky.*

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

- `${outDir}`je vlastní makro, které je `tasks` nejprve definováno před blokem. To je pak `args` volána v majetku.

Tato úloha se vztahuje na všechny soubory. Když otevřete místní nabídku v libovolném souboru v **Průzkumníku řešení**, zobrazí se v dolní části nabídky název **seznamu výstupů úlohy.** Pokud zvolíte **Seznam výstupů**, obsah *adresáře bin* je uveden v okně **Výstup** v sadě Visual Studio.

![Libovolná úloha v kontextové nabídce](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Rozsah nastavení

V kořenovém adresáři a podadresářích základu kódu může existovat více souborů *tasks.vs.json.* Tento návrh umožňuje flexibilitu mít různé chování v různých podadresářích základu kódu. Visual Studio agreguje nebo přepíše nastavení v celém základu kódu a upřednostňuje soubory v následujícím pořadí:

- Nastavení souborů v adresáři *.vs* kořenové složky.
- Adresář, kde se počítá nastavení.
- Nadřazený adresář aktuálního adresáře až ke kořenovému adresáři.
- Nastavení souborů v kořenovém adresáři.

Tato pravidla agregace platí pro *tasks.vs.json*. Informace o tom, jak jsou agregována nastavení v jiném souboru, naleznete v odpovídající části tohoto souboru v tomto článku.

### <a name="properties-for-tasksvsjson"></a>Vlastnosti pro tasks.vs.json

Tato část popisuje některé vlastnosti, které můžete zadat v *tasks.vs.json*.

#### <a name="appliesto"></a>platíTo

Úkoly pro libovolný soubor nebo složku můžete vytvořit `appliesTo` například `"appliesTo": "hello.js"`zadáním názvu v poli , například . Jako hodnoty lze použít následující masky souborů:

|||
|-|-|
|`"*"`| úloha je k dispozici pro všechny soubory a složky v pracovním prostoru|
|`"*/"`| úloha je k dispozici pro všechny složky v pracovním prostoru|
|`"*.js"`| úloha je k dispozici všem souborům s příponou *JS* v pracovním prostoru|
|`"/*.js"`| úloha je k dispozici všem souborům s příponou *JS* v kořenovém adresáři pracovního prostoru|
|`"src/*/"`| úloha je k dispozici pro všechny podsložky složky *src*|
|`"makefile"`| úloha je k dispozici pro všechny soubory *makefile* v pracovním prostoru|
|`"/makefile"`| úloha je k dispozici pouze pro *makefile* v kořenovém adresáři pracovního prostoru|

#### <a name="macros-for-tasksvsjson"></a>Makra pro tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Určuje libovolnou proměnnou prostředí (například ${env. PATH}, ${env.COMSPEC} a tak dále), která je nastavena pro příkazový řádek vývojáře. Další informace naleznete v [tématu Developer command prompt pro Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru (například *C:\sources\hello*)|
|`${file}`| Úplná cesta k souboru nebo složce vybrané ke spuštění této úlohy (například *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Relativní cesta k souboru nebo složce (například *src\hello.js)*|
|`${fileBasename}`| Název souboru bez cesty nebo přípony (například *hello)*|
|`${fileDirname}`| Úplná cesta k souboru s výjimkou názvu souboru (například *C:\sources\hello\src*)|
|`${fileExtname}`| Rozšíření vybraného souboru (například *.js)*|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurace ladění pomocí souboru launch.vs.json

Chcete-li nakonfigurovat projekty CMake pro ladění, přečtěte si informace [o konfiguraci relací ladění CMake](/cpp/build/configure-cmake-debugging-sessions).

1. Chcete-li nakonfigurovat základ kódu pro ladění, zvolte v **Průzkumníku řešení** položku nabídky **Nastavení ladění a spuštění** z nabídky pravým tlačítkem nebo v místní nabídce spustitelného souboru.

   ![Deštěná a spouštěcí nabídka nastavení](media/customize-debug-launch-menu.png)

1. V **dialogovém okně Vybrat ladicí program** zvolte volbu a pak zvolte tlačítko **Vybrat.**

   ![Výběr dialogového okna Ladicí program](media/customize-select-a-debugger.png)

   Pokud soubor *launch.vs.json* ještě neexistuje, je vytvořen.

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

1. Dále klepněte pravým tlačítkem myši na spustitelný soubor v **Průzkumníku řešení**a zvolte **Nastavit jako položku po spuštění**.

   Spustitelný soubor je určen jako položka spuštění pro váš základ kódu a ladicí **tlačítko Start** se změní tak, aby odrážel název spustitelného souboru.

   ![Přizpůsobené tlačítko Start](media/customize-start-button.png)

   Pokud zvolíte **F5**, ladicí program se spustí a zastaví na libovolné zarážky, kterou jste již nastavili. Všechna známá okna ladicího programu jsou k dispozici a funkční.

   > [!IMPORTANT]
   > Další podrobnosti o vlastních úlohách sestavení a ladění v projektech otevřených složek jazyka C++ naleznete v [tématu Podpora otevřených složek pro systémy sestavení jazyka C++ v sadě Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Zadejte argumenty pro ladění

V souboru *launch.vs.json* můžete zadat argumenty příkazového řádku, které se mají předat pro ladění. Přidejte argumenty `args` do pole, jak je znázorněno v následujícím příkladu:

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

Když uložíte tento soubor, název nové konfigurace se zobrazí v rozevíracím seznamu ladění cíle a můžete jej vybrat a spustit ladicí program. Můžete vytvořit libovolný počet konfigurací ladění.

![Rozevírací seznam Ladicí konfigurace](media/customize-debug-configurations.png)

> [!NOTE]
> Vlastnost `configurations` pole v *souboru launch.vs.json* &mdash;se čte ze dvou umístění souborů, kořenového adresáře pro základ kódu a adresáře *.vs.* Pokud dojde ke konfliktu, je upřednostněna hodnota v *souboru .vs\launch.vs.json*.

## <a name="additional-settings-files"></a>Další soubory nastavení

Kromě tří *souborů JSON popsaných* v tomto tématu visual studio také čte nastavení z některých dalších souborů, pokud existují ve vašem základu kódu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio čte omezená nastavení ze souboru s názvem *settings.json*, pokud je v adresáři s názvem *.vscode*. Tato funkce je k dispozici pro základy kódu, které byly dříve vyvinuty v kódu sady Visual Studio. V současné době je `files.exclude`jediným nastavením, které je přečteno z *souboru .vscode\settings.json* , které filtruje soubory vizuálně v Průzkumníku řešení a z některých vyhledávacích nástrojů.

V základu kódu můžete mít libovolný počet souborů *.vscode\settings.json.* Nastavení čtení z tohoto souboru jsou použita pro nadřazený adresář *.vscode* a všechny jeho podadresáře.

### <a name="gitignore"></a>.gitignore

*Soubory .gitignore* se používají k sděluje Git, které soubory mají ignorovat; to znamená, které soubory a adresáře nechcete ohlásit. *Soubory .gitignore* jsou obvykle zahrnuty jako součást základu kódu, takže nastavení lze sdílet se všemi vývojáři codebase. Visual Studio čte vzorky v *souborech .gitignore* pro vizuální filtrování položek a z některých vyhledávacích nástrojů.

Nastavení přečtená ze souboru *.gitignore* se použijí na nadřazený adresář a všechny podadresáře.

## <a name="see-also"></a>Viz také

- [Vývoj kódu bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Projekty Otevřít složku pro C++](/cpp/build/open-folder-projects-cpp)
- [CMake projekty pro C++](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE – referenční zdroje](/cpp/build/reference/nmake-reference)
- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
