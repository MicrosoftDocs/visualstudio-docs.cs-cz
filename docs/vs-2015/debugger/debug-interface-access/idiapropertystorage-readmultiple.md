---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538080"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte zadané vlastnosti z aktuální sady vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpspec`  
 pro Počet vlastností zadaných v `rgpspec` poli Pokud je nula, metoda nevrátí žádné vlastnosti, ale vrátí `S_OK` jako kód úspěšnosti.  
  
 `rgpspec`  
 pro Pole vlastností, které mají být čteny. Vlastnosti lze zadat buď ID vlastnosti, nebo nepovinným názvem řetězce. V určitém pořadí v poli není nutné zadávat vlastnosti. Pole může obsahovat duplicitní vlastnosti. výsledkem jsou duplicitní hodnoty vlastností při návratu pro jednoduché vlastnosti. Nejednoduché vlastnosti by měly vracet odepření přístupu při pokusu o jejich otevření podruhé. Pole může obsahovat kombinaci ID vlastností a ID řetězců. Toto pole musí mít alespoň `cpspec` počet hodnot vlastností.  
  
 `rgvar`  
 [in, out] Pole `PROPVARIANT` struktur (v oboru názvů Microsoft. VisualStudio. OLE. Interop), které se má vyplnit hodnotami pro každou vlastnost. Pole musí mít `cpspec` Velikost alespoň prvky. Volající nemusí v poli inicializovat hodnoty.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud nebyla nalezena jedna nebo více vlastností. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud vlastnost nebyla nalezena, odpovídající položka v `rgvar` poli obsahuje `VARIANT` typ s typem `VT_EMPTY` .  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
