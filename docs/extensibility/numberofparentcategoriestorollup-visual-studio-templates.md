---
title: Element NumberOfParentCategoriesToRollUp (šablony)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b903b9d0bdab2c17dd2e489de01badad82c15473
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702358"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Element NumberOfParentCategoriesToRollUp (šablony sady Visual Studio)
Určuje počet nadřazených kategorií, které budou šablonu zobrazovat v dialogovém okně **Nový projekt.**

 \<VSTemplate \<> TemplateData> \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Syntaxe

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je `integer` vyžadována hodnota.

 Tato hodnota určuje počet nadřazených kategorií, které se zobrazí šablona v dialogovém okně **Nový projekt.**

## <a name="remarks"></a>Poznámky
 `NumberOfParentCategoriesToRollUp`je volitelný prvek.

## <a name="example"></a>Příklad
 Tento příklad ilustruje metadata [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pro aplikaci systému Windows. Pokud je šablona s tímto metadatem umístěna o dvě úrovně pod uzlem nejvyšší úrovně, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] zobrazí se v uzlu nejvyšší úrovně v dialogovém okně Nový **projekt.** Pokud `NumberOfParentCategoriesToRollUp` není nastavena, šablona se zobrazí pouze v uzlu, ve kterém je fyzicky umístěn.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
