---
title: Icon – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku ikony a o tom, jak Určuje cestu a název souboru obrázku, který slouží jako ikona.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fced03b190ab46885c5d786b8374a05c3bd043b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883295"
---
# <a name="icon-element-visual-studio-templates"></a>Icon – element (šablony sady Visual Studio)
Určuje cestu a název souboru obrázku, který slouží jako ikona, která se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** pro šablonu.

 \<VSTemplate> \<TemplateData>
 \<Icon>

## <a name="syntax"></a>Syntax

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Package`|Volitelný atribut pro pokročilé scénáře uživatele.<br /><br /> Identifikátor GUID, který určuje ID balíčku sady Visual Studio.|
|`ID`|Volitelný atribut pro pokročilé scénáře uživatele.<br /><br /> Určuje ID prostředku sady Visual Studio.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Textová hodnota je povinná, `Package` Pokud `ID` nejsou použity atributy a.

 Text poskytuje cestu a název souboru ikony šablony, která se zobrazí v dialogovém okně **Nový projekt** .

## <a name="remarks"></a>Poznámky
 `Icon` je požadovaný podřízený prvek `TemplateData` .

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
