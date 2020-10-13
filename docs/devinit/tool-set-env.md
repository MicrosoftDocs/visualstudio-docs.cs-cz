---
title: set-env
description: Nástroj devinit vyžaduje-set-env.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7bb545a8e8713159d6833f0ed8d8c2b8784095e1
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959764"
---
# <a name="set-env"></a>set-env

`set-env`Nástroj lze použít k nastavení proměnných prostředí pro použití v aktuálním procesu. Proměnné prostředí jsou nastaveny pouze v aktuálním procesu a budou je používat `devinit` v jiných nástrojích, pokud jsou spuštěny v tomto procesu.

Tento nástroj využívá rozhraní API .NET Core `Environment.SetEnvironment` a má stejná omezení jako toto rozhraní API. Další informace najdete v [dokumentaci](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) k `Environment.SetEnvironment` .

## <a name="usage"></a>Využití

| Název                                         | Typ   | Vyžadováno | Hodnota                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **vyjádření**                                 | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                       |
| [**vstup**](#input)                          | řetězec | No       | Vstup do nástroje. Podrobnosti najdete níže v části o [zadání](#input) .               |
| [**additionalOptions**](#additional-options) | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .  |

### <a name="input"></a>Vstup

`set-env`Nástroj přijímá jeden řetězec jako vstup u `input` Vlastnosti. Řetězec by měl mít formát řetězce středníkem (;) hodnoty páry klíč-hodnota (název = hodnota) a čtyři možné akce založené na hodnotě `input` Vlastnosti.

| Akce       | Vstup            | Popis                                                                                                                                                              | Příklad             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Zobrazit vše** | prázdné nebo vynecháno | Vypíše všechny aktuální proměnné prostředí.                                                                                                                              | `"input":""`        |
| **seznam 1** | řetězec           | Vypíše hodnotu konkrétní proměnné prostředí podle názvu.                                                                                                               | `"input":"foo"`     |
| **add**      | řetězec           | Nastaví hodnotu proměnné prostředí jako dvojici klíč-hodnota. Přidá novou proměnnou prostředí, pokud ještě není přítomná, nebo nastavte hodnotu existující proměnné prostředí. | `"input":"foo=bar"` |
| **delete**   | řetězec           | Odstraní existující proměnnou prostředí předáním prázdného řetězce hodnoty.                                                                                            | `"input":"foo="`    |

`input`Řetězec může obsahovat rozšíření proměnné prostředí `%userprofile%` , které je rozbaleno například při čtení hodnoty.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

## <a name="usage-in-a-codespace"></a>Využití v codespace

Pokud používáte codespace, můžete nastavit proměnné prostředí používané v codespace prostřednictvím customizating `remoteEnv` vlastnosti v [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) souboru.

## <a name="example-usage"></a>Příklad použití

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```