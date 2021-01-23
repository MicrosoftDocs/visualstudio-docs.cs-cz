---
title: Kompilace a sestavení
description: Tento článek popisuje, jak kompilovat a sestavovat projekty a řešení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: d5613a47785f1bb3fbb2a56f8458bba1946930e7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719798"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilace a sestavování v Visual Studio pro Mac

Visual Studio pro Mac lze použít k sestavování aplikací a vytváření sestavení během vývoje projektu. Je důležité kompilovat a sestavovat kód na začátku a často, abyste mohli identifikovat neshody typu a další chyby při kompilaci.

## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE

Použití Visual Studio pro Mac umožňuje okamžité vytváření a spouštění sestavení a zároveň vám poskytuje kontrolu nad funkcemi sestavení. Visual Studio pro Mac používá nástroj MSBuild jako základní sestavovací systém.

Všechny projekty a řešení vytvořené v integrovaném vývojovém prostředí budou mít výchozí konfiguraci sestavení, která definuje kontext pro sestavení. Tyto konfigurace je možné upravit nebo můžete vytvořit vlastní. Vytvořením nebo úpravou těchto konfigurací dojde k automatické aktualizaci souboru projektu, který je poté použit nástrojem MSBuild k sestavení projektu.

Další informace o tom, jak sestavit projekty a řešení v integrovaném vývojovém prostředí, najdete v tématu Příručka pro [sestavení a čištění projektů a řešení](building-and-cleaning-projects-and-solutions.md) .

Visual Studio pro Mac můžete použít také k následujícím akcím:

* Změňte výstupní cestu. To je upraveno v možnostech projektu:

    ![Změnit výstupní cestu](media/compiling-and-building-image4.png)

* Změnit podrobnosti výstupu sestavení:

    ![Změnit podrobnosti sestavení](media/compiling-and-building-image5.png)

* Přidat vlastní příkazy před, během nebo po sestavení nebo vyčištění:

    ![Přidat vlastní příkazy](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Sestavování z příkazového řádku

Můžete použít modul sestavení MSBuild k sestavování aplikací prostřednictvím příkazového řádku.

Další informace o použití nástroje MSBuild naleznete v obsahu [MSBuild](/visualstudio/msbuild/msbuild) .

## <a name="building-from-azure-pipelines"></a>Sestavování z Azure Pipelines

* [Sestavení aplikace Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Kontinuální integrace s Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Viz také

- [Kompilovat a sestavovat (Visual Studio ve Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)