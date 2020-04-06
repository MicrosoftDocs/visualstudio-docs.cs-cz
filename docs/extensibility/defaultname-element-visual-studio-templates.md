---
title: Element DefaultName (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712310"
---
# <a name="defaultname-element-visual-studio-templates"></a>Element DefaultName (šablony sady Visual Studio)
Určuje název, který bude systém projektu sady Visual Studio generovat pro projekt nebo položku při jeho vytvoření.

 \<VSTemplate \<> TemplateData> \<DefaultName>

## <a name="syntax"></a>Syntaxe

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Tento text určuje výchozí název projektu nebo položky.

## <a name="remarks"></a>Poznámky
 `DefaultName`je volitelný prvek.

 Pro projekty tento prvek určuje název adresáře, který ukládá projekt na disk. U položek určuje název souboru zdrojového souboru.

 Při vytváření projektu nebo položky můžete upravit výchozí název pomocí možnosti **Název,** která je k dispozici buď v dialogovém okně **Nový projekt,** nebo v dialogovém okně **Přidat novou položku.**

 Pokud nechcete, aby systém projektu generoval výchozí název projektu nebo položky, `False`nastavte prvek [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) na .

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro šablonu standardní [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] položky pro třídu.

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
