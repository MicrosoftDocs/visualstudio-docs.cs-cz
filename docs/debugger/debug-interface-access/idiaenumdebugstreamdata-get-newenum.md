---
title: 'IDiaEnumDebugStreamData:: get__NewEnum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get__NewEnum method
ms.assetid: 023b3e31-0fc9-478d-88e8-af2ce762f322
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54e4d7e5061130ac88facbe17b934fa91f61df19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857088"
---
# <a name="idiaenumdebugstreamdataget__newenum"></a>IDiaEnumDebugStreamData::get__NewEnum
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
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)