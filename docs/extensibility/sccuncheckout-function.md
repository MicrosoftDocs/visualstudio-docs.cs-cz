---
title: Funkce SccUncheckout | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700249"
---
# <a name="sccuncheckout-function"></a>SccUncheckout – funkce
Tato funkce vrátit zpět předchozí operaci pokladny, čímž se obnoví obsah vybraného souboru nebo souborů do stavu před pokladnou. Všechny změny provedené v souboru od pokladny jsou ztraceny.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
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

[v] Pole plně kvalifikovaných názvů místních cest souborů, pro které chcete vrátit pokladnu.

 fMožnosti

[v] Příkazové příznaky (nepoužívané).

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vrácení pokladny vrátit od souboru bylo úspěšné.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod sohledem zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání. Vrácení pokladny vrátit od souboru bylo úspěšné.|
|SCC_E_NOTCHECKEDOUT|Uživatel nemá soubor rezervován.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen ze správy zdrojového kódu.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|

## <a name="remarks"></a>Poznámky
 Po této operaci `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` a příznaky budou oba vymazány pro soubory, na kterých byl proveden zpět pokladny.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
