---
title: -Project (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4b57a5bd51ff20de8da87798aa398db04bc1c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75567772"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifikuje jeden projekt v rámci zadané konfigurace řešení k sestavení, vyčištění, opětovnému sestavení nebo nasazení.

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

  Nepovinný parametr. Název konfigurace řešení (například nebo), který `Debug` se `Release` použije pro řešení s názvem v názvu *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud tento argument není zadán nebo je prázdný řetězec ( `""` ), nástroj použije aktivní konfiguraci řešení.

- `/Project` *Název_projektu*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*ProjConfigName*

  Nepovinný parametr. Název konfigurace sestavení projektu (například `Debug` nebo `Release` ), který má být použit pro `/Project` pojmenovaný. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ).

- `/Out`*OutputFilename*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Je nutné použít část `devenv` `/Build` `/Clean` příkazu,, `/Rebuild` nebo `/Deploy` .

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/Out` přepínačem.

## <a name="example"></a>Příklad

Tento příklad vytvoří projekt `CSharpWinApp` pomocí `Debug` konfigurace sestavení projektu v rámci `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
