---
description: Tato funkce přidá nové soubory do systému správy zdrojového kódu.
title: Funkce SccAdd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f654429f8c3faefe05a6410a3c732a6a4b1d083b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221720"
---
# <a name="sccadd-function"></a>SccAdd – funkce
Tato funkce přidá nové soubory do systému správy zdrojového kódu.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nFiles

pro Počet souborů vybraných k přidání do aktuálního projektu, které jsou uvedeny v poli `lpFileNames` .

 lpFileNames

pro Pole plně kvalifikovaných místních názvů souborů, které mají být přidány.

 lpComment

pro Komentář, který má být použit pro všechny přidávané soubory.

 pfOptions

pro Pole příznaků příkazů, které jsou k dispozici na jednotlivých souborech.

 pvOptions

pro Možnosti specifické pro modul plug-in správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace přidání byla úspěšná.|
|SCC_E_FILEALREADYEXISTS|Vybraný soubor je již pod správou zdrojových kódů.|
|SCC_E_TYPENOTSUPPORTED|Typ souboru (například Binary) není podporován systémem správy zdrojového kódu.|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba; Přidání není provedeno.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|

## <a name="remarks"></a>Poznámky
 Obvykle `fOptions` jsou zde nahrazeny polem `pfOptions` s jednou `LONG` specifikací možnosti na soubor. Důvodem je to, že typ souboru se může lišit od souboru k souboru.

> [!NOTE]
> Je neplatné zadat současně i `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` Možnosti pro stejný soubor, ale je platný, pokud nechcete zadat ani jednu z možností. Nastavení není stejné jako nastavení `SCC_FILETYPE_AUTO` . v takovém případě modul plug-in správy zdrojových kódů automaticky detekuje typ souboru.

 Níže je uveden seznam příznaků použitých v `pfOptions` poli:

|Možnost|Hodnota|Význam|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Modul plug-in správy zdrojových kódů by měl detekovat typ souboru.|
|SCC_FILETYPE_TEXT|0x01|Označuje textový soubor ASCII.|
|SCC_FILETYPE_BINARY|0x02|Označuje jiný typ souboru než ASCII text.|
|SCC_ADD_STORELATEST|0x04|Ukládá pouze poslední kopii souboru, žádné rozdíly.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Soubor považuje za text ANSI.|
|SCC_FILETYPE_UTF8|0x10|Soubor považuje za text v kódování Unicode ve formátu UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Soubor považuje za text v kódu Unicode ve formátu UTF16 Little endian.|
|SCC_FILETYPE_UTF16BE|0x40|Soubor považuje za text v kódu Unicode ve formátu UTF16 big endian.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
