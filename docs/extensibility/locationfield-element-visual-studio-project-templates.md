---
title: LocationField – – element (šablony projektů sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a5f2f47eef9c3cb047b5550e466585ef70e8f4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770022"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField – – element (šablony projektů sady Visual Studio)
Určuje, jestli je textové pole **umístění** v dialogovém okně **Nový projekt** povolené, zakázané nebo skryté pro šablonu projektu.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Syntax

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v **novém projektu**.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Platné textové hodnoty jsou:

- `Enabled`, který určuje, že je povoleno pole **umístění** v dialogovém okně **Nový projekt** .

- `Disabled`, který určuje, že pole **umístění** v dialogovém okně **Nový projekt** je zakázáno.

- `Hidden`, který určuje, že pole **umístění** v dialogovém okně **Nový projekt** je skryté.

## <a name="remarks"></a>Poznámky
 Výchozí hodnota je `Enabled`.

 Textové pole **umístění** v dialogovém okně **Nový projekt** umožňuje uživatelům změnit výchozí adresář, ve kterém jsou uloženy nové projekty.

 Hodnota zadaná v `Location` elementu je dodržena pouze v dialogovém okně, pokud je příslušný systém projektu podporuje.

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablonu.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
