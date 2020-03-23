---
title: -DoNotLoadProjects (devenv.exe)
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
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569852"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novinka pro Visual Studio 2019 verze 16.1**

Otevře zadané řešení bez načtení všech projektů. Další informace naleznete [v tématu Filtered solutions in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumenty

*SolutionName*

Povinná hodnota. Úplná cesta a název řešení, které má být otevřeno.

## <a name="example"></a>Příklad

Příklad otevře řešení MySln.sln bez načítání projektů.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Viz také

- [Filtrovaná řešení v sadě Visual Studio](../filtered-solutions.md)
- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
