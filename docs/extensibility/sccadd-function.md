---
description: Tato funkce přidá nové soubory do systému správy zdrojového kódu.
title: SccAdd – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f73a91f7f801ca89a633f1722e0c4d1183fb3dc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904848"
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
 pvContext (Kontext pv)

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 nFiles

[v] Počet souborů vybraných k přidání do aktuálního projektu, jak je uveden v `lpFileNames` poli

 lpFileNames

[v] Pole plně kvalifikovaných místních názvů souborů, které se mají přidat.

 lpComment

[v] Komentář, který se má použít u všech přidaných souborů.

 pfOptions

[v] Pole příznaků příkazů, které se poskytují pro každý soubor

 pvOptions

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace přidání byla úspěšná.|
|SCC_E_FILEALREADYEXISTS|Vybraný soubor je již ve zdrojovém kódu.|
|SCC_E_TYPENOTSUPPORTED|Systém správy zdrojového kódu nepodporuje typ souboru (například binární soubor).|
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání; nepřidá se.|
|SCC_I_OPERATIONCANCELED|Operace se před dokončením zrušila.|
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|

## <a name="remarks"></a>Poznámky
 Obvykle `fOptions` se zde nahradí polem s jednou specifikací možností `pfOptions` na `LONG` soubor. Je to proto, že se typ souboru může u jednotlivých souborů lišit.

> [!NOTE]
> Není možné zadat možnosti i pro stejný soubor, ale je platné `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` zadat ani jedno. Nastavení ani jedno z nich není stejné jako nastavení . V takovém případě modul plug-in správy zdrojového kódu automaticky detekuje `SCC_FILETYPE_AUTO` typ souboru.

 Níže je seznam příznaků použitých v `pfOptions` poli:

|Možnost|Hodnota|Význam|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Modul plug-in správy zdrojového kódu by měl rozpoznat typ souboru.|
|SCC_FILETYPE_TEXT|0x01|Označuje textový soubor ASCII.|
|SCC_FILETYPE_BINARY|0x02|Označuje jiný typ souboru než text ASCII.|
|SCC_ADD_STORELATEST|0x04|Ukládá pouze nejnovější kopii souboru, žádné rozdílové položky.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Považuje soubor za text ANSI.|
|SCC_FILETYPE_UTF8|0x10|Považuje soubor za text Unicode ve formátu UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Považuje soubor za text Unicode ve formátu UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Považuje soubor za text Unicode ve formátu UTF16 Big Endian.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
