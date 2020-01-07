---
title: -ProjectConfig (devenv.exe)
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
ms.openlocfilehash: e8bb4b2860d40828a96e25ec6e6c73d947dd60c0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567655"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv. exe)

Určuje konfiguraci sestavení projektu, která se má použít při sestavení, vyčištění, opětovném sestavení nebo nasazení projektu s názvem v argumentu `/Project`.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Požadováno. Úplná cesta a název souboru řešení.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Požadováno. [Vytvoří](build-devenv-exe.md), [vyčistí](clean-devenv-exe.md), [nasadí](deploy-devenv-exe.md)nebo [znovu sestaví](rebuild-devenv-exe.md) projekt.

- *SolnConfigName*

  Volitelné. Název konfigurace řešení (například `Debug` nebo `Release`), který se má použít pro řešení s názvem v názvu *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud tento argument není zadán nebo je prázdný řetězec (`""`), nástroj použije aktivní konfiguraci řešení.

- `/Project` *ProjName*

  Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig` *ProjConfigName*

  Volitelné. Název konfigurace sestavení projektu (například `Debug` nebo `Release`), který má být použit pro `/Project` s názvem. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`).

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Přepínač `/ProjectConfig` musí být s přepínačem `/Project` použit jako součást příkazu `/Build`,/`Clean`, `/Deploy`nebo `/Rebuild`.

Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v příkazovém okně nebo v jakémkoli souboru protokolu, který je zadán s přepínačem `/Out`.

## <a name="example"></a>Příklad

Následující příkaz sestaví projekt `CSharpWinApp`pomocí `Debug` konfigurace sestavení projektu v rámci `MySolution`:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
