---
title: Iscriptnode – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796287"
---
# <a name="iscriptnode-interface"></a>IScriptNode – rozhraní
Objekt, který implementuje `IScriptNode` rozhraní představuje webovou stránku.  
  
 Kromě metod zděděno z `IUnknown`, `IScriptNode` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Určuje, zda je objekt stále aktivní.|  
|[Iscriptnode –:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Přidá podřízený instanci `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Přidá skriptletu jako podřízené instanci `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Odstraní stromu objektů.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Vrací podřízeného, který je v zadaném indexu v uzlu.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Vrátí hodnotu definované aplikací, který se používá pro přidružení skriptlet objekt hostitele.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Vrátí index objektu v seznamu podřízených nadřazeného objektu.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Vrátí skriptovací jazyk, který používá aktuální uzel skriptu.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Vrátí počet podřízených prvků `IScriptNode` objektu.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Vrátí `IScriptNode` objekt, který je nadřazeného objektu.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)