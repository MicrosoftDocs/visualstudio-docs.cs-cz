---
title: -Build (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660986"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoří řešení pomocí zadaného konfiguračního souboru řešení.

## <a name="syntax"></a>Syntaxe

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumenty
 `SolutionName` Požadovanou. Úplná cesta a název souboru řešení.

 `SolnConfigName` Požadovanou. Název konfigurace řešení, který bude použit k sestavení řešení s názvem v `SolutionName` .

 /Project je `ProjName` nepovinný. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze `SolutionName` složky do souboru projektu nebo zobrazovaný název projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig je `ProjConfigName` nepovinný. Název konfigurace sestavení projektu, který má být použit při sestavování `/project` pojmenovaného.

## <a name="remarks"></a>Poznámky
 Tento přepínač provádí stejnou funkci jako příkaz nabídky **Sestavit řešení** v rámci integrovaného vývojového prostředí (IDE).

 Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

 Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/out` přepínačem.

 Tento příkaz vytvoří pouze projekty, které se od posledního sestavení změnily. Chcete-li sestavit všechny projekty v řešení, použijte hodnotu [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Příklad
 Tento příklad vytvoří projekt `CSharpConsoleApp` pomocí `Debug` konfigurace sestavení projektu v rámci `Debug` Konfigurace řešení `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také
 [Sestavování a čištění projektů a řešení v](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [nástroji příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) sady Visual Studio [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
