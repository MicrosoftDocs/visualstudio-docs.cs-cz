---
title: 'IJsDebugDataTarget:: readMemory – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572430"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory – metoda
Přečte paměť cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 pro Základní adresa, ze které má být načtena paměť cílového procesu.  
  
 `flags`  
 pro Příznaky ovládající chování readMemory –.  
  
 `pBuffer`  
 mimo Vyrovnávací paměť, která přijímá obsah z adresního prostoru cílového procesu. V případě chyby není obsah této vyrovnávací paměti určen.  
  
 `size`  
 pro Počet bajtů, které mají být z procesu čteny.  
  
 `pBytesRead`  
 mimo Určuje počet přečtených bajtů z cílového procesu. Pokud je JsDebugAllowPartialRead jasné, je tato hodnota vždy přesně shodná se vstupní velikostí. Pokud je zadána hodnota JsDebugAllowPartialRead (po úspěchu), bude tato hodnota větší než nula.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí hodnotu S_OK při úspěchu a kódy selhání se používají pro všechny chyby. Vrátí E_JsDEBUG_INVALID_MEMORY_ADDRESS, pokud adresa není platná. Další informace najdete v tématu JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)