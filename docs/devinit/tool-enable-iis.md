---
title: enable-iis
description: povolení nástroje devinit – IIS.
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
ms.openlocfilehash: 3324cf5faa1d9385adbbdf24a8125970c5db2c40
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862235"
---
# <a name="enable-iis"></a>enable-iis

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

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```