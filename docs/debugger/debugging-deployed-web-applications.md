---
title: Ladění nasazených aplikací ASP.NET | Microsoft Docs
ms.date: 06/30/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: c2b1838375ee878640d77a9c93808efafc9f519c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738290"
---
# <a name="debugging-deployed-aspnet-applications"></a>Ladění nasazených aplikací ASP.NET
Chcete-li použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k ladění nasazené aplikace, je nutné se připojit k pracovnímu procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a zajistit, aby ladicí program měl přístup ke symbolům pro aplikaci. Je také nutné vyhledat a otevřít zdrojové soubory aplikace. Další informace naleznete v tématu [určení symbolu (PDB) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)a [systémových požadavků](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Pokud se připojíte k pracovnímu procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pro ladění a dostanete zarážku, veškerý spravovaný kód v pracovním procesu se zastaví. Zastavení veškerého spravovaného kódu v pracovním procesu může způsobit přerušení práce pro všechny uživatele na serveru. Než začnete ladit na provozním serveru, vezměte v úvahu potenciální dopad na produkční práci.

Proces pro připojení k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu je stejný jako připojení k jinému vzdálenému procesu. Pokud jste připojeni, pokud nemáte otevřený správný projekt, zobrazí se dialogové okno při přerušení aplikace. V tomto dialogovém okně se zobrazí výzva k zadání umístění zdrojových souborů aplikace. Název souboru, který zadáte v dialogovém okně, se musí shodovat s názvem souboru zadaným v symbolech ladění na webovém serveru. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Pokud chcete nastavit vzdálené ladění ve službě IIS, přečtěte si téma [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Mnoho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací odkazuje na knihovny DLL, které obsahují obchodní logiku nebo jiný užitečný kód. Takový odkaz kopíruje knihovnu DLL z místního počítače do složky \Bin virtuálního adresáře webové aplikace při nasazení aplikace. Při ladění nezapomeňte, že vaše webová aplikace odkazuje na tuto kopii knihovny DLL a nikoli na kopii na místním počítači.

## <a name="see-also"></a>Viz také:
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: Povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: Hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)