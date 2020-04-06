---
title: Funkce SccAddFromScc | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701252"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc
Tato funkce umožňuje uživateli procházet soubory, které jsou již v systému správy zdrojového kódu a následně tyto soubory součástí aktuálního projektu. Tato funkce může například získat společný soubor záhlaví do aktuálního projektu bez zkopírování souboru. Návratové pole souborů `lplpFileNames`, obsahuje seznam souborů, které chce uživatel přidat do projektu ide.

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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 lpnSoubory

[dovnitř, ven] Vyrovnávací paměť pro počet souborů, které jsou přidávány. (Toto `NULL` je, pokud `lplpFileNames` má být uvolněna paměť, na kterou se vztahuje. Podrobnosti naleznete v části Poznámky.)

 názvy lplpFile

[dovnitř, ven] Pole ukazatelů na všechny názvy souborů bez cest k adresářům. Toto pole je přiděleno a uvolněno modulem plug-in správy zdrojového kódu. Pokud `lpnFiles` = `lplpFileNames` 1 `NULL`a není , první jméno `lplpFileNames` v poli, na které se vztahuje, obsahuje cílovou složku.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Soubory byly úspěšně lokalizovány a přidány do projektu.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena bez efektu.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|

## <a name="remarks"></a>Poznámky
 IDE volá tuto funkci. Pokud modul plug-in správy zdrojového kódu podporuje zadání `lpnFiles` místní cílové složky, ide předá = 1 a předá název místní složky do `lplpFileNames`.

 Když se volání `SccAddFromScc` funkce vrátí, modul plug-in `lpnFiles` `lplpFileNames`přiřadil hodnoty a podle potřeby přidělil paměť pro pole názvů `lplpFileNames`souborů (všimněte si, že toto přidělení nahradí ukazatel v ). Modul plug-in správy zdrojového kódu je zodpovědný za umístění všech souborů do adresáře uživatele nebo do zadané složky označení. IDE pak přidá soubory do projektu IDE.

 Nakonec ide volá tuto funkci podruhé, `NULL` `lpnFiles`předávání v . Tento je interpretován jako speciální signál modulu plug-in správy zdrojového kódu pro uvolnění paměti přidělené pro pole názvu souboru`lplpFileNames``.`

 `lplpFileNames`je `char ***` ukazatel. Modul plug-in správy zdrojového kódu umístí ukazatel na pole ukazatelů na názvy souborů, čímž se seznam předává standardním způsobem pro toto rozhraní API.

> [!NOTE]
> Počáteční verze rozhraní API VSSCI neposkytly způsob, jak označit cílový projekt pro přidané soubory. Aby se tomu přizpůsobila, sémantiku parametru `lplpFIleNames` byly vylepšeny tak, aby byly parametrem in/out spíše než výstupním parametrem. Pokud je zadán pouze jeden soubor, to znamená `lpnFiles` hodnota odkazovaná na `lplpFileNames` = 1, pak první prvek obsahuje cílovou složku. Chcete-li použít tyto nové sémantiku, ide volá `SccSetOption` funkci s parametrem `nOption`nastaveným na `SCC_OPT_SHARESUBPROJ`. Pokud modul plug-in správy zdrojového kódu nepodporuje `SCC_E_OPTNOTSUPPORTED`sémantiku, vrátí . Tím zakážete použití funkce **Přidat ze správy zdrojového kódu.** Pokud modul plug-in podporuje funkci **Přidat z řízení zdrojového kódu** (`SCC_CAP_ADDFROMSCC`), `SCC_I_SHARESUBPROJOK`musí podporovat novou sémantiku a vrátit .

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
