---
title: Funkce SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701202"
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
