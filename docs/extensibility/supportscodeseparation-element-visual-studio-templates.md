---
title: SupportsCodeSeparation – element (šablony sady Visual Studio)
titleSuffix: ''
description: Přečtěte si o prvku SupportsCodeSeparation – a o tom, jak určuje, jestli je v dialogovém okně Přidat novou položku povoleno zaškrtávací políčko umístit kód do samostatného souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 699d38f712885d1e2b08a111baa7db75fb7829da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056126"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation – element (šablony sady Visual Studio)
Určuje, zda je v dialogovém okně **Přidat novou položku** povoleno zaškrtávací políčko **umístit kód do samostatného souboru** .

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Syntax

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy
 Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Nová položka** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být buď `true` nebo `false` , což značí, zda je v dialogovém okně **Přidat novou položku** povoleno zaškrtávací políčko **umístit kód do samostatného souboru** .

## <a name="remarks"></a>Poznámky
 `SupportsCodeSeparation` je volitelný prvek. Výchozí hodnota je `false`.

 `SupportsCodeSeparation`Element je k dispozici pouze pro šablony webových položek.

 Oddělení kódu nebo model stránky s kódem na pozadí umožňuje uchovávat značky v jednom souboru a programový kód v jiném souboru. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a jiné jazyky .NET používají tento model.

## <a name="example"></a>Příklad
 Následující příklad určuje, že se má **v samostatném souboru zobrazit možnost umístit kód** .

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
