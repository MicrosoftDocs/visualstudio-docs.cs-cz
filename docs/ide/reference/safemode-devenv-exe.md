---
title: -SafeMode (devenv.exe)
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
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593587"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Spustí aplikaci Visual Studio v bezpečném režimu, načítá pouze výchozí prostředí a služby.

## <a name="syntax"></a>Syntaxe

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

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
