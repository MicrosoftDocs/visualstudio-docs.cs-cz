---
title: RequiredFrameworkVersion – – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701500"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion – – element (šablony sady Visual Studio)

Určuje minimální verzi .NET Framework, kterou šablona vyžaduje. Způsobí, že se v dialogovém okně **Nový projekt** zobrazí rozevírací seznam **verze cílového rozhraní** . `RequiredFrameworkVersion`Prvek také určuje nejnižší dostupnou hodnotu v rozevíracím seznamu.

> [!IMPORTANT]
> Počínaje verzí Visual Studio 2017 verze 15,6 není v rozevíracím seznamu **verze rozhraní Target Framework** nadále filtr pro zobrazené šablony v části **šablony** v dialogovém okně **Nový projekt** . Namísto toho rozevírací seznam funguje jako výběr architektury pro vybranou šablonu.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Text musí být minimální číslo verze .NET Framework, které je pro šablonu nutné.

## <a name="remarks"></a>Poznámky

`RequiredFrameworkVersion` je volitelný prvek. Tento prvek použijte pouze v případě, že šablona podporuje konkrétní minimální verzi (a novější verze) .NET Framework. Pokud zadáte `RequiredFrameworkVersion` element a šablona nepodporuje konkrétní minimální verzi .NET Framework, zobrazí se v rozevíracím seznamu **verze rozhraní Target Framework** , pokud není k dispozici.

## <a name="example"></a>Příklad

Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablonu standardní třídy.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

V tomto příkladu je minimální verze .NET Framework, která je vyžadována šablonou, reprezentovaná šablonou, `RequiredFrameworkVersion` je 3,0. Projekt vytvořený pomocí této šablony může cílit na .NET Framework verze počínaje od 3,0.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md)
