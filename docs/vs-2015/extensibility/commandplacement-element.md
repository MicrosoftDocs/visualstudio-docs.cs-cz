---
title: Commandplacement – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a60949cdda6d026525dcc8be5bab8f82a0fb73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741537"
---
# <a name="commandplacement-element"></a>CommandPlacement – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commandplacement – element umožňuje tlačítka, skupiny a nabídek, které mají být zahrnuty do více než jedné skupině nebo v nabídce. Pomocí commandplacement – element nemáte zcela předefinovat tyto položky, aby bylo možné změnit vzhled uživatelského rozhraní.  
  
 Další informace najdete v tématu [vytvoření opakovaně použitelného skupiny z tlačítka](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|identifikátor GUID|Požadováno. Identifikátor guid sady příkazů, jak jsou definovány v [Symbols – Element](../extensibility/symbols-element.md).|  
|id|Požadováno. Id nabídky, skupiny nebo příkaz, který byl umístěn, jak jsou definovány v `Symbols Element`.|  
|Priorita|Požadováno. Určuje vizuální umístění položky v svého nadřízeného elementu.|  
|Podmínka|Volitelné. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Nadřazené|Požadováno. Nabídky nebo skupiny, který je hostitelem položka, která má být umístěn.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[CommandPlacements – element](../extensibility/commandplacements-element.md)|Určuje skupiny commandplacements – a commandplacement – prvků.|  
  
## <a name="example"></a>Příklad  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Viz také  
 [Commandplacements – Element](../extensibility/commandplacements-element.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

