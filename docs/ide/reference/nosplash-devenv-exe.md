---
title: -NoSplash (devenv.exe)
description: Přečtěte si, jak pomocí přepínače příkazového řádku devenv pro aplikaci devenv zabránit zobrazení úvodní obrazovky.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c88d75c0658c861c4631daeeb736ed7cfdb0a487
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967225"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Zabraňuje zobrazení úvodní obrazovky.

## <a name="syntax"></a>Syntaxe

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Soubor1*

  Nepovinný parametr. Soubor, který se má otevřít v existující instanci sady Visual Studio. Pokud žádná instance sady Visual Studio neexistuje, vytvoří se nová instance se zjednodušeným rozložením okna a nástroj otevře v nové instanci příkaz *Soubor1* .

- *FileN*

  Nepovinný parametr. Jeden nebo více dalších souborů, které mají být otevřeny v existující instanci aplikace Visual Studio.

## <a name="remarks"></a>Poznámky

Tento přepínač skryje úvodní obrazovku. Když necháte tento přepínač zapnutý, zobrazí se úvodní obrazovka. Chcete-li si prohlédnout úvodní obrazovku (například pro kontrolu ikony produktu VSPackage), použijte přepínač [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) .

`/NoSplash`Přepínač lze kombinovat s jinými přepínači, například [/Run](run-devenv-exe.md) nebo [/debugexe otevře zvolený](debugexe-devenv-exe.md).

## <a name="example"></a>Příklad

Všechny tři z příkladů otevřou rozhraní IDE bez zobrazování úvodní obrazovky. Druhý příklad také zkompiluje zadané řešení a spustí sestavený spustitelný soubor. Třetí příklad otevře zadaný spustitelný soubor pro ladění v integrovaném vývojovém prostředí.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Přepínače příkazového řádku nástroje devenv pro vývoj pro VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
