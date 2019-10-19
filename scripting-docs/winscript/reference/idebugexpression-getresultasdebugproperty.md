---
title: 'IDebugExpression –:: GetResultAsDebugProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575931"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Vrátí výsledek vyhodnocení výrazu jako vlastnost ladění a návratové hodnoty operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 mimo Návratová hodnota operace.  
  
 `ppdp`  
 mimo Vlastnost ladění pro výraz  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_PENDING`|Tato operace stále čeká na vyřízení.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací výsledek vyhodnocení výrazu jako `IDebugProperty` a `HRESULT` operace.  
  
 Tato metoda vrací `S_OK` a `phrResult` vrátí `E_ABORT`, pokud `Abort` přeruší operaci.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugExpression –](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)