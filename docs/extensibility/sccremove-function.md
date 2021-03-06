---
description: Tato funkce odstraní soubory ze systému správy zdrojů.
title: Funkce SccRemove | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4a608b3556040033d9f51535ad29d0abf5d4e35
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904123"
---
# <a name="sccremove-function"></a>SccRemove – funkce
Tato funkce odstraní soubory ze systému správy zdrojů.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nFiles

pro Počet souborů, které jsou zadány v `lpFileNames` poli.

 lpFileNames

pro Pole plně kvalifikovaných názvů místních cest souborů, které mají být odebrány.

 lpComment

pro Komentář, který se má použít u každého odebraného souboru

 fOptions

pro Příznaky příkazu (nepoužívá se)

 pvOptions

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Odebrání bylo úspěšné.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod správou zdrojových kódů.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ISCHECKEDOUT|Soubor nelze odebrat, protože uživatel je aktuálně rezervován.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba; soubor nebyl odebrán.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|

## <a name="remarks"></a>Poznámky
 Tato funkce odebere soubory ze systému správy zdrojů, ale neodstraní je z místního pevného disku uživatele.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
