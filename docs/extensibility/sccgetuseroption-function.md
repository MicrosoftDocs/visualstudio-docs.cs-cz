---
description: Tato funkce načte různé možnosti specifické pro uživatele.
title: SccGetUserOption – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901107"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption – funkce
Tato funkce načte různé možnosti specifické pro uživatele.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametry
 pContext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nOption

[v] Možnost načtení (možné možnosti najdete v části Poznámky).

 lpVal

[out] Hodnota přidružená k možnosti .

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Možnost se úspěšně načítá.|
|SCC_E_OPNOTSUPPORTED|Možnost se nepodporuje.|
|SCC_E_NONSPECIFICERROR|Došlo k neurčené chybě.|

## <a name="remarks"></a>Poznámky
 Tento příkaz podporuje následující možnosti:

|Možnost uživatele|Description|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Určuje, jestli chce uživatel zkontrolovat místní verzi souborů. `lpVal` je `SCC_USEROPT_COLV_YES` přiřazený (uživatel chce si vyhánět místní soubory) nebo `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kódy chyb](../extensibility/error-codes.md)
