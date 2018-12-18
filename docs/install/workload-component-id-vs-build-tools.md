---
title: ID pracovního vytížení a komponenta Visual Studio 2017 nástroje sestavení
titleSuffix: ''
description: Pomocí ID pracovního vytížení a komponenta Visual Studio můžete vytvářet klasické aplikace pro Windows
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 2e47eca638e81cf1b99a451e3017614be45d2c59
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063043"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio 2017 nástroje sestavení součástí adresáře

Tabulky v tomto seznamu stránce ID, můžete použít k instalaci sady Visual Studio pomocí příkazového řádku nebo je můžete zadat jako závislost v manifestu VSIX. Všimněte si, že přidáme další součásti vydaných aktualizací sady Visual Studio.

Všimněte si také následující stránka:

* Každá úloha má vlastní oddíl, za nímž následuje Identifikátor pracovního vytížení a tabulku komponent, které jsou k dispozici pro pracovní vytížení.
* Ve výchozím nastavení **vyžaduje** součásti nainstaluje, když jste si nainstalovali úlohu.
* Pokud budete chtít, můžete nainstalovat také **doporučená** a **volitelné** komponenty.
* Přidali jsme také oddíl, který obsahuje další součásti, které nejsou pod něj nespadá u jakékoli úlohy.

Když nastavíte závislosti v manifestu VSIX, je nutné zadat ID součástí pouze. Určení závislostí naše minimální součástí pomocí tabulek na této stránce. V některých případech to může znamenat, že zadáváte pouze jednu komponentu z pracovního vytížení. V jiných scénářích může znamenat, že zadáte více komponent z jedné úlohy nebo více komponent z více úloh. Další informace najdete v tématu [postupy: migrace projektů rozšíření do sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) stránky.

Další informace o tom, jak pomocí těchto identifikátorů najdete v části [pomocí parametrů příkazového řádku instalace sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) stránky. A seznam pracovního vytížení a komponenta ID pro ostatní produkty, naleznete v tématu [funkcí sady Visual Studio 2017 a ID součástí](workload-and-component-ids.md) stránky.

## <a name="azure-development-build-tools"></a>Nástroje sestavení pro vývoj pro Azure

**ID:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Popis:** MSBuild úlohy a cíle pro vytváření aplikací Azure.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure – nástroje pro tvorbu | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.ClientLibs | Knihovny Azure pro .NET | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Nástroje pro vytváření Azure Cloud Services | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Sestavení vývojářských nástrojů WCF | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Sestavení nástrojů pro vývoj webů | 15.8.27729.1 | Požadováno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje .NET framework 3.5 | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,

## <a name="data-storage-and-processing-build-tools"></a>Nástroje sestavení pro ukládání a zpracování dat

**ID:** Microsoft.VisualStudio.Workload.DataBuildTools

**Popis:** sestavit projekty databází systému SQL Server

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Doporučeno
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# a Visual Basic | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | Nástroje SQL Server Data Tools – nástroje pro vytváření | 15.8.27825.0 | Doporučeno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Doporučeno

## <a name="net-desktop-build-tools"></a>Nástroje pro vytváření desktopových .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Popis:** nástroje pro vytváření WPF, Windows Forms a konzolové aplikace pomocí C#, Visual Basic a F#.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.Component.ClickOnce.MSBuild | Nástroje pro vytváření ClickOnce | 15.7.27617.1 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.TestTools.BuildTools | Základní funkce – Build Tools testovacích nástrojů | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Sestavení vývojářských nástrojů WCF | 15.6.27309.0 | Doporučeno
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje .NET framework 3.5 | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.FSharp.MSBuild | kompilátor jazyka F# | 15.8.27825.0 | volitelná,

## <a name="msbuild-tools"></a>Nástroje MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Popis:** poskytuje nástroje potřebné k sestavení aplikace založené na MSBuild.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno

## <a name="net-core-build-tools"></a>Nástroje sestavení .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Popis:** nástroje pro vytváření aplikací pomocí .NET Core, ASP.NET Core, HTML/JavaScript a kontejnerů.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Požadováno
Microsoft.NetCore.BuildTools.ComponentGroup | Nástroje sestavení .NET core | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,

