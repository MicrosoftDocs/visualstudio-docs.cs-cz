---
title: Kompilování a sestavování
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae06d11e1bdd193ebda5223c7c638c3132984147
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052647"
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilování a sestavování v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Systém Visual Studio lze použít k vytváření aplikací a k vytváření sestavení a spustitelných programů v pravidelných intervalech v průběhu vývoje. Častým sestavováním kódu lze dříve identifikovat chyby kompilace, jako je nesprávná syntaxe, překlepy v klíčových slovech a neshody typů. Častým sestavováním a spouštěním ladicí verze kódu lze také zjistit a opravit chyby za běhu, jako jsou logické a sémantické chyby.

 Pokud jste projekt nebo řešení plně vyvinuli a dostatečně odladili, lze jeho komponenty zkompilovat do sestavení určeného pro vydání. Ve výchozím nastavení je sestavení pro vydání optimalizováno a navrženo tak, aby bylo menší a rychlejší než ladicí verze. Další informace najdete v tématu [názorný postup: Tvorba aplikace](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Výběr metody sestavení
 Aplikaci lze sestavit pomocí výchozích možností sestavení v integrovaném vývojovém prostředí (IDE), v příkazovém řádku nebo pomocí systému Team Foundation Build. Každá z těchto možností použije nástroj MSBuild jako podkladovou technologii a každý přístup má určité výhody, jak ukazuje následující tabulka.

|Metoda sestavení|Výhody|Další informace|
|------------------|--------------|--------------------------|
|Používání prostředí IDE|– Můžete snadno vytvořit a spouštět sestavení okamžitě.<br />-Lze spustit víceprocesorová sestavení pro projekty jazyka C++ a C#.<br />-Si můžete přizpůsobit některé aspekty systému sestavení.|[Sestavování a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Spuštění příkazového řádku MSBuild|-Projekty lze sestavit bez instalace sady Visual Studio.<br />-Lze spustit víceprocesorová sestavení pro všechny typy projektů.<br />-Si můžete přizpůsobit většinu oblastí systému sestavení.|[MSBuild](../msbuild/msbuild.md)|
|Použití systému Team Foundation Build|-Můžete automatizovat proces sestavení. Lze například sestavit jeden nebo více projektů v noci nebo pokaždé, když je kód vrácen se změnami. Projekty lze také sestavit na sdílených serverech sestavení a nikoli na vašem vývojovém počítači.<br />– Je možné rychle zadat kód, který chcete sestavit, testy, které chcete spustit, a další běžné možnosti.<br />– Můžete upravit pracovní postup sestavení a podle potřeby a vytvořit aktivity sestavení provést hluboce přizpůsobené úkoly.|[Sestavení aplikace](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE
 Při vytváření projektu jsou definovány výchozí konfigurace sestavení a konfigurace sestavení řešení je přiřazena k projektu, čímž poskytuje kontext sestavení. Konfigurace řešení definují, jak jsou projekty v řešení sestaveny a nasazeny. Konfigurace projektu představují sadu vlastností projektu, které jsou jedinečné pro platformu a typ sestavení (například Vydaná verze Win32). Tyto výchozí konfigurace lze upravit a lze vytvořit vlastní konfigurace. Další informace najdete v tématu [Úvod do Návrháře projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) a [NIB jak: Upravte vlastnosti projektu a nastavení konfigurace](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 V rozhraní IDE lze provádět následující dodatečné úkoly:

-   [Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md).

-   [Identifikovat projekty, které jsou závislé na výstupu z jiného projektu, aby se sestavily správně](../ide/how-to-create-and-remove-project-dependencies.md).

-   [Změnit množství informací o zahrnutých v protokolu sestavení nebo v okně výstupu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

-   [Skrýt upozornění kompilátoru specifické pro jazyk Visual C#, Visual C++ nebo Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

-   [Zadejte vlastní před kompilací a po kompilaci akce sestavení](../ide/specifying-custom-build-events-in-visual-studio.md).

-   Zvýšit výkon sestavení pomocí paralelních sestavení Další informace najdete v tématu [sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) nebo blogový příspěvek [paralelního sestavení ladění jazyka C++](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).

## <a name="see-also"></a>Viz také
 [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md) [Principy konfigurace sestavení](../ide/understanding-build-configurations.md) [platformy sestavení Principy](../ide/understanding-build-platforms.md) [vytváření webových projektů (kompilace)](http://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [Postupy: vytváření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md)
