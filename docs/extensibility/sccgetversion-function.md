---
title: Funkce SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91daeca1df76f6b624d0eddf9d28222369b2cc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844538"
---
# <a name="sccgetversion-function"></a>SccGetVersion – funkce
Tato funkce získá číslo verze rozhraní API modulu plug-in správy zdrojového kódu podporovaného modulem plug-in správy zdrojových kódů.

## <a name="syntax"></a>Syntaxe

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 `LONG`Datový typ, který obsahuje číslo verze podporovaného rozhraní API modulu plug-in správy zdrojových kódů:

|WORD|Description|
|----------|-----------------|
|HIWORD|Hlavní verze|
|LOWORD|Podverze|

## <a name="remarks"></a>Poznámky
 Pokud například modul plug-in správy zdrojových kódů podporuje verzi 1,3 rozhraní API modulu plug-in správy zdrojového kódu, vrátí tato funkce 0x0103.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
