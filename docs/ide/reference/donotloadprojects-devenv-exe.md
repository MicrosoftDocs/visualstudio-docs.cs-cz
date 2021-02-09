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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907589"
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
