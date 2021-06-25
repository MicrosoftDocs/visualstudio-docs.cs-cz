---
description: Tato funkce uzavírá dávku operací správy zdrojového kódu.
title: SccEndBatch – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 11ff596f19d3a98b929f9346bbf579e0ad1258c5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904588"
---
# <a name="sccendbatch-function"></a>Funkce SccEndBatch
Tato funkce uzavírá dávku operací správy zdrojového kódu. Tyto dávky nemusí být vnořené.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dávka operací se úspěšně dokončila.|
|SCC_E_UNKNOWNERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Dávky správy zdrojového kódu slouží k provádění stejných operací správy zdrojového kódu napříč více projekty nebo více kontexty. Dávky lze použít k vyloučení redundantních dialogových oken z uživatelského prostředí během dávkové operace. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a funkce se používají jako pár k označení začátku `SccEndBatch` a konce operace. Nelze je vnořit.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
