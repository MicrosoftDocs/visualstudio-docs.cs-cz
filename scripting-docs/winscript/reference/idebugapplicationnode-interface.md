---
title: Idebugapplicationnode – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793953"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode – rozhraní
`IDebugApplicationNode` Rozhraní rozšiřuje funkce `IDebugDocumentProvider` rozhraní tím, že poskytuje kontext v rámci stromu projektu.  
  
 Kromě metod zděděno z `IDebugDocumentProvider`, `IDebugApplicationNode` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Vytvoří výčet podřízené uzly uzlu této aplikace.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Vrací nadřazeného uzlu tohoto uzlu aplikace.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Nastaví zprostředkovatele dokumentu pro tento uzel aplikace.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Způsobí, že tuto aplikaci chcete uvolnit všechny odkazy a zadejte neaktivním stavu.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Tento uzel aplikace přidá do stromu zadaného projektu.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Tento uzel aplikace odebere ze stromu projektu.|