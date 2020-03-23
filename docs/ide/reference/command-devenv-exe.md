---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 434b2ad0f2a6ca4d84c6d82bf9a1a85876a4d975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570398"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Po spuštění ide sady Visual Studio provede zadaný příkaz.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumenty

*Commandname*

Povinná hodnota. Úplný název příkazu Sady Visual Studio nebo jeho aliasu, uzavřeného v uvozovkách. Další informace o syntaxi příkazů a aliasů naleznete v [tématu Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Poznámky

Po dokončení spuštění ide provede pojmenovaný příkaz.

::: moniker range="vs-2017"

Pokud použijete tento přepínač, ide nezobrazí úvodní stránku při spuštění.

::: moniker-end

Pokud doplněk zpřístupňuje příkaz, můžete pomocí tohoto přepínače spustit doplněk z příkazového řádku. Další informace naleznete v [tématu How to: Control add-ins using the add-in manager](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Příklad

První příklad spustí Visual Studio a automaticky spustí makro Otevřít oblíbené soubory.

Druhý příklad otevře kartu procházení webu v rámci rozhraní IDE a přejde na web Microsoft Docs.

Třetí příklad vytvoří nový `some_file.cs` soubor s názvem a otevře jej v editoru kódu.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Příkazové okno](command-window.md)
