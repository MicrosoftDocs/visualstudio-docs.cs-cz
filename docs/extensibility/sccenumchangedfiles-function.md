---
title: Funkce SccEnumChangedFiles | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700909"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles
Vzhledem k tomu, seznam místních souborů, tato funkce určuje, které soubory se liší od odpovídajícíverze v databázi správy zdrojového kódu.

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
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 cSoubory

[v] Počet názvů souborů zadaných v `lpFileNames` poli. Také určuje velikost `plIsFileDifferent` pole.

 lpNázev souboru

[v] Pole místních názvů souborů ke kontrole.

 plIsFileDifferent

[dovnitř, ven] Pole hodnot označujících rozdílový stav každého souboru `cFiles` (pole musí mít alespoň položky). Nenulová znamená, že soubor se liší.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace byla úspěšně dokončena.|
|SCC_UNSPECIFIEDERROR|Obecná chyba.|

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
