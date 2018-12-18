---
title: přepínač instalací devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eca577c0e4646821262c953cf48256937eed386c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948371"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

Přepnout / Setup způsobí, že Visual Studio ke sloučení resource metadata, která popisuje nabídky, panely nástrojů a příkaz skupin, ze všech dostupných rozšíření VSPackages.

## <a name="syntax"></a>Syntaxe

```shell
devenv /setup
```

## <a name="remarks"></a>Poznámky

Tento přepínač nepřijímá žádné argumenty. `devenv /setup` Příkaz je obvykle poskytnuta jako poslední krok z procesu instalace. Použití `/setup` přepínače sady Visual Studio nespustí.

> [!NOTE]
> Je nutné spustit `devenv` jako správce, aby bylo možné používat `/setup` přepnout.

## <a name="example"></a>Příklad

Tento příklad ukazuje poslední krok při instalaci verze sady Visual Studio, která zahrnuje balíčky VSPackages.

```shell
devenv /setup
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)