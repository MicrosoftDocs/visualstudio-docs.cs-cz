---
title: PromptForSaveOnCreation – element (šablony sady Visual Studio)
titleSuffix: ''
description: Přečtěte si o prvku PromptForSaveOnCreation – a o tom, jak určuje, zda se uživateli zobrazí výzva k zadání umístění pro uložení projektu prostřednictvím dialogového okna Nový projekt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: e6897eb86f531ca86d0e935836683b8a0b244645
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903790"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation – – element (šablony sady Visual Studio)

Určuje, zda je uživatel vyzván k zadání umístění pro uložení projektu prostřednictvím dialogového okna **Nový projekt** při vytváření projektu. Pokud je tento prvek nastaven na `true` , pak se uživateli zobrazí výzva k zadání umístění pro uložení. Pokud není `false` , nebudou vyzváni (to znamená, že je vytvořen dočasný projekt).

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>Syntaxe

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
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

 Text musí být buď `true` nebo `false` , `true` což znamená, že při vytváření nového projektu se uživateli zobrazí výzva k zadání umístění pro uložení.

## <a name="remarks"></a>Poznámky
 `PromptForSaveOnCreation` je volitelný prvek. Výchozí hodnota je `false`.

 Dočasné projekty jsou projekty, které můžete vytvářet a upravovat bez uložení obsahu daného projektu na disku.

## <a name="example"></a>Příklad
 Následující příklad nastaví hodnotu `PromptForSaveOnCreation` EQUAL na `false` , která určuje, aby bylo možné vytvořit projekt jako dočasný projekt.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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
