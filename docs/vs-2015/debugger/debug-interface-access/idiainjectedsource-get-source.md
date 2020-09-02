---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 856d0111e65b51b798dfe44a324c58c4db5457fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192426"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte bajty zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 pro Počet bajtů, které představují velikost datové vyrovnávací paměti.  
  
 `pcbData`  
 mimo Vrátí počet bajtů, které představují vrácené bajty. Pokud `data` je `NULL` , pak `pcbData` je celkový počet bajtů dat, který je k dispozici.  
  
 `data[]`  
 mimo Vyrovnávací paměť, která se má vyplnit zdrojovými bajty  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
