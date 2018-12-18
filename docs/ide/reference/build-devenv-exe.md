---
title: Přepínač nástroje DevEnv sestavení
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd510e523aaabc468c1f01626593e51d0ad1558
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410959"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Sestavení řešení je používán konfigurační soubor zadaného řešení.

## <a name="syntax"></a>Syntaxe

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|*Název řešení*|Požadováno. Úplná cesta a název souboru řešení.|
|*SolnConfigName*|Požadováno. Název konfigurace řešení, která se použije k vytvoření řešení s názvem v *SolutionName*. Pokud jsou k dispozici více platformy řešení, musíte zadat také platformu, například **"ladění\|Win32"**.|
|/ project *název_projektu*|Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu z *SolutionName* složku do souboru projektu nebo zobrazované jméno projektu, nebo úplnou cestu a název souboru projektu.|
|/ projectconfig *ProjConfigName*|Volitelné. Název projektu sestavení konfigurace má být použit při sestavení s názvem projektu. Pokud jsou k dispozici více platforem v projektu, musíte zadat také platformu, například **"ladění\|Win32"**.|

## <a name="remarks"></a>Poznámky

- **/Build** přepínač provádí stejnou funkci jako **sestavit řešení** příkazu nabídky v rámci integrovaného vývojového prostředí (IDE).

- Uzavření řetězců, které obsahují mezery v dvojitých uvozovkách.

- Souhrnné informace o sestavení, včetně chyb, lze zobrazit, v příkazovém okně nebo do jakéhokoli souboru protokolu zadaný **/out** přepnout.

- **/Build** přepínač sestavuje pouze projekty, které se změnily od posledního sestavení. Chcete-li sestavit všechny projekty v řešení, použijte [/rebuild](../../ide/reference/rebuild-devenv-exe.md) místo.

- Pokud se zobrazí chybová zpráva s upozorněním **neplatná konfigurace projektu**, ujistěte se, že jste zadali platforma řešení nebo projektu platformy, například **"ladění\|Win32"**.

## <a name="example"></a>Příklad

Následující příkaz sestaví projekt "CSharpConsoleApp" pomocí konfigurace sestavení projektu "Ladění" v rámci konfigurace "Debug" řešení "MySolution".

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také:

- [Sestavení a vyčištění projektů a řešení](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)