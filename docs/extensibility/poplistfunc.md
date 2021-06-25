---
title: POPLISTFUNC | Microsoft Docs
description: Přečtěte si o funkci zpětného volání POPLISTFUNC, kterou používá modul plug-in správy zdrojových kódů k aktualizaci seznamu souborů nebo adresářů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52ed40397793b44f8a9c7ed9c36aa5996ae0176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900379"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Toto zpětné volání je dodáno rozhraním IDE do [SccPopulateList](../extensibility/sccpopulatelist-function.md) a používá ho modul plug-in správy zdrojových kódů k aktualizaci seznamu souborů nebo adresářů (také dodaných do `SccPopulateList` funkce).

 Když uživatel zvolí příkaz **Get** v integrovaném vývojovém prostředí (IDE), rozhraní IDE zobrazí seznam všech souborů, které uživatel může získat. Rozhraní IDE bohužel neví přesný seznam všech souborů, které uživatel může získat. Tento seznam obsahuje jenom modul plug-in. Pokud jiní uživatelé přidali soubory do projektu správy zdrojového kódu, tyto soubory by se měly zobrazit v seznamu, ale rozhraní IDE je neví. Rozhraní IDE vytvoří seznam souborů, které může uživatel získat. Před zobrazením tohoto seznamu uživateli volá SccPopulateList, který dává modulu [](../extensibility/sccpopulatelist-function.md) `,` Plug-in správy zdrojového kódu možnost Přidat a odstranit soubory ze seznamu.

## <a name="signature"></a>Podpis
 Modul plug-in správy zdrojových kódů upraví seznam voláním funkce implementované rozhraním IDE s následujícím prototypem:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData `pvCallerData` parametr předaný volajícím (IDE) do [SccPopulateList](../extensibility/sccpopulatelist-function.md). Modul plug-in správy zdrojových kódů by neměl předpokládat žádné informace o obsahu tohoto parametru.

 fAddRemove `TRUE` , pokud `lpFileName` je soubor, který by měl být přidán do seznamu souborů. Pokud `FALSE` `lpFileName` je soubor, který by se měl odstranit ze seznamu souborů.

 Stav nStatus `lpFileName` (kombinace `SCC_STATUS` bitů; podrobnosti naleznete v části [stavový kód souboru](../extensibility/file-status-code-enumerator.md) ).

 lpFileName úplná cesta k adresáři pro název souboru, který se má přidat nebo odstranit ze seznamu.

## <a name="return-value"></a>Vrácená hodnota

|Hodnota|Popis|
|-----------|-----------------|
|`TRUE`|Modul plug-in může pokračovat v volání této funkce.|
|`FALSE`|Došlo k potížím na straně integrovaného vývojového prostředí (například situace typu nedostatek paměti). Modul plug-in by měl zastavit operaci.|

## <a name="remarks"></a>Poznámky
 Pro každý soubor, který modul plug-in správy zdrojových kódů chce přidat nebo odstranit ze seznamu souborů, volá tuto funkci, která předává do `lpFileName` . `fAddRemove`Příznak označuje nový soubor, který se má přidat do seznamu, nebo starý soubor, který se má odstranit. `nStatus`Parametr poskytuje stav souboru. Když modul plug-in SCC dokončí přidávání a odstraňování souborů, vrátí se z volání [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

> [!NOTE]
> V `SCC_CAP_POPULATELIST` aplikaci Visual Studio je vyžadován bit schopností.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
