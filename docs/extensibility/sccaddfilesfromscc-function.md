---
description: Tato funkce přidá seznam souborů ze správy zdrojového kódu do aktuálně otevřeného projektu.
title: Funkce SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 056e918642e75bbd74c310499544cb2500428646
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060468"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC – funkce
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
 pContext

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpUser

[in, out] Uživatelské jméno (až do SCC_USER_SIZE, včetně ukončovacího znaku null).

 lpAuxProjPath

[in, out] Pomocný řetězec identifikující projekt ( `SCC_PRJPATH_` velikost, včetně ukončovacího znaku null).

 cFiles

pro Počet souborů vydaných `lpFilePaths` .

 lpFilePaths

[in, out] Pole názvů souborů, které chcete přidat do aktuálního projektu.

 lpDestination

pro Cílová cesta, kam se mají soubory zapisovat

 lpComment

pro Komentář, který se má použít u každého přidávaného souboru.

 pbResults

[in, out] Pole příznaků, které jsou nastaveny pro indikaci úspěchu (nenulového nebo TRUE) nebo chyby (nula nebo FALSE) pro každý soubor (velikost pole musí být alespoň `cFiles` dlouhá).

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt není otevřený.|
|SCC_E_OPNOTPERFORMED|Připojení není ke stejnému projektu, jako je určeno `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k aktualizaci databáze.|
|SCC_E_NONSPECIFICERROR|Neznámou chybu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
