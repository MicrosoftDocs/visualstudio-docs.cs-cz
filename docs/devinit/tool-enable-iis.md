---
title: enable-iis
description: povolení nástroje devinit – IIS.
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
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671628"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

Tento `enable-iis` nástroj slouží k povolení funkcí služby IIS a k instalaci [modulu ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) pro vývoj ASP.NET pomocí služby IIS.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                               |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se.                                                                           |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se.                                                                           |

### <a name="input"></a>Vstup

Nepoužívá se.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním tohoto `enable-iis` nástroje je povolit funkce služby IIS: IIS – webserver, IIS-WebServerRole, IIS-WebSockets a IIS-Webauthentication a pak nainstalovat nejnovější verzi sady hostování ASP.NET, která obsahuje modul ASP.NET Core.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `enable-iis` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.js, které umožní vývoj ve službě IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```