---
title: Funkce SccAddFilesFromSCC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701287"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC
Tato funkce přidá seznam souborů ze správy zdrojového kódu do aktuálně otevřeného projektu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpUživatel

[dovnitř, ven] Uživatelské jméno (až SCC_USER_SIZE, včetně zakončení null).

 lpAuxProjPath

[dovnitř, ven] Pomocný řetězec identifikující projekt `SCC_PRJPATH_`(až do velikosti, včetně zakončení null).

 cSoubory

[v] Počet souborů daných `lpFilePaths`společností .

 lpFilePaths

[dovnitř, ven] Pole názvů souborů, které chcete přidat do aktuálního projektu.

 lpCíl

[v] Cílová cesta, kde mají být zapsány soubory.

 lpKomentář

[v] Komentář, který má být použit pro každý z přidávaných souborů.

 pbVýsledky

[dovnitř, ven] Pole příznaků, které jsou nastaveny tak, aby označovat úspěch (nenulová nebo PRAVDA) nebo `cFiles` selhání (nula nebo NEPRAVDA) pro každý soubor (velikost pole musí být alespoň dlouhá).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt není otevřen.|
|SCC_E_OPNOTPERFORMED|Připojení není ke stejnému projektu, jak je určeno`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn aktualizovat databázi.|
|SCC_E_NONSPECIFICERROR|Neznámou chybu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
