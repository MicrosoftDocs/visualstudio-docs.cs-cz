---
title: Použití spravovaného rozhraní balíčků pro typ projektu (C#)
description: Seznamte se s architekturou spravovaného balíčku, která poskytuje třídy .NET, které můžete použít nebo zdědit z k implementaci vlastních typů projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb047c9ef8c5c47c6509a6a5947be77a488e22f5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060728"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Použití rozhraní MPF (Managed Package Framework) k implementaci typu projektu (C#)
Sada Managed Package Framework (MPF) poskytuje třídy jazyka C#, které můžete použít nebo zdědit z k implementaci vlastních typů projektů. Příkaz MPF implementuje mnoho rozhraní. Visual Studio očekává typ projektu, který má poskytnout, a zachová se soustředit na implementaci podrobností o typu projektu.

## <a name="using-the-mpf-project-source-code"></a>Použití zdrojového kódu projektu MPF
 Managed Package Framework for Projects (MPFProj) poskytuje pomocné třídy pro vytváření a správu systému nových projektů. Na rozdíl od jiných tříd v poli MPF nejsou třídy projektu zahrnuty v sestaveních dodaných se sadou Visual Studio. Místo toho jsou třídy projektu poskytovány jako zdrojový kód v [případě projektů 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Chcete-li přidat tento projekt do řešení VSPackage, postupujte následovně:

1. Stáhněte si soubory MPFProj do *MPFProjectDir*.

2. V *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.File změňte následující blok:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Vytvořte projekt VSPackage.

2. Uvolněte projekt VSPackage.

3. Upravte soubor VSPackage. csproj přidáním následujícího bloku před ostatní `<Import>` bloky:

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

3. Znovu otevřete projekt VSPackage. Měl by se zobrazit nový adresář s názvem ProjectBase.

4. Do projektu VSPackage přidejte následující odkaz:

     Microsoft. Build. Tasks. 4.0

5. Sestavte projekt.

## <a name="hierarchy-classes"></a>Třídy hierarchie
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

## <a name="document-handling-classes"></a>Třídy Document-Handling
 V následující tabulce jsou uvedeny třídy v poli MPF, které podporují zpracování dokumentů. Další informace naleznete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Třídy konfigurace a výstupu
 V následující tabulce jsou uvedeny třídy v MPF, které umožňují, aby typy projektů podporovaly více konfigurací, jako je například ladění a vydání, a kolekce výstupů projektu. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Třídy Automation-Support
 V následující tabulce jsou uvedeny třídy v MPF, které podporují automatizaci, aby uživatelé typu projektu mohli zapisovat doplňky.

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Třídy vlastností
 V následující tabulce jsou uvedeny třídy v MPF, které umožňují typy projektů přidat vlastnosti, které mohou uživatelé procházet a upravovat v prohlížeči vlastností.

|Název třídy|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
