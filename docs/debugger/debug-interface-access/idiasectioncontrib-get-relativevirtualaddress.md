---
description: Načte relativní virtuální adresu (RVA) pro obrázek příspěvku.
title: 'IDiaSectionContrib:: get_relativeVirtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relativeVirtualAddress method
ms.assetid: 32f9674d-94f1-4590-99de-a2eb60da4af8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4bd7e1271ed163e9efe4971ca4af08858e79c7ff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147994"
---
# <a name="idiasectioncontribget_relativevirtualaddress"></a>IDiaSectionContrib::get_relativeVirtualAddress
Načte relativní virtuální adresu (RVA) pro obrázek příspěvku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí adresu RVA příspěvku pro obrázek.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
