---
title: Funkce SccGetUserOption | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700691"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption – funkce
Tato funkce načte různé možnosti specifické pro uživatele.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nMožnost

[v] Možnost načíst (možné možnosti naleznete v části Poznámky).

 lpVal (Šp.)

[out] Hodnota přidružená k možnosti.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Možnost byla úspěšně načtena.|
|SCC_E_OPNOTSUPPORTED|Možnost není podporována.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované chybě.|

## <a name="remarks"></a>Poznámky
 Tímto příkazem jsou podporovány následující možnosti:

|Možnost uživatele|Popis|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Určuje, zda chce uživatel rezervovat místní verzi souborů. `lpVal``SCC_USEROPT_COLV_YES` (uživatel chce rezervovat místní soubory) `SCC_USEROPT_COLV_NO`nebo .|

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kódy chyb](../extensibility/error-codes.md)
