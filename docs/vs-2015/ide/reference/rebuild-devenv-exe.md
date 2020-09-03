---
title: -Znovu sestavit (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665652"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyčistí a potom vytvoří zadanou konfiguraci řešení.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName` Požadovanou. Název konfigurace řešení, který se použije k opětovnému sestavení řešení s názvem v `SolutionName` .

 `SolutionName` Požadovanou. Úplná cesta a název souboru řešení.

 /Project je `ProjName` nepovinný. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze `SolutionName` složky do souboru projektu nebo zobrazovaný název projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig je `ProjConfigName` nepovinný. Název konfigurace sestavení projektu, který má být použit při opětovném sestavení `/project` pojmenovaného.

## <a name="remarks"></a>Poznámky

- Tento přepínač provede stejnou funkci jako příkaz v nabídce **znovu sestavit řešení** v rámci integrovaného vývojového prostředí (IDE).

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace o vyčištění a sestavení, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/out` přepínačem.

## <a name="example"></a>Příklad
 Tento příklad čistí a znovu sestaví projekt `CSharpWinApp` pomocí `Debug` konfigurace sestavení projektu v rámci `Debug` Konfigurace řešení `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také
 [Přepínače příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
