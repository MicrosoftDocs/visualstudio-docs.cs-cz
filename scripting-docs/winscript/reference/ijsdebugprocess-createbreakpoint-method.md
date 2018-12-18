---
title: Ijsdebugprocess::createbreakpoint – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794589"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint – metoda
Nastaví zarážce na pozici zadaný dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Ukazatel na idebugdocumenttext –.  
  
 `characterOffset`  
 [v] Znak posun od začátku souboru.  
  
 `characterCount`  
 [v] Délka textu dokumentu v rámci kterého se mají vložit zarážku.  
  
 `isEnabled`  
 [v] Určuje, zda je povoleno zarážku.  
  
 `ppDebugBreakPoint`  
 [out] Objekt reprezentující zarážek, který byl vytvořen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugprocess – rozhraní](../../winscript/reference/ijsdebugprocess-interface.md)