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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894605"
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
