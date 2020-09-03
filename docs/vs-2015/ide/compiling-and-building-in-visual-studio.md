---
title: Kompilace a sestavení
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8ec7d6508ec025a2b2005754da03bdd4db38943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300257"
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilování a sestavování v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Systém Visual Studio lze použít k vytváření aplikací a k vytváření sestavení a spustitelných programů v pravidelných intervalech v průběhu vývoje. Častým sestavováním kódu lze dříve identifikovat chyby kompilace, jako je nesprávná syntaxe, překlepy v klíčových slovech a neshody typů. Častým sestavováním a spouštěním ladicí verze kódu lze také zjistit a opravit chyby za běhu, jako jsou logické a sémantické chyby.

 Pokud jste projekt nebo řešení plně vyvinuli a dostatečně odladili, lze jeho komponenty zkompilovat do sestavení určeného pro vydání. Ve výchozím nastavení je sestavení pro vydání optimalizováno a navrženo tak, aby bylo menší a rychlejší než ladicí verze. Další informace najdete v tématu [Návod: sestavování aplikace](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Výběr metody sestavení
 Aplikaci lze sestavit pomocí výchozích možností sestavení v integrovaném vývojovém prostředí (IDE), v příkazovém řádku nebo pomocí systému Team Foundation Build. Každá z těchto možností použije nástroj MSBuild jako podkladovou technologii a každý přístup má určité výhody, jak ukazuje následující tabulka.

|Metoda sestavení|Výhody|Další informace|
|------------------|--------------|--------------------------|
|Používání prostředí IDE|– Sestavení můžete snadněji vytvářet a spouštět hned.<br />– Můžete spouštět víceprocesorové sestavení pro projekty v jazyce C++ a C#.<br />– Můžete přizpůsobit některé aspekty systému sestavení.|[Sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Spuštění příkazového řádku MSBuild|– Projekty můžete sestavit bez instalace sady Visual Studio.<br />– Pro všechny typy projektů můžete spustit sestavení s více procesory.<br />– Můžete přizpůsobit většinu oblastí systému sestavení.|[Nástroji](../msbuild/msbuild.md)|
|Použití systému Team Foundation Build|– Proces sestavení můžete automatizovat. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Projekty lze také sestavit na sdílených serverech sestavení a nikoli na vašem vývojovém počítači.<br />– Můžete rychle zadat kód, který chcete sestavit, testy, které chcete spustit, a další běžné možnosti.<br />– Pracovní postup sestavení můžete upravit a podle potřeby vytvářet aktivity sestavení pro provádění hluboce přizpůsobených úkolů.|[Sestavení aplikace](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE
 Při vytváření projektu jsou definovány výchozí konfigurace sestavení a konfigurace sestavení řešení je přiřazena k projektu, čímž poskytuje kontext sestavení. Konfigurace řešení definují, jak jsou projekty v řešení sestaveny a nasazeny. Konfigurace projektu představují sadu vlastností projektu, které jsou jedinečné pro platformu a typ sestavení (například Vydaná verze Win32). Tyto výchozí konfigurace lze upravit a lze vytvořit vlastní konfigurace. Další informace naleznete v tématu [Úvod do Návrháře projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) a [NIB postupy: Úprava vlastností projektu a nastavení konfigurace](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 V rozhraní IDE lze provádět následující dodatečné úkoly:

- [Změňte výstupní adresář sestavení](../ide/how-to-change-the-build-output-directory.md).

- [Identifikujte projekty, které jsou závislé na výstupu z jiného projektu, aby bylo sestavení správně sestaveno](../ide/how-to-create-and-remove-project-dependencies.md).

- [Změna množství informací obsažených v protokolu sestavení nebo v okně výstup pro sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Skrýt specifická upozornění kompilátoru pro Visual C#, Visual C++ nebo Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Zadejte vlastní akce před kompilací a po kompilaci pro sestavení](../ide/specifying-custom-build-events-in-visual-studio.md).

- Zvýšit výkon sestavení pomocí paralelních sestavení Další informace najdete v článku [sestavování více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) nebo v příspěvku na blogu [ladění sestavení C++](https://blogs.msdn.microsoft.com/msbuild/2010/03/07/tuning-c-build-parallelism-in-vs2010/).

## <a name="see-also"></a>Viz také
 [Návod: sestavování aplikace](../ide/walkthrough-building-an-application.md) [porozumění konfiguracím sestavení](../ide/understanding-build-configurations.md) [porozumění vývojovým platformám sestavení](../ide/understanding-build-platforms.md) [(kompilace) projektů](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) webu [Postupy: vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md)
