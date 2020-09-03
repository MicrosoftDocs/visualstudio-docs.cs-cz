---
title: -Log (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666847"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zaznamená veškerou aktivitu do souboru protokolu pro řešení potíží. Tento soubor se zobrazí poté, co jste alespoň jednou zavolali `devenv /log` . Ve výchozím nastavení je soubor protokolu:

 *% Data%* \Microsoft\VisualStudio \\ *verze*\ActivityLog.xml

 kde *Version* je verze sady Visual Studio. Je však možné zadat jinou cestu a název souboru.

## <a name="syntax"></a>Syntax

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Poznámky
 Tento přepínač musí být uvedeny na konci příkazového řádku po všech ostatních přepínačích.

 Protokol je napsán pro všechny instance aplikace Visual Studio, které jste vyvolali pomocí přepínače/log. Neprotokoluje instance sady Visual Studio, které jste vyvolali bez přepínače.

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
