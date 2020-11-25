---
title: -Clean (devenv.exe)
description: Naučte se používat přepínač příkazového řádku Clean devenv k čištění všech zprostředkujících souborů a výstupních adresářů.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6023df4e0f8721f18a82950c0ea507406fd48e02
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041046"
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

- *Konfigurace*

  Nepovinný parametr. Konfigurace (například `Debug` nebo `Release` ) pro vyčištění zprostředkujících souborů pro řešení s názvem v souboru *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud tento argument není zadán nebo je prázdný řetězec ( `""` ), nástroj použije aktivní konfiguraci řešení.

- `/Project` *Název_projektu*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*ProjConfigName*

  Nepovinný parametr. Název konfigurace sestavení projektu (například `Debug` nebo `Release` ), který má být použit při čištění `/Project` pojmenovaného. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32` ). Pokud je tento přepínač zadán, přepíše *konfigurační* argument.

- `/Out`*OutputFilename*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Tento přepínač provede stejnou funkci jako příkaz v nabídce **Vyčistit řešení** v rámci rozhraní IDE.

Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

Souhrnné informace o vyčištění a sestavování, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu zadaného pomocí přepínače [/out](out-devenv-exe.md) .

Není `/Project` -li přepínač zadán, je akce čištění provedena u všech projektů v řešení, a to i v případě, že byl *název* souboru zadán jako soubor projektu.

## <a name="example"></a>Příklad

První příklad vyčistí `MySolution` řešení pomocí výchozí konfigurace zadané v souboru řešení.

Druhý příklad vyčistí projekt `CSharpWinApp` pomocí `Debug` konfigurace sestavení projektu v rámci `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
