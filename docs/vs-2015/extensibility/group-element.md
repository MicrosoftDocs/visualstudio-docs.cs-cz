---
title: Group – element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35c332682b609f6620f96cc8eb8499cca921d399
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204269"
---
# <a name="group-element"></a>Group – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje skupinu příkazů VSPackage.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|  
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|  
|upřednostněn|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Nadřazený|Nepovinný parametr. Nadřazený element tlačítka|  
|Poznámka|Volitelný komentář.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Groups – element](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů VSPackage.|  
  
## <a name="example"></a>Příklad  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>  
</Group>  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
