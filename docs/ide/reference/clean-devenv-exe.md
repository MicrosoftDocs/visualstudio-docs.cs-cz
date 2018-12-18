---
title: -Clean (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7827f11a93e517f81eb03cfe2e33305859b4d78
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948852"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
Vyčistí všechny zprostředkující soubory a výstupní adresáře.

## <a name="syntax"></a>Syntaxe

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Arguments
 `FileName`

 Požadováno. Úplná cesta a název souboru řešení nebo soubor projektu.

 / Project `ProjName`

 Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu z `SolutionName` složku do souboru projektu nebo zobrazované jméno projektu, nebo úplnou cestu a název souboru projektu.

 / projectconfig `ProjConfigName`

 Volitelné. Název projektu sestavení konfigurace, která se použije při čištění `/project` s názvem.

## <a name="remarks"></a>Poznámky
 Tento přepínač provádí stejnou funkci jako **Vyčistit řešení** příkazu nabídky v rámci integrovaného vývojového prostředí (IDE).

 Uzavření řetězců, které obsahují mezery v dvojitých uvozovkách.

 Souhrnné informace o vyčistí a sestavení, včetně chyb, mohou být zobrazeny v **příkaz** okna, nebo do jakéhokoli souboru protokolu zadaný `/out` přepnout.

## <a name="example"></a>Příklad
 Vyčistí v prvním příkladu `MySolution` řešení pomocí výchozí konfigurace zadaná v souboru řešení.

 V druhém příkladu vyčistí projektu `CSharpConsoleApp`, použije `Debug` konfigurace sestavení projektu v rámci `Debug` konfigurace řešení `MySolution`.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)