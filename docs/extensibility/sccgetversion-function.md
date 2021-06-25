---
description: Tato funkce získá číslo verze rozhraní API modulu plug-in správy zdrojového kódu, které podporuje modul plug-in správy zdrojového kódu.
title: SccGetVersion – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901081"
---
# <a name="sccgetversion-function"></a>SccGetVersion – funkce
Tato funkce získá číslo verze rozhraní API modulu plug-in správy zdrojového kódu, které podporuje modul plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 Datový `LONG` typ, který obsahuje číslo verze podporovaného rozhraní API modulu plug-in správy zdrojového kódu:

|WORD|Description|
|----------|-----------------|
|HIWORD|Hlavní verze|
|LOWORD|Podverze|

## <a name="remarks"></a>Poznámky
 Pokud například modul plug-in správy zdrojového kódu podporuje verzi 1.3 rozhraní API modulu plug-in správy zdrojového kódu, vrátí tato funkce 0x0103.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
