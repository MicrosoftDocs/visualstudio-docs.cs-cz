---
title: require-nuget
description: Nástroj devinit vyžaduje – NuGet.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c49f77fe8b32ce6617b34d522e36cc5988d0c33c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672287"
---
# <a name="require-nuget"></a>require-nuget

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

`require-nuget`Nástroj stáhne rozhraní NUGET CLI a přidá ho do nástroje `PATH` . NuGet CLI poskytuje kompletní rozsah funkcí NuGet pro instalaci, vytváření, publikování a správu balíčků bez nutnosti provádět změny v souborech projektu. Další informace o rozhraní příkazového řádku NuGet si [můžete přečíst zde](/nuget/reference/nuget-exe-cli-reference).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                |
| [**vstup**](#input)                              | řetězec | No       | Verze rozhraní příkazového řádku NuGet pro instalaci. Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                     |

### <a name="input"></a>Vstup

`input`Je volitelná vlastnost, která se používá ke konkrétní verzi rozhraní NUGET CLI, která se má nainstalovat. Pokud `input` je tento parametr vynechán, bude nainstalována nejnovější verze rozhraní příkazového řádku.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-nuget` nástroje je instalace nejnovějšího rozhraní příkazového řádku NuGet.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-nuget` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.js, na které se nainstaluje zadaná verze NuGetu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```