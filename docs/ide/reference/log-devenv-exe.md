---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb33eedf322009cfd5602c481bce36beb4126a9b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948390"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Zaznamená veškerou aktivitu do souboru protokolu pro řešení potíží. Tento soubor se zobrazí poté, co jste volat `devenv /log` alespoň jednou. Ve výchozím nastavení je soubor protokolu:

 *% APPDATA %* \Microsoft\VisualStudio\\*verze*\ActivityLog.xml

 kde *verze* je verze sady Visual Studio. Můžete ale zadat jiný název a cesta k souboru.

## <a name="syntax"></a>Syntaxe

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Poznámky
 Tento přepínač musí být uvedeny na konci příkazového řádku po všech ostatních přepínačích.

 Protokol je zapsán pro všechny instance sady Visual Studio, které jste voláno s přepínačem/log. To není protokolu instance sady Visual Studio, který jste vyvolán bez přepínače.

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)