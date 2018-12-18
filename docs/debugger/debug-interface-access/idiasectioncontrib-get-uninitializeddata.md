---
title: Idiasectioncontrib::get_uninitializeddata – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_uninitializedData method
ms.assetid: 39736f35-6c73-4f54-a092-517192e417ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0929897f5dba77282fa056b5b1a00e05782c9f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916319"
---
# <a name="idiasectioncontribgetuninitializeddata"></a>IDiaSectionContrib::get_uninitializedData
Získá příznak, který označuje, zda oddíl obsahuje neinicializovaná data.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_uninitializedData (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí `TRUE` Pokud oddíl obsahuje neinicializovaná data; v opačném případě vrátí `FALSE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)