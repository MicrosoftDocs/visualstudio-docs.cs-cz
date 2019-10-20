---
title: -Rebuild (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 008169829a6cf76e959d00f010959239a5f390b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665652"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyčistí a potom vytvoří zadanou konfiguraci řešení.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments
 `SolnConfigName` nutné. Název konfigurace řešení, který se použije k opětovnému sestavení řešení s názvem v `SolutionName`.

 `SolutionName` nutné. Úplná cesta a název souboru řešení.

 /Project `ProjName` nepovinná. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze složky `SolutionName` do souboru projektu, nebo zobrazované jméno projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig `ProjConfigName` nepovinná. Název konfigurace sestavení projektu, který se má použít při opětovném sestavování `/project` s názvem.

## <a name="remarks"></a>Poznámky

- Tento přepínač provede stejnou funkci jako příkaz v nabídce **znovu sestavit řešení** v rámci integrovaného vývojového prostředí (IDE).

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace pro vyčištění a sestavení, včetně chyb, se dají zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadaný pomocí přepínače `/out`.

## <a name="example"></a>Příklad
 Tento příklad čistí a znovu sestaví projekt `CSharpWinApp` pomocí konfigurace sestavení projektu `Debug` v rámci konfigurace řešení `Debug` `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
