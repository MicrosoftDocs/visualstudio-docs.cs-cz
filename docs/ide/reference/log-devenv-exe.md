---
title: -Log (devenv.exe)
description: Přečtěte si, jak pomocí přepínače příkazového řádku devenv pro protokolovat všechny aktivity do souboru protokolu pro účely řešení potíží.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7a4f8f3fc7fe0e0f8b7ff6bd460ea2efd8192d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919402"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Zaznamená veškerou aktivitu do souboru protokolu pro řešení potíží. Tento soubor se zobrazí poté, co jste alespoň jednou zavolali `devenv /log` . Ve výchozím nastavení se nachází soubor protokolu:

**% Data% \\ActivityLog.xml\\ Microsoft \\ VisualStudio** \<Version\> **\\**

kde \<Version\> je verze sady Visual Studio. Je však možné zadat jinou cestu a název souboru.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NameOfLogFile*

  Povinná hodnota. Úplná cesta a název souboru protokolu, do kterého se má uložit.

## <a name="remarks"></a>Poznámky

Tento přepínač musí být uvedeny na konci příkazového řádku po všech ostatních přepínačích.

Protokol je zapsán pouze pro všechny instance aplikace Visual Studio, které jste otevřeli pomocí `/Log` přepínače.

## <a name="example"></a>Příklad

Tento příklad přesměruje protokolování do `MyVSLog.xml` souboru v domovském adresáři uživatele.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
