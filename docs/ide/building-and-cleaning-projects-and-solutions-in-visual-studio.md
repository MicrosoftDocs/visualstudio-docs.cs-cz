---
title: Sestavování a čištění projektů a řešení
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c96a3b6699428b156a23ad643eb7958cb438b994
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349267"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Sestavení a vyčištění projektů a řešení v sadě Visual Studio

Pomocí postupů v tomto tématu můžete vytvářet, znovu sestavit nebo vyčistit všechny nebo některé projekty nebo položky projektu v řešení. Podrobný návod najdete v části [názorný postup: Tvorba aplikace](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [sestavení a vyčištění projektů a řešení v sadě Visual Studio pro Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Uživatelské rozhraní v vaší edicí sady Visual Studio se mohou lišit od co toto téma popisuje, v závislosti na aktivních nastaveních. Chcete-li změnit nastavení, například k **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje** > **nastavení importu a exportu**a klikněte na tlačítko **obnovit všechna nastavení**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pokud chcete vytvořit, znovu sestavit nebo vyčištění celé řešení

1.  V **Průzkumníka řešení**, zvolte nebo otevřete řešení.

2.  V panelu nabídky zvolte **sestavení**a pak vyberte jednu z následujících příkazů:

    -   Zvolte **sestavení** nebo **sestavit řešení** zkompilovat pouze ty soubory a komponenty, které se změnily od posledního sestavení projektu.

        > [!NOTE]
        > **Sestavení** příkaz bude **sestavit řešení** Pokud řešení obsahuje více než jeden projekt.

    -   Zvolte **znovu sestavit řešení** "clean" řešení a následně vytvořit všechny soubory projektu a komponent.

    -   Zvolte **Vyčistit řešení** odstranit všechny pomocných a výstupních souborů. Pouze projekt a součást soubory vlevo nových instancí přechodný a výstupních souborů může pak být sestavena.

## <a name="to-build-or-rebuild-a-single-project"></a>Chcete-li sestavit nebo opětovně sestavit jeden projekt

1.  V **Průzkumníka řešení**, zvolte nebo otevřete projekt.

2.  V panelu nabídky zvolte **sestavení**a klikněte na tlačítko buď **sestavení** *ProjectName* nebo **znovu sestavit** *ProjectName*.

    -   Zvolte **sestavení** *ProjectName* sestavit pouze ty součásti, které se změnily od posledního sestavení projektu.

    -   Zvolte **znovu sestavit** *ProjectName* "clean" projekt a pak vytvářet soubory projektu a všechny součásti projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Sestavit pouze projekt po spuštění a jeho závislosti

1.  V panelu nabídky zvolte **nástroje** > **možnosti**.

2.  V **možnosti** dialogového okna rozbalte **projekty a řešení** uzel a klikněte na tlačítko **sestavíte a spustíte** stránky.

     **Sestavíte a spustíte** > **projekty a řešení** > **možnosti** zobrazí se dialogové okno.

3.  Vyberte **pouze při spuštění sestavit projekty a závislosti** zaškrtávací políčko.

     Když je toto políčko zaškrtnuto, pouze aktuální spouštěcí projekt a jeho závislosti jsou vytvořeny při proveďte některý z následujících kroků:

    -   V panelu nabídky zvolte **ladění** > **Start** (**F5**).

    -   V panelu nabídky zvolte **sestavení** > **sestavit řešení** (**Ctrl**+**Shift** +  **B**).

    Když toto políčko zaškrtnuté, všechny projekty, jejich závislosti a soubory řešení jsou vytvořeny při spuštění některou z předchozích příkazů. Ve výchozím nastavení je toto políčko zaškrtnuté.

## <a name="to-build-only-the-selected-visual-c-project"></a>Sestavit jenom vybrané projektu Visual C++

Zvolte [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu a pak na panelu nabídek zvolte **sestavení** > **projektu pouze**a jeden z následujících příkazů:

- **Jenom Build** *ProjectName*

- **Znovu sestavit pouze** *ProjectName*

- **Vyčistit pouze** *ProjectName*

- **Pouze propojit** *ProjectName*

Platí pouze pro tyto příkazy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt, který jste zvolili, bez vytváření, nové sestavení, čištění nebo propojení všechny závislosti projektu nebo soubory řešení. V závislosti na vaší verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **projektu pouze** podnabídky může obsahovat další příkazy.

## <a name="to-compile-multiple-c-project-items"></a>Chcete-li zkompilovat několik položek projektu C++

V **Průzkumníka řešení**, zvolte více souborů, které mají mohou být zkompilovaný akce, otevřete místní nabídku pro jednu z těchto souborů a klikněte na tlačítko **kompilaci**.

Pokud mají soubory závislosti, budou soubory zkompilovány v pořadí závislosti. Operace kompilace se nezdaří, pokud soubory vyžadují předkompilované hlavičky, která není k dispozici při kompilaci. Kompilace operace použije aktuální konfiguraci aktivního řešení.

## <a name="to-stop-a-build"></a>Zastavit sestavení

Proveďte některý z následujících kroků:

- Na panelu nabídek vyberte **sestavení** > **zrušit**.

- Stisknutím klávesy **Ctrl**+**přerušit**.

## <a name="see-also"></a>Viz také:

- [Postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilování a sestavování](../ide/compiling-and-building-in-visual-studio.md)
- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Postupy: Nastavení konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md)
- [Reference sestavení C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Přepínače příkazového řádku nástroje devenv](../ide/reference/devenv-command-line-switches.md)
- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Sestavení a vyčištění projektů a řešení (Visual Studio for Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)