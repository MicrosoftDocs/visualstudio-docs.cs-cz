---
title: Sestavujte řešení vyčištění projektů
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05e8d13454ab9698ae855f1e937e85eb287a3a35
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057630"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Sestavování a čištění projektů a řešení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí postupů v tomto tématu můžete vytvářet, znovu sestavit nebo vyčistit všechny nebo některé projekty nebo položky projektu v řešení. Podrobný návod najdete v části [názorný postup: Tvorba aplikace](../ide/walkthrough-building-an-application.md).

> [!NOTE]
>  Uživatelské rozhraní v vaší edicí sady Visual Studio se mohou lišit od co toto téma popisuje, v závislosti na aktivních nastaveních. Chcete-li změnit nastavení, otevřete **nástroje** nabídky a klikněte na tlačítko **nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Pokud chcete vytvořit, znovu sestavit nebo vyčištění celé řešení

1.  V **Průzkumníka řešení**, zvolte nebo otevřete řešení.

2.  V panelu nabídky zvolte **sestavení**a pak vyberte jednu z následujících příkazů:

    -   Zvolte **sestavení** nebo **sestavit řešení** zkompilovat pouze ty soubory a komponenty, které se změnily od posledního sestavení projektu.

        > [!NOTE]
        >  **Sestavení** příkaz bude **sestavit řešení** Pokud řešení obsahuje více než jeden projekt.

    -   Zvolte **znovu sestavit řešení** "clean" řešení a následně vytvořit všechny soubory projektu a komponent.

    -   Zvolte **Vyčistit řešení** odstranit všechny pomocných a výstupních souborů. Pouze projekt a součást soubory vlevo nových instancí přechodný a výstupních souborů může pak být sestavena.

### <a name="to-build-or-rebuild-a-single-project"></a>Chcete-li sestavit nebo opětovně sestavit jeden projekt

1.  V **Průzkumníka řešení**, zvolte nebo otevřete projekt.

2.  V panelu nabídky zvolte **sestavení**a klikněte na tlačítko buď **sestavení**_ProjectName_ nebo **znovu sestavit**_ProjectName_.

    -   Zvolte **sestavení**_ProjectName_ sestavit pouze ty součásti, které se změnily od posledního sestavení projektu.

    -   Zvolte **znovu sestavit**_ProjectName_ "clean" projekt a pak vytvářet soubory projektu a všechny součásti projektu.

### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Sestavit pouze projekt po spuštění a jeho závislosti

1. V panelu nabídky zvolte **nástroje**, **možnosti**.

2. V **možnosti** dialogového okna rozbalte **projekty a řešení** uzel a klikněte na tlačítko **sestavíte a spustíte** stránky.

    **Sestavení a spuštění projektů a řešení, možnosti** zobrazí se dialogové okno.

3. Vyberte **pouze při spuštění sestavit projekty a závislosti** zaškrtávací políčko.

    Když je toto políčko zaškrtnuto, pouze aktuální spouštěcí projekt a jeho závislosti jsou vytvořeny při proveďte některý z následujících kroků:

   - V panelu nabídky zvolte **ladění**, **Start** (F5).

   - V panelu nabídky zvolte **sestavení**, **sestavit řešení** (CTRL + SHIFT + B).

     Když toto políčko zaškrtnuté, všechny projekty, jejich závislosti a soubory řešení jsou vytvořeny při spuštění některou z předchozích příkazů. Ve výchozím nastavení je toto políčko zaškrtnuté.

### <a name="to-build-only-the-selected-visual-c-project"></a>Sestavit jenom vybrané projektu Visual C++

1. Zvolte [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu a pak na panelu nabídek zvolte **sestavení**, **projektu pouze**a jeden z následujících příkazů:

   - **Jenom Build** *ProjectName*

   - **Znovu sestavit pouze** *ProjectName*

   - **Vyčistit pouze** *ProjectName*

   - **Pouze propojit** *ProjectName*

     Platí pouze pro tyto příkazy [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekt, který jste zvolili, bez vytváření, nové sestavení, čištění nebo propojení všechny závislosti projektu nebo soubory řešení. V závislosti na vaší verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **projektu pouze** podnabídky může obsahovat další příkazy.

### <a name="to-compile-multiple-c-project-items"></a>Chcete-li zkompilovat několik položek projektu C++

1.  V **Průzkumníka řešení**, zvolte více souborů, které mají mohou být zkompilovaný akce, otevřete místní nabídku pro jednu z těchto souborů a klikněte na tlačítko **kompilaci**.

     Pokud mají soubory závislosti, budou soubory zkompilovány v pořadí závislosti. Operace kompilace se nezdaří, pokud soubory vyžadují předkompilované hlavičky, která není k dispozici při kompilaci. Kompilace operace použije aktuální konfiguraci aktivního řešení.

### <a name="to-stop-a-build"></a>Zastavit sestavení

1.  Proveďte některý z následujících kroků:

    -   V panelu nabídky zvolte **sestavení**, **zrušit**.

    -   Zvolte Ctrl + Break klíče.

## <a name="see-also"></a>Viz také
 [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md) [získat protokoly o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) [kompilování a sestavování](../ide/compiling-and-building-in-visual-studio.md) [Principy konfigurace sestavení](../ide/understanding-build-configurations.md) [ Ladění a vydání konfigurace projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) [Reference sestavení C/C++](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [přepínače příkazového řádku nástroje Devenv](../ide/reference/devenv-command-line-switches.md) [řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
