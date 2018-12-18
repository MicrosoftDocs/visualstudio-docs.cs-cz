---
title: Maxframeworkversion – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5201d42bddb02eade61546ee61ae99283347082
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778173"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje maximální verzi rozhraní .NET Framework, který vyžaduje šablony. Určuje, zda šablony se zobrazí v **šablony** část **přidat nový projekt** dialogovém okně na základě hodnoty vybrané v **cílovou verzi rozhraní Framework** pomocí boxingu **přidat nový projekt** dialogové okno.  
  
 \<Vstemplate – >  
 \<Maxframeworkversion – >  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Rozděluje šablonu a definuje, jak se zobrazí buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Text musí být nejvyšší číslo verze rozhraní .NET Framework, který je povolen pomocí šablony.  
  
## <a name="remarks"></a>Poznámky  
 `MaxFrameworkVersion` je volitelný prvek. Element v `TemplateData` část souboru .vstemplate funguje jako filtr pro **šablony** část **přidat nový projekt** dialogové okno. Pouze šablony, jehož požadavky na rozhraní .NET Framework jsou menší než `MaxFrameworkVersion` hodnoty prvků se zobrazí, na základě hodnoty vybrané v **cílovou verzi rozhraní Framework** pomocí boxingu **přidat nový projekt**dialogové okno. `MaxFrameworkVersion` Elementu musí vynechat, pokud to není nutné, aby nedopatřením šablony zobrazení při použití s novějšími verzemi rozhraní .NET Framework.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro standardní [!INCLUDE[csprcs](../includes/csprcs-md.md)] šablony třídy.  
  
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
  
 V tomto příkladu, maximální verze rozhraní .NET Framework, která je nutná šablonou, reprezentovaný `MaxFrameworkVersion`, je 3.5. Výše uvedené šablony se zobrazí, pouze když zvolíte 3.0 nebo 3.5 v **cílovou verzi rozhraní Framework** pole **přidat nový projekt** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)

