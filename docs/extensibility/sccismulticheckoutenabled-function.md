---
title: Funkce SccIsMultiCheckoutEnabled | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700585"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled – funkce
Tato funkce kontroluje, zda modul plug-in správy zdrojového kódu umožňuje více násobné pokladny v souboru.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 pKontext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 pbMultiPokladna

[out] Určuje, zda je pro tento projekt povoleno více pořazování (nenulová znamená, že je podporováno více rezervován).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Kontrola byla úspěšná.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE provede dvě kontroly k určení, zda soubory mohou být rezervovány současně více než jeden uživatel. Nejprve musí systém správy zdrojového kódu podporovat více pořazovacích možností. Modul plug-in správy zdrojového kódu může tuto `SCC_CAP_MULTICHECKOUT`funkci určit během inicializace zadáním modulu . Potom jako druhá kontrola ide volá tuto funkci k určení, zda aktuální projekt podporuje více povýběrů. Pokud je pro vybraný projekt podporováno více políček, modul plug-in vrátí kód úspěchu a nastaví `pbMultiCheckout` na nenulovou hodnotu (`TRUE`). `FALSE`

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
