---
title: -Clean (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac184f25d79a47814fee52b99bce1cddce247fc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570463"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Vyčistí všechny zprostředkující soubory a výstupní adresáře.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- *Config*

  Nepovinný parametr. Konfigurace (například `Debug` `Release`nebo ) vyčistit zprostředkující soubory pro řešení s názvem V *SolutionName*. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud tento argument není zadán nebo`""`prázdný řetězec ( ), nástroj používá aktivní konfiguraci řešení.

- `/Project`*ProjName*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *SolutionName* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*Název ProjConfig*

  Nepovinný parametr. Název konfigurace sestavení projektu `Debug` (například `Release`nebo ), který `/Project` se má použít při čištění pojmenované. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud je tento přepínač zadán, přepíše argument *Config.*

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Tento přepínač má stejnou funkci jako příkaz nabídky **Vyčistit řešení** v rámci prostředí IDE.

Uzavřete řetězce, které obsahují mezery v uvozovkách.

Souhrnné informace při čištění a vytváření, včetně chyb, lze zobrazit v okně **Příkaz** nebo v libovolném souboru protokolu určeném přepínačem [/Out.](out-devenv-exe.md)

Pokud `/Project` přepínač není zadán, čištění akce se provádí na všech projektech v řešení, i když *FileName* byl zadán jako soubor projektu.

## <a name="example"></a>Příklad

První příklad vyčistí `MySolution` řešení pomocí výchozí konfigurace zadané v souboru řešení.

Druhý příklad čistí projekt `CSharpWinApp`pomocí `Debug` konfigurace sestavení `MySolution`projektu v rámci .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
