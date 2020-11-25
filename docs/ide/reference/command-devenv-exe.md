---
title: -Command (devenv.exe)
description: Naučte se, jak použít přepínač příkazového řádku devenv k provedení zadaného příkazu po spuštění integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bcfff93ac9cb4903c534c0d4d57387a5143b6b40
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040872"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Spustí zadaný příkaz po spuštění integrovaného vývojového prostředí (IDE) sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumenty

*CommandName*

Povinná hodnota. Úplný název příkazu aplikace Visual Studio nebo jeho alias uzavřený do dvojitých uvozovek. Další informace o syntaxi příkazu a aliasu naleznete v tématu [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Poznámky

Po dokončení spuštění IDE spustí pojmenovaný příkaz.

::: moniker range="vs-2017"

Pokud použijete tento přepínač, rozhraní IDE nezobrazuje úvodní stránku při spuštění.

::: moniker-end

Pokud doplněk zpřístupňuje příkaz, můžete pomocí tohoto přepínače spustit doplněk z příkazového řádku. Další informace najdete v tématu [Postup: ovládání doplňků pomocí Správce doplňků](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Příklad

První příklad spustí aplikaci Visual Studio a automaticky spustí makro otevření oblíbených souborů.

Druhý příklad otevře kartu procházení webu v rámci integrovaného vývojového prostředí (IDE) a přejde na web Microsoft Docs.

Třetí příklad vytvoří nový soubor s názvem `some_file.cs` a otevře jej v editoru kódu.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Okno Příkaz](command-window.md)
