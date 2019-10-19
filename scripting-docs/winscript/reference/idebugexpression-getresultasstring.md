---
title: 'IDebugExpression –:: GetResultAsString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573515"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Vrátí výsledek vyhodnocení výrazu jako řetězec a návratovou hodnotu operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 mimo Návratová hodnota operace.  
  
 `pbstrResult`  
 mimo Výsledek vyhodnocení výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_PENDING`|Tato operace stále čeká na vyřízení.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací výsledek vyhodnocení výrazu jako řetězec a `HRESULT` operace.  
  
 Tato metoda vrací `S_OK` a `phrResult` vrátí `E_ABORT`, pokud `Abort` přeruší operaci.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugExpression – rozhraní](../../winscript/reference/idebugexpression-interface.md)