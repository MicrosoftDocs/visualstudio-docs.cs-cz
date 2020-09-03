---
title: 'IDiaImageData:: get_relativeVirtualAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_relativeVirtualAddress method
ms.assetid: e6d6deee-dc12-4b38-af15-f917b2d4368e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03233b0fad369786a58374ac7949ed2182559f7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202232"
---
# <a name="idiaimagedataget_relativevirtualaddress"></a>IDiaImageData::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte umístění ve virtuální paměti modulu vzhledem k aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí relativní posun virtuální paměti modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
