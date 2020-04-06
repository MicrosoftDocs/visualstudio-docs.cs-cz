---
title: Funkce SccCloseProject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701052"
---
# <a name="scccloseproject-function"></a>SccCloseProject
Tato funkce zavře projekt a označí konec určité relace.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametry
 pvContext Kontextová struktura modulu plug-in správy zdrojového kódu.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Projekt byl úspěšně uzavřen.|
|SCC_E_PROJNOTOPEN|V současné době není otevřen žádný projekt.|
|SCC_E_NOTAUTHORIZED|Uživatel není oprávněn provádět tuto operaci.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 [SccOpenProject](../extensibility/sccopenproject-function.md) je vždy volána před touto funkcí. Po volání této funkce následuje volání `SccOpenProject` funkce nebo [sccUninitialize](../extensibility/sccuninitialize-function.md), které zcela ukončí připojení k systému správy zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
