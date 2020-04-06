---
title: Funkce SccDiff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701024"
---
# <a name="sccdiff-function"></a>SccDiff
Tato funkce zobrazí (nebo volitelně pouze zkontroluje) rozdíly mezi aktuálním souborem (na místním disku) a jeho poslední verzí se změnami v systému správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 název lpFileName

[v] Název souboru, pro který je požadován rozdíl.

 fMožnosti

[v] Příkazové vlajky. Podrobnosti najdete v části Poznámky.

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pracovní kopie a verze serveru jsou identické.|
|SCC_I_FILESDIFFERS|Pracovní kopie se liší od verze pod správu zdrojového kódu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod smělou směřovač zdroj.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání; nebyl získán rozdíl.|
|SCC_E_FILENOTEXIST|Místní soubor nebyl nalezen.|

## <a name="remarks"></a>Poznámky
 Tato funkce slouží dvěma různým účelům. Ve výchozím nastavení zobrazuje seznam změn souboru. Modul plug-in správy zdrojového kódu otevře vlastní okno v libovolném formátu, ve které se rozhodne, aby se zobrazily rozdíly mezi souborem uživatele na disku a nejnovější verzí souboru pod správou zdrojového kódu.

 Alternativně ide může jednoduše potřebovat určit, zda došlo ke změně souboru. Například rozhraní IDE může být nutné určit, zda je bezpečné rezervovat soubor bez informování uživatele. V takovém případě ide prochází `SCC_DIFF_CONTENTS` ve vlajce. Modul plug-in správy zdrojového kódu musí soubor zkontrolovat na disku, bajt po bajtu proti zdrojově řízenému souboru a vrátit hodnotu označující, zda se oba soubory liší bez zobrazení cokoli uživateli.

 Jako optimalizace výkonu modul plug-in správy zdrojového kódu může použít alternativu založenou na kontrolním součtu `SCC_DIFF_CONTENTS`nebo časovém razítku namísto porovnání bajtpo bajtu, které požaduje : tyto formy porovnání jsou samozřejmě rychlejší, ale méně spolehlivé. Ne všechny systémy správy zdrojového kódu může podporovat tyto alternativní metody porovnání a modul plug-in může mít k převrácení k porovnání obsahu. Všechny moduly plug-in správy zdrojového kódu musí minimálně podporovat porovnání obsahu.

> [!NOTE]
> Příznaky rychlého rozdílu se vzájemně vylučují. Je platné předat žádné příznaky, ale není platné současně předat více než jeden. `SCC_DIFF_QUICK_DIFF`, což je maska, která kombinuje všechny příznaky, lze použít k testování, ale nikdy by neměla být předána jako parametr.

|`fOption`|Význam|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Porovnání bez rozlišování velkých a malých písmen (lze použít pro rychlý nebo vizuální rozdíl).|
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné znaky (lze použít pro rychlý nebo vizuální rozdíl).|
|SCC_DIFF_QD_CONTENTS|Tiše porovnává soubor, bajt byte.|
|SCC_DIFF_QD_CHECKSUM|Tiše porovnává soubor přes kontrolní součet, pokud je podporován. Pokud není podporována, přejde zpět na porovnání obsahu.|
|SCC_DIFF_QD_TIME|Tiše porovnává soubor prostřednictvím časového razítka, pokud je podporován. Pokud není podporována, přejde zpět na porovnání obsahu.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
