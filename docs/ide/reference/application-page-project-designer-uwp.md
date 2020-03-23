---
title: Stránka vlastností aplikace pro aplikace UPW
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3c8f72d4e1d1caeacd5dfefef5310dc2cef83b92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77173080"
---
# <a name="application-property-page-uwp-projects"></a>Stránka vlastností aplikace (projekty UPW)

Na stránce **vlastností aplikace** můžete určit informace o sestavení a balíčku projektu univerzální platformy Windows (UPW) a cílit na verzi windows 10.

![Stránka vlastností aplikace](media/application-page-uwp.png)

Chcete-li získat přístup ke stránce **Aplikace,** zvolte uzel projektu v **Průzkumníku řešení**. Pak na řádku nabídek zvolte**Vlastnosti** **projektu.** >  Stránky vlastností se otevřou na kartě **Aplikace.**

## <a name="general-section"></a>Obecná sekce

**Název sestavení**&mdash;Určuje název výstupního souboru, který bude obsahovat manifest sestavení.

Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.AssemblyName%2A>této vlastnosti programově, naleznete v tématu .

**Výchozí obor**&mdash;názvů Určuje základní obor názvů pro soubory přidané do projektu. Další informace o oborech názvů naleznete v [tématu Namespaces (Programovací průvodce Jazyka C# ),](/dotnet/csharp/programming-guide/namespaces/) [Obory názvů (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)nebo [Obory názvů (C++).](/cpp/cpp/namespaces-cpp)

Chcete-li získat přístup k <xref:VSLangProj.ProjectProperties.RootNamespace%2A>této vlastnosti programově, naleznete v tématu .

**Informace o**&mdash;sestavě: Pokud zvolíte toto tlačítko, zobrazí [se dialogové okno Informace o sestavě](../../ide/reference/assembly-information-dialog-box.md).

**Manifest balíčku:**&mdash;Výběrtohoto tlačítka otevře návrháře manifestu. Návrhář manifestu lze také přistupovat výběrem _Souboru Package.appxmanifest_ v **Průzkumníku řešení**. Další informace naleznete [v tématu Konfigurace balíčku s návrhářem manifestu](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Sekce cílení

Cílovou verzi a minimální verzi Windows 10 pro aplikaci můžete nastavit pomocí rozevíracích seznamů v této části. Doporučujeme cílit na nejnovější verzi Windows 10 a pokud vyvíjíte podnikovou aplikaci, podporujete také starší minimální verzi. Další informace o tom, kterou verzi Windows 10 zvolit, najdete [v tématu Volba verze UPW](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informace o cílení na platformu ve Visual Studiu najdete v [tématu Cílení na platformu](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Viz také

- [Vytvoření první aplikace UPW](/windows/uwp/get-started/your-first-app)
- [Výběr verze UPW](/windows/uwp/updates-and-versions/choose-a-uwp-version)
