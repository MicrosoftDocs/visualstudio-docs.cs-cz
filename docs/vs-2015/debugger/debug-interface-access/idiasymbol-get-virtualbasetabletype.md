---
title: Idiasymbol::get_virtualbasetabletype – | Dokumentace Microsoftu
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
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e975cfdeff4d732c0b685665468705f6329702
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803588"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte typ ukazatele virtuální základní tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_virtualBaseTableType(  
   IDiaSymbol *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pRetVal`|[out] Vrátí [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objekt, který určuje typ základní tabulky.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Základní virtuální tabulky ukazatele (`vbtptr`) je skrytý ukazatel v [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] vtable, který zpracovává dědičnosti z virtuální základní třídy. A `vbtptr` může mít různě v závislosti na zděděné třídy.  
  
 Tato metoda vrátí [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objekt, který můžete použít k určení velikosti vbtptr.  
  
## <a name="requirements"></a>Požadavky  
  
|Požadavek|Popis|  
|-----------------|-----------------|  
|Záhlaví:|dia2.h|  
|Verze:|Ve verzi 8.0 DIA SDK|  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



