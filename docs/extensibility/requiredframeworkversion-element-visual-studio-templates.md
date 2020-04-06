---
title: Funkce RequiredFrameworkVersion Element (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701500"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Prvek RequiredFrameworkVersion (šablony sady Visual Studio)

Určuje minimální verzi rozhraní .NET Framework, kterou šablona vyžaduje. Způsobí, že **cílové verze architektury rozbalovací** zobrazí v dialogovém okně **Nový projekt.** Prvek `RequiredFrameworkVersion` také určuje nejnižší hodnotu, která je k dispozici v rozevírací mase.

> [!IMPORTANT]
> Počínaje Visual Studio 2017 verze 15.6, cílový **rámec verze** rozevírací seznam již není filtr pro zobrazené šablony v části **Šablony** dialogového okna **Nový projekt.** Místo toho rozevírací rozbalovací akce funguje jako výběr architektury pro vybranou šablonu.

 \<VSTemplate \<> TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntaxe

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být minimální číslo verze rozhraní .NET Framework, které je požadováno pro šablonu.

## <a name="remarks"></a>Poznámky

`RequiredFrameworkVersion`je volitelný prvek. Tento prvek použijte pouze v případě, že šablona podporuje určitou minimální verzi (a novější verze, pokud existuje) rozhraní .NET Framework. Pokud zadáte `RequiredFrameworkVersion` prvek a vaše šablona nepodporuje konkrétní minimální verzi rozhraní .NET Framework, zobrazí se rozevírací seznam **Verze cílového rozhraní,** pokud není použitelná.

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

V tomto příkladu je minimální verze rozhraní .NET Framework, `RequiredFrameworkVersion`která je vyžadována šablonou, reprezentovaná rozhraním , 3.0. Projekt vytvořený pomocí této šablony může cílit na verze rozhraní .NET Framework od verze 3.0.

## <a name="see-also"></a>Viz také

- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md)
