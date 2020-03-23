---
title: Kompilace a sestavení
description: Tento článek popisuje, jak kompilovat a vytvářet projekty a řešení v Sadě Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983602"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilace a vytváření v Visual Studiu pro Mac

Visual Studio pro Mac lze použít k vytváření aplikací a vytváření sestavení během vývoje projektu. Je důležité zkompilovat a sestavit kód brzy a často, takže můžete identifikovat neshody typů a další chyby v době kompilace.

## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE

Použití Visual Studia pro Mac umožňuje vytvářet a spouštět sestavení okamžitě, zatímco stále poskytuje kontrolu nad funkcemi sestavení. Visual Studio pro Mac používá MSBuild jako základní systém sestavení.

Všechny projekty a řešení vytvořené v ide bude mít výchozí konfiguraci sestavení, která definuje kontext pro sestavení. Tyto konfigurace lze upravovat nebo si můžete vytvořit vlastní. Vytvoření nebo úprava těchto konfigurací automaticky aktualizuje soubor projektu, který pak používá MSBuild k vytvoření projektu.

Další informace o vytváření projektů a řešení v ide naleznete v [tématu vytváření a čištění projekty a řešení](building-and-cleaning-projects-and-solutions.md) průvodce.

Visual Studio pro Mac lze také použít k provedení následujících akcí:

* Změňte výstupní cestu. Tato možnost se upravuje v možnostech aplikace Project:

    ![Změna výstupní cesty](media/compiling-and-building-image4.png)

* Změňte podrobnost výstupu sestavení:

    ![Změna podrobností sestavení](media/compiling-and-building-image5.png)

* Přidání vlastních příkazů před, během nebo po vytváření nebo čištění:

    ![přidání vlastních příkazů](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Vytváření z příkazového řádku

Modul sestavení MSBuild můžete použít k vytváření aplikací prostřednictvím příkazového řádku.

Další informace o používání msbuildu naleznete v obsahu [MSBuild.](/visualstudio/msbuild/msbuild)

## <a name="building-from-azure-pipelines"></a>Vytváření z Azure Pipelines

* [Sestavte si aplikaci Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Průběžná integrace s Xamarinem](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Viz také

- [Kompilace a sestavení (Visual Studio ve Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)