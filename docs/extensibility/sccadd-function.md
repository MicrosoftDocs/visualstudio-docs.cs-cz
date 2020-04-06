---
title: Funkce SccAdd | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701317"
---
# <a name="sccadd-function"></a>SccAdd
Tato funkce přidává nové soubory do systému správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů vybraných k přidání do aktuálního `lpFileNames` projektu, jak je uvedeno v poli.

 lpNázev souboru

[v] Pole plně kvalifikovaných místních názvů souborů, které mají být přidány.

 lpKomentář

[v] Komentář, který má být použit pro všechny přidané soubory.

 pfMožnosti

[v] Pole příznaků příkazů, poskytované pro soubor.

 pvMožnosti

[v] Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace přidání byla úspěšná.|
|SCC_E_FILEALREADYEXISTS|Vybraný soubor je již pod směřovat zdroj.|
|SCC_E_TYPENOTSUPPORTED|Typ souboru (například binární) není systémem správy zdrojového kódu podporován.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání; přidat není provedena.|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTEXIST|Místní soubor nebyl nalezen.|

## <a name="remarks"></a>Poznámky
 Obvyklé `fOptions` jsou zde nahrazeny pole, `pfOptions`, `LONG` s jednou specifikací možnosti na soubor. Důvodem je, že typ souboru se může u jednotlivých souborů lišit.

> [!NOTE]
> Je neplatné zadat `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` obě možnosti pro stejný soubor, ale je platný pro určení ani jeden. Nastavení není stejné jako `SCC_FILETYPE_AUTO`nastavení , v takovém případě modul plug-in správy zdrojového kódu automaticky detekuje typ souboru.

 Níže je uveden seznam příznaků `pfOptions` používaných v poli:

|Možnost|Hodnota|Význam|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Modul plug-in správy zdrojového kódu by měl rozpoznat typ souboru.|
|SCC_FILETYPE_TEXT|0x01|Označuje textový soubor ASCII.|
|SCC_FILETYPE_BINARY|0x02|Označuje jiný typ souboru než text ASCII.|
|SCC_ADD_STORELATEST|0x04|Ukládá pouze nejnovější kopii souboru, žádné rozdíly.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Zachází se souborem jako s textem ANSI.|
|SCC_FILETYPE_UTF8|0x10|Zachází se souborem jako s textem Unicode ve formátu UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Zachází se souborem jako s textem Unicode ve formátu UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Zachází se souborem jako s textem Unicode ve formátu UTF16 Big Endian.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
