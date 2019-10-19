---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc37f4cd7441fc7945ca1762d16300c18d9ecbfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610374"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Zaznamená veškerou aktivitu do souboru protokolu pro řešení potíží. Tento soubor se zobrazí poté, co byl alespoň jednou volán `devenv /log`. Ve výchozím nastavení se nachází soubor protokolu:

**% Data% \\Microsoft \\VisualStudio \\** \<Version \> **\\ActivityLog. XML**

kde \<Version \> je verze sady Visual Studio. Je však možné zadat jinou cestu a název souboru.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Arguments

- *NameOfLogFile*

  Požadováno. Úplná cesta a název souboru protokolu, do kterého se má uložit.

## <a name="remarks"></a>Poznámky

Tento přepínač musí být uvedeny na konci příkazového řádku po všech ostatních přepínačích.

Protokol je zapsán pouze pro všechny instance aplikace Visual Studio, které jste otevřeli pomocí přepínače `/Log`.

## <a name="example"></a>Příklad

Tento příklad přesměruje protokolování do souboru `MyVSLog.xml` v domovském adresáři uživatele.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)