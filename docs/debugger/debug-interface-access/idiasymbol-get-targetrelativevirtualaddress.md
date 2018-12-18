---
title: Idiasymbol::get_targetrelativevirtualaddress – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3426fdf356e61239da2751bd068a38a4172382c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861316"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Načte relativní virtuální adresu (RVA) cíle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí adresu RVA převodní rutina cíle.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Tato vlastnost je platná pouze tehdy, pokud symbol jako [symtagenum – výčet](../../debugger/debug-interface-access/symtagenum.md) hodnotu `SymTagThunk`.  
  
 "Převodní rutina" je část kódu, který převede mezi 32-bit paměti adresní prostor (označované také jako plochý adresní prostor) a 16bitových adresní prostor, (označované jako segmentovaným adresní prostor).  
  
## <a name="see-also"></a>Viz také  
 [Idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)