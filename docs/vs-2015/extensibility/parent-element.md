---
title: Nadřazený element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194074"
---
# <a name="parent-element"></a>Nadřazený element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nadřazený prvek tlačítka nebo pole se seznamem může být pouze skupina. Nadřazeným objektem nabídky nebo skupiny může být jakákoli jiná nabídka nebo skupina. V [elementu CommandPlacement](../extensibility/commandplacement-element.md)je tento element povinný; ve všech ostatních případech je volitelná. Pokud je tento prvek vynechán, bude odvozen nadřazený objekt `Group_Undefined:0` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|  
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které VSPackage poskytuje integrovanému vývojovému prostředí (IDE). Například položky nabídky, nabídky, panely nástrojů a pole se seznamem.|  
|[Buttons – element](../extensibility/buttons-element.md)|Prvky [prvku tlačítka](../extensibility/button-element.md) skupiny.|  
|[Menus – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|  
|[Groups – element](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů VSPackage.|  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
