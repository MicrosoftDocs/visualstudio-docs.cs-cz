---
title: IDiaPropertyStorage::ReadMultiple | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b8be22e2a855f19c412725833fa18e182ebff6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904041"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Přečte určený vlastností z aktuální sadu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpspec`  
 [in] Počet podle vlastnosti `rgpspec` pole. Pokud je nula, metoda vrátí žádné vlastnosti, ale vrátí `S_OK` jako kód úspěchu.  
  
 `rgpspec`  
 [in] Pole vlastnosti pro čtení. Vlastnosti lze zadat ID vlastnosti nebo názvu volitelný řetězec. Není potřeba zadávat vlastnosti v libovolném pořadí v poli. Pole může obsahovat duplicitní vlastnosti, což vede k duplicitní vlastnost hodnoty na návratovou hodnotu pro jednoduché vlastnosti. Non jednoduché vlastnosti by měla vrátit odepřen přístup při pokusu otevřít znovu. Pole může obsahovat kombinaci ID vlastnosti a řetězec ID. Toto pole musí mít minimálně `cpspec` počet hodnot vlastností.  
  
 `rgvar`  
 [out v] Pole `PROPVARIANT` struktury (v oboru názvů sestavení Microsoft.VisualStudio.OLE.Interop) Chcete-li vyplní hodnoty pro každou vlastnost. Pole musí být dlouhý aspoň `cpspec` prvky velikosti. Volající není potřeba inicializovat hodnoty v poli.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` Pokud jeden nebo více vlastností nebyl nalezen. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nebyla nalezena vlastnost, odpovídající položku v `rgvar` obsahuje pole `VARIANT` s typem `VT_EMPTY`.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)