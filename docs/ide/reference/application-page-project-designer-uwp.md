---
title: Stránka vlastností aplikace pro aplikace UWP
description: Naučte se používat stránku aplikace k určení sestavení a informací o balíčku projektu Univerzální platforma Windows (UWP) a cílové verzi Windows 10.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 826d408d8e1a6a2cb8bcad956ce930781a9155db
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871363"
---
# <a name="application-property-page-uwp-projects"></a>Stránka vlastností aplikace (projekty UWP)

Pomocí stránky vlastností **aplikace** zadejte sestavení a informace balíčku projektu univerzální platforma Windows (UWP) a cílovou verzi Windows 10.

![Stránka vlastností aplikace](media/application-page-uwp.png)

Chcete-li získat přístup ke stránce **aplikace** , vyberte uzel projektu v **Průzkumník řešení**. Pak zvolte **Project**  >  **vlastnosti** projektu na řádku nabídek. Stránky vlastností otevřené na kartě **aplikace**

## <a name="general-section"></a>Oddíl obecné

**Název sestavení** &mdash; Určuje název výstupního souboru, který bude obsahovat manifest sestavení.

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

**Výchozí obor názvů** &mdash; Určuje základní obor názvů pro soubory přidané do projektu. Další informace o oborech názvů najdete v tématu [obory názvů (Průvodce programováním v C#)](/dotnet/csharp/programming-guide/namespaces/), [obory názvů (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)nebo [obory názvů (C++)](/cpp/cpp/namespaces-cpp).

Chcete-li získat přístup k této vlastnosti programově, přečtěte si téma <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

**Informace o sestavení** &mdash; Kliknutím na toto tlačítko se zobrazí [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

**Manifest balíčku** &mdash; Kliknutím na toto tlačítko otevřete návrhář manifestu. K nástroji manifest Designer lze také přistupovat výběrem souboru _Package. appxmanifest_ v **Průzkumník řešení**. Další informace najdete v tématu [konfigurace balíčku pomocí nástroje manifest Designer](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Oddíl cílení

Pomocí rozevíracích seznamů v této části můžete nastavit cílovou verzi a minimální verzi Windows 10 pro vaši aplikaci. Doporučujeme, abyste si vycíleni na nejnovější verzi Windows 10 a pokud vyvíjíte podnikovou aplikaci, která podporuje také starší minimální verzi. Další informace o tom, kterou verzi Windows 10 zvolit, najdete v tématu [Volba verze UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informace o cílení na platformu v aplikaci Visual Studio naleznete v tématu [cílení na platformu](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Viz také

- [Vytvoření první aplikace pro UWP](/windows/uwp/get-started/your-first-app)
- [Zvolit verzi UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
