---
description: Tato funkce zobrazuje rozdíly mezi aktuálním místním adresářem na disku klienta a odpovídajícím projektem v rámci správy zdrojového kódu.
title: SccDirDiff – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904640"
---
# <a name="sccdirdiff-function"></a>SccDirDiff – funkce
Tato funkce zobrazuje rozdíly mezi aktuálním místním adresářem na disku klienta a odpovídajícím projektem v rámci správy zdrojového kódu.

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

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpDirName

[v] Plně kvalifikovaná cesta k místnímu adresáři, pro který chcete zobrazit vizuální rozdíl.

 dwFlags

[v] Příznaky příkazů (viz část Poznámky).

 pvOptions

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Adresář na disku je stejný jako projekt v rámci správy zdrojového kódu.|
|SCC_I_FILESDIFFER|Adresář na disku se liší od projektu ve řízení zdrojového kódu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Adresář není pod schůdou zdrojového kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecikátní selhání.|
|SCC_E_FILENOTEXIST|Místní adresář se nenašel.|

## <a name="remarks"></a>Poznámky
 Tato funkce slouží k instruování modulu plug-in správy zdrojového kódu, aby uživateli zobrazí seznam změn v zadaném adresáři. Modul plug-in otevře vlastní okno ve formátu podle svého výběru a zobrazí rozdíly mezi adresářem uživatele na disku a odpovídajícím projektem ve řízení verzí.

 Pokud modul plug-in podporuje porovnání adresářů vůbec, musí podporovat porovnání adresářů na základě názvu souboru, i když nejsou podporovány možnosti rychlého rozdílu.

|`dwFlags`|Interpretace|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Porovnání bez rozlišení velkých a malých písmen (lze použít pro rychlý rozdíl nebo vizuál).|
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné znaky (lze použít pro rychlý rozdíl nebo vizuál).|
|SCC_DIFF_QD_CONTENTS|Pokud je modul plug-in správy zdrojového kódu podporován, bezobslužně porovná adresář byte byte.|
|SCC_DIFF_QD_CHECKSUM|Pokud modul plug-in podporuje, bezobslužně porovná adresář prostřednictvím kontrolního součtu, nebo pokud není podporován, vrátí se zpět k SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Pokud modul plug-in podporuje, bezobslužně porovná adresář prostřednictvím jeho časového razítka, nebo pokud není podporován, vrátí se zpět na SCC_DIFF_QD_CHECKSUM nebo SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Tato funkce používá stejné příznaky příkazu jako [SccDiff](../extensibility/sccdiff-function.md). Modul plug-in správy zdrojového kódu se ale může rozhodnout, že nepodporuje operaci "quick-diff" pro adresáře.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
