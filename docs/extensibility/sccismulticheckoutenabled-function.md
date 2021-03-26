---
description: Tato funkce kontroluje, zda modul plug-in správy zdrojových kódů umožňuje více rezervací souboru.
title: Funkce SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3ff3943524c37d2150adb0607f62be9b8ddef95
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063796"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled – funkce
Tato funkce kontroluje, zda modul plug-in správy zdrojových kódů umožňuje více rezervací souboru.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 pContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 pbMultiCheckout

mimo Určuje, zda je pro tento projekt povoleno více rezervací (nenulové znamená, že je podporováno více rezervací).

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Ověření proběhlo úspěšně.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE umožňuje pomocí dvou kontrol zjistit, zda lze soubory rezervovat současně více než jedním uživatelem. Nejprve musí systém správy zdrojů podporovat více rezervací. Modul plug-in správy zdrojových kódů může tuto schopnost zadat při inicializaci zadáním `SCC_CAP_MULTICHECKOUT` . Pak při druhé kontrole rozhraní IDE volá tuto funkci, aby určila, jestli aktuální projekt podporuje více rezervací. Pokud je pro vybraný projekt podporováno více rezervací, modul plug-in vrátí kód úspěšnosti a nastaví `pbMultiCheckout` nenulovou hodnotu ( `TRUE` ) nebo `FALSE` .

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
