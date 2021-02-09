---
title: SupportsMasterPage – – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku SupportsMasterPage – a o tom, jak určuje, zda je v dialogovém okně Přidat novou položku zaškrtnuto políčko vybrat hlavní stránku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e9509d7bc0f8141b01ed1a0a600fa5d77a6d6916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839373"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage – element (šablony sady Visual Studio)
Určuje, zda je v dialogovém okně **Přidat novou položku** zaškrtnuto políčko **Vybrat hlavní stránku** .

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

## <a name="syntax"></a>Syntax

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje data, která kategorizují šablonu, a definují, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Nová položka** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být buď `true` nebo `false` , což značí, zda je zaškrtnuto políčko **Vybrat hlavní stránku** v dialogovém okně **Přidat novou položku** .

## <a name="remarks"></a>Poznámky
 `SupportsMasterPage` je volitelný prvek. Výchozí hodnota je `false`.

 `SupportsMasterPage`Element je k dispozici pouze pro šablony webových položek.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro webový projekt, který obsahuje podporu pro stránku předlohy.

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
        <SupportsMasterPage>true</SupportsMasterPage>
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
