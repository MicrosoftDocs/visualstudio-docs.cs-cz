---
title: MaxFrameworkVersion – – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194320"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje maximální verzi .NET Framework, kterou šablona vyžaduje. Určuje, zda je šablona zobrazena v části **šablony** v dialogovém okně **Přidat nový projekt** , na základě hodnoty, která je vybrána v poli **cílová verze rozhraní** dialogového okna **Přidat nový projekt** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Syntax  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
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
  
 Text musí být nejvyšší číslo verze .NET Framework, které šablona povoluje.  
  
## <a name="remarks"></a>Poznámky  
 `MaxFrameworkVersion` je volitelný prvek. Element v části v `TemplateData` souboru. vstemplate funguje jako filtr pro oddíl **Templates** v dialogovém okně **Přidat nový projekt** . Pouze šablony, jejichž požadavky .NET Framework jsou menší než `MaxFrameworkVersion` hodnoty prvků, budou zobrazeny na základě hodnoty, která je vybrána v poli **cílová verze rozhraní** dialogového okna **Přidat nový projekt** . `MaxFrameworkVersion`Element by měl být vynechán, pokud není požadován, takže neúmyslně nechtěně nezpůsobí zobrazení šablon, pokud jsou použity v novějších verzích .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] šablonu standardní třídy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 V tomto příkladu je maximální verze .NET Framework, která je požadována šablonou reprezentovaná `MaxFrameworkVersion` , 3,5. Výše uvedená šablona se zobrazí pouze v případě, že v poli **cílová verze rozhraní** v dialogovém okně **Přidat nový projekt** vyberete hodnotu 3,0 nebo 3,5.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
