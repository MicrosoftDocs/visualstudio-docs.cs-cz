---
title: 'IJsDebugDataTarget:: FreeVirtualMemory – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577611"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory – metoda
Vydává nebo odváže oblast paměti v rámci virtuálního adresového prostoru cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 pro Adresa v cílovém procesu, kde by měla být paměť uvolněna.  
  
 `size`  
 pro Počet bajtů, které se mají odpotvrdit. Pro uvolnění oblasti paměti musí být tato hodnota nula.  
  
 `freeType`  
 pro Určuje typ bezplatné operace, která se má provést. To je obvykle MEM_RELEASE (0x8000), které uvolní určenou oblast stránek. Po operaci jsou stránky v bezplatném stavu. MEM_DECOMMIT (0x4000) lze použít místo toho k zrušení potvrzení stránek bez jejich uvolnění.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v Win32 API VirtualFree.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)