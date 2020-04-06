---
title: Funkce SccProperties | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700507"
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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 název lpFileName

[v] Plně kvalifikovaný název cesty souboru nebo projektu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vlastnosti byly úspěšně zobrazeny.|
|SCC_I_RELOADFILE|Systém správy verzí změnil vlastnosti souboru, takže ide by měl znovu načíst tento soubor.|
|SCC_E_PROJNOTOPEN|Zadaný projekt nebyl otevřen v směřovaném zdrojovou kódu.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn zobrazit vlastnosti tohoto souboru nebo projektu.|
|SCC_E_FILENOTCONTROLLED|Zadaný soubor nebo projekt není pod smělou směřovačnou složky.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Došlo k neznámé nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu zobrazuje vlastnosti ve vlastním dialogovém okně.

 Vlastnosti jsou definovány modulem plug-in správy zdrojového kódu a mohou se lišit od modulu plug-in k modulu plug-in. Pokud modul plug-in umožňuje uživateli změnit vlastnosti správy zdrojového kódu souboru, měl by se vrátit `SCC_I_RELOAD` k signalizaci ide, že tento soubor nebo projekt je třeba znovu načíst.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
