---
description: Vzhledem k seznamu místních souborů tato funkce určuje, které soubory se liší od odpovídajících verzí v databázi správy zdrojového kódu.
title: SccEnumChangedFiles – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0707c049013fd3a0272d1f024e4fdbc342bab1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904536"
---
# <a name="sccenumchangedfiles-function"></a>Funkce SccEnumChangedFiles
Vzhledem k seznamu místních souborů tato funkce určuje, které soubory se liší od odpovídajících verzí v databázi správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parametry
 pContext

[v] Ukazatel na kontext modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna integrovaného vývojového prostředí, který může modul plug-in správy zdrojového kódu použít jako nadřazený prvek pro všechna dialogová okna, která poskytuje.

 cFiles

[v] Počet názvů souborů zadaných v `lpFileNames` poli Určuje také velikost `plIsFileDifferent` pole.

 lpFileNames

[v] Pole místních názvů souborů, které se mají zkontrolovat.

 plIsFileDifferent

[in, out] Pole hodnot označující stav rozdílu každého souboru (pole musí mít alespoň `cFiles` položky). Nenulové znamená, že se soubor liší.

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace se úspěšně dokončila.|
|SCC_UNSPECIFIEDERROR|Obecná chyba.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
