---
title: Listovat moduly – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86e479879051d38df1da3ed2677303a76ea2d289
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747917"
---
# <a name="list-modules-command"></a>Listovat moduly – příkaz
Vypíše moduly pro aktuální proces.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
/Address: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat adresy paměti modulů. Výchozí hodnota je `yes`.

/Name: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat názvy modulů. Výchozí hodnota je `yes`.

/Order: `yes|no`

Volitelné. Určuje, zda se má zobrazovat pořadí modulů. Výchozí hodnota je `no`.

/Path: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat cesty modulů. Výchozí hodnota je `yes`.

/Process: `yes|no`

Volitelné. Určuje, zda se mají zobrazit procesy modulů. Výchozí hodnota je `no`.

/SymbolFile: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat soubory symbolů modulů. Výchozí hodnota je `no`.

/SymbolStatus: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat stavy symbolů modulů. Výchozí hodnota je `yes`.

/Timestamp: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat časová razítka modulů. Výchozí hodnota je `no`.

/Version: `yes|no`

Volitelné. Určuje, zda se mají zobrazovat verze modulů. Výchozí hodnota je `no`.

## <a name="example"></a>Příklad
V tomto příkladu jsou uvedeny názvy modulů, adresy a časová razítka pro aktuální proces.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Postupy: Použití okna Moduly](../../debugger/how-to-use-the-modules-window.md)