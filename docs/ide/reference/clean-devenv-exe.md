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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f46a17371f0c83d3bdb3873c0138eca87c6b3d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663819"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Vyčistí všechny zprostředkující soubory a výstupní adresáře.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Požadováno. Úplná cesta a název souboru řešení.

- *Konfigurace*

  Volitelné. Konfigurace (například `Debug` nebo `Release`) k vyčištění zprostředkujících souborů pro řešení s názvem v souboru *řešení*. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud tento argument není zadán nebo je prázdný řetězec (`""`), nástroj použije aktivní konfiguraci řešení.

- `/Project` *ProjName*

  Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat zobrazovaný název projektu nebo relativní cestu ze složky *řešení* do souboru projektu. Můžete také zadat úplnou cestu a název souboru projektu.

- `/ProjectConfig` *ProjConfigName*

  Volitelné. Název konfigurace sestavení projektu (například `Debug` nebo `Release`), který se má použít při čištění `/Project` s názvem. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud je tento přepínač zadán, přepíše *konfigurační* argument.

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Tento přepínač provede stejnou funkci jako příkaz v nabídce **Vyčistit řešení** v rámci rozhraní IDE.

Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

Souhrnné informace o vyčištění a sestavování, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu zadaného pomocí přepínače [/out](out-devenv-exe.md) .

Pokud není zadán přepínač `/Project`, je akce čištění provedena u všech projektů v řešení, a to i v případě, že *název* souboru byl zadán jako soubor projektu.

## <a name="example"></a>Příklad

První příklad vyčistí `MySolution` řešení pomocí výchozí konfigurace zadané v souboru řešení.

Druhý příklad vyčistí `CSharpWinApp` projektu pomocí konfigurace sestavení projektu `Debug` v rámci `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)