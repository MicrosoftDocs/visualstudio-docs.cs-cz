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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aef4dcdc9069c1bbfe71a90bbaba214ebcd18ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667885"
---
# <a name="build-devenvexe"></a>/Build (devenv. exe)

Vytvoří řešení nebo projekt pomocí zadaného konfiguračního souboru řešení.

## <a name="syntax"></a>Syntaxe

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Požadováno. Úplná cesta a název souboru řešení.

- *SolnConfigName*

  Volitelné. Název konfigurace řešení (například `Debug` nebo `Release`), který se má použít k sestavení řešení s názvem v názvu *řešení*. Pokud je k dispozici více platforem řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud tento argument není zadán nebo je prázdný řetězec (`""`), nástroj použije aktivní konfiguraci řešení.

- `/Project` *ProjName*

  Volitelné. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze složky *řešení* do souboru projektu nebo zobrazovaný název projektu nebo úplnou cestu a název souboru projektu.

- `/ProjectConfig` *ProjConfigName*

  Volitelné. Název konfigurace sestavení projektu (například `Debug` nebo `Release`), který má být použit při sestavování pojmenovaného projektu. Pokud je k dispozici více než jedna platforma řešení, je nutné zadat také platformu (například `Debug|Win32`). Pokud je tento přepínač zadán, přepíše argument *SolnConfigName* .

- `/Out` *OutputFilename*

  Volitelné. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

- Přepínač `/Build` provádí stejnou funkci jako příkaz nabídky **Sestavit řešení** v integrovaném vývojovém prostředí (IDE).

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace o sestaveních, včetně chyb, lze zobrazit v příkazovém okně nebo v jakémkoli souboru protokolu, který je zadán s přepínačem `/Out`.

- Přepínač `/Build` vytvoří pouze projekty, které se od posledního sestavení změnily. Chcete-li sestavit všechny projekty v řešení, použijte místo toho hodnotu [/Rebuild](../../ide/reference/rebuild-devenv-exe.md) .

- Pokud se zobrazí chybová zpráva s informacemi o **neplatné konfiguraci projektu**, ujistěte se, že jste zadali platformu řešení nebo platformu projektu (například `Debug|Win32`).

## <a name="example"></a>Příklad

Následující příkaz sestaví projekt `CSharpWinApp` pomocí `Debug` konfigurace sestavení projektu v rámci `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Viz také:

- [Sestavení a vyčištění projektů a řešení](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)