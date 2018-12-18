---
title: Idsymbol – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d88acb221abfc26c45c9002abb92f704936334b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500378"
---
# <a name="idsymbol-element"></a>Idsymbol – element
`IDSymbol` Prvek obsahuje ID GUID:ID pár, který představuje nabídky, skupiny nebo příkaz. Identifikátor GUID pochází z nadřazeného `GuidSymbol` elementu. `IDSymbol` Element má `name` atribut, který poskytuje popisný název pro Identifikátor, který je součástí `value` atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Požadováno. Název symbolu ID.|  
|value|Požadováno. Číselná hodnota ID ID symbolu.|  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Guidsymbol – element](../extensibility/guidsymbol-element.md)|Obsahuje GUID GUID:ID pár, který představuje nabídky, skupiny nebo příkaz. Skupiny `IDSymbol` elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Každý `IDSymbol` element v danou `GuidSymbol` element musí mít jedinečný `value`. Ale `IDSymbol` prvky, které mají stejné hodnoty může existovat v balíčku tak dlouho, dokud mají jiné nadřazené položky.  
  
## <a name="see-also"></a>Viz také:  
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)