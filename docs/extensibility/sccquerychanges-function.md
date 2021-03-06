---
description: Tato funkce vypíše daný seznam souborů a poskytuje informace o změnách názvů jednotlivých souborů prostřednictvím funkce zpětného volání.
title: Funkce SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34c37ca999b05e7148d910032fe90c33470ce50
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220518"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges – funkce
Tato funkce vypíše daný seznam souborů a poskytuje informace o změnách názvů jednotlivých souborů prostřednictvím funkce zpětného volání.

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

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 nFiles

pro Počet souborů v `lpFileNames` poli

 lpFileNames

pro Pole názvů souborů, o kterých se mají získat informace

 pfnCallback

pro Funkce zpětného volání, která se má volat pro každý název souboru v seznamu (podrobnosti najdete v [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) )

 pvCallerData

pro Hodnota, která bude předána beze změny funkci zpětného volání.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Proces dotazu byl úspěšně dokončen.|
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen ve správě zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize.|
|SCC_E_NONSPECIFICERROR|Došlo k nespecifikované nebo obecné chybě.|

## <a name="remarks"></a>Poznámky
 Dotazy na změny jsou v oboru názvů: konkrétně, přejmenování, přidání a odebrání souboru.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kódy chyb](../extensibility/error-codes.md)
