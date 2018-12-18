---
title: Idiasectioncontrib::get_initializeddata – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_initializedData method
ms.assetid: f5c108be-a0cc-408b-9590-b8d44361810c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b972c70fd0cc8a9c7f02476434a7f8f9394a8a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866504"
---
# <a name="idiasectioncontribgetinitializeddata"></a>IDiaSectionContrib::get_initializedData
Získá příznak označující, zda oddíl obsahuje inicializovaná data.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_initializedData (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí `TRUE` Pokud oddíl obsahuje inicializovaná data; v opačném případě vrátí `FALSE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)