---
title: Funkce SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e35ae460d6ceb505bc7ad64a0e522bf2841260f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886610"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc – funkce
Tato funkce umožňuje uživateli vyhledat soubory, které již jsou v systému správy zdrojů, a následně tyto soubory zpřístupnit v rámci aktuálního projektu. Tato funkce může například získat společný hlavičkový soubor do aktuálního projektu bez kopírování souboru. Vrácené pole souborů, `lplpFileNames` , obsahuje seznam souborů, které chce uživatel přidat do projektu IDE.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpnFiles

[in, out] Vyrovnávací paměť pro počet souborů, které se přidávají do. (To znamená, `NULL` že `lplpFileNames` je uvolněna paměť, na kterou odkazovalo. Podrobnosti najdete v části poznámky.)

 lplpFileNames

[in, out] Pole ukazatelů na všechny názvy souborů bez cesty k adresáři. Toto pole je přiděleno a uvolněno modulem plug-in správy zdrojových kódů. Pokud `lpnFiles` = 1 a `lplpFileNames` není `NULL` , křestní jméno v poli, na které ukazuje, `lplpFileNames` obsahuje cílovou složku.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Soubory byly úspěšně umístěny a přidány do projektu.|
|SCC_I_OPERATIONCANCELED|Operace se zrušila bez efektu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE tuto funkci volá. Pokud modul plug-in správy zdrojových kódů podporuje zadání místní cílové složky, rozhraní IDE projde `lpnFiles` = 1 a předá název místní složky do `lplpFileNames` .

 Když volání `SccAddFromScc` funkce vrátí, modul plug-in přiřadí hodnoty k `lpnFiles` a a `lplpFileNames` podle potřeby přiděluje paměť poli názvu souboru (Všimněte si, že toto přidělení nahrazuje ukazatel v `lplpFileNames` ). Modul plug-in správy zdrojových kódů zodpovídá za umístění všech souborů do adresáře uživatele nebo do určené složky pro jmenování. Rozhraní IDE pak přidá soubory do projektu IDE.

 Nakonec rozhraní IDE tuto funkci volá podruhé a předává `NULL` pro `lpnFiles` . To je interpretováno jako speciální signál modulem plug-in správy zdrojových kódů k uvolnění paměti přidělené poli název souboru v. `lplpFileNames``.`

 `lplpFileNames` je `char ***` ukazatel. Modul plug-in správy zdrojových kódů umístí ukazatel na pole ukazatelů na názvy souborů, čímž se seznam nastaví standardním způsobem pro toto rozhraní API.

> [!NOTE]
> Počáteční verze rozhraní VSSCI API neposkytovaly způsob, jak určit cílový projekt pro přidané soubory. Aby to bylo možné, sémantika `lplpFIleNames` parametru byla vylepšena, aby byl parametrem in/out, nikoli výstupním parametrem. Je-li zadán pouze jeden soubor, tedy hodnota, na kterou odkazovalo `lpnFiles` = 1, pak první prvek `lplpFileNames` obsahuje cílovou složku. Chcete-li použít tyto nové sémantiky, rozhraní IDE zavolá `SccSetOption` funkci s `nOption` parametrem nastaveným na `SCC_OPT_SHARESUBPROJ` . Pokud modul plug-in správy zdrojových kódů nepodporuje sémantiku, vrátí `SCC_E_OPTNOTSUPPORTED` . Tím se zakáže použití funkce **Přidat ze správy zdrojového kódu** . Pokud modul plug-in podporuje funkci **Přidat ze správy zdrojového kódu** ( `SCC_CAP_ADDFROMSCC` ), musí podporovat novou sémantiku a vrátit se `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
