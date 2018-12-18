---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6df78ec4be1fc94951634b84a98e80dc1403a41b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948735"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Spustí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v nouzovém režimu, načítání výchozí prostředí a služeb.

## <a name="syntax"></a>Syntaxe

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Poznámky
 Při načítání rozšíření VSPackages všechny třetích stran zabraňuje tento přepínač [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se spustí, čímž zajišťuje stabilní spuštění.

## <a name="description"></a>Popis
 Následující příklad spustí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v nouzovém režimu.

## <a name="code"></a>Kód

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)