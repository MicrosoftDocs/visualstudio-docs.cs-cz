---
title: Funkce SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720135"
---
# <a name="sccuninitialize-function"></a>SccUninitialize – funkce
Tato funkce vyčistí všechna přidělení nebo otevřená připojení vytvořená předchozím voláním [SccInitialize](../extensibility/sccinitialize-function.md) při přípravě na vypnutí modulu plug-in správy zdrojových kódů.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

pro Ukazatel na strukturu kontextu modulu plug-in správy zdrojového kódu vytvořenou v [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vyčištění se úspěšně dokončilo.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojových kódů zodpovídá za přípravu a uvolnění paměti, kterou modul plug-in přidělil pro strukturu kontextu. Funkce se volá jednou pro každou danou instanci modulu plug-in. Volání [SccInitialize](../extensibility/sccinitialize-function.md) předchází tomuto volání. V době volání `SccUninitialize` nemůžou být otevřené žádné projekty.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)