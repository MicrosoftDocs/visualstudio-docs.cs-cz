---
title: Funkce SccHistory | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700667"
---
# <a name="scchistory-function"></a>SccHistory – funkce
Tato funkce zobrazuje historii zadaných souborů.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 `pvContext`

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 `hWnd`

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 `nFiles`

[v] Počet souborů zadaných `lpFileName` v poli.

 `lpFileName`

[v] Pole plně kvalifikovaných názvů souborů.

 `fOptions`

[v] Příkazové příznaky (aktuálně nepoužívané).

 `pvOptions`

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Historie verzí byla úspěšně získána.|
|SCC_I_RELOADFILE|Systém správy zdrojového kódu skutečně upravil soubor na disku při načítání historie (například získáním staré verze), takže ide by měl znovu načíst tento soubor.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod smělou směřovač zdroj.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání. Nelze získat historii souborů.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu může zobrazit vlastní dialogové `hWnd` okno pro zobrazení historie každého souboru pomocí jako nadřazené okno. Alternativně volitelná funkce zpětného volání výstupu textu dodávané [sccOpenProject](../extensibility/sccopenproject-function.md) lze použít, pokud je podporována.

 Všimněte si, že za určitých okolností může dojít ke změně zkoumaného souboru během provádění tohoto volání. Například příkaz [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] historie dává uživateli možnost získat starou verzi souboru. V takovém případě se modul plug-in správy zdrojového kódu vrátí `SCC_I_RELOAD` a upozorní ide, že je třeba znovu načíst soubor.

> [!NOTE]
> Pokud modul plug-in správy zdrojového kódu nepodporuje tuto funkci pro pole souborů, lze zobrazit pouze historii souborů pro první soubor.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
