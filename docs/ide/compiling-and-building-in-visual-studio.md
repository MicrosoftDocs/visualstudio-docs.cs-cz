---
title: Kompilování sestavení
description: Přečtěte si, jak používat metodu sestavení integrovaného vývojového prostředí (IDE) sady Visual Studio, metodu sestavení nástrojů příkazového řádku MSBuild nebo Azure Pipelines metodu sestavení pro sestavení aplikace.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61abd28890fe92918c8ee2c9067820a781fac9c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970891"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilovat a sestavit v aplikaci Visual Studio

První Úvod do sestavení v rámci integrovaného vývojového prostředí naleznete v tématu [Návod: sestavování aplikace](walkthrough-building-an-application.md).

K sestavení aplikace můžete použít kteroukoli z následujících metod: integrované vývojové prostředí (IDE) sady Visual Studio, nástroje příkazového řádku MSBuild a Azure Pipelines:

| Metoda sestavení | Výhody |
| --- |--- | --- |
| IDE – integrované vývojové prostředí |– Vytvářejte sestavení hned a otestujte je v ladicím programu.<br />-Spustit víceprocesorové sestavení pro projekty v jazyce C++ a C#.<br />-Přizpůsobení různých aspektů systému sestavení. |
| CMake | – Sestavení projektů pomocí nástroje CMake<br />– Použijte stejný systém sestavení napříč platformami Linux a Windows. |
| Příkazový řádek nástroje MSBuild| -Sestavit projekty bez instalace sady Visual Studio.<br />-Spustit sestavení s více procesory pro všechny typy projektů.<br />-Přizpůsobit většinu oblastí systému sestavení.|
| Azure Pipelines | – Automatizujte proces sestavení jako součást kanálu průběžné integrace nebo průběžného doručování.<br />– Použít automatizované testy u každého sestavení.<br />– Využívat prakticky neomezené cloudové prostředky pro procesy sestavení.<br />– Upravte pracovní postup sestavení a vytvořte aktivity sestavení, abyste mohli provádět hluboko přizpůsobené úkoly.|

Dokumentace v této části se podrobněji popisuje procesu sestavení založeného na rozhraní IDE. Další informace o dalších metodách naleznete v části [MSBuild](../msbuild/msbuild.md) a [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)v uvedeném pořadí.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [kompilace a sestavování v Visual Studio pro Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Přehled sestavování z integrovaného vývojového prostředí

Při vytváření projektu aplikace Visual Studio vytvořila výchozí konfigurace sestavení pro projekt a řešení, které obsahuje projekt.  Tyto konfigurace definují, jak jsou řešení a projekty sestaveny a nasazeny. Konkrétní konfigurace projektu jsou jedinečné pro cílovou platformu (například Windows nebo Linux) a typ sestavení (například ladění nebo vydání). Tyto konfigurace můžete upravit tak, jak chcete, a také můžete podle potřeby vytvářet vlastní konfigurace.

První Úvod do sestavení v rámci integrovaného vývojového prostředí naleznete v tématu [Návod: sestavování aplikace](walkthrough-building-an-application.md).

Dále si přečtěte téma [sestavování a čištění projektů a řešení v aplikaci Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) , kde se dozvíte o různých přizpůsobeních aspektů, které můžete provádět v procesu. Vlastní nastavení zahrnuje [změnu výstupních adresářů](how-to-change-the-build-output-directory.md), [určení vlastních událostí sestavení](specifying-custom-build-events-in-visual-studio.md), [správu závislostí projektu](how-to-create-and-remove-project-dependencies.md), [správu souborů protokolu sestavení](how-to-view-save-and-configure-build-log-files.md)a [potlačení upozornění kompilátoru](how-to-suppress-compiler-warnings.md).

Odtud můžete prozkoumat celou řadu dalších úloh:
- [Vysvětlení konfigurací sestavení](understanding-build-configurations.md)
- [Vysvětlení platforem sestavení](understanding-build-platforms.md)
- [Spravovat vlastnosti projektu a řešení](managing-project-and-solution-properties.md).
- Zadejte události sestavení v [jazyce C#](how-to-specify-build-events-csharp.md) a [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Nastavit možnosti sestavení](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Viz také

- [Sestavení (kompilace) projektů webu](/previous-versions/hwxa5aha(v=vs.140))
- [Kompilovat a sestavovat (Visual Studio pro Mac)](/visualstudio/mac/compiling-and-building)
- [Projekty CMake v sadě Visual Studio](/cpp/build/cmake-projects-in-visual-studio)