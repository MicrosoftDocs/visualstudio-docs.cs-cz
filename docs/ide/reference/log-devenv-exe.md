---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595459"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Zaznamená veškerou aktivitu do souboru protokolu pro řešení potíží. Tento soubor se zobrazí `devenv /log` po volání alespoň jednou. Ve výchozím nastavení je soubor protokolu umístěn zde:

**%APPDATA%\\\\Microsoft\\VisualStudio**\<Version\>**\\ActivityLog.xml**

kde \<\> Version je verze sady Visual Studio. Můžete však zadat jinou cestu a název souboru.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NameofLogFile*

  Povinná hodnota. Úplná cesta a název souboru protokolu, do který chcete uložit.

## <a name="remarks"></a>Poznámky

Tento přepínač musí být uvedeny na konci příkazového řádku po všech ostatních přepínačích.

Protokol je zapsán pouze pro všechny instance sady Visual Studio, které jste otevřeli pomocí přepínače. `/Log`

## <a name="example"></a>Příklad

Tento příklad přesměruje `MyVSLog.xml` protokolování do souboru v domovském adresáři uživatele.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
