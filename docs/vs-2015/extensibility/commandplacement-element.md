---
title: Element CommandPlacement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43fd417c4d54c0ab57133cf6dbff2c770c1ffc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184339"
---
# <a name="commandplacement-element"></a>CommandPlacement – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element CommandPlacement umožňuje zahrnutí tlačítek, skupin a nabídek do více než jedné skupiny nebo nabídky. Pomocí elementu CommandPlacement není nutné zcela předefinovat tyto položky, aby bylo možné změnit vzhled uživatelského rozhraní.  
  
 Další informace najdete v tématu [vytváření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntax  
  
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
|guid|Povinná hodnota. Identifikátor GUID sady příkazů, jak je definováno v [elementu Symbols](../extensibility/symbols-element.md).|  
|id|Povinná hodnota. ID nabídky, skupiny nebo příkazu, který se má umístit, jak je definováno v `Symbols Element` .|  
|upřednostněn|Povinná hodnota. Určuje vizuální pozici položky v jejím nadřazeném prvku.|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Nadřazený|Povinná hodnota. Nabídka nebo skupina, která hostuje položku, která se má umístit|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[CommandPlacements – element](../extensibility/commandplacements-element.md)|Určuje skupiny prvků CommandPlacements a CommandPlacement.|  
  
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
 [Element CommandPlacements](../extensibility/commandplacements-element.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
