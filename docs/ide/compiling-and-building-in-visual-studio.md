---
title: Kompilace sestavení
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d583553c0382598681ab3aa52ca3a41a27ed2c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585493"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilace a sestavení v sadě Visual Studio

Při sestavování zdrojového kódu se jádro sestavení vytvoří sestavení a spustitelný soubor aplikace. Proces sestavení je obecně velmi podobné napříč mnoha různých typech projektů jako je například Windows, ASP.NET, mobilní aplikace a další. Proces sestavení je také podobné jako napříč programovacími jazyky, jako C#, Visual Basic, C++, a F#.

Podle častým sestavováním kódu, můžete rychle identifikovat chyby kompilace, jako je nesprávná syntaxe, překlepy v klíčových slovech a neshody typu. Můžete také zjistit a opravit chyby za běhu, jako jsou logické a sémantické chyby, sestavováním a spouštěním ladicí verze kódu.

Úspěšné sestavení ověří, že zdrojový kód aplikace obsahuje správnou syntaxi a, umí přeložit všechny statické odkazy na knihovny, sestavení a další komponenty. Je vytvořen spustitelný soubor aplikace, které můžete testovat pro správné fungování v obou [ladicí prostředí](../debugger/index.yml) a s celou řadou ručních a automatizovaných testů, které [ověření kvality kódu](../test/improve-code-quality.md). Jakmile aplikace byly plně testovány, můžete kompilaci verze vydání k nasazení na vaše zákazníky. Úvod k tomuto procesu najdete v tématu [názorný postup: Tvorba aplikace](../ide/walkthrough-building-an-application.md).

Pro vytvoření aplikace můžete použít některý z následujících metod: integrované vývojové prostředí sady Visual Studio, nástroje příkazového řádku MSBuild a kanály Azure:

| Metoda sestavení | Výhody |
| --- |--- | --- |
| IDE – integrované vývojové prostředí |-Okamžité sestavení a testování v ladicí program.<br />-Spusťte víceprocesorová sestavení pro projekty jazyka C++ a C#.<br />-Přizpůsobení různé aspekty systému sestavení. |
| Příkazového řádku MSBuild| -Projekty sestavit bez instalace sady Visual Studio.<br />-Spustit víceprocesorová sestavení pro všechny typy projektů.<br />-Přizpůsobte většinu oblastí systému sestavení.|
| Azure Pipelines | -Automatizujte proces sestavení jako součást kanálu průběžné integrace a doručování.<br />-Použijte automatizované testy s každým sestavením.<br />-Využívejte skoro neomezené cloudové prostředky pro procesy sestavení.<br />-Upravte pracovní postup sestavení a vytvořit aktivity sestavení, chcete-li provést hluboce přizpůsobené úkoly.|

Dokumentace v této části platí další podrobnosti o procesu sestavení na základě integrovaného vývojového prostředí. Další informace o dalších metodách, naleznete v tématu [MSBuild](../msbuild/msbuild.md) a [kanály Azure](/azure/devops/pipelines/index?view=vsts)v uvedeném pořadí.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [kompilace a sestavení v sadě Visual Studio pro Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Přehled vytváření v prostředí IDE

Při vytváření projektu sady Visual Studio vytvoří výchozí konfigurace sestavení pro projekt a řešení, které obsahuje projekt.  Tyto konfigurace definovat, jak jsou vytvořené a nasazené řešení a projekty. Konfigurace projektu zejména jsou jedinečné pro cílovou platformu (například Windows nebo Linux) a typ (například ladění nebo vydání) sestavení. Můžete upravit tyto konfigurace však a můžete také vytvořit vlastní konfigurace, podle potřeby.

První Úvod do vytváření integrovaného vývojového prostředí, najdete v části [názorný postup: Tvorba aplikace](walkthrough-building-an-application.md).

Dál si představíme [sestavování a čištění projektů a řešení v sadě Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) Další informace o přizpůsobení různé aspekty můžete provést proces. Vlastní nastavení zahrnují [změna výstupního adresáře](how-to-change-the-build-output-directory.md), [určení vlastních událostí sestavení](specifying-custom-build-events-in-visual-studio.md), [správu závislostí projektu](how-to-create-and-remove-project-dependencies.md), [Správa protokol sestavení soubory](how-to-view-save-and-configure-build-log-files.md), a [potlačení upozornění kompilátoru](how-to-suppress-compiler-warnings.md).

Odtud můžete prozkoumat celou řadu dalších úloh:
- [Principy konfigurací sestavení](understanding-build-configurations.md)
- [Principy platforem sestavení](understanding-build-platforms.md)
- [Správa vlastností projektů a řešení](managing-project-and-solution-properties.md).
- Určení událostí sestavení v [jazyka C#](how-to-specify-build-events-csharp.md) a [jazyka Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Nastavení možností sestavení](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Viz také:

- [Sestavení (kompilace) webu projektů](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Kompilace a sestavení (Visual Studio for Mac)](/visualstudio/mac/compiling-and-building)
