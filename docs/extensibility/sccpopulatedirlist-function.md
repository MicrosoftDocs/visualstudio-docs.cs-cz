---
title: Funkce SccPopulateDirList | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700558"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList – funkce
Tato funkce určuje, které adresáře a (volitelně) soubory jsou uloženy ve správě zdrojového kódu, vzhledem k tomu, seznam adresářů zkoumat.

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
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nDirs

[v] Počet cest adresáře `lpDirPaths` v poli.

 lpDirPaths

[v] Pole adresářových cest ke kontrole.

 pfnPopulate

[v] Funkce zpětného volání pro volání pro každou cestu `lpDirPaths` k adresáři a (volitelně) název souboru v (podrobnosti naleznete v [tématu POPDIRLISTFUNC).](../extensibility/popdirlistfunc.md)

 pvCallerData

[v] Hodnota, která má být předána beze změny funkci zpětného volání.

 fMožnosti

[v] Kombinace hodnot, které řídí způsob zpracování adresářů (pro možné hodnoty naleznete v části "PopulateDirList flags" v části [Bitflags Used by specific commands).](../extensibility/bitflags-used-by-specific-commands.md)

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace byla úspěšně dokončena.|
|SCC_E_UNKNOWNERROR|Došlo k chybě.|

## <a name="remarks"></a>Poznámky
 Pouze tyto adresáře a (volitelně) názvy souborů, které jsou ve skutečnosti v úložišti správy zdrojového kódu jsou předány funkci zpětného volání.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Kódy chyb](../extensibility/error-codes.md)
