---
title: -Deploy (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660776"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nasadí řešení po sestavení nebo opětovném sestavení. Vztahuje se pouze na projekty spravovaného kódu.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName` Požadovanou. Název konfigurace řešení, který bude použit k sestavení řešení s názvem v `SolutionName` .

 `SolutionName` Požadovanou. Úplná cesta a název souboru řešení.

 /Project je `ProjName` nepovinný. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze `SolutionName` složky do souboru projektu nebo zobrazovaný název projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig je `ProjConfigName` nepovinný. Název konfigurace sestavení projektu, který má být použit při sestavování `/project` pojmenovaného.

## <a name="remarks"></a>Poznámky
 Zadaný projekt musí být projekt nasazení. Pokud zadaný projekt není projektem nasazení, při předaném projektu, který je sestaven tak, aby byl nasazen, dojde k chybě s chybou.

 Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

 Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/out` přepínačem.

## <a name="example"></a>Příklad
 Tento příklad nasadí projekt `CSharpConsoleApp` pomocí `Release` konfigurace sestavení projektu v rámci `Release` Konfigurace řešení `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Viz také
 [Přepínač příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
