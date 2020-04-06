---
title: Použití MSBuild | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704292"
---
# <a name="using-msbuild"></a>Použití nástroje MSBuild
MSBuild poskytuje dobře definovaný, rozšiřitelný formát XML pro vytváření souborů projektu, které plně popisují položky projektu, které mají být sestaveny, vytvářet úkoly a vytvářet konfigurace.

## <a name="general-msbuild-considerations"></a>Obecné důležité informace o sestavení msbuildu
 MSBuild soubory projektu, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] například .csproj a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj soubory, obsahují data, která se používá v době sestavení, ale také může obsahovat data, která se používá v době návrhu. Data v době sestavení jsou uložena pomocí primitiv MSBuild, včetně [elementu položky (MSBuild)](../../msbuild/item-element-msbuild.md) a [elementu vlastnosti (MSBuild).](../../msbuild/property-element-msbuild.md) Data návrhu, která jsou specifická pro typ projektu a všechny související podtypy projektu, jsou uložena ve volném xml vyhrazeném pro něj.

 MSBuild nemá nativní podporu pro objekty konfigurace, ale poskytuje podmíněné atributy pro určení dat specifických pro konfiguraci. Například:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Další informace o podmíněných atributech naleznete [v tématu Podmíněné konstrukce](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Rozšíření msbuild u typu projektu
 Rozhraní MSBuild a rozhraní API se mohou měnit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]v budoucích verzích aplikace . Proto je vhodné použít spravované balíček framework (MPF) třídy, protože poskytují stínění před změnami.

 Architektura spravovaného balíčku pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nového systému projektu. Zdrojový kód a pokyny pro kompilaci najdete na [mpf pro projekty - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Třídy MPF specifické pro projekt jsou následující:

|Třída|Implementace|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`třída je obálka pro položky MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generátory jednoho souboru vs. Úlohy sestavení MSBuild
 Generátory jednotlivých souborů jsou přístupné pouze v době návrhu, ale úlohy MSBuild lze použít v době návrhu a sestavení. Pro maximální flexibilitu, proto použijte MSBuild úkoly transformovat a generovat kód. Další informace naleznete [v tématu Vlastní nástroje](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Viz také
- [Referenční dokumentace nástroje MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Vlastní nástroje](../../extensibility/internals/custom-tools.md)
