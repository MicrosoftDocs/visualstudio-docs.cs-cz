---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570138"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Otevře zadaný spustitelný soubor, který se má ladit.

## <a name="syntax"></a>Syntaxe

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumenty

- *ExecutableFile*

  Povinná hodnota. Cesta a název souboru `.exe` . Pokud `.exe` soubor nenalezne nebo neexistuje, nezobrazí se žádné upozornění nebo chyba a aplikace Visual Studio se spustí normálně.

## <a name="remarks"></a>Poznámky

Všechny řetězce za parametrem *ExecutableFile* jsou do tohoto souboru předány jako argumenty.

## <a name="example"></a>Příklad

Následující příklad otevře soubor `MyApplication.exe` pro ladění.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
