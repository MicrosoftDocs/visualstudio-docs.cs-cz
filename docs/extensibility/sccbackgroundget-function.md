---
title: Funkce SccBackgroundGet | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701233"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet
Tato funkce načte ze správy zdrojového kódu každý ze zadaných souborů bez interakce uživatele.

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
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nSoubory

[v] Počet souborů zadaných `lpFileNames` v poli.

 lpNázev souboru

[dovnitř, ven] Pole názvů souborů, které mají být načteny.

> [!NOTE]
> Názvy musí být plně kvalifikované místní názvy souborů.

 dwFlags

[v] Příkazové`SCC_GET_ALL`příznaky `SCC_GET_RECURSIVE`( , ).

 dwBackgroundOperationID

[v] Jedinečná hodnota přidružená k této operaci.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace byla úspěšně dokončena.|
|SCC_E_BACKGROUNDGETINPROGRESS|Načítání na pozadí již probíhá (modul plug-in správy zdrojového kódu by měl vrátit pouze v případě, že nepodporuje souběžné dávkové operace).|
|SCC_I_OPERATIONCANCELED|Operace byla před dokončením zrušena.|

## <a name="remarks"></a>Poznámky
 Tato funkce je vždy volána na vlákno odlišné od toho, který načetl modul plug-in správy zdrojového kódu. Neočekává se, že by se tato funkce vrátila, dokud nebude provedena; však může být volána vícekrát s více seznamy souborů, všechny ve stejnou dobu.

 Použití argumentu `dwFlags` je stejné jako [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
