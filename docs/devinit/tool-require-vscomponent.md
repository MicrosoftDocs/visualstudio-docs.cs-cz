---
title: require-vscomponent
description: devinit Tool vyžaduje – vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7d6609c49efb9f77c9823ca3f703b8843ddb753e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672671"
---
# <a name="require-vscomponent"></a>require-vscomponent

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

Tento `require-vscomponent` nástroj slouží k importu konfigurací sady Visual Studio do existující sady Visual Studio. Další informace `.vsconfig` [najdete tady](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                     | Typ   | Vyžadováno | Hodnota                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **vyjádření**                             | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                |
| [**vstup**](#input)                      | řetězec | No       | Úplná cesta k `.vsconfig` . Podrobnosti najdete níže v části o [zadání](#input) . |
| [additionalOptions](#additional-options) | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .     |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení úplné cesty k `.vsconfig` souboru. Pokud není uvedeno, nástroj vyhledá `.vsconfig` v aktuálním adresáři a předáte hodnotu do instalační program pro Visual Studio.

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . 

| Název                      | Typ      | Vyžadováno | Hodnota                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | řetězec    | No       | Instalační cesta instance sady Visual Studio, kterou chcete upravit.                                                                                                                       |

Pokud není zadána žádná cesta pro instalaci, nástroj změní nejstarší nainstalovanou aplikaci Visual Studio na váš počítač, pokud je v počítači více instancí. 

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-vscomponent` nástroje je vyhledat `.vsconfig` soubor v aktuálním adresáři a spustit instalační program pro Visual Studio s těmito podrobnostmi v tichém režimu. `require-vscomponent` podporuje pouze úpravu stávající instalace sady Visual Studio. 

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-vscomponent` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js, která importuje konfigurace dané cesty k souboru. vsconfig:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.js, která importuje konfiguraci dané cesty k souboru. vsconfig do instance sady Visual Studio zadané prostřednictvím instalační cesty:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```