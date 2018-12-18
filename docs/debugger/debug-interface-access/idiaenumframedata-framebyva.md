---
title: Idiaenumframedata::framebyva – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa12d481811538430385aeda08c1ea01a156d924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854010"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Vrátí objektu frame pomocí virtuální adresy (VA).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 virtualAddress  
 [in] Posouzení ohrožení zabezpečení rámce, které vás zajímají.  
  
 rámec  
 [out] Vrátí [idiaframedata –](../../debugger/debug-interface-access/idiaframedata.md) objekt, který reprezentuje rámce, který obsahuje adresu k dispozici.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` pokud neodpovídají žádná data rámec zadané adrese. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Idiaenumframedata –](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)