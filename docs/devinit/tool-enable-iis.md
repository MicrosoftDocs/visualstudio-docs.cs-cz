---
title: povolení – IIS
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
ms.openlocfilehash: 245ea76f988b9a9e320a51ba6b2df01382668cc0
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127829"
---
# <a name="enable-iis"></a>povolení – IIS

Tento `enable-iis` nástroj slouží k povolení funkcí služby IIS a k instalaci [modulu ASP.NET Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module) pro vývoj ASP.NET pomocí služby IIS.

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
