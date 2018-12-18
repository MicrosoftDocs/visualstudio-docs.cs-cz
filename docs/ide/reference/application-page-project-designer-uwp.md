---
title: Stránka vlastností aplikace pro aplikace pro UPW
ms.date: 01/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 206c856eb87243fd6021c4ff8bb9f6890b8eaf25
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384211"
---
# <a name="application-property-page-uwp-projects"></a>Stránka vlastností aplikace (projektů UPW).

Použití **aplikace** zadejte sestavení projektu univerzální platformu Windows (UPW) a informace o balíčku a verzi cíl Windows 10 na stránce vlastností.

![Stránka vlastností aplikace](media/application-page-uwp.png)

Pro přístup **aplikace** zvolte uzel projektu v **Průzkumníka řešení**. Klikněte na tlačítko **projektu** > **vlastnosti** na řádku nabídek. Stránky vlastností otevřít v **aplikace** kartu.

## <a name="general-section"></a>Části Obecné

**Název sestavení**&mdash;Určuje název výstupního souboru, který bude obsahovat manifest sestavení.

Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Výchozí obor názvů**&mdash;určuje základní obor názvů pro soubory přidané do projektu. Další informace o oborech názvů najdete v tématu [obory názvů (C# programováním)](/dotnet/csharp/programming-guide/namespaces/), [oborů názvů (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces), nebo [obory názvů (C++)](/cpp/cpp/namespaces-cpp).

Programový přístup k této vlastnosti, najdete v článku <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informace o sestavení**&mdash;zvolíte toto tlačítko se zobrazí [dialogové okno informace o sestavení](../../ide/reference/assembly-information-dialog-box.md).

**Manifest balíčku**&mdash;zvolíte toto tlačítko otevře manifest designer. Manifest designer lze rovněž přistupovat výběrem _Package.appxmanifest_ ve **Průzkumníka řešení**. Další informace najdete v tématu [konfigurace balíčku pomocí návrháře manifestu](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Cílení na oddíl

Pomocí rozevírací seznamy v této části můžete nastavit cílovou verzi a minimální verzi Windows 10 pro vaši aplikaci. Je doporučeno cílit na nejnovější verzi Windows 10, a pokud vyvíjíte podnikové aplikace, příliš podporují starší minimální verze. Další informace o verzi Windows 10, která se má vybrat, najdete v části [zvolte verzi UPW](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informace o platformě cílení v sadě Visual Studio 2017, najdete v části [cílení na platformy](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Viz také:

- [Vytvoření první aplikace pro UPW](/windows/uwp/get-started/your-first-app)
- [Zvolte verzi UPW](/windows/uwp/updates-and-versions/choose-a-uwp-version)