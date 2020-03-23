---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76fe4bcf3441163604d93e9264ed6f78fcf0224b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565614"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Vyčistí a vytvoří zadanou konfiguraci řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- *Název SolnConfig*

  Nepovinný parametr. Název konfigurace řešení (například `Debug` `Release`nebo ) pro opětovné sestavení řešení pojmenované v *SolutionName*. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud tento argument není zadán nebo`""`prázdný řetězec ( ), nástroj používá aktivní konfiguraci řešení.

- `/Project`*ProjName*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *SolutionName* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig`*Název ProjConfig*

  Nepovinný parametr. Název konfigurace sestavení projektu `Debug` (například `Release`nebo ), který `/Project` se má použít při opětovném sestavení pojmenované. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud je tento přepínač zadán, přepíše argument *SolnConfigName.*

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Tento přepínač provádí stejnou věc jako příkaz nabídky **Znovu sestavit řešení** v rámci ide.

- Uzavřete řetězce, které obsahují mezery v uvozovkách.

- Souhrnné informace pro čištění a vytváření, včetně chyb, lze zobrazit v okně **Příkaz** nebo v libovolném souboru protokolu určeném přepínačem [/Out.](out-devenv-exe.md)

## <a name="example"></a>Příklad

Tento příklad čistí a znovu `CSharpWinApp`sestavuje projekt pomocí konfigurace sestavení `Debug` projektu v rámci `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
