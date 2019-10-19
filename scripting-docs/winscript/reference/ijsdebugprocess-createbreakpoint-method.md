---
title: 'IJsDebugProcess:: Createbreakpoint – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575095"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint – metoda
Nastaví zarážku na zadané pozici dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `documentId`  
 pro Ukazatel na IDebugDocumentText –.  
  
 `characterOffset`  
 pro Posun znaků od začátku souboru.  
  
 `characterCount`  
 pro Délka textu dokumentu, do nějž má být vložena zarážka  
  
 `isEnabled`  
 pro Určuje, zda je povolena zarážka.  
  
 `ppDebugBreakPoint`  
 mimo Objekt představující zarážku, která byla vytvořena.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugProcess – rozhraní](../../winscript/reference/ijsdebugprocess-interface.md)