---
title: Funkce SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e269727441eebc93cd78b70f11fdb571f111ee8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720838"
---
# <a name="sccproperties-function"></a>SccProperties – funkce
Tato funkce zobrazuje vlastnosti správy zdrojového kódu pro soubor nebo projekt.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpFileName

pro Plně kvalifikovaný název cesty souboru nebo projektu.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vlastnosti se úspěšně zobrazily.|
|SCC_I_RELOADFILE|Systém správy verzí změnil vlastnosti souboru, takže IDE by měl tento soubor znovu načíst.|
|SCC_E_PROJNOTOPEN|Zadaný projekt nebyl otevřen ve správě zdrojového kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k zobrazení vlastností tohoto souboru nebo projektu.|
|SCC_E_FILENOTCONTROLLED|Zadaný soubor nebo projekt není pod správou zdrojových kódů.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Došlo k neznámé nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojových kódů zobrazuje vlastnosti ve vlastním dialogovém okně.

 Vlastnosti jsou definovány modulem plug-in správy zdrojových kódů a mohou se lišit od modulu plug-in s modulem plug-in. Pokud modul plug-in umožní uživateli změnit vlastnosti správy zdrojového kódu souboru, měl by vrátit `SCC_I_RELOAD` k signalizaci rozhraní IDE, že musí být tento soubor nebo projekt znovu načten.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)