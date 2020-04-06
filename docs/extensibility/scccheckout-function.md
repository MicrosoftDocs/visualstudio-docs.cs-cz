---
title: Funkce SccCheckout | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701097"
---
# <a name="scccheckout-function"></a>SccCheckout
Vzhledem k tomu, seznam plně kvalifikovaných názvů souborů, tato funkce zkontroluje je na místní jednotku. Komentář se vztahuje na všechny soubory, které jsou rezervovány. Argument komentáře může `null` být řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů vybraných k rezervování.

 lpNázev souboru

[v] Pole plně kvalifikovaných místních cest názvy souborů, které mají být rezervovány.

 lpKomentář

[v] Komentář, který má být použit pro každý z vybraných souborů, které jsou rezervovány.

 fMožnosti

[v] Příkazové příznaky (viz [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)).

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Check out byl úspěšný.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod sohledem zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání. Soubor nebyl rezervován.|
|SCC_E_ALREADYCHECKEDOUT|Uživatel již má soubor rezervován.|
|SCC_E_FILEISLOCKED|Soubor je uzamčen, což zakazuje vytváření nových verzí.|
|SCC_E_FILEOUTEXCLUSIVE|Jiný uživatel provedl výhradní pokladnu tohoto souboru.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Bitové příznaky používané určitými příkazy](../extensibility/bitflags-used-by-specific-commands.md)
