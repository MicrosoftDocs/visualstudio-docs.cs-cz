---
description: Tato funkce zobrazí vlastnosti správy zdrojového kódu pro soubor nebo projekt.
title: SccProperties – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd50353ab29c05e5e5db2dc2b3f363af46ca8aa7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904188"
---
# <a name="sccproperties-function"></a>SccProperties – funkce
Tato funkce zobrazí vlastnosti správy zdrojového kódu pro soubor nebo projekt.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parametry
 pvContext (Kontext pv)

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 lpFileName

[v] Plně kvalifikovaný název cesty k souboru nebo projektu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vlastnosti se úspěšně zobrazují.|
|SCC_I_RELOADFILE|Systém pro řízení verzí změnil vlastnosti souboru, takže integrované vývojové prostředí by mělo tento soubor znovu načíst.|
|SCC_E_PROJNOTOPEN|Zadaný projekt nebyl otevřen ve zdrojovém kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k zobrazení vlastností tohoto souboru nebo projektu.|
|SCC_E_FILENOTCONTROLLED|Zadaný soubor nebo projekt se nenachová ve zdrojovém kódu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Došlo k neznámé nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu zobrazí vlastnosti ve vlastním dialogovém okně.

 Vlastnosti jsou definovány modul plug-in správy zdrojového kódu a mohou se lišit od modulu plug-in k modulu plug-in. Pokud modul plug-in umožňuje uživateli změnit vlastnosti správy zdrojového kódu souboru, měl by se vrátit k signálu integrovaného vývojového prostředí (IDE), že tento soubor nebo projekt je potřeba `SCC_I_RELOAD` znovu načíst.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