## <a name="nodejs-build-tools"></a>Nástroje pro sestavování Node.js

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Popis:** MSBuild úlohy a cíle pro vytvoření škálovatelné síťové aplikace využívající Node.js, asynchronního runtime JavaScriptu založený na událostech.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Podporu nástroje Node.js MSBuild | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno

## <a name="officesharepoint-build-tools"></a>Nástroje pro vytváření Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Popis:** vytvářet doplňky Office a SharePoint a doplňky VSTO.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Nástroje pro vytváření ClickOnce | 15.7.27617.1 | Požadováno
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet | Správce balíčků NuGet | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Nástroje sestavení pro vývoj pro Office/SharePoint | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.Workflow.BuildTools | Nástroje sestavení aplikace Windows Workflow Foundation | 15.8.27906.1 | Požadováno
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Sestavení vývojářských nástrojů WCF | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Sestavení nástrojů pro vývoj webů | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Nástroje sestavení Visual Studio Tools for Office (VSTO) | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,

## <a name="universal-windows-platform-build-tools"></a>Nástroje sestavení pro univerzální platformu Windows

**ID:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Popis:** poskytuje nástroje potřebné k vytváření aplikací univerzální platformy Windows.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Požadováno
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilátory jazyka Visual C++ a knihovny pro ARM | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | Požadováno
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Požadavky na sestavování univerzální platforma Windows | 15.8.27705.0 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | volitelná,

## <a name="visual-c-build-tools"></a>Visual C++ build tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Popis:** vytváření aplikací klasické pracovní plochy Windows pomocí sady nástrojů Microsoft C++, ATL nebo MFC.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | Požadováno
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Základní funkce Visual C++ Build Tools | 15.8.27729.1 | Požadováno
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Distribuovatelné součásti Visual C++ 2017 Update | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | Požadováno
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.TestTools.BuildTools | Základní funkce – Build Tools testovacích nástrojů | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.VC.CMake.Project | Nástroje Visual C++ pro CMake | 15.8.27906.1 | Doporučeno
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Doporučeno
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | volitelná,
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.VC.140 | Nástrojů VC ++ 2015.3 v14.00 (v140) pro desktop | 15.7.27617.1 | volitelná,
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ CLI podpory | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduly pro standardní knihovnu (experimentální) | 15.6.27309.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilátory jazyka Visual C++ a knihovny pro ARM | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilátory jazyka Visual C++ a knihovny pro ARM64 | 15.9.28230.55 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [x86 a x64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) pro Desktop C++ [ARM a ARM64] | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) pro UPW: C#, VB, JS | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) pro UPW: C++ | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.WinXP | Podpora Windows XP pro C++ | 15.8.27924.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK a UCRT SDK | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Podpora Windows XP pro C++ | 15.8.27705.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | volitelná,
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | volitelná,

## <a name="visual-studio-extension-development"></a>Vývoj rozšíření sady Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**Popis:** nástroje pro vytváření doplňků a rozšíření pro Visual Studio, včetně nových příkazů, analyzátorů kódu a nástrojů systému windows.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Microsoft.VisualStudio.Component.VSSDKBuildTools | Základní nástroje pro sestavení sady Visual Studio SDK | 15.8.27924.0 | Požadováno
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Visual Studio předpoklady pro vývoj rozšíření | 15.8.27729.1 | Požadováno
Component.Dotfuscator | PreEmptive ochranu – řešení Dotfuscator | 15.0.26208.0 | volitelná,
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ runtime pro UPW | 15.6.27406.0 | volitelná,
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Nástroje statické analýzy | 15.0.26208.0 | volitelná,
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC pro x86 a x64 | 15.7.27625.0 | volitelná,
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 verze 15.9 v14.16 nejnovější nástroje v141 pro | 15.9.28230.55 | volitelná,

