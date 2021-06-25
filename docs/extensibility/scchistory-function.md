---
description: Tato funkce zobrazí historii zadaných souborů.
title: SccHistory – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902537"
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

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 `hWnd`

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 `nFiles`

[v] Počet souborů zadaných v `lpFileName` poli

 `lpFileName`

[v] Pole plně kvalifikovaných názvů souborů

 `fOptions`

[v] Příznaky příkazů (aktuálně se nepoužíly)

 `pvOptions`

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Historie verzí se úspěšně získala.|
|SCC_I_RELOADFILE|Systém správy zdrojového kódu ve skutečnosti změnil soubor na disku při načítání historie (například získáním staré verze), takže integrované vývojové prostředí by mělo tento soubor znovu načíst.|
|SCC_E_FILENOTCONTROLLED|Soubor není ve zdrojovém kódu.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání. Historii souborů se nepokusí získat.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu může zobrazit vlastní dialogové okno pro zobrazení historie jednotlivých souborů pomocí příkazu `hWnd` jako nadřazeného okna. Případně je možné použít volitelnou funkci zpětného volání textového výstupu dodanou projektu [SccOpenProject,](../extensibility/sccopenproject-function.md) pokud je podporována.

 Všimněte si, že za určitých okolností se při provádění tohoto volání může zkoumaný soubor změnit. Například příkaz [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] history dává uživateli možnost získat starou verzi souboru. V takovém případě se modul plug-in správy zdrojového kódu vrátí, aby upozornil integrované vývojové prostředí `SCC_I_RELOAD` (IDE), že musí soubor znovu načíst.

> [!NOTE]
> Pokud modul plug-in správy zdrojového kódu nepodporuje tuto funkci pro pole souborů, může se zobrazit pouze historie souborů pro první soubor.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
