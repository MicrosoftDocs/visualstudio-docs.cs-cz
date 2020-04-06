---
title: Funkce SccEndBatch | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700924"
---
# <a name="sccendbatch-function"></a>SccEndBatch
Tato funkce uzavírá dávku operací správy zdrojového kódu. Tyto dávky nemusí být vnořené.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Žádné.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dávka operací byla úspěšně dokončena.|
|SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Dávky správy zdrojového kódu se používají k provádění stejných operací správy zdrojového kódu ve více projektech nebo více kontextech. Listy lze použít k odstranění redundantních dialogových oken z uživatelského prostředí během dávkové operace. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a `SccEndBatch` funkce se používají jako pár k označení začátku a konce operace. Nemohou být vnořeny.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
