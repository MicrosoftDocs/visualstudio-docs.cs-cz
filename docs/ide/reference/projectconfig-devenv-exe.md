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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567655"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Určuje konfiguraci sestavení projektu, která má být použita při vytváření, `/Project` čištění, opětovném sestavení nebo nasazení projektu pojmenovaného v argumentu.

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

  Nepovinný parametr. Název konfigurace řešení (například `Debug` `Release`nebo ), které mají být použity pro řešení s názvem *V SolutionName*. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud tento argument není zadán nebo`""`prázdný řetězec ( ), nástroj používá aktivní konfiguraci řešení.

- `/Project`*ProjName*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *SolutionName* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*Název ProjConfig*

  Nepovinný parametr. Název konfigurace sestavení projektu `Debug` (například `Release`nebo ), `/Project` který má být použit pro pojmenované. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například).

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Přepínač `/ProjectConfig` musí být použit `/Project` s přepínačem `/Build`jako`Clean` `/Deploy`součást `/Rebuild` příkazu , / , nebo příkazu.

Uzavřete řetězce, které obsahují mezery v uvozovkách.

Souhrnné informace pro sestavení, včetně chyb, lze zobrazit v příkazovém okně `/Out` nebo v libovolném souboru protokolu určeném přepínačem.

## <a name="example"></a>Příklad

Následující příkaz vytvoří projekt `CSharpWinApp`pomocí `Debug` konfigurace sestavení `MySolution`projektu v části :

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
