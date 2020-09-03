---
title: Použití nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1ad59e6d8f4cb88004629b0dfd2cdf0631a7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297676"
---
# <a name="using-msbuild"></a>Použití nástroje MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nástroj MSBuild poskytuje dobře definovaný rozšiřitelný formát XML pro vytváření souborů projektu, které plně popisují položky projektu, které mají být sestaveny, úkoly sestavení a konfigurace sestavení.  
  
 Kompletní ukázku jazykového projektového systému založeného na MSBuildu najdete v ukázce VSSDK Sample podrobně v[ukázkách](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Obecné předpoklady pro MSBuild  
 Soubory projektu MSBuild, například [!INCLUDE[csprcs](../../includes/csprcs-md.md)] soubory. csproj a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . vbproj, obsahují data, která se používají v době sestavování, ale mohou obsahovat také data, která se používají v době návrhu. Data při sestavení se ukládají pomocí primitiv MSBuild, včetně [prvku Item (MSBuild)](../../msbuild/item-element-msbuild.md) a [elementu Property (MSBuild)](../../msbuild/property-element-msbuild.md). Data v době návrhu, která jsou specifická pro typ projektu a všechny související podtypy projektu, jsou uložena v souboru XML, který je pro něj vyhrazený.  
  
 Nástroj MSBuild nemá nativní podporu pro objekty konfigurace, ale poskytuje podmíněné atributy pro zadávání dat specifických pro konfiguraci. Příklad:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Další informace o podmíněných atributech naleznete v tématu [podmíněné konstrukce](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Rozšíření nástroje MSBuild pro typ projektu  
 Rozhraní a rozhraní API nástroje MSBuild se mohou v budoucích verzích nástroje změnit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Proto je vhodné použít třídy spravovaného balíčku (MPF), protože poskytují stínění proti změnám.  
  
 Managed Package Framework for Projects (MPFProj) poskytuje pomocné třídy pro vytváření a správu systému nových projektů. Zdrojový kód a pokyny k kompilaci najdete na stránce [MPF pro projekty – Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
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
 [Referenční dokumentace nástroje MSBuild](../../msbuild/msbuild-reference.md)   
 [Nástroji](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Vlastní nástroje](../../extensibility/internals/custom-tools.md)
