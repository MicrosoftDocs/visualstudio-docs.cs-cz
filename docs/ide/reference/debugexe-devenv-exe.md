---
title: -DebugExe (devenv.exe)
description: Naučte se používat přepínač příkazového řádku DebugExe devenv k otevření zadaného spustitelného souboru, který se má ladit.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6e60c3fb8a72caa44bcf70ac36850748ce240d42
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039468"
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
