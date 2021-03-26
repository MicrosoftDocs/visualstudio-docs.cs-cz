---
description: Tato funkce zobrazuje rozdíl mezi aktuálním souborem (na místním disku) a jeho poslední verzí vrácenou se změnami v systému správy zdrojového kódu (nebo volitelně pouze kontroly).
title: Funkce SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 151620a81af515bd8cd74938a1006d4a98959dd9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073986"
---
# <a name="sccdiff-function"></a>SccDiff – funkce
Tato funkce zobrazuje rozdíl mezi aktuálním souborem (na místním disku) a jeho poslední verzí vrácenou se změnami v systému správy zdrojového kódu (nebo volitelně pouze kontroly).

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpFileName

pro Název souboru, pro který je požadován rozdíl.

 fOptions

pro Příznaky příkazu Podrobnosti najdete v části poznámky.

 pvOptions

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pracovní kopie a verze serveru jsou identické.|
|SCC_I_FILESDIFFERS|Pracovní kopie se liší od verze v rámci správy zdrojového kódu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba; nezískal se rozdíl souborů.|
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|

## <a name="remarks"></a>Poznámky
 Tato funkce slouží pro dva různé účely. Ve výchozím nastavení se zobrazí seznam změn souboru. Modul plug-in správy zdrojových kódů otevře vlastní okno v libovolném formátu, ve kterém se zvolí, aby se zobrazily rozdíly mezi souborem uživatele na disku a nejnovější verzí souboru v rámci správy zdrojového kódu.

 Případně může rozhraní IDE jednoduše potřebovat určit, zda došlo ke změně souboru. Rozhraní IDE může například potřebovat určit, zda je bezpečné rezervovat soubor bez informování uživatele. V takovém případě rozhraní IDE projde do `SCC_DIFF_CONTENTS` příznaku. Modul plug-in správy zdrojových kódů musí kontrolovat soubor na disku, bajt po bajtu proti souboru se správou zdrojového kódu a vracet hodnotu, která označuje, jestli se tyto dva soubory liší, aniž by uživatel musel zobrazit cokoli.

 V rámci optimalizace výkonu může modul plug-in správy zdrojových kódů použít alternativu na základě kontrolního součtu nebo časového razítka namísto porovnání po bajtech, které je vyvoláno pomocí `SCC_DIFF_CONTENTS` : tyto formy porovnání jsou zjevně rychlejší, ale méně spolehlivé. Ne všechny systémy správy zdrojového kódu mohou podporovat tyto alternativní metody porovnání a modul plug-in může přejít zpět na porovnání obsahu. Všechny moduly plug-in správy zdrojového kódu musí přinejmenším podporovat porovnání obsahu.

> [!NOTE]
> Příznaky rychlého rozdílu se vzájemně vylučují. Je platný pro předání žádného příznaku, ale není platná současně předávat více než jeden příznak. `SCC_DIFF_QUICK_DIFF`, což je maska, která kombinuje všechny příznaky, lze použít k otestování, ale neměla by být nikdy předána jako parametr.

|`fOption`|Význam|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Porovnávání bez rozlišení velkých a malých písmen (může být použito pro rychlý nebo vizuální rozdíl).|
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné znaky (lze použít buď pro rychlý, nebo pro vizuální rozdíl).|
|SCC_DIFF_QD_CONTENTS|Potichě porovná soubor bajt po bajtu.|
|SCC_DIFF_QD_CHECKSUM|Bez tiché porovná soubor prostřednictvím kontrolního součtu, pokud je tato podpora podporována. Pokud není podporováno, přejde zpět na porovnání obsahu.|
|SCC_DIFF_QD_TIME|Bez tiché porovná soubor přes časové razítko, pokud je podporovaný. Pokud není podporováno, přejde zpět na porovnání obsahu.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
