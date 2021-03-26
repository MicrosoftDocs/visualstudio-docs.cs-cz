---
description: Tato funkce načítá ze správy zdrojového kódu každý ze zadaných souborů bez zásahu uživatele.
title: Funkce SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d850b1f8493f3118cb4d3e49915361daa1e4837
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060455"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet – funkce
Tato funkce načítá ze správy zdrojového kódu každý ze zadaných souborů bez zásahu uživatele.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametry
 pContext

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 nFiles

pro Počet souborů, které jsou zadány v `lpFileNames` poli.

 lpFileNames

[in, out] Pole názvů souborů, které mají být načteny.

> [!NOTE]
> Názvy musí být plně kvalifikované místní názvy souborů.

 dwFlags

pro Příznaky příkazu ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

pro Jedinečná hodnota přidružená k této operaci.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace se úspěšně dokončila.|
|SCC_E_BACKGROUNDGETINPROGRESS|Načítání na pozadí již probíhá (modul plug-in správy zdrojových kódů by měl vrátit tuto hodnotu pouze v případě, že nepodporuje souběžné operace s dávkou).|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|

## <a name="remarks"></a>Poznámky
 Tato funkce je vždy volána v jiném vlákně než ta, která načetla modul plug-in správy zdrojových kódů. U této funkce se neočekává, že se vrátí, dokud se nedokončí. dá se ale volat víckrát s více seznamy souborů, a to všechno současně.

 Použití `dwFlags` argumentu je stejné jako [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
