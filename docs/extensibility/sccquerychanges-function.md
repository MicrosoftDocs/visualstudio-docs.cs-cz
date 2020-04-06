---
title: Funkce SccQueryChanges | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700486"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges – funkce
Tato funkce obsahuje výčet daného seznamu souborů a poskytuje informace o změnách názvů pro každý soubor prostřednictvím funkce zpětného volání.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nSoubory

[v] Počet souborů `lpFileNames` v poli.

 lpNázev souboru

[v] Pole názvů souborů, o kterých můžete získat informace.

 pfnZpětné volání

[v] Funkce zpětného volání pro volání pro každý název souboru v seznamu (podrobnosti naleznete v tématu [QUERYCHANGESFUNC).](../extensibility/querychangesfunc.md)

 pvCallerData

[v] Hodnota, která bude předána beze změny funkci zpětného volání.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Proces dotazu byl úspěšně dokončen.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen v směřované mj.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Změny, které jsou dotazovány, jsou v oboru názvů: konkrétně přejmenování, přidání a odebrání souboru.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kódy chyb](../extensibility/error-codes.md)
