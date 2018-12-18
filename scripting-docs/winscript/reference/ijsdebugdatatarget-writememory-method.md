---
title: Ijsdebugdatatarget::writememory – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794523"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory – metoda
Přečte paměť tento cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] Základní adresa, ze kterého chcete zapsat tento cílový proces paměti.  
  
 `pMemory`  
 [v] Data, která má být zapsán v adresním prostoru procesu zadaný.  
  
 `size`  
 [v] Počet bajtů k zápisu do procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Předtím, než dojde k přenosu dat, systém ověří, že všechna data v základní adresu a po zadanou velikost paměti je přístupný pro přístup k zápisu, a pokud není dostupný, funkce vyvolá chybu E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugdatatarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)