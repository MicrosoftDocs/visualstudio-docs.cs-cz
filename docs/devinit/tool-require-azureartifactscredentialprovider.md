---
title: require-azureartifactscredentialprovider
description: devinit Tool vyžaduje – azureartifactscredentialprovider.
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
ms.openlocfilehash: e5ba9847b09f06f853f48a0885de5e0d63664fac
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671607"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

`require-azureartifactscredentialprovider`Nástroj nainstaluje poskytovatele pověření Azure Artifacts. Zprostředkovatel pověření Azure Artifacts automatizuje získání přihlašovacích údajů potřebných k obnovení balíčků NuGet jako součást pracovního postupu vývoje .NET. Přečtěte si další informace o Azure Artifacts poskytovateli přihlašovacích údajů [tady](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                     |

### <a name="input"></a>Vstup

Nepoužívá se. Pokud je uvedeno, ignoruje všechny vstupy.

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány jako příkaz poskytovatele pověření.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-azureartifactscredentialprovider` nástroje je instalace nejnovější verze poskytovatele pověření Azure Artifacts.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-azureartifactscredentialprovider` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.js, které budou instalovat poskytovatele pověření Azure Artifacts:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
