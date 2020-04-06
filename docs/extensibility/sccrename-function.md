---
title: Funkce SCCPřejmenovat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700433"
---
# <a name="sccrename-function"></a>SccRename – funkce
Tato funkce přejmenuje soubor v systému správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 název lpFileName

[v] Plně kvalifikovaný název souboru, který byl přejmenován.

 lpNewName

[v] Plně kvalifikovaný nový název. Pokud se cesta k adresáři liší, soubor se přesunul z jednoho podadresáře do jiného.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace přejmenování byla úspěšně dokončena.|
|SCC_E_PROJNOTOPEN|Projekt není otevřen pod směřovanou zdrojovou kódu.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod smělou směřovač zdroj.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn dokončit tuto operaci.|
|SCC_E_COULDNOTCREATEPROJECT|Projekt nelze vytvořit jako součást procesu přejmenování.|
|SCC_E_OPNOTPERFORMED|Operace nebyla provedena.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Tuto funkci lze použít k přejmenování souboru nebo jeho přesunutí z jednoho umístění do druhého v systému správy zdrojového kódu. Modul plug-in správy zdrojového kódu by se neměl pokoušet o přístup k souboru na disku. Je odpovědností ide přejmenovat místní soubor.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
