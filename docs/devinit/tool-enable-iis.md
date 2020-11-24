---
title: enable-iis
description: povolení nástroje devinit – IIS.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b4b7c3f9681dd636ef88a5cd9f59c84c4ecac89c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440359"
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