---
title: Funkce SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720899"
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

pro Počet cest k adresáři v poli `lpDirPaths`.

 lpDirPaths

pro Pole cest adresářů k prohlédnutí

 pfnPopulate

pro Funkce zpětného volání, která se má zavolat pro každou cestu k adresáři a název souboru (volitelně) v `lpDirPaths` (podrobnosti najdete v [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) ).

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

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Chybové kódy](../extensibility/error-codes.md)