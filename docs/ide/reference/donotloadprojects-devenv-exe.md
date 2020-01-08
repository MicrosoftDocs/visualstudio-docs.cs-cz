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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569852"
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
