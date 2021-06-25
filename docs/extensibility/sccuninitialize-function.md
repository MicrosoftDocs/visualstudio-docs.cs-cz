---
description: Tato funkce vyčistí všechna přidělení nebo otevřená připojení vytvořená předchozím voláním funkce SccInitialize v rámci přípravy na vypnutí modulu plug-in správy zdrojového kódu.
title: SccUninitialize – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d46aedd3e962d0684689ff29a34061b777fe08e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904071"
---
# <a name="sccuninitialize-function"></a>SccUninitialize – funkce
Tato funkce vyčistí všechna přidělení nebo otevřená připojení vytvořená předchozím voláním [funkce SccInitialize](../extensibility/sccinitialize-function.md) v rámci přípravy na vypnutí modulu plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext (Kontext pv)

[v] Ukazatel na kontextovou strukturu modulu plug-in správy zdrojového kódu vytvořenou v [objektu SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vyčištění bylo úspěšně dokončeno.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu zodpovídá za přípravu na vypnutí a za volný přístup k paměti, kterou modul plug-in přidělil pro kontextovou strukturu. Funkce se volá jednou pro každou danou instanci modulu plug-in. Volání funkce [SccInitialize](../extensibility/sccinitialize-function.md) předchází tomuto volání. V době volání metody stále není možné otevřít žádné `SccUninitialize` projekty.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
