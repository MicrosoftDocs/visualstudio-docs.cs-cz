---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794628"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Vrátí výsledek vyhodnocení výrazu jako řetězec a operace návratovou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Operace návratovou hodnotu.  
  
 `pbstrResult`  
 [out] Výsledek vyhodnocení výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_PENDING`|Operace je stále čekající na vyřízení.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí výsledek jako řetězec a operace vyhodnocení výrazu `HRESULT`.  
  
 Tato metoda vrátí hodnotu `S_OK` a `phrResult` vrátí `E_ABORT` Pokud `Abort` operaci zruší.  
  
## <a name="see-also"></a>Viz také  
 [Idebugexpression – rozhraní](../../winscript/reference/idebugexpression-interface.md)