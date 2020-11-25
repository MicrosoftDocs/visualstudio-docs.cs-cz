---
title: -ProjectConfig (devenv.exe)
description: Naučte se, jak použít přepínač příkazového řádku devenv ProjectConfig k určení konfigurace sestavení projektu, která se má použít při sestavování, čištění, opětovném sestavení nebo nasazení projektu.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06c6f98e9d022a7b253fdd0ea25a60ff01a4d756
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040066"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Určuje konfiguraci sestavení projektu, která se má použít při sestavení, vyčištění, opětovném sestavení nebo nasazení projektu s názvem v `/Project` argumentu.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Povinná hodnota. [Vytvoří](build-devenv-exe.md), [vyčistí](clean-devenv-exe.md), [nasadí](deploy-devenv-exe.md)nebo [znovu sestaví](rebuild-devenv-exe.md) projekt.

- *SolnConfigName*

  Nepovinný parametr. Název konfigurace řešení (například `Debug` nebo `Release` ), který má být použit pro řešení s názvem v názvu *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud tento argument není zadán nebo je prázdný řetězec ( `""` ), nástroj použije aktivní konfiguraci řešení.

- `/Project` *Název_projektu*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*ProjConfigName*

  Nepovinný parametr. Název konfigurace sestavení projektu (například `Debug` nebo `Release` ), který má být použit pro `/Project` pojmenovaný. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ).

- `/Out`*OutputFilename*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

`/ProjectConfig`Přepínač musí být použit spolu s `/Project` přepínačem jako součást `/Build` příkazu,/ `Clean` , `/Deploy` nebo `/Rebuild` .

Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v příkazovém okně nebo v jakémkoli souboru protokolu, který je zadán s `/Out` přepínačem.

## <a name="example"></a>Příklad

Následující příkaz `CSharpWinApp` `Debug` sestaví projekt pomocí konfigurace sestavení projektu v rámci `MySolution` :

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
