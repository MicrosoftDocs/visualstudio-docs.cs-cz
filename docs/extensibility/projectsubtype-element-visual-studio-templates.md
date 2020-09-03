---
title: ProjectSubType – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701832"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType – element (šablony sady Visual Studio)
Klasifikuje šablonu do podkategorie hodnoty zadané v `ProjectType` elementu.

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Syntax

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tato hodnota určuje podkategorii šablony.

## <a name="remarks"></a>Poznámky
 `ProjectSubType` je volitelný podřízený prvek elementu `TemplateData` .

 `ProjectSubType`Element poskytuje podkategorii elementu [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) . Tato hodnota může zahrnovat:

- `SmartDevice-NETCFv1`: Určuje, zda šablona cílí na [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] verzi 1,0.

- `SmartDevice-NETCFv2`: Určuje, zda šablona cílí na [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] verzi 2,0.

  Pokud šablona obsahuje `ProjectType` element s hodnotou `Web` , `ProjectSubType` element určuje programovací jazyk šablony. Tento prvek může mít následující hodnoty:

- `CSharp`: Určuje, zda šablona vytvoří [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] webový projekt nebo položku.

- `VisualBasic`: Určuje, zda šablona vytvoří [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] webový projekt nebo položku.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci zařízení cílící na [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] verzi 2,0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
- [ProjectType – element (šablony sady Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
