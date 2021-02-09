---
title: -Deploy (devenv.exe)
description: Naučte se, jak použít přepínač příkazového řádku devenv pro nasazení řešení po sestavení nebo opětovném sestavení.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf8fbe09d1bbe2b340e52bd070fccfff802e8dc9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916019"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Nasadí řešení po sestavení nebo opětovném sestavení. Vztahuje se pouze na projekty spravovaného kódu.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- *SolnConfigName*

  Nepovinný parametr. Název konfigurace řešení (například `Debug` nebo `Release` ), který se má použít k sestavení řešení s názvem v názvu *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud tento argument není zadán nebo je prázdný řetězec ( `""` ), nástroj použije aktivní konfiguraci řešení.

- `/Project` *Název_projektu*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*ProjConfigName*

  Nepovinný parametr. Názvy konfigurace sestavení projektu (například `Debug` nebo `Release` ), které mají být použity při vytváření `/Project` pojmenovaného. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud je tento přepínač zadán, přepíše argument *SolnConfigName* .

- `/Out`*OutputFilename*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Zadaný projekt musí být projekt nasazení. Pokud zadaný projekt není projektem nasazení, pokud je projekt sestaven pro nasazení, dojde k chybě s chybou.

Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu zadaného pomocí přepínače [/out](out-devenv-exe.md) .

## <a name="example"></a>Příklad

Tento příklad nasadí projekt `CSharpWinApp` pomocí `Release` konfigurace sestavení projektu v rámci `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
