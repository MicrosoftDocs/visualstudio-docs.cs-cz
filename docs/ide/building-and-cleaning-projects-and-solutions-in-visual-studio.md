---
title: Sestavování a čištění projektů a řešení
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1cf71abb19f6d4a3a459b4e5559e536f18f41c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114555"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Vytváření a čištění projektů a řešení v sadě Visual Studio

Pomocí postupů v tomto tématu můžete vytvořit, znovu sestavit nebo vyčistit všechny nebo některé projekty nebo položky projektu v řešení. Podrobný kurz najdete v [tématu Návod: Vytváření aplikace](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete v [tématu Vytváření a čištění projektů a řešení v Visual Studiu pro Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> V závislosti na aktivním nastavení se může použití hlavního nastavení ve vaší edici sady Visual Studio lišit od toho, co popisuje toto téma. Chcete-li změnit nastavení, například **na Obecné** nebo Vizuální **nastavení c++,** zvolte **Nástroje** > **Import a export nastavení**a pak zvolte Obnovit všechna **nastavení**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Vytvoření, opětovné sestavení nebo čištění celého řešení

1. V **Průzkumníku řešení**zvolte nebo otevřete řešení.

2. Na řádku nabídek zvolte **Sestavit**a pak zvolte jeden z následujících příkazů:

    - Zvolte **Sestavení** nebo **sestavení řešení** zkompilovat pouze ty soubory projektu a součásti, které se změnily od posledního sestavení.

        > [!NOTE]
        > Sestavení **Build** příkaz ustane **sestavení řešení,** pokud řešení obsahuje více než jeden projekt.

    - Zvolte **znovu sestavit řešení** "vyčistit" řešení a pak vytvořit všechny soubory projektu a součásti.

    - Zvolte **Čisté řešení,** chcete-li odstranit všechny zprostředkující a výstupní soubory. S pouze projekt a dílčí soubory vlevo, nové instance zprostředkující a výstupní soubory pak mohou být vytvořeny.

## <a name="to-build-or-rebuild-a-single-project"></a>Vytvoření nebo opětovné sestavení jednoho projektu

1. V **Průzkumníku řešení**zvolte nebo otevřete projekt.

2. Na řádku nabídek zvolte **Sestavení**a pak zvolte **Buď Vytvořit** *název projektu* nebo Znovu **sestavit** *název_projektu*.

    - Zvolte **Build** *ProjectName,* chcete-li vytvořit pouze ty součásti projektu, které se změnily od posledního sestavení.

    - Zvolte **Znovu sestavit** *název projektu* "vyčistit" projekt a potom vytvořit soubory projektu a všechny součásti projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Vytvoření pouze spouštěcího projektu a jeho závislostí

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. V dialogovém okně **Možnosti** rozbalte uzel **Projekty a řešení** a pak zvolte stránku **Sestavení a spuštění.**

     Otevře se dialogové okno**Možnosti** **sestavení a spuštění** > **projektů a řešení.** > 

3. Zaškrtněte políčko **Pouze spouštěcí projekty a závislosti na spouštění na spouštění.**

     Pokud je toto políčko zaškrtnuto, je při provedení některého z následujících kroků vytvořen pouze aktuální projekt při spuštění a jeho závislosti:

    - Na řádku nabídek zvolte Ladění > **úvodního** **(F5).** **Debug**

    - Na řádku nabídek zvolte **Build** > **Build Build Solution** **(Ctrl**+**Shift**+**B**).

    Pokud toto políčko není zaškrtnuto, jsou při spuštění některého z předchozích příkazů vytvořeny všechny projekty, jejich závislosti a soubory řešení. Ve výchozím nastavení je toto políčko zaškrtnuto.

## <a name="to-build-only-the-selected-visual-c-project"></a>Sestavení pouze vybraného projektu Visual C++

Vyberte [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt a potom na řádku nabídek zvolte **Build** > **Project Only**a jeden z následujících příkazů:

- **Název** *projektu* pouze pro sestavení

- **Vytvořit pouze** *název projektu*

- **Vyčistit pouze** *název_projektu*

- **Link Only** *Název projektu* pouze pro propojení

Tyto příkazy platí [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] pouze pro projekt, který jste zvolili, bez vytváření, opětovnésestavení, čištění nebo propojení závislostí projektu nebo souborů řešení. V závislosti na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]verzi aplikace může podnabídka **Pouze projekt** obsahovat více příkazů.

## <a name="to-compile-multiple-c-project-items"></a>Kompilace více položek projektu jazyka C++

V **Průzkumníku řešení**zvolte více souborů, které mají zkompilované akce, otevřete místní nabídku pro jeden z těchto souborů a pak zvolte **Kompilovat**.

Pokud soubory mají závislosti, soubory budou zkompilovány v pořadí závislostí. Operace kompilace se nezdaří, pokud soubory vyžadují předkompilované záhlaví, které není k dispozici při kompilaci. Operace kompilace používá aktuální konfiguraci aktivního řešení.

## <a name="to-stop-a-build"></a>Zastavení sestavení

Proveďte některý z následujících kroků:

- Na řádku nabídek vyberte **Zrušit sestavení** > **.**

- Stiskněte **klávesu Ctrl**+**Break**.

## <a name="see-also"></a>Viz také

- [Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilace a výstavba](../ide/compiling-and-building-in-visual-studio.md)
- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Postupy: Nastavení konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ odkaz na budovu](/cpp/build/reference/c-cpp-building-reference)
- [Přepínače příkazového řádku Devenv](../ide/reference/devenv-command-line-switches.md)
- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Vytváření a čištění projektů a řešení (Visual Studio pro Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
