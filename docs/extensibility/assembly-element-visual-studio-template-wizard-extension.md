---
title: Element sestavení (rozšíření Průvodce šablonou sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43f5adb8abc17f0509fb58263f307e5051af85dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740063"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Element sestavení (rozšíření průvodce šablonou sady Visual Studio)
Určuje název nebo silný název sestavení, které `IWizard` implementuje rozhraní.

 \<> \<sestavení \<> vstemplate> rozšíření montovního>

## <a name="syntax"></a>Syntaxe

```
<Assembly>AssemblyName</Assembly>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Obsahuje registrační prvky pro přizpůsobení průvodce šablonou.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tento text určuje sestavení, které `IWizard` implementuje rozhraní. Tento název sestavení musí být zadán jako úplný název sestavení. Například, `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.

## <a name="remarks"></a>Poznámky
 `Assembly`je povinnýpodřízený `WizardExtension`prvek .

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro standardní šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu pro aplikaci systému Windows.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Viz také

- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)
