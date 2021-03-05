---
description: Přijímá zpětná volání z procesu hledání symbolů DIA, což umožňuje, aby bylo omezení uloženo na proces vyhledávání.
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9103157791f5ce67bb14bb05e708f7ffd87ee435
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148197"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Přijímá zpětná volání z procesu hledání symbolů DIA, což umožňuje, aby bylo omezení uloženo na proces vyhledávání.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v rozhraní [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) toto rozhraní zpřístupňuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Určuje, zda je v původním adresáři pro ladění hledán soubor. pdb.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Určuje, zda je v cestě, kde je umístěn soubor. exe, povolen soubor. pdb.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Určuje, zda je povoleno hledání informací o ladění ze souborů. dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Určuje, zda je v kořenovém adresáři systému povoleno hledání souborů. pdb.|

## <a name="remarks"></a>Poznámky
 Klientská aplikace implementuje toto rozhraní a poskytuje odkaz na něj ve volání metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Nezapomeňte implementovat i všechny metody v rozhraní [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
