---
description: Tato funkce načte ze správy zdrojového kódu každý ze zadaných souborů bez zásahu uživatele.
title: SccBackgroundGet – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 316a02e84b4d51f309aecdd98d0409c85ccbdbef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901237"
---
# <a name="sccbackgroundget-function"></a>Funkce SccBackgroundGet
Tato funkce načte ze správy zdrojového kódu každý ze zadaných souborů bez zásahu uživatele.

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

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nFiles

[v] Počet souborů zadaných v `lpFileNames` poli

 lpFileNames

[in, out] Pole názvů souborů, které se mají načíst.

> [!NOTE]
> Názvy musí být plně kvalifikované místní názvy souborů.

 dwFlags

[v] Příznaky příkazů ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

[v] Jedinečná hodnota přidružená k této operaci.

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace se úspěšně dokončila.|
|SCC_E_BACKGROUNDGETINPROGRESS|Načítání na pozadí už probíhá (modul plug-in správy zdrojového kódu by ho měl vrátit pouze v případě, že nepodporuje souběžné dávkové operace).|
|SCC_I_OPERATIONCANCELED|Operace se před dokončením zrušila.|

## <a name="remarks"></a>Poznámky
 Tato funkce se vždy volá ve vlákně jiném než ve vlákně, které načetl modul plug-in správy zdrojového kódu. Tato funkce se neočekává, že se vrátí, dokud není hotová. Lze ji ale volat vícekrát s více seznamy souborů najednou.

 Použití `dwFlags` argumentu je stejné jako u [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
