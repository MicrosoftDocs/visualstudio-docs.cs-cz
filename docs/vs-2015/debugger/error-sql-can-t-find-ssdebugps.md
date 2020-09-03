---
title: 'Chyba: SQL může&#39;najít SSDEBUGPS. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185195"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Chyba: SQL může&#39;najít SSDEBUGPS.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll je SQL Server ladění součásti hostitele.  
  
 K této chybě dochází při pokusu o spuštění ladění a indikuje, že zadaný soubor není v [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] počítači přítomen. Možnou příčinou je, že buď nebylo spuštěno nastavení vzdáleného ladění, nebo nějaký soubor byl odstraněn.  
  
 Tuto chybu můžete vyřešit dvěma způsoby: pomocí znovu spuštěného nastavení vzdáleného ladění a zkopírováním souboru do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] počítače.  
  
 Chcete-li znovu spustit nastavení vzdáleného ladění, postupujte podle pokynů na stránce [vzdálené ladění](../debugger/remote-debugging.md).  
  
 Pokud můžete najít kopii ssdebugps.dll, můžete ji zkopírovat do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] počítače. Pokud je k dispozici, soubor bude v adresáři \Program Files \ Common Files\Microsoft Shared\SQL Debugging. Můžete ji najít na jiném [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] počítači nebo na počítači, na kterém je [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] nainstalovaná aplikace.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Zkopírování SSDEBUGPS.dll do počítače s SQL Server 2005  
  
1. Zkopírujte soubor do adresáře se stejným názvem a cestou v [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] počítači.  
  
2. Zaregistrujte ho tak, že otevřete **příkazový řádek**a spustíte tento příkaz:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
