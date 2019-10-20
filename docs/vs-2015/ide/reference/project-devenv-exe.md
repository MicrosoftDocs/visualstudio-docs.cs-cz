---
title: -Project (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662111"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Identifikuje jeden projekt v rámci zadané konfigurace řešení k sestavení, vyčištění, opětovnému sestavení nebo nasazení.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
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

- Je nutné použít část `devenv /build`,/`clean`, `/rebuild` nebo příkaz `/deploy`.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s přepínačem `/out`.

## <a name="example"></a>Příklad
 Tento příklad sestaví projekt `CSharpConsoleApp` pomocí konfigurace sestavení projektu `Debug` v rámci konfigurace řešení `Debug` `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také
 [Příkazového řádku Devenv – přepínače](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
