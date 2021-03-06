---
description: SSDEBUGPS.dll je SQL Server ladění součásti hostitele.
title: SQL může &apos; Najít SSDEBUGPS. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a746759f294a1d8ac6b13350efd56976a1f3ae21
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146753"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Chyba: SQL může&#39;najít SSDEBUGPS.

SSDEBUGPS.dll je SQL Server ladění součásti hostitele.

K této chybě dochází při pokusu o spuštění ladění a indikuje, že zadaný soubor není v [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači přítomen. Možnou příčinou je, že buď nebylo spuštěno nastavení vzdáleného ladění, nebo nějaký soubor byl odstraněn.

Tuto chybu můžete vyřešit dvěma způsoby: pomocí znovu spuštěného nastavení vzdáleného ladění a zkopírováním souboru do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače.

Chcete-li znovu spustit nastavení vzdáleného ladění, postupujte podle pokynů na stránce [vzdálené ladění](../debugger/remote-debugging.md).

Pokud můžete najít kopii ssdebugps.dll, můžete ji zkopírovat do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače. Pokud je k dispozici, soubor bude v adresáři \Program Files \ Common Files\Microsoft Shared\SQL Debugging. Můžete ji najít na jiném [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači nebo na počítači, na kterém je nainstalována aplikace Visual Studio 2005.

Zkopírování SSDEBUGPS.dll do počítače s SQL Server 2005:

1. Zkopírujte soubor do adresáře se stejným názvem a cestou v [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači.

2. Zaregistrujte ho tak, že otevřete **příkazový řádek** a spustíte tento příkaz:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
