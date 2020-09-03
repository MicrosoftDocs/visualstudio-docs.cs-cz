---
title: 'IDiaSession:: FindFile – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ba8422ed2be8f06ac64fb9c7fa81c5b1b3c3f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465823"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Načte zdrojové soubory podle kompilantu a Name.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `pCompiland`

pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující kompilantu, který se má použít jako kontext pro hledání. Nastavením tohoto parametru na `NULL` vyhledáte zdrojové soubory ve všech compilands.

 `name`

pro Určuje název zdrojového souboru, který se má načíst. Nastavte tento parametr na `NULL` pro všechny zdrojové soubory, které se mají načíst.

 `option`

pro Určuje možnosti porovnání použité pro hledání názvu. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.

 `ppResult`

mimo Vrátí objekt [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , který obsahuje seznam načtených zdrojových souborů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="example"></a>Příklad

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Viz také
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)