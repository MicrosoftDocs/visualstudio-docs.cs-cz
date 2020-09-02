---
title: 'IDiaStackWalkHelper:: imageForVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f28af62a4e5eaa89e92db533bf461dbecaf039d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464714"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Vrátí začátek image spustitelného souboru v paměti dané virtuální adresou v paměťovém prostoru spustitelného souboru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametry
 `vaContext`

pro Virtuální adresa, která se nachází někde v prostoru spustitelného souboru.

 `pvaImageStart`

mimo Vrátí počáteční virtuální adresu obrázku spustitelného souboru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)