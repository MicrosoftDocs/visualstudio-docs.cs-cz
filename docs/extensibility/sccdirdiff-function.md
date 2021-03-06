---
description: Tato funkce zobrazuje rozdíly mezi aktuálním místním adresářem na klientském disku a odpovídajícím projektem v rámci správy zdrojového kódu.
title: Funkce SccDirDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98a843c061941765404397186af74ab71923a9da
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221597"
---
# <a name="sccdirdiff-function"></a>SccDirDiff – funkce
Tato funkce zobrazuje rozdíly mezi aktuálním místním adresářem na klientském disku a odpovídajícím projektem v rámci správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpDirName

pro Plně kvalifikovaná cesta k místnímu adresáři, pro který se má zobrazit vizuální rozdíl

 dwFlags

pro Příznaky příkazu (viz oddíl poznámky).

 pvOptions

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Adresář na disku je stejný jako projekt ve správě zdrojového kódu.|
|SCC_I_FILESDIFFER|Adresář na disku je jiný než projekt ve správě zdrojového kódu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Adresář není v rámci správy zdrojového kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|
|SCC_E_FILENOTEXIST|Místní adresář se nepovedlo najít.|

## <a name="remarks"></a>Poznámky
 Tato funkce slouží k tomu, aby modul plug-in správy zdrojových kódů zobrazoval uživateli seznam změn v zadaném adresáři. Modul plug-in otevře vlastní okno ve formátu svého výběru, aby zobrazoval rozdíly mezi adresářem uživatele na disku a odpovídajícím projektem v rámci správy verzí.

 Pokud modul plug-in podporuje porovnání adresářů, musí podporovat porovnání adresářů na základě názvu souboru, i když možnosti "rychlé rozdíly" nejsou podporovány.

|`dwFlags`|Interpretace|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Porovnávání bez rozlišení velkých a malých písmen (lze použít pro rychlé rozdíly nebo pro vizuální účely).|
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné znaky (lze použít buď pro rychlé rozdíly, nebo pro vizuál).|
|SCC_DIFF_QD_CONTENTS|V případě, že modul plug-in správy zdrojových kódů podporuje, tiše porovná adresář po bajtu.|
|SCC_DIFF_QD_CHECKSUM|Pokud je tento modul podporován modulem plug-in, potichě porovná adresář pomocí kontrolního součtu, nebo pokud není podporován, přejde zpět na SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Pokud je to podporováno modulem plug-in, potichě porovná adresář přes jeho časové razítko, nebo pokud není podporováno, přejde zpět na SCC_DIFF_QD_CHECKSUM nebo SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Tato funkce používá stejný příznak příkazu jako [SccDiff](../extensibility/sccdiff-function.md). Nicméně modul plug-in správy zdrojových kódů se může rozhodnout, že pro adresáře nepodporuje operaci "rychlé rozdíly".

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
