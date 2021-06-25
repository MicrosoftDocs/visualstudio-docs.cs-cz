---
description: Tato funkce načte událost stavu ve frontě.
title: SccGetEvents – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9438ac10301e2da43b26a88575e44a8ad2c0bf82
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901055"
---
# <a name="sccgetevents-function"></a>Funkce SccGetEvents
Tato funkce načte událost stavu ve frontě.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametry
 pvContext (Kontext pv)

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 lpFileName

[in, out] Vyrovnávací paměť, kam modul plug-in správy zdrojového kódu zadá vrácený název souboru (až _MAX_PATH znaků).

 stav lp

[in, out] Vrátí stavový kód (možné [hodnoty najdete v části Stavový](../extensibility/file-status-code-enumerator.md) kód souboru).

 pnEventsRemaining

[in, out] Vrátí počet položek, které zůstaly ve frontě po tomto volání. Pokud je toto číslo velké, volající se může rozhodnout zavolat [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a získat všechny informace najednou.

## <a name="return-value"></a>Vrácená hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Získání událostí bylo úspěšné.|
|SCC_E_OPNOTSUPPORTED|Tato funkce se nepodporuje.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce se volá během zpracování nečinnosti, aby bylo možné zkontrolovat, jestli u souborů ve zdrojovém kódu nebyly nějaké aktualizace stavu. Modul plug-in správy zdrojového kódu udržuje stav všech souborů, o kterých ví, a kdykoli modul plug-in pozná změnu stavu, stav a přidružený soubor se uloží do fronty. Při volání se načte a vrátí horní prvek `SccGetEvents` fronty. Tato funkce je omezena tak, aby vracela pouze informace uložené v mezipaměti, a musí mít velmi rychlý přehled (to znamená, že nečte disk nebo žádá systém správy zdrojového kódu o stav); V opačném případě se může výkon integrovaného vývojového prostředí (IDE) začít zhoršovat.

 Pokud sestava nemá žádnou aktualizaci stavu, uloží modul plug-in správy zdrojového kódu prázdný řetězec ve vyrovnávací paměti, na kterou odkazuje `lpFileName` . V opačném případě modul plug-in uloží úplný název cesty k souboru, pro který se změnily informace o stavu, a vrátí odpovídající stavový kód (jedna z hodnot podrobných v části Stavový kód [souboru).](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
- [Stavový kód souboru](../extensibility/file-status-code-enumerator.md)
