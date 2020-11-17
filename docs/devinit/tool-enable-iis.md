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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671924"
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