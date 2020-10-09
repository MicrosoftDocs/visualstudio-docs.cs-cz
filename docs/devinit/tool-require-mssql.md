---
title: require-mssql
description: Nástroj devinit vyžaduje – MSSQL.
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
ms.openlocfilehash: a14830e39cf39f0228fcb0e468df779f35f08ebe
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860720"
---
# <a name="require-mssql"></a>require-mssql

Tento `require-mssql` nástroj slouží k instalaci [edice Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) přes MS SQL Server ISO. SQL Server bude k dispozici při `localhost` použití integrovaného ověřování systému Windows. systém SQL Server bude přístupný pomocí připojovacího řetězce `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                   |
| [**vstup**](#input)                              | řetězec | No       | Podrobnosti najdete níže v části o [zadání](#input) .                                                  |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .              |

### <a name="input"></a>Vstup

`input`Vlastnost může být řetězec s jednou ze dvou hodnot:

| Hodnota     | Popis                              |
|-----------|------------------------------------------|
| install   | Nainstaluje SQL Server.                     |
| Uninstall | Odinstaluje všechny instalace systému SQL Server. |

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-mssql` nástroje je instalace systému SQL Server.

### <a name="builtin-options"></a>Předdefinované možnosti

`require-mssql`Nástroj nastaví řadu argumentů příkazového řádku instalačního programu, aby bylo zajištěno, že instalační program může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [dokumentaci k instalaci SQL](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?preserve-view=true&view=sql-server-ver15).

| Název                                                               | Popis |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| Za akci = instalovat                                                    |             |
| /FEATURES = SQLEngine, LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = false                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = ruční                                          |             |
| /SQLSVCSTARTUPTYPE = automatické                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = Administrators                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs MSSQL.",
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```