---
title: Idiaframedata::get_program – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 125c809f32b34b077fae0bb661ef9c2f010a4b8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849460"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Načte řetězec program, který se používá k výpočtu do registru, nastavte před voláním na aktuální funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí řetězec programu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Program řetězec je posloupnost makra, která je interpretován, aby bylo možné navázat prologu. Například typické zásobníku použít program řetězec `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Formát je polština zpětného zápisu, ve kterém operátory následují operandy. `T0` představuje dočasné proměnné do zásobníku. V tomto příkladu provede následující kroky:  
  
1. Přesunout obsah registru `ebp` k `T0`.  
  
2. Přidat `4` s hodnotou v `T0` vytvářel adresu, získat hodnotu z této adresy a uložení hodnoty v registru `eip`.  
  
3. Získá hodnotu z adresu uloženou v `T0` a uložit do registru tuto hodnotu `ebp`.  
  
4. Přidat `8` s hodnotou v `T0` a uložit do registru tuto hodnotu `esp`.  
  
   Všimněte si, že je řetězec program konkrétním procesoru a konvence volání pro funkci reprezentované aktuální rámec zásobníku.  
  
## <a name="see-also"></a>Viz také  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)