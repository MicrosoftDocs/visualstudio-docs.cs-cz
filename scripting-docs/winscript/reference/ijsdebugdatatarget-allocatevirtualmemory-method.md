---
title: Ijsdebugdatatarget::allocatevirtualmemory – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794673"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory – metoda
Rezerv nebo potvrdí oblasti paměti ve virtuálním adresním prostoru tento cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Adresa v rámci tento cílový proces, kde by měla být paměť potvrzené nebo vyhrazena. Tato hodnota je obvykle nule, ve kterém případ systému zvolí adresu.  
  
 `size`  
 [v] Velikost oblasti paměti k přidělení v bajtech. Systém bude automaticky zaokrouhlí na další stránce hranici.  
  
 `allocationType`  
 [v] Určuje typ přidělení k provedení. To je obvykle MEM_COMMIT &#124; MEM_RESERVE (0x3000), která si vyhrazuje a potvrdí přidělení v jednom kroku.  
  
 `pageProtection`  
 [v] Ochrana paměti pro oblast stránky, která bude přidělena. Pokud jsou přiděleny jako stránky, můžete zadat kterékoli z ochrany konstanty paměti (například PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Základní adresa přidělené oblasti stránek.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Funkce inicializuje paměti, které přiděluje na hodnotu nula, pokud se používá MEM_RESET. Další informace najdete v tématu VirtualAlloc Win32 API.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugdatatarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)