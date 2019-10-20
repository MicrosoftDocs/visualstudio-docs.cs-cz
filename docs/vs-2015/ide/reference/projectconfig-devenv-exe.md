---
title: -ProjectConfig (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662090"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv. exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje konfiguraci sestavení projektu, která se má použít při sestavení, vyčištění, opětovném sestavení nebo nasazení projektu s názvem v argumentu `/project`.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments
 /Build sestaví projekt určený `/project` `ProjName`.

 /Clean vyčistí všechny zprostředkující soubory a výstupní adresáře vytvořené během sestavení.

 /Rebuild čistí a pak sestaví projekt určený `/project` `ProjName`.

 /Deploy určuje, že projekt bude nasazen po sestavení nebo opětovném sestavení.

 `SolnConfigName` nutné. Název konfigurace řešení, která bude použita pro řešení s názvem v `SolutionName`.

 `SolutionName` nutné. Úplná cesta a název souboru řešení.

 /Project `ProjName` nepovinná. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze složky `SolutionName` do souboru projektu, nebo zobrazované jméno projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig `ProjConfigName` nepovinná. Název konfigurace sestavení projektu, který má být použit pro `/project` s názvem.

## <a name="remarks"></a>Poznámky

- Se musí použít s přepínačem `/project` jako součást příkazu `devenv /build`,/`clean`, `/rebuild` nebo `/deploy`.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s přepínačem `/out`.

## <a name="example"></a>Příklad
 Tento příklad sestaví projekt `CSharpConsoleApp` pomocí konfigurace sestavení projektu `Debug` v rámci konfigurace řešení `Debug` `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také
 [Příkazového řádku Devenv – přepínače](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
