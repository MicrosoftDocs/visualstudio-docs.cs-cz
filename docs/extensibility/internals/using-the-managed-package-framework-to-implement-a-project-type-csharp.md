---
title: Použití architektury spravovaného balíčku pro typ projektu (C#) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704124"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Použití rozhraní MPF (Managed Package Framework) k implementaci typu projektu (C#)
Rozhraní MPF (Managed Package Framework) poskytuje třídy Jazyka C#, které můžete použít nebo zdědit k implementaci vlastních typů projektů. MPF implementuje mnoho rozhraní Visual Studio očekává, že typ projektu poskytnout, takže můžete soustředit na implementaci podrobnosti typu projektu.

## <a name="using-the-mpf-project-source-code"></a>Použití zdrojového kódu projektu MPF
 Architektura spravovaného balíčku pro projekty (MPFProj) poskytuje pomocné třídy pro vytváření a správu nového systému projektu. Na rozdíl od jiných tříd v MPF, třídy projektu nejsou zahrnuty v sestavení chod u sady Visual Studio. Místo toho jsou třídy projektu k dispozici jako zdrojový kód na [MPF pro projekty 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Chcete-li přidat tento projekt do řešení VSPackage, postupujte takto:

1. Stáhněte soubory MPFProj do *MPFProjectDir*.

2. V *souboru MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file změňte následující blok:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Vytvořte projekt VSPackage.

2. Uvolnění projektu VSPackage.

3. Upravte soubor VSPackage .csproj přidáním následujícího bloku před ostatní `<Import>` bloky:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Uložte projekt.

2. Zavřete a znovu otevřete řešení VSPackage.

3. Znovu otevřete projekt VSPackage. Měli byste vidět nový adresář s názvem ProjectBase.

4. Přidejte následující odkaz na projekt VSPackage:

     Microsoft.Build.Tasks.4.0

5. Sestavte projekt.

## <a name="hierarchy-classes"></a>Třídy hierarchie
 Následující tabulka shrnuje třídy v MPFProj, které podporují hierarchie projektů. Další informace naleznete v [tématu Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md).

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
 V následující tabulce jsou uvedeny třídy v MPF, které podporují zpracování dokumentů. Další informace naleznete v [tématu Otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Třídy konfigurace a výstupu
 V následující tabulce jsou uvedeny třídy v MPF, které umožňují typy projektů podporovat více konfigurací, jako je například ladění a vydání a kolekce výstupu projektu. Další informace naleznete v [tématu Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Třídy podpory automatizace
 V následující tabulce jsou uvedeny třídy v MPF, které podporují automatizaci tak, aby uživatelé typu projektu mohou psát doplňky.

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Třídy vlastností
 V následující tabulce jsou uvedeny třídy v MPF, které umožňují typům projektů přidávat vlastnosti, které mohou uživatelé procházet a upravovat v prohlížeči vlastností.

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
