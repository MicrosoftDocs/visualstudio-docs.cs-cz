---
title: Default – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu default a o tom, jak Určuje název, který bude systém projektu sady Visual Studio generovat pro projekt nebo položku při jejím vytvoření.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a34fa9fd362f7a344dc13f1c557f8362e9e10b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968460"
---
# <a name="defaultname-element-visual-studio-templates"></a>Default – element (šablony sady Visual Studio)
Určuje název, který bude systém projektu sady Visual Studio generovat pro projekt nebo položku při jejím vytvoření.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Syntax

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Tento text určuje výchozí název projektu nebo položky.

## <a name="remarks"></a>Poznámky
 `DefaultName` je volitelný prvek.

 Pro projekty tento prvek určuje název adresáře, ve kterém je uložen projekt na disku. Pro položky určuje název souboru zdrojového souboru.

 Když vytvoříte projekt nebo položku, můžete změnit výchozí název pomocí možnosti **název** , která je k dispozici v dialogovém okně **Nový projekt** nebo v dialogovém okně **Přidat novou položku** .

 Pokud nechcete, aby systém projektu vygeneroval výchozí název pro projekt nebo položku, pak nastavte element [ProvideDefaultName –](../extensibility/providedefaultname-element-visual-studio-templates.md) na hodnotu `False` .

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro standardní šablonu položky pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] třídu.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
