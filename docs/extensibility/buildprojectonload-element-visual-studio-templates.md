---
title: Element BuildProjectOnload (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72d1981aab67762b3ee4aa8d62e0643f4c2a8963
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739948"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Element BuildProjectOnload (šablony sady Visual Studio)
Vytvoří pouze nové projekty při vytváření a jejich přidání do řešení. Celé řešení není postaveno.

Hierarchie prvků:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Syntaxe

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|`TemplateData`|Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogových oknech **Nový projekt** i Přidat **novou položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být `true` `false` buď nebo k označení, zda chcete vytvořit pouze nový projekt, když je vytvořen ze šablony.

## <a name="remarks"></a>Poznámky
 `BuildProjectOnLoad`je volitelný prvek. Výchozí hodnota je `false`.

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro šablonu Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [Atribut a element BuildOnLoad](buildonload-visual-studio-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
