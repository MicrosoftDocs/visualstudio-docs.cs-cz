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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595498"
---
# <a name="list-modules-command"></a>Listovat moduly – příkaz
Zobrazí seznam modulů pro aktuální proces.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametry
/Adresa:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat adresy paměti modulů. Výchozí hodnota `yes`je .

/Název:`yes|no`

Nepovinný parametr. Určuje, zda mají být názvy modulů zobrazovány. Výchozí hodnota `yes`je .

/Objednat:`yes|no`

Nepovinný parametr. Určuje, zda se má zobrazit pořadí modulů. Výchozí hodnota `no`je .

/Cesta:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit cesty modulů. Výchozí hodnota `yes`je .

/Proces:`yes|no`

Nepovinný parametr. Určuje, zda mají být procesy modulů zobrazovány. Výchozí hodnota `no`je .

/SymbolFile:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit soubory symbolů modulů. Výchozí hodnota `no`je .

/SymbolStatus:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazovat stavy symbolů modulů. Výchozí hodnota `yes`je .

/Časové razítko:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit časová razítka modulů. Výchozí hodnota `no`je .

/Verze:`yes|no`

Nepovinný parametr. Určuje, zda mají být verze modulů zobrazovány. Výchozí hodnota `no`je .

## <a name="example"></a>Příklad
V tomto příkladu jsou uvedeny názvy modulů, adresy a časová razítka pro aktuální proces.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Postupy: Použití okna Moduly](../../debugger/how-to-use-the-modules-window.md)
