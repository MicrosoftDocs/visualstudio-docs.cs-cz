---
title: ProjectItem – Element (šablony sady Visual Studio položku) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fe6613288cac93034dd32a3203f1bb73004f83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747956"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem – element (šablony položek sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje soubor, který je součástí šablony položky.  
  
> [!NOTE]
>  `ProjectItem` Element přijímá různé atributy v závislosti na tom, jestli je šablona pro projekt nebo položku. Toto téma vysvětluje, `ProjectItem` – element pro položku. Pro vysvětlení, `ProjectItem` – element pro šablony projektů, naleznete v tématu [ProjectItem – Element (šablony projektů Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<ProjectItem – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`SubType`|Nepovinný atribut.<br /><br /> Určuje podtyp položky v šabloně položek s více soubory. Tato hodnota se používá k určení editoru, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] použije k otevření položky.|  
|`CustomTool`|Nepovinný atribut.<br /><br /> Nastaví CustomTool pro položku v souboru projektu.|  
|`ItemType`|Nepovinný atribut.<br /><br /> Nastaví typ položky pro položky v souboru projektu.|  
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota určující, zda položka má hodnoty parametrů, které musí být nahrazen, když je projekt vytvořen z šablony. Výchozí hodnota je `false`.|  
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název položky, který je vytvořen z šablony. Tento atribut je užitečné pro vytváření název položky pomocí nahrazení parametru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|Určuje obsah značek šablony.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 A `string` , která představuje název souboru v souboru ZIP šablony.  
  
## <a name="remarks"></a>Poznámky  
 `ProjectItem` je volitelný podřízený `TemplateContent`.  
  
 `TargetFileName` Atribut lze použít k přejmenování souborů s parametry. Například pokud soubor `MyFile.vb` existuje v kořenovém adresáři soubor ZIP šablony, ale budete chtít soubor s názvem založený na název souboru zadaný uživatelem v **přidat novou položku** dialogové okno, můžete využít následující kód XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Když je vytvořena položka z této šablony, názvu souboru se podle zadaný název uživatele v **přidat novou položku** dialogové okno. To je užitečné při vytváření šablon položek s více soubory. Další informace najdete v tématu [postupy: vytváření šablon položek vícesouborové](../ide/how-to-create-multi-file-item-templates.md) a [parametry šablony](../ide/template-parameters.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablony pro standardní položky [!INCLUDE[csprcs](../includes/csprcs-md.md)] třídy.  
  
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
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)

