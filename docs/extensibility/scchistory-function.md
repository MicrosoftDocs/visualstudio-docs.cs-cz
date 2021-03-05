---
description: Tato funkce zobrazí historii zadaných souborů.
title: Funkce SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b7e1cd6fa6d5b9b3a5ab42cd1b4cafec215deca
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220570"
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

pro Počet souborů, které jsou zadány v `lpFileName` poli.

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
 Modul plug-in správy zdrojových kódů může zobrazit vlastní dialogové okno, aby zobrazoval historii jednotlivých souborů, a to pomocí `hWnd` nadřazeného okna. Alternativně lze použít funkci zpětného volání pro textové výstupy dodané do [SccOpenProject](../extensibility/sccopenproject-function.md) , pokud je tato funkce podporována.

 Všimněte si, že za určitých okolností se může testovaný soubor změnit během provádění tohoto volání. Například [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] příkaz History dává uživateli možnost získat starou verzi souboru. V takovém případě se modul plug-in správy zdrojových kódů vrátí `SCC_I_RELOAD` k upozornění rozhraní IDE, které potřebuje k opětovnému načtení souboru.

> [!NOTE]
> Pokud modul plug-in správy zdrojových kódů nepodporuje tuto funkci pro pole souborů, lze zobrazit pouze historii souborů pro první soubor.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
