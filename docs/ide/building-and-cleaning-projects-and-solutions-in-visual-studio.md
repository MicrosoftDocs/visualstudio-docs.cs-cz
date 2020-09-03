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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114555"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Sestavování a čištění projektů a řešení v aplikaci Visual Studio

Pomocí postupů v tomto tématu můžete sestavit, znovu sestavit nebo vyčistit všechny nebo některé projekty nebo položky projektu v řešení. Podrobný kurz najdete v tématu [Návod: sestavování aplikace](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [sestavování a čištění projektů a řešení v Visual Studio pro Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Uživatelské rozhraní ve vaší edici sady Visual Studio se může lišit od toho, co toto téma popisuje, v závislosti na aktivním nastavení. Chcete-li změnit nastavení, například **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje**  >  **Nastavení importu a exportu**a pak zvolte možnost **resetovat všechna nastavení**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Sestavení, opětovné sestavení nebo vyčištění celého řešení

1. V **Průzkumník řešení**vyberte nebo otevřete řešení.

2. Na panelu nabídek zvolte možnost **sestavit**a pak zvolte jeden z následujících příkazů:

    - Vyberte **sestavení** nebo **Sestavit řešení** pro zkompilování pouze těch souborů projektu a komponent, které se od posledního sestavení změnily.

        > [!NOTE]
        > Příkaz **Build** se vytvoří **řešení sestavení** , když řešení obsahuje více než jeden projekt.

    - Zvolte **znovu sestavit řešení** pro vyčištění a pak Sestavte všechny soubory projektu a součásti.

    - Vyberte možnost **Vyčistit řešení** a odstraňte všechny mezilehlé a výstupní soubory. Pouze v případě, že zbývá pouze soubory projektu a součásti, lze sestavit nové instance zprostředkujících a výstupních souborů.

## <a name="to-build-or-rebuild-a-single-project"></a>Sestavení nebo opětovné sestavení jednoho projektu

1. V **Průzkumník řešení**vyberte nebo otevřete projekt.

2. Na panelu nabídek zvolte možnost **sestavit**a pak zvolte možnost **sestavit** *ProjectName* nebo **znovu sestavit** *ProjectName*.

    - Zvolením možnosti **sestavit** *ProjectName* sestavíte pouze součásti projektu, které se od posledního sestavení změnily.

    - Zvolte možnost **znovu sestavit** *ProjectName* do "vyčistit" projekt a pak Sestavte soubory projektu a všechny součásti projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Sestavení pouze spouštěného projektu a jeho závislostí

1. Na panelu nabídek vyberte **Tools**  >  **Možnosti**nástroje.

2. V dialogovém okně **Možnosti** rozbalte uzel **projekty a řešení** a potom zvolte stránku **sestavení a spuštění** .

     Otevře se dialogové okno **Sestavit a spustit**  >  **projekty a**  >  **Možnosti** řešení.

3. Zaškrtněte políčko  **sestavit projekty po spuštění a závislosti při spuštění** .

     Pokud je toto políčko zaškrtnuto, budou vytvořeny pouze aktuální spouštěné projekty a jejich závislosti, pokud provedete některý z následujících kroků:

    - Na řádku nabídek klikněte na tlačítko **Debug**  >  **Spustit ladění Start** (**F5**).

    - Na řádku nabídek klikněte na **sestavit**  >  **sestavení řešení** (**CTRL** + **SHIFT** + **B**).

    Pokud je toto políčko zaškrtnuté, všechny projekty, jejich závislosti a soubory řešení jsou sestaveny při spuštění některého z předchozích příkazů. Ve výchozím nastavení je toto políčko zaškrtnuto.

## <a name="to-build-only-the-selected-visual-c-project"></a>Chcete-li vytvořit pouze vybraný projekt Visual C++

Zvolte [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt a pak na panelu nabídek zvolte pouze **sestavit**  >  **projekt**a jeden z následujících příkazů:

- **Sestavit pouze** *ProjectName*

- **Opětovné sestavení pouze** *ProjectName*

- **Vyčistit pouze** *ProjectName*

- **Pouze propojit** *ProjectName*

Tyto příkazy se vztahují pouze na [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt, který jste zvolili, aniž byste museli sestavovat, znovu sestavovat, vyčistit nebo propojit všechny závislosti projektu nebo soubory řešení. V závislosti na vaší verzi nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může podnabídka **projektu** obsahovat více příkazů.

## <a name="to-compile-multiple-c-project-items"></a>Kompilace více položek projektu C++

V **Průzkumník řešení**zvolte více souborů, které mají být kompilovány akce, otevřete místní nabídku pro jeden z těchto souborů a pak zvolte možnost **kompilovat**.

Pokud jsou soubory závislé, budou soubory zkompilovány v pořadí závislostí. Operace kompilace se nezdaří, pokud soubory vyžadují předkompilovanou hlavičku, která není při kompilaci k dispozici. Operace kompilace používá aktuální aktivní konfiguraci řešení.

## <a name="to-stop-a-build"></a>Zastavení sestavení

Proveďte jeden z následujících kroků:

- Na panelu nabídek vyberte **vytvořit**  >  **Zrušit**.

- Stiskněte klávesu **CTRL** + **Break**.

## <a name="see-also"></a>Viz také

- [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilace a sestavování](../ide/compiling-and-building-in-visual-studio.md)
- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Postupy: Nastavení konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ – referenční dokumentace sestavení](/cpp/build/reference/c-cpp-building-reference)
- [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Sestavování a čištění projektů a řešení (Visual Studio pro Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
