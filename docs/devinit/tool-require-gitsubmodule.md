---
title: vyžadovat – gitsubmodule
description: devinit Tool vyžaduje – gitsubmodule.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810128"
---
# <a name="require-gitsubmodule"></a>vyžadovat – gitsubmodule

`require-gitsubmodule`Nástroj obnoví dílčí moduly Git pro daný `.gitmodules` soubor. `.gitmodules`Pokud není předán žádný vstup, používá místní soubor v kořenovém adresáři. Další informace o podmodulech Git najdete [tady](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                |
| [**vstup**](#input)                              | řetězec | No       | `.gitmodules` Úplná cesta k souboru. Podrobnosti najdete níže v části o [zadání](#input) .               |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                     |

### <a name="input"></a>Vstup

Volitelné, `input` slouží k získání `.gitmodules` cesty k souboru pro obnovení. Pokud `input` je tento parametr vynechán, použije se soubor kořenového adresáře `.gitmodules` .

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-gitsubmodule` nástroje je obnovení dílčích modulů Git, které jsou uvedeny v `.gitmodules` souboru.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
