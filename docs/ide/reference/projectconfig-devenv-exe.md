---
title: Přepínač nástroje DevEnv ProjectConfig
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764651"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Určuje, který bude použit při sestavení, vyčistit, znovu sestavit nebo nasazení projektu s názvem v konfigurace sestavení projektu **/project** argument.

## <a name="syntax"></a>Syntaxe

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments

|||
|-|-|
|/ Build|Sestavení projektu určeného **/project** argument.|
|/ clean|Odstraní všechny zprostředkující soubory a adresáře výstup vytvořené během sestavení.|
|/ rebuild|Vyčistí pak sestavení projektu určeného **/project** argument.|
|/ nasazení|Určuje, že projekt nasazen po sestavení nebo opětovném sestavení.|
|*SolnConfigName*|Požadováno. Název konfigurace řešení, které se použijí k řešení s názvem v *název řešení SolutionName*. Pokud jsou k dispozici více platforem řešení, musíte zadat také platformu, například **"ladění\|Win32"**.|
|*Název řešení SolutionName*|Požadováno. Úplná cesta a název souboru, řešení.|
|/ project *ProjName*|Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu z *název řešení SolutionName* složku pro soubor projektu nebo projektu zobrazovaný název, nebo úplnou cestu a název souboru projektu.|
|/ projectconfig – *ProjConfigName*|Volitelné. Název projektu vytváření konfigurace má být použita pro projekt určeného **/project** argument. Pokud jsou k dispozici více platforem řešení, musíte zadat také platformu, například **"ladění\|Win32"**.|

## <a name="remarks"></a>Poznámky

**Projectconfig** přepínače musí být použit s **/project** přepínače v rámci **/build**, **/ clean**,  **/rebuild**, nebo **/ nasazení** příkaz.

Uzavřete řetězců, které obsahují mezery v uvozovkách.

Souhrnné informace o sestavení, včetně chyb, lze zobrazit v příkazovém okně nebo v jakékoli souboru protokolu zadaný **/out** přepínače.

## <a name="example"></a>Příklad

Následující příkaz vytvoří projekt "CSharpConsoleApp" pomocí konfigurace sestavení projektu "Debug" v "Ladění" konfigurace řešení "MySolution":

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Nasadit (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)