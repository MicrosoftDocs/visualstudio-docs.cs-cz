---
title: Rozhraní IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572026"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames – rozhraní
Implementováno ladicím programem pro poskytnutí unwind zásobníku pro Jscript9diag. dll pro JavaScript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Name|Popis|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next – metoda](../../winscript/reference/ienumjsstackframes-next-method.md)|Získá zadaný počet snímků.|  
|[IEnumJsStackFrames::Reset – metoda](../../winscript/reference/ienumjsstackframes-reset-method.md)|Obnoví rámec zásobníku na pozici před prvním prvkem.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)