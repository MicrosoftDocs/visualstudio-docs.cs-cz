---
title: Element WizardData (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3f9d2e971d944b964f4b194d1324ff960fbd24
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740389"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData – element (šablony sady Visual Studio)

Určuje vlastní kód XML.

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Syntaxe

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

Žádné.

### <a name="child-elements"></a>Podřízené elementy

Žádné.

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Obsahuje všechna metadata pro šablonu projektu, šablonu položky nebo startovní soupravu.|

## <a name="text-value"></a>Textová hodnota

Textová hodnota je volitelná.

Tento text určuje vlastní xml, který má být předáván vlastnímu rozšíření průvodce určenému v elementu [WizardExtension.](../extensibility/wizardextension-element-visual-studio-templates.md)

## <a name="remarks"></a>Poznámky

V tomto prvku lze zadat libovolný kód XML. Xml bude předán jako parametr do rozšíření vlastního průvodce, což umožňuje rozšíření použít obsah tohoto prvku. U těchto dat se neprovádí žádné ověření.

Obsah elementu **WizardData** je předán beze změny jako parametr uvnitř řetězcového `IWizard.RunStarted` slovníku parametrů v metodě. Klíč slovníku má `$wizarddata$`název .

## <a name="example"></a>Příklad

Následující příklad ilustruje metadata pro šablonu standardního projektu pro aplikaci C# Windows.

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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Viz také

- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [WizardExtension – element (šablony sady Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Postupy: Použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)
