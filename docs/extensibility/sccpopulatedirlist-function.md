---
title: Funkce SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700558"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList – funkce
Tato funkce určuje, které adresáře a (volitelně) soubory jsou uloženy ve správě zdrojového kódu s uvedením seznamu adresářů k prohlédnutí.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parametry
 pContext

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 nDirs

pro Počet cest k adresáři v `lpDirPaths` poli

 lpDirPaths

pro Pole cest adresářů k prohlédnutí

 pfnPopulate

pro Funkce zpětného volání, která se má zavolat pro každou cestu adresáře a (volitelně) název souboru v `lpDirPaths` (podrobnosti najdete v [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) ).

 pvCallerData

pro Hodnota, která má být předána beze změny funkci zpětného volání.

 fOptions

pro Kombinace hodnot, které řídí zpracování adresářů (viz část "příznaky PopulateDirList" v [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) pro možné hodnoty).

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace se úspěšně dokončila.|
|SCC_E_UNKNOWNERROR|Došlo k chybě.|

## <a name="remarks"></a>Poznámky
 Funkci zpětného volání předávají pouze ty adresáře a (volitelně) názvy souborů, které jsou ve skutečnosti v úložišti správy zdrojů.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Kódy chyb](../extensibility/error-codes.md)
