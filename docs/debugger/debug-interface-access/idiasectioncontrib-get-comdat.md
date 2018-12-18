---
title: Idiasectioncontrib::get_comdat – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cabd6b5736bd4f84916159a59bf43dc8442ae3b0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847749"
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
Získá příznak označující, zda je oddíl COMDAT záznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí `TRUE` oddíl je záznam sekvencí COMDAT; v opačném případě vrátí `FALSE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Záznam sekvencí COMDAT je záznam Common Object File Format (COFF), který zviditelní zabalené funkce pro linker.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)