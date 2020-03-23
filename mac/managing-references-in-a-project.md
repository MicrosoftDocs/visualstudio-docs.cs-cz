---
title: Správa referencí v projektu
description: Tento článek popisuje, jak spravovat odkazy v projektu v Sadě Visual Studio pro Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: a14630c5448632a939e1768040b910caf6276c2a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692921"
---
# <a name="managing-references-in-a-project"></a>Správa referencí v projektu

Visual Studio pro Mac poskytuje dva způsoby přidávání dalších odkazů na váš projekt:

![Odkazy na projekty](media/projects-and-solutions-image10.png)

Jsou to:

* Odkazy
* NuGets (Přidáno prostřednictvím složky Balíčky)

Kromě toho webové odkazy a nativní odkazy lze také přidat do libovolného projektu.

## <a name="assembly-references"></a>Odkazy na sestavení

Každý rámec v Xamarinu je dodáván s více než tuctem shromáždění. Ne všechny tyto balíčky sestavení jsou odkazovány v projektu ve výchozím nastavení.

Chcete-li upravit balíčky, na které se odkazuje v projektu, použijte dialogové okno **Upravit odkazy,** které lze zobrazit poklepáním na složku Reference nebo výběrem **možnosti Upravit odkazy** v akcích kontextové nabídky:

![Dialogové okno Odkazy na sestavení](media/projects-and-solutions-image11.png)

Informace o sestaveních dostupných pro každý rámec Xamarin naleznete v příručce [K dispozici sestavení.](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/)

## <a name="nuget"></a>NuGet

NuGet je nejoblíbenější správce balíčků pro vývoj rozhraní .NET. Visual Studio pro Mac NuGet podpora umožňuje vyhledávat balíčky přidat do projektu.

Chcete-li to provést, klikněte pravým tlačítkem myši na složku **Balíček** v panelu řešení a vyberte přidat balíčky.

Další informace o použití balíčku NuGet je k dispozici v [včetně balíčku NuGet v](nuget-walkthrough.md) návodu k projektu.

## <a name="see-also"></a>Viz také

- [Správa odkazů (Visual Studio v systému Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Přidání odkazů pomocí NuGet versus rozšíření SDK (Visual Studio v systému Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)