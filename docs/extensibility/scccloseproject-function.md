---
title: Funkce SccCloseProject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701052"
---
# <a name="scccloseproject-function"></a>SccCloseProject – funkce
Tato funkce zavře projekt, což označuje konec určité relace.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametry
 pvContext strukturu kontextu modulu plug-in správy zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Projekt se úspěšně zavřel.|
|SCC_E_PROJNOTOPEN|V tuto chvíli není otevřený žádný projekt.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 [SccOpenProject](../extensibility/sccopenproject-function.md) se před touto funkcí volá vždycky. Volání této funkce je následně následováno voláním `SccOpenProject` funkce nebo [SccUninitialize](../extensibility/sccuninitialize-function.md), které ukončí připojení k systému správy zdrojového kódu zcela.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
