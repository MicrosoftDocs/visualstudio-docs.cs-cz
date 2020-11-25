---
title: -DoNotLoadProjects (devenv.exe)
description: Naučte se používat přepínač příkazového řádku DoNotLoadProjects devenv k otevření zadaného řešení bez načtení projektů.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040625"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novinka pro Visual Studio 2019 verze 16,1**

Otevře zadané řešení bez načtení jakýchkoli projektů. Další informace najdete v tématu [filtrovaná řešení v aplikaci Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumenty

*SolutionName*

Povinná hodnota. Úplná cesta a název řešení, které má být otevřeno.

## <a name="example"></a>Příklad

V příkladu se otevře řešení MySln. sln bez načtení jakýchkoli projektů.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Viz také

- [Filtrovaná řešení v aplikaci Visual Studio](../filtered-solutions.md)
- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
