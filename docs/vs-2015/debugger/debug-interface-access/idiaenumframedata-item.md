---
title: Idiaenumframedata::Item – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e110251cf646c99851503a04d44a8886a0fc1b81
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728653"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte datový prvek rámce pomocí indexu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 index  
 [in] Index o [idiaframedata –](../../debugger/debug-interface-access/idiaframedata.md) objekt, který se má načíst. Index je v rozsahu 0 až `count`-1, kde `count` je vrácený [idiaenumframedata::get_count –](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) metody.  
  
 section  
 [out] Vrátí [idiaframedata –](../../debugger/debug-interface-access/idiaframedata.md) objekt reprezentující datový element požadovaného snímku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Idiaenumframedata –](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



