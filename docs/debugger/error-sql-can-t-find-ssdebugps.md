---
title: Chyba – SQL může &apos; Najít SSDEBUGPS. | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59a1a603aa44ceed46c160443508080072046e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706474"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Chyba: SQL může&#39;najít SSDEBUGPS.

SSDEBUGPS.dll je SQL Server ladění součásti hostitele.

K této chybě dochází při pokusu o spuštění ladění a indikuje, že zadaný soubor není v [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači přítomen. Možnou příčinou je, že buď nebylo spuštěno nastavení vzdáleného ladění, nebo nějaký soubor byl odstraněn.

Tuto chybu můžete vyřešit dvěma způsoby: pomocí znovu spuštěného nastavení vzdáleného ladění a zkopírováním souboru do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače.

Chcete-li znovu spustit nastavení vzdáleného ladění, postupujte podle pokynů na stránce [vzdálené ladění](../debugger/remote-debugging.md).

Pokud můžete najít kopii ssdebugps.dll, můžete ji zkopírovat do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítače. Pokud je k dispozici, soubor bude v adresáři \Program Files \ Common Files\Microsoft Shared\SQL Debugging. Můžete ji najít na jiném [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači nebo na počítači, na kterém je nainstalována aplikace Visual Studio 2005.

Zkopírování SSDEBUGPS.dll do počítače s SQL Server 2005:

1. Zkopírujte soubor do adresáře se stejným názvem a cestou v [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] počítači.

2. Zaregistrujte ho tak, že otevřete **příkazový řádek**a spustíte tento příkaz:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
