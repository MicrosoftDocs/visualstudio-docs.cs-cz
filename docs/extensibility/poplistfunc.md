---
title: POPLISTFUNC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702065"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Toto zpětné volání je dodáváno do [SccPopulateList](../extensibility/sccpopulatelist-function.md) pomocí ide a je používáno modulem plug-in správy `SccPopulateList` zdrojového kódu k aktualizaci seznamu souborů nebo adresářů (také dodaných do funkce).

 Když uživatel vybere **příkaz Získat** v rozhraní IDE, ide zobrazí seznam všech souborů, které uživatel může získat. Bohužel ide nezná přesný seznam všech souborů, které by uživatel mohl získat; pouze plug-in má tento seznam. Pokud ostatní uživatelé přidali soubory do projektu správy zdrojového kódu, tyto soubory by se měly zobrazit v seznamu, ale ide o nich neví. Rozhraní IDE vytvoří seznam souborů, které si myslí, že uživatel může získat. Před zobrazením tohoto seznamu uživateli volá [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dává modul plug-in správy zdrojového kódu možnost přidat a odstranit soubory ze seznamu.

## <a name="signature"></a>Podpis
 Modul plug-in správy zdrojového kódu upraví seznam voláním funkce implementované rozhraním IDE s následujícím prototypem:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData `pvCallerData` Parametr předaný volajícím (IDE) [sccPopulateList](../extensibility/sccpopulatelist-function.md). Modul plug-in správy zdrojového kódu by neměl předpokládat nic o obsahu tohoto parametru.

 fAddRemove `TRUE`If `lpFileName` je soubor, který by měl být přidán do seznamu souborů. Pokud `FALSE` `lpFileName` je soubor, který by měl být odstraněn ze seznamu souborů.

 nStav stavu `lpFileName` (kombinace `SCC_STATUS` bitů; podrobnosti viz [Stavový kód souboru).](../extensibility/file-status-code-enumerator.md)

 lpFileName Úplná cesta k názvu souboru, který chcete přidat nebo odstranit ze seznamu.

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Popis|
|-----------|-----------------|
|`TRUE`|Modul plug-in může pokračovat v volání této funkce.|
|`FALSE`|Došlo k potížím na straně IDE (například situace nedostatku paměti). Modul plug-in by měl zastavit provoz.|

## <a name="remarks"></a>Poznámky
 Pro každý soubor, který chce modul plug-in správy zdrojového kódu přidat nebo odstranit `lpFileName`ze seznamu souborů, volá tuto funkci a předá v souboru . Příznak `fAddRemove` označuje nový soubor, který chcete přidat do seznamu, nebo starý soubor, který chcete odstranit. Parametr `nStatus` udává stav souboru. Po dokončení přidání a odstranění souborů sccsclist se vrátí z volání [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Bit `SCC_CAP_POPULATELIST` schopností je vyžadován pro visual studio.

## <a name="see-also"></a>Viz také
- [Funkce zpětného volání implementované ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Stavový kód souboru](../extensibility/file-status-code-enumerator.md)
