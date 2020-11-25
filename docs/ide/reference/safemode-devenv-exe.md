---
title: -SafeMode (devenv.exe)
description: Naučte se, jak pomocí přepínače příkazového řádku devenv SafeMode spustit Visual Studio v nouzovém režimu a načíst jenom výchozí prostředí a služby.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d8f663ca581892ba3207acbb0271586c322bad2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039869"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Spustí aplikaci Visual Studio v bezpečném režimu, načítá pouze výchozí prostředí a služby.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Poznámky

Tento přepínač brání načtení všech VSPackage od jiných výrobců při spuštění sady Visual Studio, což umožňuje stabilní spuštění.

## <a name="example"></a>Příklad

Následující příklad spustí aplikaci Visual Studio v nouzovém režimu.

```shell
devenv /safemode
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
