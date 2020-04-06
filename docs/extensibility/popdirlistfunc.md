---
title: POPDIRLISTFUNC | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702084"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Toto je funkce zpětného volání udělená funkci [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) k aktualizaci kolekce adresářů a (volitelně) názvů souborů, aby bylo třeba zjistit, které jsou pod správou zdrojového kódu.

 Zpětné `POPDIRLISTFUNC` volání by měla být volána pouze pro ty adresáře `SccPopulateDirList` a názvy souborů (v seznamu dané funkce), které jsou ve skutečnosti pod správou zdrojového kódu.

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

[v] Uživatelská hodnota daná [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bSložka

[v] `TRUE` pokud je `lpDirectoryOrFileName` název v adresáři; v opačném případě je název souboru.

 název lpDirectoryOrFileName

[v] Úplná místní cesta k adresáři nebo názvu souboru, který je pod správou zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Rozhraní IDE vrátí odpovídající kód chyby:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pokračujte ve zpracování.|
|SCC_I_OPERATIONCANCELED|Zastavit zpracování.|
|SCC_E_xxx|Jakékoli příslušné chyby správy zdrojového kódu by měl zastavit zpracování.|

## <a name="remarks"></a>Poznámky
 Pokud `fOptions` parametr `SccPopulateDirList` funkce obsahuje `SCC_PDL_INCLUDEFILES` příznak, seznam bude pravděpodobně obsahovat názvy souborů i názvy adresářů.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kódy chyb](../extensibility/error-codes.md)
