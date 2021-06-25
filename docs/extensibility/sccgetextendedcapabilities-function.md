---
description: Tato funkce vrací další funkce, které podporuje modul plug-in správy zdrojového kódu.
title: SccGetExtendedCapabilities – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc047fee2c92f47c181aef455b8175a4e7998176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905589"
---
# <a name="sccgetextendedcapabilities-function"></a>Funkce SccGetExtendedCapabilities
Tato funkce vrací další funkce, které podporuje modul plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametry
 pContext

[v] Ukazatel na kontext modulu plug-in správy zdrojového kódu.

 lSccExCaps

[v] Příznak určující rozšířenou schopnost, pro kterou se má testovat [](../extensibility/capability-flags.md) (možné příznaky najdete v tabulce Extended Capability Code v tématu Příznaky schopností).

 pbSupported

[out] Pokud je zadaná funkce podporovaná, vrátí nenulovou hodnotu ( ). V `TRUE` opačném případě vrátí nulu ( `FALSE` ).

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace získání schopností se úspěšně dokončila.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Došlo k neznámé nebo neurčené chybě.|

## <a name="remarks"></a>Poznámky
 Tato metoda se volá na vyžádání. To znamená, že pokud je potřeba otestovat schopnost, volá se tato metoda, aby se určilo, jestli je tato schopnost podporovaná. V jednu chvíli je zadán pouze jeden příznak.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Kódy chyb](../extensibility/error-codes.md)
- [Příznaky schopností](../extensibility/capability-flags.md)
