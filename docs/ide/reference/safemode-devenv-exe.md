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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957865"
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
