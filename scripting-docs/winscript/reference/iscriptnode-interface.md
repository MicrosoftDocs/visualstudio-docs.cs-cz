---
title: Rozhraní Iscriptnode – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577507"
---
# <a name="iscriptnode-interface"></a>IScriptNode – rozhraní
Objekt, který implementuje rozhraní `IScriptNode` představuje webovou stránku.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `IScriptNode` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Označuje, zda je objekt stále aktivní.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Přidá podřízenou instanci `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Přidá skriptletu jako podřízenou instanci `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Odstraní strom objektů.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Vrátí podřízenou položku, která se nachází na zadaném indexu v uzlu.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Vrátí hodnotu definovanou aplikací, která se používá k přidružení skriptletu k objektu hostitele.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Vrátí index objektu v podřízeném seznamu nadřazených objektů.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Vrátí skriptovací jazyk, který je používán aktuálním uzlem skriptu.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Vrátí počet podřízených uzlů objektu `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Vrátí objekt `IScriptNode`, který je nadřazený objektem objektu.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)