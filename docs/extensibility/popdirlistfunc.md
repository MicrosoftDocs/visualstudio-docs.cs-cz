---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702084"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Toto je funkce zpětného volání, která je předána funkci [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) pro aktualizaci kolekce adresářů a (volitelně) názvů souborů k zjištění, které jsou pod správou zdrojových kódů.

 `POPDIRLISTFUNC`Zpětné volání by se mělo volat pouze pro tyto adresáře a názvy souborů (v seznamu daného `SccPopulateDirList` funkce), které jsou ve skutečnosti pod správou zdrojových kódů.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

pro Hodnota uživatele zadaná pro [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` je-li název v `lpDirectoryOrFileName` adresáři, v opačném případě se jedná o název souboru.

 lpDirectoryOrFileName

pro Úplná místní cesta k adresáři nebo souboru, který se nachází v rámci správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Rozhraní IDE vrátí příslušný kód chyby:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pokračovat ve zpracování.|
|SCC_I_OPERATIONCANCELED|Zastavit zpracování.|
|SCC_E_xxx|Jakákoli vhodná Chyba správy zdrojového kódu by měla zastavit zpracování.|

## <a name="remarks"></a>Poznámky
 Pokud `fOptions` parametr `SccPopulateDirList` funkce obsahuje `SCC_PDL_INCLUDEFILES` příznak, pak seznam bude pravděpodobně obsahovat názvy souborů i názvy adresářů.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kódy chyb](../extensibility/error-codes.md)
