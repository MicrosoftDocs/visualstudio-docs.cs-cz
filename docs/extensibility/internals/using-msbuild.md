---
title: Použití nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27d3c5c7465314a7e9005972dec1349c1b9d89f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902228"
---
# <a name="using-msbuild"></a>Použití nástroje MSBuild
Nástroj MSBuild poskytuje dobře definovaný a rozšiřitelné formátu XML pro vytvoření souborů projektu, která plně popisují položky projektu sestavit úlohy sestavení a konfigurace sestavení.  
  
## <a name="general-msbuild-considerations"></a>Nástroj MSBuild Obecné aspekty  
 Soubory projektu MSBuild, například [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] csproj a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj soubory obsahují data, která se používá v okamžiku sestavení, ale může také obsahovat data, která se používá v době návrhu. Čas sestavení data uložená pomocí nástroje MSBuild primitiv, včetně [Item – Element (MSBuild)](../../msbuild/item-element-msbuild.md) a [Property – Element (MSBuild)](../../msbuild/property-element-msbuild.md). Doby návrhu data, která jsou specifická pro typ projektu a všechny související projekt podtypy data, uložená v volného tvaru XML pro ně vyhrazené.  
  
 MSBuild neobsahuje nativní podporu pro objekty konfigurace, ale poskytuje podmíněné atributy pro zadávání dat pro konkrétní konfiguraci. Příklad:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Další informace o podmíněné atributy, naleznete v tématu [podmíněné konstrukce](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Rozšíření nástroje MSBuild pro váš typ projektu  
 Nástroj MSBuild rozhraní a rozhraní API se můžou změnit v budoucích verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Proto je vhodné použít třídy rozhraní framework (MPF) spravovaného balíčku, protože poskytují stínění od změn.  
  
 Managed Package Framework pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nový systém projektů. Zdrojového kódu a kompilace pokyny najdete v [MPF projektů – Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Třídy specifické pro projekt MPF jsou následující:  
  
|Třída|Implementace|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` Třída tvoří obálku pro položky nástroje MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Vs generátorů tvořených jedním souborem. Úlohy nástroje MSBuild  
 Jediný soubor generátory jsou dostupné v době návrhu pouze, ale úlohy nástroje MSBuild lze použít v době návrhu a čas sestavení. Kvůli maximální flexibilitě proto použijte úlohy nástroje MSBuild k transformaci a generování kódu. Další informace najdete v tématu [vlastní nástroje](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../../msbuild/msbuild-reference.md)   
 [Nástroj MSBuild](../../msbuild/msbuild.md)   
 [Vlastní nástroje](../../extensibility/internals/custom-tools.md)