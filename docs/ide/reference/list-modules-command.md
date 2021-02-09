---
title: Listovat moduly – příkaz
description: Přečtěte si o příkazu seznam modulů a o tom, jak seznam modulů pro aktuální proces.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a38a5423568528d267fd92894b8b06b4e5667c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852060"
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
Adresáře`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat adresy paměti modulů. Výchozí hodnota je `yes`.

Název`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat názvy modulů. Výchozí hodnota je `yes`.

Za`yes|no`

Nepovinný parametr. Určuje, zda se má zobrazovat pořadí modulů. Výchozí hodnota je `no`.

Dílčí`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat cesty modulů. Výchozí hodnota je `yes`.

Přihlášení`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit procesy modulů. Výchozí hodnota je `no`.

SymbolFile`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat soubory symbolů modulů. Výchozí hodnota je `no`.

SymbolStatus`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat stavy symbolů modulů. Výchozí hodnota je `yes`.

Časové razítko`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat časová razítka modulů. Výchozí hodnota je `no`.

Znění`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat verze modulů. Výchozí hodnota je `no`.

## <a name="example"></a>Příklad
V tomto příkladu jsou uvedeny názvy modulů, adresy a časová razítka pro aktuální proces.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Postupy: Použití okna Moduly](../../debugger/how-to-use-the-modules-window.md)
