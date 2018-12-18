---
title: Kompilování a sestavování
description: Tento článek popisuje, jak kompilovat a sestavit projekty a řešení v sadě Visual Studio pro Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: fece226d9e7fd7ba023369928171553c393b46d5
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294315"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilování a sestavování v sadě Visual Studio pro Mac

Visual Studio for Mac slouží k vytváření aplikací a vytváření sestavení při vývoji projektu. Je důležité ke kompilaci a vytváření kódu již v rané fázi a často, aby mohli identifikovat neshody typů a další chyby kompilace.

## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE

Pomocí sady Visual Studio pro Mac umožňuje vytvářet a spouštět sestavení okamžitě, přitom stále ovládat funkce sestavení. Visual Studio pro Mac nástroj MSBuild používá jako základní systém sestavení.

Všechny projekty a řešení vytvořené v integrovaném vývojovém prostředí budou mít výchozí konfigurace sestavení, která definuje kontext pro sestavení. Tyto konfigurace se dá upravit nebo můžete vytvořit svoje vlastní. Vytvoření nebo úprava tyto konfigurace se automaticky aktualizuje soubor projektu, který se pak použije nástroj MSBuild k sestavení projektu.

Další informace o tom, jak vytvářet projekty a řešení v integrovaném vývojovém prostředí, najdete v článku [sestavování a čištění projektů a řešení](building-and-cleaning-projects-and-solutions.md) průvodce.

Visual Studio for Mac je možné také provést následující kroky:

* Změna cesty výstupu. To je upravit v možnostech projektu:

    ![Změnit výstupní cesta](media/compiling-and-building-image4.png)

* Změna podrobnost výstupu sestavení:

    ![Podrobnost sestavení změn](media/compiling-and-building-image5.png)

* Přidáte vlastní příkazy před, během nebo po vytváření nebo čištění:

    ![Přidat vlastní příkazy](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Sestavování z příkazového řádku

Můžete použít modul sestavení MSBuild pro vytváření aplikací pomocí příkazového řádku.

Zobrazit [MSBuild](/visualstudio/msbuild/msbuild) obsahu pro další informace o použití nástroje MSBuild.

## <a name="building-from-azure-pipelines"></a>Vytváření z Azure kanály

* [Sestavení aplikace pro Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Průběžná integrace se sadou Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Viz také:

- [Kompilace a sestavení (Visual Studio na Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)