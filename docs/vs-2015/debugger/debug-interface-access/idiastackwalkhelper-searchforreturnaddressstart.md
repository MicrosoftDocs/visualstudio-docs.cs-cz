---
title: Idiastackwalkhelper::searchforreturnaddressstart – | Dokumentace Microsoftu
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
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14501945db96f1e95c33c50e312e92447e266cca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775976"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhledá zadaný zásobník snímků pro zpáteční adresu na nebo blízko ní adresu určeném zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `frame`  
 [in] [Idiaframedata –](../../debugger/debug-interface-access/idiaframedata.md) objekt, který představuje aktuální rámec zásobníku.  
  
 `startAddress`  
 [in] Virtuální paměť adresa, ze kterého má být prohledávání.  
  
 `ReturnAddress`  
 [out] Vrátí funkci nejbližší zpětná adresa `startAddress`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



