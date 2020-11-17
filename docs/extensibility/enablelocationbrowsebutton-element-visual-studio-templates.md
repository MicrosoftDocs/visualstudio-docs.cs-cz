---
title: EnableLocationBrowseButton – element (šablony sady Visual Studio)
description: Přečtěte si o prvku Enablelocationbrowsebutton – a o tom, jak určuje, zda je v dialogovém okně Nový projekt k dispozici tlačítko Procházet.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 463219218994c9ec1e0f8a5be6e43a0bfd3f5d49
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671256"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Enablelocationbrowsebutton – – element (šablony sady Visual Studio)
Určuje, zda je v dialogovém okně **Nový projekt** k dispozici tlačítko **Procházet** , aby uživatelé mohli snadno upravit výchozí adresář, do kterého je uložen nový projekt.

 \<VSTemplate> \<TemplateData>
 \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntax

```xml
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

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

 Text musí být buď `true` nebo `false` , který označuje, jestli se má v dialogovém okně **Nový projekt** zobrazit tlačítko pro **procházení** .

## <a name="remarks"></a>Poznámky
 `EnableLocationBrowseButton` je volitelný prvek. Výchozí hodnota je `true` , která zobrazuje tlačítko **Procházet** v dialogovém okně **Nový projekt** .

 V dialogovém okně **Nový projekt** Určuje textové pole **umístění** adresář, do kterého se uloží nový projekt. Tlačítko **Procházet** umožňuje upravit tento adresář zobrazením dialogového okna **umístění projektu** , které vám umožní snadno přejít do jiného adresáře, který je k dispozici z počítače, a vybrat ho jako adresář, ve kterém je nový projekt uložený.

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci systému Windows.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
