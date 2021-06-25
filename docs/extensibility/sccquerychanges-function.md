---
description: Tato funkce vytvoří výčet daného seznamu souborů a poskytne informace o změnách názvů jednotlivých souborů prostřednictvím funkce zpětného volání.
title: SccQueryChanges – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f93ed14671995502356ae4a19664b14bbd32ce7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900470"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges – funkce
Tato funkce vytvoří výčet daného seznamu souborů a poskytne informace o změnách názvů jednotlivých souborů prostřednictvím funkce zpětného volání.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametry
 pContext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nFiles

[v] Počet souborů v `lpFileNames` poli

 lpFileNames

[v] Pole názvů souborů, o které chcete získat informace.

 pfnCallback

[v] Funkce zpětného volání pro volání pro každý název souboru v seznamu (podrobnosti najdete v [části QUERYCHANGESFUNC).](../extensibility/querychangesfunc.md)

 pvCallerData

[v] Hodnota, která bude předána beze změny funkci zpětného volání.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Proces dotazu se úspěšně dokončil.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen ve zdrojovém kódu.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi vyřešit.|
|SCC_E_NONSPECIFICERROR|Došlo k neurčené nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Dotazované změny jsou v oboru názvů : konkrétně přejmenování, přidání a odebrání souboru.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kódy chyb](../extensibility/error-codes.md)
