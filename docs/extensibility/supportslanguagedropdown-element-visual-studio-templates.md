---
title: SupportsLanguageDropDown – element (šablony sady Visual Studio)
titleSuffix: ''
description: Přečtěte si o prvku SupportsLanguageDropDown – a o tom, jak určuje, zda je šablona webové položky identická pro více jazyků, a pokud je možnost jazyka povolená.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67bf92c8c447faac2969bde3f208823158663712
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056074"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown – element (šablony sady Visual Studio)

Určuje, zda je šablona položky webu identická pro více jazyků a zda je v dialogovém okně **Přidat novou položku** možnost **jazyk** povolená.

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Syntax

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota

 Je vyžadována textová hodnota.

 Text musí být buď `true` nebo `false` , což značí, zda je možnost **jazyka** k dispozici v dialogovém okně **Přidat novou položku** .

## <a name="remarks"></a>Poznámky

 `SupportsLanguageDropDown` je volitelný prvek. Výchozí hodnota je `false`.

 `SupportsLanguageDropDown`Element je k dispozici pouze pro šablony webových položek.

 Pokud je hodnota tohoto prvku nastavena na `true` , je šablona položky shodná pro všechny programovací jazyky a možnost **jazyk** je povolena v dialogovém okně **Přidat novou položku** . Tato možnost umožňuje zvolit programovací jazyk nové položky, kterou chcete vytvořit z šablony.

## <a name="example"></a>Příklad

 Následující příklad určuje, že se má zobrazit možnost rozevíracího seznamu **jazyka** .

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
