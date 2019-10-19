---
title: 'IJsDebugDataTarget:: Allocatevirtualmemory – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577643"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory – metoda
Rezervuje nebo potvrdí oblast paměti v rámci virtuálního adresového prostoru cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 pro Adresa v cílovém procesu, kde by měla být paměť potvrzena nebo vyhrazena. Tato hodnota je obvykle nulová. v takovém případě systém zvolí adresu.  
  
 `size`  
 pro Velikost oblasti paměti, která se má přidělit (v bajtech) Systém se automaticky zaokrouhlí na hranici další stránky.  
  
 `allocationType`  
 pro Určuje typ přidělení, který má být proveden. Obvykle se jedná o &#124; MEM_COMMIT MEM_RESERVE (0x3000), který rezervuje a potvrdí přidělení v jednom kroku.  
  
 `pageProtection`  
 pro Ochrana paměti pro oblast stránek, která má být přidělena. Pokud jsou stránky potvrzené, můžete zadat libovolnou z konstant ochrany paměti (například PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 mimo Základní adresa přidělené oblasti stránek  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Funkce inicializuje paměť, která je alokována nula, pokud se nepoužije MEM_RESET. Další informace najdete v Win32 API VirtualAlloc.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)