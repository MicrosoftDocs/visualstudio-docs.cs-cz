---
description: Tato funkce uzavře dávku operací správy zdrojového kódu.
title: Funkce SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3bad3604c57661d0e0e091299cef127d9215d56
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090210"
---
# <a name="sccendbatch-function"></a>SccEndBatch – funkce
Tato funkce uzavře dávku operací správy zdrojového kódu. Tyto dávky nemůžou být vnořené.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dávka operací se úspěšně uzavřela.|
|SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Dávky správy zdrojového kódu se používají ke spouštění stejných operací správy zdrojových kódů napříč více projekty nebo několika kontexty. Dávky lze použít k vyloučení redundantních dialogových oken z uživatelského prostředí během dávkové operace. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a `SccEndBatch` funkce slouží jako dvojice k označení začátku a konce operace. Nemohou být vnořené.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
