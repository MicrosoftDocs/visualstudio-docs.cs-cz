---
title: Vytváření řešení čištění projektů
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f2817b6fd0aee312ff41af218d01ad80bc785e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620553"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Sestavování a čištění projektů a řešení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí postupů v tomto tématu můžete sestavit, znovu sestavit nebo vyčistit všechny nebo některé projekty nebo položky projektu v řešení. Podrobný kurz najdete v tématu [Návod: sestavování aplikace](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Uživatelské rozhraní ve vaší edici sady Visual Studio se může lišit od toho, co toto téma popisuje, v závislosti na aktivním nastavení. Chcete-li změnit nastavení, otevřete nabídku **nástroje** a pak zvolte **Nastavení importu a exportu**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

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

2. Na panelu nabídek zvolte možnost **sestavit**a pak zvolte možnost **sestavit** _ProjectName_ nebo **znovu sestavit** _ProjectName_.

    - Zvolením možnosti **sestavit** _ProjectName_ sestavíte pouze součásti projektu, které se od posledního sestavení změnily.

    - Zvolte možnost **znovu sestavit** _ProjectName_ do "vyčistit" projekt a pak Sestavte soubory projektu a všechny součásti projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Sestavení pouze spouštěného projektu a jeho závislostí

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. V dialogovém okně **Možnosti** rozbalte uzel **projekty a řešení** a potom zvolte stránku **sestavení a spuštění** .

    Otevře se dialogové okno **sestavení a spuštění, projekty a řešení, možnosti** .

3. Zaškrtněte políčko **sestavit projekty po spuštění a závislosti při spuštění** .

    Pokud je toto políčko zaškrtnuto, budou vytvořeny pouze aktuální spouštěné projekty a jejich závislosti, pokud provedete některý z následujících kroků:

   - Na panelu nabídek vyberte možnost **ladit**  > **Spustit ladění** (F5).

   - Na panelu nabídek vyberte **sestavení**  > **Sestavit řešení** (CTRL + SHIFT + B).

     Pokud je toto políčko zaškrtnuté, všechny projekty, jejich závislosti a soubory řešení jsou sestaveny při spuštění některého z předchozích příkazů. Ve výchozím nastavení je toto zaškrtávací políčko zrušeno.

## <a name="to-build-only-the-selected-visual-c-project"></a>Chcete-li vytvořit pouze vybraný C++ projekt Visual

1. Zvolte projekt [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] a pak na panelu nabídek zvolte možnost **sestavení**, **pouze projekt**a jeden z následujících příkazů:

   - **Sestavit pouze** *ProjectName*

   - **Opětovné sestavení pouze** *ProjectName*

   - **Vyčistit pouze** *ProjectName*

   - **Pouze propojit** *ProjectName*

     Tyto příkazy se vztahují pouze na [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekt, který jste zvolili, aniž byste museli sestavovat, znovu sestavovat, vyčistit nebo propojit všechny závislosti projektu nebo soubory řešení. V závislosti na vaší verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může podnabídka **pouze projekt** obsahovat více příkazů.

## <a name="to-compile-multiple-c-project-items"></a>Kompilace více C++ položek projektu

1. V **Průzkumník řešení**zvolte více souborů, které mají být kompilovány akce, otevřete místní nabídku pro jeden z těchto souborů a pak zvolte možnost **kompilovat**.

     Pokud jsou soubory závislé, budou soubory zkompilovány v pořadí závislostí. Operace kompilace se nezdaří, pokud soubory vyžadují předkompilovanou hlavičku, která není při kompilaci k dispozici. Operace kompilace používá aktuální aktivní konfiguraci řešení.

## <a name="to-stop-a-build"></a>Zastavení sestavení

1. Proveďte jeden z následujících kroků:

    - Na řádku nabídek klikněte na položku **sestavení**, **Zrušit**.

    - Vyberte klávesy CTRL + BREAK.

## <a name="see-also"></a>Viz také:
 [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md) [získávání](../msbuild/obtaining-build-logs-with-msbuild.md) [a sestavování](../ide/compiling-and-building-in-visual-studio.md) [porozumění konfiguracím sestavení](../ide/understanding-build-configurations.md) [ladění a vydávání konfigurací projektů](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) v jazyce [C/C++ sestavení ](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md) [přepínače příkazového řádku devenv](../ide/reference/devenv-command-line-switches.md)