## <a name="web-development-build-tools"></a>Sestavení nástrojů pro vývoj webů

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Popis:** úlohy MSBuild a cíle pro vytváření webových aplikací.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Vývojové nástroje .NET framework 4.6.1 | 15.8.27825.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Požadováno
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Sestavení nástrojů pro vývoj webů | 15.8.27729.1 | Požadováno
Microsoft.Component.ClickOnce.MSBuild | Nástroje pro vytváření ClickOnce | 15.7.27617.1 | Doporučeno
Microsoft.Net.Component.4.5.1.TargetingPack | Rozhraní .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.2.TargetingPack | Rozhraní .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Doporučeno
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Vývojové nástroje .NET framework 4 – 4.6 | 15.6.27406.0 | Doporučeno
Microsoft.Net.Core.Component.SDK.2.1 | Vývojové nástroje .NET core 2.1 | 15.8.27924.0 | Doporučeno
Microsoft.VisualStudio.Component.AspNet45 | Rozšířené funkce ASP.NET | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Kontejnerové vývojové nástroje – Build Tools | 15.7.27617.1 | Doporučeno
Microsoft.VisualStudio.Component.TestTools.BuildTools | Základní funkce – Build Tools testovacích nástrojů | 15.7.27625.0 | Doporučeno
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Doporučeno
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Sestavení vývojářských nástrojů WCF | 15.6.27309.0 | Doporučeno
Microsoft.Net.Component.3.5.DeveloperTools | Vývojové nástroje .NET framework 3.5 | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.SDK | Rozhraní .NET framework 4.6.2 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.6.2.TargetingPack | Rozhraní .NET framework 4.6.2 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.SDK | Rozhraní .NET framework 4.7.1 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.1.TargetingPack | Rozhraní .NET framework 4.7.1 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.2.SDK | Rozhraní .NET framework 4.7.2 SDK | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.2.TargetingPack | Rozhraní .NET framework 4.7.2 targeting pack | 15.8.27825.0 | volitelná,
Microsoft.Net.Component.4.7.SDK | Rozhraní .NET framework 4.7 SDK | 15.6.27406.0 | volitelná,
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Vývojové nástroje .NET framework 4.6.2 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Vývojové nástroje .NET framework 4.7.1 | 15.6.27406.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Vývojové nástroje .NET framework 4.7.2 | 15.8.27825.0 | volitelná,
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Vývojové nástroje .NET framework 4.7 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK | Vývojové nástroje .NET core 2.0 | 15.6.27406.0 | volitelná,
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 až 1.1. vývojové nástroje | 15.6.27406.0 | volitelná,

## <a name="mobile-development-with-net"></a>Vývoj mobilních aplikací pomocí .NET

**ID:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Popis:** nástroje pro vytváření multiplatformních aplikací pro iOS, Android a Windows pomocí C# a F#.

### <a name="components-included-by-this-workload"></a>Pomocí této úlohy zahrnuté komponenty

ID součásti | Název | Version | Typ závislosti
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Požadováno
Microsoft.Net.Component.4.6.1.SDK | Rozhraní .NET framework 4.6.1 SDK | 15.6.27406.0 | Požadováno
Microsoft.Net.Component.4.6.1.TargetingPack | Rozhraní .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Požadováno
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cíle a úlohy sestavení | 15.9.28016.0 | Požadováno
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilátory C# a Visual Basic Roslyn | 15.6.27309.0 | Požadováno
Component.Android.SDK25 | Instalace sady Android SDK (úroveň rozhraní API 25) | 15.9.28107.0 | volitelná,
Component.OpenJDK | OpenJDK je distribuce Microsoftu | 15.9.28125.51 | volitelná,

## <a name="unaffiliated-components"></a>Nespojená komponenty

Toto jsou komponenty, které nejsou zahrnuty u jakékoli úlohy, ale může vybrat jako jednotlivých komponent.

ID součásti | Název | Version
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 sady SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 sady SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL pro ARM se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL pro ARM64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC pro x86/x64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimentální) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC pro ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC pro ARM se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC pro ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Podpora Visual C++ MFC pro ARM64 se zmírněními hrozeb Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC ++ 2017 verze 15.9 v14.16 knihovny pro Spectre (x86 a x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Sada nástrojů 14.11 pro VC ++ 2017 verze 15.4 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Sada nástrojů VC ++ 2017 verze 15.5 14.12 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC ++ 2017 verze 15.6 v14.13 – sada nástrojů | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Sada nástrojů VC ++ 2017 verze 15.7 v14.14 – | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Sada nástrojů VC ++ 2017 verze 15.8 v14.15 | 15.0.28230.55

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Build Tools pro Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
