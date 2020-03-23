---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595758"
---
# <a name="build-devenvexe"></a>/Sestavení (devenv.exe)

Vytvoří řešení nebo projekt pomocí zadaného konfiguračního souboru řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Povinná hodnota. Úplná cesta a název souboru řešení.

- *Název SolnConfig*

  Nepovinný parametr. Název konfigurace řešení (například `Debug` `Release`nebo ) pro sestavení řešení s názvem *V SolutionName*. Pokud je k dispozici více platforem řešení, musíte `Debug|Win32`také zadat platformu (například). Pokud tento argument není zadán nebo`""`prázdný řetězec ( ), nástroj používá aktivní konfiguraci řešení.

- `/Project`*ProjName*

  Nepovinný parametr. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze složky *SolutionName* do souboru projektu nebo zobrazovaného názvu projektu nebo úplnou cestu a název souboru projektu.

- `/ProjectConfig`*Název ProjConfig*

  Nepovinný parametr. Název konfigurace sestavení projektu `Debug` (například `Release`nebo ), který má být použit při vytváření pojmenovaného projektu. Pokud je k dispozici více než jedna platforma řešení, `Debug|Win32`musíte také zadat platformu (například). Pokud je tento přepínač zadán, přepíše argument *SolnConfigName.*

- `/Out`*Název_výstupního souboru*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Přepínač `/Build` plní stejnou funkci jako příkaz nabídky **Sestavení řešení** v integrovaném vývojovém prostředí (IDE).

- Uzavřete řetězce, které obsahují mezery v uvozovkách.

- Souhrnné informace pro sestavení, včetně chyb, lze zobrazit v příkazovém okně `/Out` nebo v libovolném souboru protokolu určeném přepínačem.

- Přepínač `/Build` pouze vytvoří projekty, které se změnily od posledního sestavení. Chcete-li vytvořit všechny projekty v řešení, použijte [/rebuild](../../ide/reference/rebuild-devenv-exe.md) místo.

- Pokud se zobrazí chybová zpráva **s textem Neplatná konfigurace projektu**, ujistěte se, že jste zadali platformu řešení nebo platformu projektu (například ). `Debug|Win32`

## <a name="example"></a>Příklad

Následující příkaz vytvoří projekt `CSharpWinApp`pomocí `Debug` konfigurace sestavení `MySolution`projektu v rámci .

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také

- [Sestavení a vyčištění projektů a řešení](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [/Znovu sestavit (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
