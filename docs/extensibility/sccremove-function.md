---
title: Funkce SccRemove | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700459"
---
# <a name="sccremove-function"></a>SccRemove – funkce
Tato funkce odstraní soubory ze systému správy zdrojového kódu.

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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů zadaných `lpFileNames` v poli.

 lpNázev souboru

[v] Pole plně kvalifikovaných názvů místních cest souborů, které mají být odebrány.

 lpKomentář

[v] Komentář, který má být použit pro každý soubor, který je odebírán.

 fMožnosti

[v] Příkazové příznaky (nepoužité).

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Odstranění bylo úspěšné.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod směřovat zdroj.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ISCHECKEDOUT|Soubor nelze odebrat, protože jej uživatel má aktuálně rezervován.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání; soubor nebyl odebrán.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|

## <a name="remarks"></a>Poznámky
 Tato funkce odebere soubory ze systému správy zdrojového kódu, ale neodstraní je z místního pevného disku uživatele.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
