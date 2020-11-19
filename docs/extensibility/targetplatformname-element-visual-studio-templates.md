---
title: TargetPlatform – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu TargetPlatform a o tom, jak Určuje platformu, na kterou se šablona projektu zaměřuje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b8f81ad86c98ab31e8f5d5dddf0efa1b2c89d85
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903985"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName – element (šablony sady Visual Studio)
Určuje platformu, na kterou se šablona projektu zaměřuje. Tento prvek slouží k určení toho, že se šablona projektu používá k vytváření [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikací.

## <a name="syntax"></a>Syntaxe

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Určuje verzi operačního systému, který cílí na šablonu projektu.|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

## <a name="remarks"></a>Poznámky
 Text musí být **Windows**.

## <a name="example"></a>Příklad
 Tento příklad určuje, zda jsou cíle šablony projektu [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo novější.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
