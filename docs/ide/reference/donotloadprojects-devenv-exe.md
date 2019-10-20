---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654498"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv. exe)

**Novinka pro Visual Studio 2019 verze 16,1**

Otevře zadané řešení bez načtení jakýchkoli projektů. Další informace najdete v tématu [filtrovaná řešení v aplikaci Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntaxe

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Arguments

*SolutionName*

Požadováno. Úplná cesta a název řešení, které má být otevřeno.

## <a name="example"></a>Příklad

V příkladu se otevře řešení MySln. sln bez načtení jakýchkoli projektů.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Viz také:

- [Filtrovaná řešení v aplikaci Visual Studio](../filtered-solutions.md)
- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
