---
title: Funkce SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700233"
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
 Modul plug-in správy zdrojových kódů zodpovídá za přípravu a uvolnění paměti, kterou modul plug-in přidělil pro strukturu kontextu. Funkce se volá jednou pro každou danou instanci modulu plug-in. Volání [SccInitialize](../extensibility/sccinitialize-function.md) předchází tomuto volání. V době volání do nelze stále otevřít žádné projekty `SccUninitialize` .

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
