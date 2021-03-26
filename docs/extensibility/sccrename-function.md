---
description: Tato funkce přejmenuje soubor v systému správy zdrojů.
title: Funkce SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9d42e796f1ec2176e9de79ca392aab070581324
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073830"
---
# <a name="sccrename-function"></a>SccRename – funkce
Tato funkce přejmenuje soubor v systému správy zdrojů.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 lpFileName

pro Plně kvalifikovaný název souboru, který se má přejmenovat.

 lpNewName

pro Plně kvalifikovaný nový název. Pokud se cesta k adresáři liší, soubor se přesunul z jednoho podadresáře do druhého.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace přejmenování se úspěšně dokončila.|
|SCC_E_PROJNOTOPEN|Projekt není otevřen v rámci správy zdrojového kódu.|
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá autorizaci k dokončení této operace.|
|SCC_E_COULDNOTCREATEPROJECT|V rámci procesu přejmenování nelze projekt vytvořit.|
|SCC_E_OPNOTPERFORMED|Operace nebyla provedena.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Pomocí této funkce lze přejmenovat soubor nebo ho přesunout z jednoho umístění do jiného v systému správy zdrojového kódu. Modul plug-in správy zdrojových kódů by se neměl pokoušet o přístup k souboru na disku. Je zodpovědností integrovaného vývojového prostředí (IDE) k přejmenování místního souboru.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
