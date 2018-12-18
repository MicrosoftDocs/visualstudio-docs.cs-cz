---
title: Supportscodeseparation – Element (šablony sady Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edd8eb9bbabb47444754d3756216fc81d02c7d7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140739"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation – element (šablony sady Visual Studio)
Určuje, jestli **umístit kód do samostatného souboru** zaškrtávací políčko je dostupné v **přidat novou položku** dialogové okno.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Supportscodeseparation – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Rozděluje šablonu a definuje, jak se zobrazuje v buď **nový projekt** nebo **nová položka** dialogové okno.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Text musí být buď `true` nebo `false`, která udává, jestli **umístit kód do samostatného souboru** zaškrtávací políčko je dostupné v **přidat novou položku** dialogové okno.  
  
## <a name="remarks"></a>Poznámky  
 `SupportsCodeSeparation` je volitelný element. Výchozí hodnota je `false`.  
  
 `SupportsCodeSeparation` Element je dostupná jenom pro webové šablony položek.  
  
 Kód oddělení nebo model kódu stránky umožňuje uchovávat značky v jeden soubor a programový kód v jiném souboru. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a jinými jazyky rozhraní .NET pomocí tohoto modelu.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje zobrazíte **umístit kód do samostatného souboru** možnost.  
  
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
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
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