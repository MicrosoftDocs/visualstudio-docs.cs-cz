---
title: Používání Managed Package Framework pro implementaci typu projektu (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f248bdafaf0fdd632069e6cffe367cf0ed21135f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741974"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Použití rozhraní MPF (Managed Package Framework) k implementaci typu projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Managed Package Framework (MPF) poskytuje třídy jazyka C# můžete použít nebo dědí implementovat vlastní typy projektů. MPF mnoho rozhraní sady Visual Studio očekává, že typ projektu chcete poskytnout, implementuje, poskytne vám zdarma soustředit na implementaci údaje vašeho typu projektu.  
  
## <a name="using-the-mpf-project-source-code"></a>Pomocí MPF projektů zdrojového kódu.  
 Managed Package Framework pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nový systém projektů. Na rozdíl od jiných tříd v MPF projektů třídy nejsou součástí sestavení součástí sady Visual Studio. Místo toho jsou k dispozici tříd projektu jako zdrojový kód v [MPF projektů 2013](http://mpfproj12.codeplex.com).  
  
 Chcete-li přidat tento projekt do řešení sady VSPackage, postupujte takto:  
  
1.  Stáhnout soubory MPFProj *MPFProjectDir*.  
  
2.  V *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, změnit následující blok:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Vytvořte projekt VSPackage.  
  
2.  Uvolněte projekt VSPackage.  
  
3.  Upravit soubor .csproj VSPackage tak, že přidáte následující blok před druhou `<Import>` bloků:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Uložte projekt.  
  
2.  Zavřete a znovu otevřete řešení VSPackage.  
  
3.  Znovu otevřete projekt VSPackage. Měli byste vidět nový adresář s názvem ProjectBase.  
  
4.  Přidejte následující odkaz na projekt VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Sestavte projekt.  
  
## <a name="hierarchy-classes"></a>Hierarchie tříd  
 Následující tabulka shrnuje třídy v MPFProj, které podporují hierarchie projektu. Další informace najdete v tématu [hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Název třídy|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Třídy zpracování dokumentů  
 V následující tabulce jsou uvedeny třídy v MPF, které podporují zpracování dokumentů. Další informace najdete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Název třídy|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Konfigurace a třídy výstupu  
 V následující tabulce jsou uvedeny třídy v MPF, která aplikacím umožňují podporu více konfigurací, jako je ladění a vydání a kolekce výstup projektu typy projektů. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
|Název třídy|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Třídy pro podporu automatizace  
 V následující tabulce jsou uvedeny třídy v MPF, které podporují automatizaci, tak, aby uživatelé typu projektu můžete psát doplňky.  
  
|Název třídy|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Vlastnosti třídy  
 V následující tabulce jsou uvedeny třídy v MPF, která aplikacím umožňují typy projektů přidat vlastnosti, že uživatelé mohou procházet a upravovat v prohlížeči vlastností.  
  
|Název třídy|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

