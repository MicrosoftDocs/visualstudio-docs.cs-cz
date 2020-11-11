---
title: Správa odkazů v projektu
description: Tento článek popisuje, jak spravovat odkazy v projektu v Visual Studio pro Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 41d49fe6b23818f3cb9de8dec72462d4b2029bb6
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493514"
---
# <a name="managing-references-in-a-project"></a>Správa odkazů v projektu

Visual Studio pro Mac poskytuje dva způsoby přidávání dalších odkazů do projektu:

![Odkazy na projekty](media/projects-and-solutions-image10.png)

Jsou to:

* Reference
* Balíčky NuGet (přidané prostřednictvím složky Packages)

Kromě toho lze do libovolného projektu přidat také webové odkazy a nativní odkazy.

## <a name="assembly-references"></a>Odkazy na sestavení

Každá architektura v rámci platformy Xamarin je dodávána s více než deseti sestaveními. Ve výchozím nastavení nejsou v projektu odkazovány všechny tyto balíčky sestavení.

Chcete-li upravit balíčky, které jsou odkazovány v projektu, použijte dialogové okno **Upravit odkazy** , které lze zobrazit dvojitým kliknutím na složku odkazy, nebo výběrem možnosti **Upravit odkazy** v rámci jejich kontextové nabídky:

![Dialogové okno odkazy na sestavení](media/projects-and-solutions-image11.png)

Informace o sestaveních dostupných pro každé rozhraní Xamarin Framework naleznete v průvodci [dostupnými sestaveními](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) .

## <a name="nuget"></a>NuGet

NuGet je nejoblíbenější správce balíčků pro vývoj pro .NET. Podpora NuGet Visual Studio pro Mac umožňuje vyhledat balíčky, které se mají přidat do projektu.

Provedete to tak, že kliknete pravým tlačítkem na složku **balíčku** v okně řešení a vyberete Přidat balíčky.

Další informace o použití balíčku NuGet najdete v návodu [zahrnutí balíčku NuGet v projektu](nuget-walkthrough.md) .

## <a name="see-also"></a>Viz také

- [Správa odkazů (Visual Studio ve Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Přidání odkazů pomocí NuGet oproti sadě SDK rozšíření (Visual Studio ve Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)