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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565614"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Vyčistí a potom vytvoří zadanou konfiguraci řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Požadováno. Úplná cesta a název souboru řešení.

- *SolnConfigName*

  Volitelné. Název konfigurace řešení (například `Debug` nebo `Release`), který se použije k opětovnému sestavení řešení s názvem v názvu *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud tento argument není zadán nebo je prázdný řetězec (`""`), nástroj použije aktivní konfiguraci řešení.

- `/Project` *ProjName*

  Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig` *ProjConfigName*

  Volitelné. Název konfigurace sestavení projektu (například `Debug` nebo `Release`), který se má použít při opětovném sestavování `/Project` s názvem. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud je tento přepínač zadán, přepíše argument *SolnConfigName* .

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Tento přepínač provede stejnou akci jako příkaz nabídky **znovu sestavit řešení** v rámci rozhraní IDE.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace pro čištění a sestavování, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu zadaného pomocí přepínače [/out](out-devenv-exe.md) .

## <a name="example"></a>Příklad

Tento příklad čistí a znovu sestaví projekt `CSharpWinApp`pomocí konfigurace sestavení projektu `Debug` v rámci `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
