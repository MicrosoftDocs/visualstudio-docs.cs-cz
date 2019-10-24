---
title: Funkce SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ce0b38b8e602688875549edbac671e664809482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721245"
---
# <a name="scchistory-function"></a>SccHistory – funkce
Tato funkce zobrazí historii zadaných souborů.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 `hWnd`

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 `nFiles`

pro Počet souborů zadaných v poli `lpFileName`.

 `lpFileName`

pro Pole plně kvalifikovaných názvů souborů.

 `fOptions`

pro Příznaky příkazu (aktuálně se nepoužívají).

 `pvOptions`

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Historie verzí se úspěšně získala.|
|SCC_I_RELOADFILE|Systém správy zdrojového kódu skutečně změnil soubor na disku při načítání historie (například načtením staré verze), takže by IDE měl tento soubor znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba. Nepovedlo se získat historii souborů.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojových kódů může zobrazit vlastní dialogové okno pro zobrazení historie jednotlivých souborů pomocí `hWnd` jako nadřazeného okna. Alternativně lze použít funkci zpětného volání pro textové výstupy dodané do [SccOpenProject](../extensibility/sccopenproject-function.md) , pokud je tato funkce podporována.

 Všimněte si, že za určitých okolností se může testovaný soubor změnit během provádění tohoto volání. Například příkaz historie [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] dává uživateli možnost získat starou verzi souboru. V takovém případě modul plug-in správy zdrojových kódů vrátí `SCC_I_RELOAD` pro upozornění rozhraní IDE, které potřebuje k opětovnému načtení souboru.

> [!NOTE]
> Pokud modul plug-in správy zdrojových kódů nepodporuje tuto funkci pro pole souborů, lze zobrazit pouze historii souborů pro první soubor.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)