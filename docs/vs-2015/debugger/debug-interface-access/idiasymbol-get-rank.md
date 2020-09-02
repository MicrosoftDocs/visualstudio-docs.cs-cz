---
title: 'IDiaSymbol:: get_rank | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf7c39213ae2eb233509d720b7e7c2eab0a17560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64809710"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte pořadí (počet rozměrů) multidimenzionálního pole FORTRAN.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí počet dimenzí v multidimenzionálním poli FORTRAN.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Rank odkazuje na počet dimenzí v poli, kde je pole deklarováno jako `myarray[1,2,3]` . Tento příklad má pořadí 3 a 3 rozměry. Rozsah se nevztahuje na jazyk C++, který používá koncept pole polí pro každou dimenzi (tj `myarray[1][2][3]` .).  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
