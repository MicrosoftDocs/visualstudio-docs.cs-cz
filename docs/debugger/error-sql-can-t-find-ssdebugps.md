---
title: 'Chyba: SQL můžete&#39;t najít ssdebugps. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058253"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Chyba: SQL můžete&#39;t najít ssdebugps.

SSDEBUGPS.dll je součást ladění hostitel systému SQL Server.

Tato chyba nastane, když se pokoušíte spustit ladění a určuje, že zadaný soubor se nenachází na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače. Možné příčiny jsou buď vzdálené ladění instalační program se nebude nikdy spuštěn, nebo zda nějakým způsobem nebyl odstraněn tento soubor.

Existují dva způsoby, jak vyřešit tuto chybu: opětovným spuštěním instalačního programu vzdálené ladění a pomocí kopírování souborů do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače.

Vzdálené ladění instalační program znovu spustíte, postupujte podle pokynů v [vzdálené ladění](../debugger/remote-debugging.md).

Pokud můžete vyhledat kopii ssdebugps.dll, můžete je zkopírovat do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače. Pokud je k dispozici, soubor bude v \Program Files\ directory běžné Files\Microsoft Shared\SQL ladění. Může být na jiném [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače, nebo na počítači, který má nainstalované Visual Studio 2005.

Kopírování SSDEBUGPS.dll do počítače serveru SQL Server 2005:

1. Zkopírujte soubor do adresáře se stejným názvem a cestu na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače.

2. Registraci otevřením **příkazového řádku**a spuštěním následujícího příkazu:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
