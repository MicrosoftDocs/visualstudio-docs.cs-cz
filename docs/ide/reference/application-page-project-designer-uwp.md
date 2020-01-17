---
title: Stránka vlastností aplikace pro aplikace UWP
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
ms.openlocfilehash: 85ee317b315f8f8d21f5a2d97d91a9950fd395f9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114405"
---
# <a name="application-property-page-uwp-projects"></a>Stránka vlastností aplikace (projekty UWP)

Pomocí stránky vlastností **aplikace** zadejte sestavení a informace balíčku projektu univerzální platforma Windows (UWP) a cílovou verzi Windows 10.

![Stránka vlastností aplikace](media/application-page-uwp.png)

Chcete-li získat přístup ke stránce **aplikace** , vyberte uzel projektu v **Průzkumník řešení**. Pak zvolte **projekt** > **vlastnosti** na řádku nabídek. Stránky vlastností otevřené na kartě **aplikace**

## <a name="general-section"></a>Oddíl obecné

**Název sestavení**&mdash;Určuje název výstupního souboru, který bude obsahovat manifest sestavení.

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Výchozí obor názvů**&mdash;určuje základní obor názvů pro soubory přidané do projektu. Další informace o oborech názvů najdete v tématu [obory názvů (C# Průvodce programováním)](/dotnet/csharp/programming-guide/namespaces/), [obory názvů (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)nebo [obory názvů (C++)](/cpp/cpp/namespaces-cpp).

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informace o sestavení**&mdash;kliknutím na toto tlačítko zobrazíte [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

**Manifest balíčku**&mdash;kliknutím na toto tlačítko Otevřete návrháře manifestu. K nástroji manifest Designer lze také přistupovat výběrem souboru _Package. appxmanifest_ v **Průzkumník řešení**. Další informace najdete v tématu [konfigurace balíčku pomocí nástroje manifest Designer](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Oddíl cílení

Pomocí rozevíracích seznamů v této části můžete nastavit cílovou verzi a minimální verzi Windows 10 pro vaši aplikaci. Doporučujeme, abyste si vycíleni na nejnovější verzi Windows 10 a pokud vyvíjíte podnikovou aplikaci, která podporuje také starší minimální verzi. Další informace o tom, kterou verzi Windows 10 zvolit, najdete v tématu [Volba verze UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informace o cílení na platformu v aplikaci Visual Studio naleznete v tématu [cílení na platformu](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Viz také:

- [Vytvoření první aplikace pro UWP](/windows/uwp/get-started/your-first-app)
- [Zvolit verzi UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
