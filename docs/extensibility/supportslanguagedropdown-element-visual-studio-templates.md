---
title: Supportslanguagedropdown – Element (šablony sady Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b02dcf9b54cfec3dcccca62f9529291e01a912f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138825"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown – element (šablony sady Visual Studio)
Určuje, zda Web šablony položek se shoduje více jazyků a zda **jazyk** je zapnuta možnost **přidat novou položku** dialogové okno.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Supportslanguagedropdown – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Rozděluje šablonu a definuje, jak se zobrazuje v buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Text musí být buď `true` nebo `false`, která udává, jestli **jazyk** možnost je dostupná z **přidat novou položku** dialogové okno.  
  
## <a name="remarks"></a>Poznámky  
 `SupportsLanguageDropDown` je volitelný element. Výchozí hodnota je `false`.  
  
 `SupportsLanguageDropDown` Element je dostupná jenom pro webové šablony položek.  
  
 Je nastavena na hodnotu pro tento element `true`, pak šablony položky je stejný pro všechny programovací jazyky a **jazyk** v povolena možnost **přidat novou položku** dialogové okno. Tato možnost umožňuje vybrat programovací jazyk nové položky, kterou chcete vytvořit ze šablony.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje zobrazíte **jazyk** rozevírací nabídky možnost.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)