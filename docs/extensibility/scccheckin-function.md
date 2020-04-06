---
title: Funkce SccCheckin | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701185"
---
# <a name="scccheckin-function"></a>SccCheckin
Tato funkce vrátí se změnami dříve zasazených souborů do systému správy zdrojového kódu, uvejte změny a vytvoříte novou verzi. Tato funkce je volána s počtem a pole názvy souborů, které mají být uvedeny se změnami.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in SCC použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů vybraných ke vrácení se změnami.

 lpNázev souboru

[v] Pole plně kvalifikovaných názvů místních cest souborů, které mají být uvedeny se změnami.

 lpKomentář

[v] Komentář, který má být použit pro každý z vybraných souborů, které jsou soubory se změnami. Tento parametr `NULL` je, pokud modul plug-in správy zdrojového kódu by měl vyzvat k zadání komentáře.

 fMožnosti

[v] Příkazové příznaky, `SCC_KEEP_CHECKEDOUT`buď 0 nebo .

 pvMožnosti

[v] Možnosti specifické pro modul plug-in SCC.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Soubor byl úspěšně odbaven.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod sohledem zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání. Soubor nebyl se změnami.|
|SCC_E_NOTCHECKEDOUT|Uživatel soubor nezadal, takže jej nelze provést se změnami.|
|SCC_E_CHECKINCONFLICT|Vrácení se změnami nelze provést, protože:<br /><br /> - Jiný uživatel se přihlásil `bAutoReconcile` dopředu a byl nepravdivý.<br /><br /> -nebo-<br /><br /> - Automatické sloučení nelze provést (například když jsou soubory binární).|
|SCC_E_VERIFYMERGE|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami v čekajícím ověření uživatele.|
|SCC_E_FIXMERGE|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami z důvodu konfliktu sloučení, který je nutné ručně vyřešit.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTEXIST|Místní soubor nebyl nalezen.|

## <a name="remarks"></a>Poznámky
 Komentář se vztahuje na všechny soubory, které jsou kontrolovány. Argument komentáře může `null` být řetězec, v takovém případě může modul plug-in správy zdrojového kódu vyzvat uživatele k zadání řetězce komentáře pro každý soubor.

 Argument `fOptions` může být uveden a `SCC_KEEP_CHECKEDOUT` hodnota příznaku k označení záměru uživatele vrátit se změnami souboru a rezervovat znovu.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
