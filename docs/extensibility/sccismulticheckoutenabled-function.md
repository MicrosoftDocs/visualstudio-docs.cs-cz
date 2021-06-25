---
description: Tato funkce zkontroluje, jestli modul plug-in správy zdrojového kódu umožňuje vícenásobné pokladny v souboru.
title: SccIsMultiCheckoutEnabled – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7b9fc81a20e3a8078a2d4cebbc6a8db10c2e2e49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902511"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled – funkce
Tato funkce zkontroluje, jestli modul plug-in správy zdrojového kódu umožňuje vícenásobné pokladny v souboru.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 pContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 pbMultiCheckout

[out] Určuje, jestli je pro tento projekt povoleno více pokladny (nenulové znamená, že se podporuje více pokladn).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Kontrola byla úspěšná.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Integrované vývojové prostředí (IDE) provádí dvě kontroly, aby bylo možné určit, jestli soubory může současně rezervuje více než jeden uživatel. Systém správy zdrojového kódu musí nejprve podporovat více pokladn. Modul plug-in správy zdrojového kódu může tuto možnost zadat během inicializace zadáním `SCC_CAP_MULTICHECKOUT` . Poté při druhé kontrole volá integrované vývojové prostředí tuto funkci, aby určilo, jestli aktuální projekt podporuje více pokladny. Pokud je pro vybraný projekt podporováno více pokladny, vrátí modul plug-in kód úspěchu a nastaví se na nenulovou `pbMultiCheckout` hodnotu ( ) nebo `TRUE` `FALSE` .

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
