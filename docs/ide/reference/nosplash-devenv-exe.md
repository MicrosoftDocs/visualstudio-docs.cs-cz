---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1e8118faa743398271fb282a2603aab5fcd76b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62950651"
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
