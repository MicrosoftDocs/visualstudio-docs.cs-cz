---
title: Správa odkazů v projektu
description: Tento článek popisuje, jak Správa odkazů v projektu v sadě Visual Studio pro Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 54e07d3c170859405ef584b884547dad335788f3
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295277"
---
# <a name="managing-references-in-a-project"></a>Správa odkazů v projektu

Visual Studio for Mac obsahuje dva prostředky přidáte další odkazy do projektu:

![Odkazy na projekt](media/projects-and-solutions-image10.png)

Toto jsou:

* Odkazy
* Balíčky Nuget (přidané prostřednictvím složku Packages)

Kromě toho odkazů na webové a nativní odkazy můžete také přidat do jakéhokoli projektu.

## <a name="assembly-references"></a>Odkazy na sestavení

Každé platformě Xamarin se dodává s více než deseti sestavení. Ne všechny tyto balíčky sestavení je odkazováno v projektu ve výchozím nastavení.

Chcete-li upravit balíčky, které je odkazováno v projektu, použijte **upravit odkazy** dialogové okno, které lze zobrazit dvojitým kliknutím na odkazy na složku, nebo výběrem **upravit odkazy** na jeho kontextu Nabídka Akce:

![Dialogové okno odkazy na sestavení](media/projects-and-solutions-image11.png)

Informace o sestavení dostupných pro každé rozhraní, Xamarin, najdete [dostupných sestavení](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) průvodce.

## <a name="nuget"></a>NuGet

Správce balíčků NuGet je nejoblíbenější Správce balíčků pro vývoj na platformě .NET. Visual Studio pro Mac podpora NuGet umožňuje vyhledat balíčky k přidání do projektu.

Chcete-li to provést, klikněte pravým tlačítkem na **balíčku** složky v oblasti řešení a vyberte možnost přidat balíčky.

Další informace o použití balíčku NuGet je součástí [balíček včetně NuGet ve vašem projektu](nuget-walkthrough.md) návodu.

## <a name="see-also"></a>Viz také:

- [Správa odkazů (Visual Studio na Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Přidání odkazů pomocí nástroje NuGet a sady extension SDK (Visual Studio na Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)