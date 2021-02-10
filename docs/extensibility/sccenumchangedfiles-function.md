---
title: Funkce SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e871f244082374bcf24ea49062cdcefd6e08d888
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942994"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles – funkce
Vzhledem k seznamu místních souborů Tato funkce určuje, které soubory se liší od odpovídajících verzí v databázi správy zdrojového kódu.

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

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 cFiles

pro Počet názvů souborů zadaných v `lpFileNames` poli Určuje také velikost `plIsFileDifferent` pole.

 lpFileNames

pro Pole místních názvů souborů, které chcete kontrolovat.

 plIsFileDifferent

[in, out] Pole hodnot, které označují stav rozdílů jednotlivých souborů (pole musí obsahovat alespoň `cFiles` položky). Nenulové znamená, že soubor je jiný.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace se úspěšně dokončila.|
|SCC_UNSPECIFIEDERROR|Obecná chyba|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
