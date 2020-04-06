---
title: Prvek ProvideDefaultName (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701721"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Element ProvideDefaultName (šablony sady Visual Studio)
Určuje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zda systém projektu vygeneruje výchozí název šablony v dialogovém okně **Přidat novou položku** nebo Nový **projekt.**

 \<VSTemplate \<> TemplateData> \<ProvideDefaultName>

## <a name="syntax"></a>Syntaxe

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené elementy
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být `true` `false`buď nebo , označující, zda má být v dialogovém okně **Přidat novou položku** nebo **Nový projekt** generován výchozí název šablony.

## <a name="remarks"></a>Poznámky
 `ProvideDefaultName`je volitelný prvek. Výchozí hodnota je `true`.

 Pokud `ProvideDefaultName` je `false`prvek , pole **Název** dialogových oken Přidat novou `<Enter_name>` **položku** a Nový **projekt** obsahují hodnotu .

 Pomocí elementu [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) určete výchozí název projektu nebo položky v dialogových oknech **Přidat novou položku** a **Nový projekt.** Pokud `ProvideDefaultName` je `true`hodnota prvku , vynechání `DefaultName` prvku pro projekty naplní dialogové okno s názvem šablony, to znamená hodnota z [Name](../extensibility/name-element-visual-studio-templates.md) element.

## <a name="example"></a>Příklad
 Následující příklad kódu `ProvideDefaultName` nastaví `false`prvek na .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
