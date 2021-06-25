---
title: POPDIRLISTFUNC – | Microsoft Docs
description: Přečtěte si o funkci zpětného volání POPDIRLISTFUNC, která se předává adresářům aktualizací, aby se zjistilo, které jsou pod sekcí zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c98b35d9f915e16072333c72df2e1e045850f5d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900392"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Toto je funkce zpětného volání předána funkci [SccPopulateDirList,](../extensibility/sccpopulatedirlist-function.md) která aktualizuje kolekci adresářů a (volitelně) názvy souborů, aby bylo možné zjistit, které jsou ve zdrojovém kódu.

 Zpětné volání by mělo být voláno pouze pro adresáře a názvy souborů (v seznamu předavaném funkci), které jsou ve skutečnosti pod `POPDIRLISTFUNC` `SccPopulateDirList` schůdou zdrojového kódu.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[v] Uživatelská hodnota zadaná [pro SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[v] `TRUE` pokud je název `lpDirectoryOrFileName` v adresáři, v opačném případě je název souboru.

 lpDirectoryOrFileName

[v] Úplná místní cesta k adresáři nebo názvu souboru, který je pod svládem zdrojového kódu.

## <a name="return-value"></a>Vrácená hodnota
 Integrované vývojové prostředí (IDE) vrátí odpovídající kód chyby:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Pokračujte ve zpracování.|
|SCC_I_OPERATIONCANCELED|Zastavte zpracování.|
|SCC_E_xxx|Zpracování by měla přestat zpracovávat jakákoli odpovídající chyba správy zdrojového kódu.|

## <a name="remarks"></a>Poznámky
 Pokud parametr funkce obsahuje příznak , bude seznam pravděpodobně obsahovat názvy souborů i `fOptions` `SccPopulateDirList` `SCC_PDL_INCLUDEFILES` názvy adresářů.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kódy chyb](../extensibility/error-codes.md)
