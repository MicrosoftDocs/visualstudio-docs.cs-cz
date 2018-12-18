---
title: Iactivescriptprofilercontrol5::enumheap2 – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793491"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 – metoda
Vrátí rozhraní ([iactivescriptprofilerheapenum – rozhraní](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), lze použít k iteraci nad objekty haldě GC v kontextu přidružené skriptovací stroj.  
  
 Můžete volat tuto metodu buď ladění nebo režimu vydání. Tato metoda by měla být volána při nečinnosti vlákna uživatelského rozhraní. Po zavolání metody žádné operace by měla být adresovat skriptovací stroj s výjimkou [iactivescriptprofilerheapenum::Next – metoda](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) dokud [iactivescriptprofilerheapenum::Next – metoda](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)vrátí S_FALSE nebo [iactivescriptprofilerheapenum – rozhraní](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) vydání ukazatel rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 enumFlags  
 Hodnota, která určuje, zda je vystaven doplňující informace o objektu odkazoval na relaci objektu. Další informace může znamenat, zda je objekt ukazuje metodu getter a setter. Další informace najdete v tématu [PROFILER_HEAP_ENUM_FLAGS – výčet](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Vrátí [iactivescriptprofilerheapenum – rozhraní](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT. Možné hodnoty jsou následující:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Halda výčtu byla úspěšně dokončena.|  
|`E_OUTOFMEMORY`|Nebyl k dispozici dostatek paměti k provedení haldy výčtu.|  
|`E_FAIL`|Došlo k vnitřní chybě.|