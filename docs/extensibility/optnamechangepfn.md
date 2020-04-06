---
title: OPTNAMECHANGEPFN | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702249"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Jedná se o funkci zpětného volání zadanou ve volání `SCC_OPT_NAMECHANGEPFN` [sccsetoption](../extensibility/sccsetoption-function.md) (pomocí volby) a slouží ke komunikaci změn názvů provedených modulem plug-in správy zdrojového kódu zpět do ide.

## <a name="signature"></a>Podpis

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[v] Uživatelská hodnota zadaná v předchozím volání [SccSetOption](../extensibility/sccsetoption-function.md) (pomocí volby). `SCC_OPT_USERDATA`

 pszOldName

[v] Původní název souboru.

 pszNewName

[v] Název, na který byl soubor přejmenován.

## <a name="return-value"></a>Návratová hodnota
 Žádné.

## <a name="remarks"></a>Poznámky
 Pokud je soubor přejmenován během operace správy zdrojového kódu, modul plug-in správy zdrojového kódu může upozornit ide na změnu názvu prostřednictvím tohoto zpětného volání.

 Pokud ide nepodporuje toto zpětné volání, nebude volat [SccSetOption](../extensibility/sccsetoption-function.md) k jeho určení. Pokud modul plug-in nepodporuje toto zpětné `SCC_E_OPNOTSUPPORTED` volání, vrátí se z `SccSetOption` funkce, když se ide pokusí nastavit zpětné volání.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
