---
title: Sestavování budovy
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b5f00b3e71f0deb15d6266640db39751f2ae22f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76269106"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilace a sestavení v sadě Visual Studio

První úvod do vytváření v rámci ide, naleznete v [tématu Návod: Vytváření aplikace](walkthrough-building-an-application.md).

K vytvoření aplikace můžete použít některou z následujících metod: IDE Visual Studio, nástroje příkazového řádku MSBuild a Kanály Azure:

| Metoda sestavení | Výhody |
| --- |--- | --- |
| IDE – integrované vývojové prostředí |- Vytvořte sestavení okamžitě a otestujte je v ladicím programu.<br />- Spusťte víceprocesorová sestavení pro projekty C++ a C#.<br />- Přizpůsobit různé aspekty systému sestavení. |
| CMake | - Vytváření projektů pomocí nástroje CMake<br />- Použijte stejný systém sestavení napříč platformami Linux a Windows. |
| Příkazový řádek MSBuild| - Vytvářejte projekty bez instalace sady Visual Studio.<br />- Spusťte víceprocesorová sestavení pro všechny typy projektů.<br />- Přizpůsobte většinu oblastí systému sestavení.|
| Azure Pipelines | - Automatizujte proces sestavení jako součást průběžné integrace / průběžného doručovacího kanálu.<br />- Použít automatizované testy s každým sestavením.<br />- Používejte prakticky neomezené cloudové prostředky pro procesy sestavení.<br />- Upravte pracovní postup sestavení a vytvořte aktivity sestavení k provádění hluboce přizpůsobených úkolů.|

Dokumentace v této části přejde do další podrobnosti o procesu sestavení založené na ide. Další informace o dalších metodách najdete v tématu [MSBuild](../msbuild/msbuild.md) a [Azure pipelines](/azure/devops/pipelines/index?view=vsts).

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Kompilace a sestavení ve Visual Studiu pro Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Přehled stavby z IDE

Při vytváření projektu Visual Studio vytvořilvýchozí konfigurace sestavení pro projekt a řešení, které obsahuje projekt.  Tyto konfigurace definují, jak jsou vytvořena a nasazena řešení a projekty. Konfigurace projektu jsou jedinečné pro cílovou platformu (například Windows nebo Linux) a typ sestavení (například ladění nebo vydání). Tyto konfigurace můžete upravit, jak chcete, a můžete také vytvořit vlastní konfigurace podle potřeby.

První úvod do vytváření v rámci ide, naleznete v [tématu Návod: Vytváření aplikace](walkthrough-building-an-application.md).

Dále najdete [v tématu vytváření a čištění projektů a řešení v sadě Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) se dozvíte o různých aspektech přizpůsobení, které můžete provést v procesu. Vlastní nastavení zahrnují [změnu výstupních adresářů](how-to-change-the-build-output-directory.md), [určení vlastních událostí sestavení](specifying-custom-build-events-in-visual-studio.md), [správu závislostí projektu](how-to-create-and-remove-project-dependencies.md), [správu souborů protokolu sestavení](how-to-view-save-and-configure-build-log-files.md)a potlačení upozornění [kompilátoru](how-to-suppress-compiler-warnings.md).

Odtud můžete prozkoumat řadu dalších úkolů:
- [Vysvětlení konfigurací sestavení](understanding-build-configurations.md)
- [Vysvětlení platforem sestavení](understanding-build-platforms.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md).
- Zadejte události sestavení v [jazyce C#](how-to-specify-build-events-csharp.md) a [visual basicu](how-to-specify-build-events-visual-basic.md).
- [Nastavení možností sestavení](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Vytvořte více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Viz také

- [Vytváření (kompilace) webových projektů](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Kompilace a sestavení (Visual Studio pro Mac)](/visualstudio/mac/compiling-and-building)
- [CMake projekty v sadě Visual Studio](/cpp/build/cmake-projects-in-visual-studio)
