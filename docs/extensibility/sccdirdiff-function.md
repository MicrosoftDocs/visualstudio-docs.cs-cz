---
title: Funkce SccDirDiff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701018"
---
# <a name="sccdirdiff-function"></a>SccDirDiff
Tato funkce zobrazuje rozdíly mezi aktuálním místním adresářem na klientském disku a odpovídajícím projektem pod směřování zdrojového kódu.

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
 pKontext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 název lpDir

[v] Plně kvalifikovaná cesta k místnímu adresáři, pro který chcete zobrazit vizuální rozdíl.

 dwFlags

[v] Příznaky příkazu (viz oddíl Poznámky).

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Adresář na disku je stejný jako projekt v ovládacím prvku zdrojového kódu.|
|SCC_I_FILESDIFFER|Adresář na disku se liší od projektu v ovládacím prvku zdrojového kódu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Adresář není pod sohledem zdrojového kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifické selhání.|
|SCC_E_FILENOTEXIST|Místní adresář nebyl nalezen.|

## <a name="remarks"></a>Poznámky
 Tato funkce slouží k instruování modulu plug-in správy zdrojového kódu k zobrazení seznamu změn v zadaném adresáři. Modul plug-in otevře vlastní okno ve formátu podle vlastního výběru, aby se zobrazily rozdíly mezi adresářem uživatele na disku a odpovídajícím projektem pod správou verzí.

 Pokud modul plug-in podporuje porovnání adresářů vůbec, musí podporovat porovnání adresářů na základě názvu souboru i v případě, že možnosti "quick-diff" nejsou podporovány.

|`dwFlags`|Interpretace|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Porovnání bez rozlišování velkých a malých písmen (lze použít pro rychlý rozdíl nebo vizuální).|
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné místo (lze použít pro rychlé diff nebo vizuální).|
|SCC_DIFF_QD_CONTENTS|Pokud je podporován modulem plug-in správy zdrojového kódu, tiše porovnává adresář, bajt po bajtu.|
|SCC_DIFF_QD_CHECKSUM|Pokud je podporován modulem plug-in, tiše porovnává adresář prostřednictvím kontrolního součtu nebo, pokud není podporován, přejde zpět na SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Pokud je podporován modulem plug-in, tiše porovnává adresář prostřednictvím časového razítka, nebo pokud není podporován, vrátí se na SCC_DIFF_QD_CHECKSUM nebo SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Tato funkce používá stejné příkazové příznaky jako [SccDiff](../extensibility/sccdiff-function.md). Modul plug-in správy zdrojového kódu se však může rozhodnout nepodporovat operaci "quick-diff" pro adresáře.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
