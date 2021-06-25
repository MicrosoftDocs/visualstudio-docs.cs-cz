---
description: Tato funkce spustí dávkovou sekvenci operací správy zdrojového kódu.
title: Funkce SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 08b9199b98e566a71bfeb95124ebd85781e69950
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904757"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch – funkce
Tato funkce spustí dávkovou sekvenci operací správy zdrojového kódu. [SccEndBatch](../extensibility/sccendbatch-function.md) bude volána pro ukončení dávky. Tyto dávky nemůžou být vnořené.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dávku operací bylo úspěšně zahájeno.|
|SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Dávky správy zdrojového kódu se používají ke spouštění stejných operací napříč více projekty nebo několika kontexty. Dávky lze použít k vyloučení redundantních dialogových oken na projekt z uživatelského prostředí během dávkové operace. `SccBeginBatch`Funkce a [SccEndBatch](../extensibility/sccendbatch-function.md) se používají jako dvojice funkcí k označení začátku a konce operace. Nemohou být vnořené. `SccBeginBatch` nastaví příznak označující, že probíhá operace dávky.

 I když je aktivní operace dávky, modul plug-in správy zdrojových kódů by měl být přítomen v jednom z dialogových oken pro každou otázku uživateli a použít odpověď z tohoto dialogového okna na všechny následné operace.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
