---
title: Použití nástroje MSBuild | Microsoft Docs
description: Nástroj MSBuild poskytuje rozšiřitelný formát XML pro vytváření souborů projektu, které plně popisují položky projektu, které mají být sestaveny, úkoly sestavení a konfigurace sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92c423254c2e2e0a605ab3f7ff2238db41f4b45a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883126"
---
# <a name="using-msbuild"></a>Použití nástroje MSBuild
Nástroj MSBuild poskytuje dobře definovaný rozšiřitelný formát XML pro vytváření souborů projektu, které plně popisují položky projektu, které mají být sestaveny, úkoly sestavení a konfigurace sestavení.

## <a name="general-msbuild-considerations"></a>Obecné předpoklady pro MSBuild
 Soubory projektu MSBuild, například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] soubory. csproj a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . vbproj, obsahují data, která se používají v době sestavování, ale mohou obsahovat také data, která se používají v době návrhu. Data při sestavení se ukládají pomocí primitiv MSBuild, včetně [prvku Item (MSBuild)](../../msbuild/item-element-msbuild.md) a [elementu Property (MSBuild)](../../msbuild/property-element-msbuild.md). Data v době návrhu, která jsou specifická pro typ projektu a všechny související podtypy projektu, jsou uložena v souboru XML, který je pro něj vyhrazený.

 Nástroj MSBuild nemá nativní podporu pro objekty konfigurace, ale poskytuje podmíněné atributy pro zadávání dat specifických pro konfiguraci. Příklad:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Další informace o podmíněných atributech naleznete v tématu [podmíněné konstrukce](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Rozšíření nástroje MSBuild pro typ projektu
 Rozhraní a rozhraní API nástroje MSBuild se mohou v budoucích verzích nástroje změnit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Proto je vhodné použít třídy spravovaného balíčku (MPF), protože poskytují stínění proti změnám.

 Managed Package Framework for Projects (MPFProj) poskytuje pomocné třídy pro vytváření a správu systému nových projektů. Zdrojový kód a pokyny k kompilaci najdete na stránce [MPF pro projekty – Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Třídy MPF specifické pro projekt jsou následující:

|Třída|Implementace|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` Třída je obálkou pro položky MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Generátory jediného souboru vs. MSBuild – úlohy
 Jednotlivé generátory souborů jsou přístupné pouze při návrhu, ale úlohy nástroje MSBuild lze použít v době návrhu a v době sestavení. Pro zajištění maximální flexibility proto použijte úlohy MSBuild pro transformaci a generování kódu. Další informace najdete v tématu [vlastní nástroje](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Viz také
- [Referenční dokumentace nástroje MSBuild](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Vlastní nástroje](../../extensibility/internals/custom-tools.md)
