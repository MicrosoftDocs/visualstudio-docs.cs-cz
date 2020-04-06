---
title: Element LocationField (šablony projektů sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702888"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Element LocationField (šablony projektů sady Visual Studio)
Určuje, zda je textové pole **Umístění** v dialogovém okně **Nový projekt** pro šablonu projektu povoleno, zakázáno nebo skryto.

 \<> VSTemplate \<> \<TemplateData>

## <a name="syntax"></a>Syntaxe

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Kategorizuje šablonu a definuje, jak se zobrazí v **novém projektu**.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Platné textové hodnoty jsou:

- `Enabled`, který určuje, že je povoleno pole **Umístění** dialogového okna **Nový projekt.**

- `Disabled`, který určuje, že pole **Umístění** dialogového okna **Nový projekt** je zakázáno.

- `Hidden`, který určuje, že pole **Umístění** dialogového okna **Nový projekt** je skryté.

## <a name="remarks"></a>Poznámky
 Výchozí hodnota je `Enabled`.

 Textové pole **Umístění** v dialogovém okně **Nový projekt** umožňuje uživatelům změnit výchozí adresář, ve kterém jsou uloženy nové projekty.

 Hodnota zadaná `Location` v prvku je dodržena pouze dialogovéokno, pokud základní systém projektu podporuje.

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
