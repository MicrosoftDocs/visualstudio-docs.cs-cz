---
title: set-env
description: Nástroj devinit vyžaduje-set-env.
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
ms.openlocfilehash: 86e6f7c22ac75d976050858eb2853f9036377fee
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672657"
---
# <a name="set-env"></a>set-env

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

`set-env`Nástroj lze použít k nastavení proměnných prostředí pro použití v aktuálním procesu. Proměnné prostředí jsou nastaveny pouze v aktuálním procesu a budou je používat `devinit` v jiných nástrojích, pokud jsou spuštěny v tomto procesu.

Tento nástroj využívá rozhraní API .NET Core `Environment.SetEnvironment` a má stejná omezení jako toto rozhraní API. Další informace najdete v [dokumentaci](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) k `Environment.SetEnvironment` .

## <a name="usage"></a>Využití

| Název                                         | Typ   | Vyžadováno | Hodnota                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **vyjádření**                                 | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                       |
| [**vstup**](#input)                          | řetězec | No       | Vstup do nástroje. Podrobnosti najdete níže v části o [zadání](#input) .               |
| [**additionalOptions**](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .            |

### <a name="input"></a>Vstup

`set-env`Nástroj přijímá jeden řetězec jako vstup u `input` Vlastnosti. Řetězec by měl mít formát řetězce středníkem (;) hodnoty páry klíč-hodnota (název = hodnota) a čtyři možné akce založené na hodnotě `input` Vlastnosti.

| Akce       | Vstup            | Popis                                                                                                                                                              | Příklad             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Zobrazit vše** | prázdné nebo vynecháno | Vypíše všechny aktuální proměnné prostředí.                                                                                                                           | `"input":""`        |
| **seznam 1** | řetězec           | Vypíše hodnotu konkrétní proměnné prostředí podle názvu.                                                                                                               | `"input":"foo"`     |
| **add**      | řetězec           | Nastaví hodnotu proměnné prostředí jako dvojici klíč-hodnota. Přidá novou proměnnou prostředí, pokud ještě není přítomná, nebo nastavte hodnotu existující proměnné prostředí. | `"input":"foo=bar"` |
| **delete**   | řetězec           | Odstraní existující proměnnou prostředí předáním prázdného řetězce hodnoty.                                                                                            | `"input":"foo="`    |

`input`Řetězec může obsahovat rozšíření proměnné prostředí `%userprofile%` , které je rozbaleno například při čtení hodnoty.

### <a name="additional-options"></a>Další možnosti

 `--user`, `--process` nebo `--machine` lze zahrnout k určení, kde nastavit proměnné prostředí. Ve výchozím nastavení cílíme na uživatele. Další informace o možných cílech pro proměnné prostředí naleznete v tématu [EnvironmentVariableTarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget).

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `set-env` nástroje je zobrazit seznam všech aktuálních proměnných prostředí.

## <a name="usage-in-a-codespace"></a>Využití v codespace

Pokud používáte codespace, můžete nastavit proměnné prostředí používané v codespace prostřednictvím přizpůsobení `remoteEnv` vlastnosti v [`.devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) souboru.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `set-env` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.js, která nastaví proměnnou prostředí, `foo` na hodnotu `bar` :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.js, která nastaví proměnnou prostředí, `foo` na hodnotu, `bar` uloženou v bloku prostředí přidruženého k aktuálnímu procesu:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "additionalOptions": "--process",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.jsse zobrazí hodnota proměnné prostředí:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.jsse zobrazí seznam všech proměnných prostředí:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.js, které odstraní proměnnou prostředí:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.js, která bude používat rozšíření proměnné prostředí:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.jsse nastaví hodnota proměnné prostředí pomocí manipulace s cestou:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.js, který obnoví cestu z uložené kopie:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
