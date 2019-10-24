---
title: Funkce SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721483"
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
 @No__t_0 datový typ obsahující číslo verze podporovaného rozhraní API modulu plug-in správy zdrojového kódu:

|WORD|Popis|
|----------|-----------------|
|HIWORD|Hlavní verze|
|LOWORD|Dílčí verze|

## <a name="remarks"></a>Poznámky
 Pokud například modul plug-in správy zdrojových kódů podporuje verzi 1,3 rozhraní API modulu plug-in správy zdrojového kódu, vrátí tato funkce 0x0103.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)