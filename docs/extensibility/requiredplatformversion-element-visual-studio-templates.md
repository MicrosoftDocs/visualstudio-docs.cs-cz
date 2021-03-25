---
description: Určuje minimální verzi operačního systému, který šablona projektu vyžaduje pro správnou práci.
title: RequiredPlatformVersion – element (šablony sady Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b1d7e3b8cc67f839977eb1e53d80731e59c064e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068424"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion – – element (šablony sady Visual Studio)

Určuje minimální verzi operačního systému, který šablona projektu vyžaduje pro správnou práci. Tento prvek slouží pro šablony projektu, které vytvářejí [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace.

 `RequiredPlatformVersion`Hodnota je porovnána přímo s verzí operačního systému. Pokud `RequiredPlatformVersion` je vyšší než verze operačního systému, šablona se nezobrazí v dialogovém okně **Nový projekt** . Chcete-li určit šablonu pro [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo vyšší, nastavte `RequiredPlatformVersion` na 6.2.0. Chcete-li určit šablonu pro [!INCLUDE[win81](../debugger/includes/win81_md.md)] nebo vyšší, nastavte `RequiredPlatformVersion` na 6.3.0.

 Šablony, které určují `RequiredPlatformVersion` = 8, jsou kompatibilní s předchozími [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] šablonami zákazníka.

 VSTemplate TemplateData.... TargetPlatform RequiredPlatformVersion –

## <a name="syntax"></a>Syntax

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Žádné

### <a name="attributes"></a>Atributy

 Žádné

### <a name="child-elements"></a>Podřízené prvky

 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje platformu, na kterou se šablona projektu zaměřuje.|

## <a name="text-value"></a>Textová hodnota

 Je vyžadována textová hodnota.

## <a name="remarks"></a>Poznámky

 Tento text určuje minimální verzi operačního systému, kterou šablona vyžaduje.

## <a name="example"></a>Příklad

 Tento příklad určuje, zda jsou cíle šablony projektu [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo novější.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také

- [TargetPlatform – element (šablony sady Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
