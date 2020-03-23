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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950651"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Zabrání zobrazení úvodní obrazovky.

## <a name="syntax"></a>Syntaxe

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Soubor1*

  Nepovinný parametr. Soubor otevřít v existující instanci sady Visual Studio. Pokud neexistuje žádná instance sady Visual Studio, vytvoří se nová instance se zjednodušeným rozložením okna a nástroj otevře *soubor 1* v nové instanci.

- *Soubor N*

  Nepovinný parametr. Jeden nebo více dalších souborů, které chcete otevřít v existující instanci sady Visual Studio.

## <a name="remarks"></a>Poznámky

Tento přepínač skryje úvodní obrazovku. Ponechání tohoto přepínače způsobí, že se zobrazí úvodní obrazovka. Pokud chcete dále prozkoumat úvodní obrazovku (například zkontrolovat ikonu produktu VSPackage), použijte přepínač [/Splash.](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)

Přepínač `/NoSplash` lze kombinovat s jinými přepínači, například [/Run](run-devenv-exe.md) nebo [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Příklad

Všechny tři příklady otevřít ide bez zobrazení úvodní obrazovky. Druhý příklad také zkompiluje zadané řešení a spustí vytvořený spustitelný soubor. Třetí příklad otevře zadaný spustitelný soubor pro ladění v ide.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Přepínače příkazového řádku Devenv pro vývoj vbalíčku VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
