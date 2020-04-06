---
title: Funkce SccGetExtendedCapabilities | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700727"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities
Tato funkce vrací další funkce podporované modulem plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 LSccExCaps

[v] Příznak určující rozšířené schopnosti, pro které chcete testovat (viz tabulka Rozšířený kód schopností v [příznaky schopnosti](../extensibility/capability-flags.md) pro možné příznaky).

 pbPodporováno

[out] Vrátí hodnotu`TRUE`nenulová ( ), pokud je zadaná schopnost podporována; v opačném případě`FALSE`vrátí hodnotu nula ( ).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Operace získání schopností byla úspěšně dokončena.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Došlo k neznámé nebo nespecifikované chybě.|

## <a name="remarks"></a>Poznámky
 Tato metoda je volána na vyžádání; to znamená, že pokud je třeba otestovat schopnost, je tato metoda volána k určení, zda je tato schopnost podporována. Je zadán pouze jeden příznak současně.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API pro řízení zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Kódy chyb](../extensibility/error-codes.md)
- [Příznaky schopností](../extensibility/capability-flags.md)
