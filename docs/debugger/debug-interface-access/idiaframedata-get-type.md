---
title: Idiaframedata::get_type – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0209a715ece3e1fa760080ad7ccf0803d11950df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834588"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Načte typ rámce specifických pro kompilátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí hodnotu z [stackframetypeenum – výčet](../../debugger/debug-interface-access/stackframetypeenum.md) výčet, který určuje typ rámce specifických pro kompilátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Idiaframedata –](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum – výčet](../../debugger/debug-interface-access/stackframetypeenum.md)