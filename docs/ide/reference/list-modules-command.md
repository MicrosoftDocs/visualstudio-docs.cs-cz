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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595498"
---
# <a name="list-modules-command"></a>Listovat moduly – příkaz
Seznam modulů pro aktuální proces.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
/Address:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat adresy paměti modulů. Výchozí hodnota je `yes`.

/Name:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat názvy modulů. Výchozí hodnota je `yes`.

/Order:`yes|no`

Volitelné. Určuje, zda se má zobrazovat pořadí modulů. Výchozí hodnota je `no`.

/Path:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat cesty modulů. Výchozí hodnota je `yes`.

/Process:`yes|no`

Volitelné. Určuje, zda se mají zobrazit procesy modulů. Výchozí hodnota je `no`.

/SymbolFile:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat soubory symbolů modulů. Výchozí hodnota je `no`.

/SymbolStatus:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat stavy symbolů modulů. Výchozí hodnota je `yes`.

/Timestamp:`yes|no`

Volitelné. Určuje, zda se mají zobrazovat časová razítka modulů. Výchozí hodnota je `no`.

/Version:`yes|no`

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
