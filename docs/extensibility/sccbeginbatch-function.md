---
title: Funkce SccBeginBatch | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701202"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch
Tato funkce spustí dávkovou posloupnost operací správy zdrojového kódu. [SccEndBatch](../extensibility/sccendbatch-function.md) bude volána k ukončení dávky. Tyto dávky nemusí být vnořené.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Parametry
 Žádné.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dávka operací byla úspěšně zahájena.|
|SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Dávky správy zdrojového kódu se používají k provádění stejných operací ve více projektech nebo více kontextech. Listy lze použít k odstranění redundantní hoprojektová dialogová okna z uživatelského prostředí během dávkové operace. Funkce `SccBeginBatch` a [SccEndBatch](../extensibility/sccendbatch-function.md) se používají jako dvojice funkcí k označení začátku a konce operace. Nemohou být vnořeny. `SccBeginBatch`nastaví příznak označující, že probíhá dávková operace.

 Zatímco dávková operace je v platnosti, modul plug-in správy zdrojového kódu by měl prezentovat maximálně jedno dialogové okno pro všechny otázky pro uživatele a použít odpověď z tohoto dialogového okna na všechny následné operace.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
