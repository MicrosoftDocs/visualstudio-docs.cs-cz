---
description: Vzhledem k seznamu plně kvalifikovaných názvů souborů je tato funkce zkontroluje na místní jednotce.
title: SccCheckout – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904718"
---
# <a name="scccheckout-function"></a>Funkce SccCheckout
Vzhledem k seznamu plně kvalifikovaných názvů souborů je tato funkce zkontroluje na místní jednotce. Komentář platí pro všechny soubory, které jsou rezervovány. Argumentem komentáře může být `null` řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 nFiles

[v] Počet souborů vybraných k rezervování

 lpFileNames

[v] Pole plně kvalifikovaných názvů místních cest k souborům, které se mají rezervováno.

 lpComment

[v] Komentář, který se má použít u každého vybraného souboru, který se má rezervován.

 Možnosti fOptions

[v] Příznaky příkazů (viz [Bitflags used by specific commands](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[v] Možnosti modulu plug-in správy zdrojového kódu

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Kontrola byla úspěšná.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod svládem zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit. Doporučuje se opakování.|
|SCC_E_NOTAUTHORIZED|Uživatel nemůže tuto operaci provést.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání. Soubor nebyl rezervován.|
|SCC_E_ALREADYCHECKEDOUT|Uživatel už má soubor rezervován.|
|SCC_E_FILEISLOCKED|Soubor je uzamčený a zakazuje vytváření nových verzí.|
|SCC_E_FILEOUTEXCLUSIVE|Jiný uživatel provedl u tohoto souboru výhradní pokladnu.|
|SCC_I_OPERATIONCANCELED|Operace se před dokončením zrušila.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflagy používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
