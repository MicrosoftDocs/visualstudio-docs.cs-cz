---
title: Ijsdebugdatatarget::readmemory – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794703"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory – metoda
Přečte paměť tento cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Základní adresa, ze kterého se mají číst tento cílový proces paměti.  
  
 `flags`  
 [v] Příznaky řízení chování readmemory –.  
  
 `pBuffer`  
 [out] Vyrovnávací paměti, který přijme obsah z adresního prostoru procesu cíl. Při selhání neurčené obsah této vyrovnávací paměti.  
  
 `size`  
 [v] Počet bajtů ke čtení z procesu.  
  
 `pBytesRead`  
 [out] Udává počet bajtů přečtených z tento cílový proces. Pokud JsDebugAllowPartialRead jasné, v případě úspěchu tato hodnota bude vždy rovná vstupní velikost. Pokud je zadán JsDebugAllowPartialRead, v případě úspěchu bude tato hodnota větší než nula.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí S_OK na úspěchy a selhání kódy se používají pro všechny chyby. Vrátí E_JsDEBUG_INVALID_MEMORY_ADDRESS, pokud adresa není platná. Další informace naleznete v tématu JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugdatatarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)