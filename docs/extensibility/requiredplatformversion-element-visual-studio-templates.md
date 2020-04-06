---
title: Prvek RequiredPlatformVersion (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701487"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Prvek RequiredPlatformVersion (šablony sady Visual Studio)
Určuje minimální verzi operačního systému, kterou šablona projektu vyžaduje, aby fungovala správně. Tento prvek se používá pro šablony [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektů, které vytvářejí aplikace.

 Hodnota `RequiredPlatformVersion` je porovnána přímo s verzí operačního systému. Pokud `RequiredPlatformVersion` je verze operačního systému vyšší, šablona se nezobrazí v dialogovém okně **Nový projekt.** Chcete-li zadat [!INCLUDE[win8](../debugger/includes/win8_md.md)] šablonu `RequiredPlatformVersion` pro nebo vyšší, nastavte hodnotu 6.2.0. Chcete-li zadat [!INCLUDE[win81](../debugger/includes/win81_md.md)] šablonu `RequiredPlatformVersion` pro nebo vyšší, nastavte hodnotu 6.3.0.

 Šablony, které `RequiredPlatformVersion`určují =8, [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] jsou kompatibilní s předchozími šablonami zákazníků.

 VSTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Syntaxe

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Žádné.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Název platformy TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje platformu, na kterou se šablona projektu zaměřuje.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

## <a name="remarks"></a>Poznámky
 Tento text určuje minimální verzi operačního systému požadovanou šablonou.

## <a name="example"></a>Příklad
 Tento příklad určuje, že [!INCLUDE[win8](../debugger/includes/win8_md.md)] šablona projektu cílí nebo novější.

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
- [Element TargetPlatformName (šablony sady Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
