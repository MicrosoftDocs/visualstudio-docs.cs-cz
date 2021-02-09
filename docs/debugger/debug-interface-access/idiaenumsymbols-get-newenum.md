---
title: 'IDiaEnumSymbols:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get__NewEnum method
ms.assetid: 879609ea-8e5a-4fa3-afa6-d24870fb4392
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36c093143b98f27c6baaac3ae68003f284e86589
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865172"
---
# <a name="idiaenumsymbolsget__newenum"></a>IDiaEnumSymbols::get__NewEnum
Načte <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> verzi tohoto enumerátoru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

mimo Vrátí `IUnknown` rozhraní, které představuje <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> verzi tohoto enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)