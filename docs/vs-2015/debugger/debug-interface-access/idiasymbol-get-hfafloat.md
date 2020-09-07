---
title: 'IDiaSymbol:: get_hfaFloat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaFloat method
ms.assetid: 73ddcffe-cdac-4b03-be42-82ef985d17ee
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97f635688ff5cc96885479081962c9a48fccea84
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "64782620"
---
# <a name="idiasymbolget_hfafloat"></a>IDiaSymbol::get_hfaFloat
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte příznak, který určuje, zda uživatelem definovaný typ (UDT) obsahuje homogenní data agregace s plovoucí desetinnou čárkou (HFA) typu float.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_hfaFloat(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí, `TRUE` zda parametr UDT obsahuje data HFA typu float. v opačném případě vrátí `FALSE` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2. h  
  
 Knihovna: diaguids. lib  
  
 KNIHOVNA DLL: msdia100.dll  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
