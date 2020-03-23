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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567772"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifikuje jeden projekt v rámci zadané konfigurace řešení pro sestavení, čištění, opětovné sestavení nebo nasazení.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Povinná hodnota. [Vytvoří](build-devenv-exe.md), [vyčistí](clean-devenv-exe.md), [nasazuje](deploy-devenv-exe.md)nebo [obnovuje](rebuild-devenv-exe.md) projekt.

- *Název SolnConfig*

  Nepovinný parametr. Název konfigurace řešení (například `Debug` `Release`nebo ) použitý pro řešení pojmenované v *SolutionName*. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud tento argument není zadán nebo`""`prázdný řetězec ( ), nástroj používá aktivní konfiguraci řešení.

- `/Project`*ProjName*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *SolutionName* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*Název ProjConfig*

  Nepovinný parametr. Název konfigurace sestavení projektu `Debug` (například `Release`nebo ), `/Project` který má být použit pro pojmenované. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například).

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Musí být použita `devenv` `/Build` `/Clean`část `/Rebuild`, `/Deploy` , nebo příkaz.

- Uzavřete řetězce, které obsahují mezery v uvozovkách.

- Souhrnné informace pro sestavení, včetně chyb, lze zobrazit v okně **Příkaz** nebo `/Out` v libovolném souboru protokolu určeném přepínačem.

## <a name="example"></a>Příklad

Tento příklad vytvoří `CSharpWinApp`projekt pomocí `Debug` konfigurace sestavení `MySolution`projektu v rámci .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
