---
title: Ladění nasazených aplikací ASP.NET | Microsoft Docs
description: Pomocí sady Visual Studio můžete ladit nasazenou aplikaci ASP.NET připojením k pracovnímu procesu a zajištěním, aby ladicí program měl přístup ke symbolům pro aplikaci.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
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
ms.openlocfilehash: 1e8c99f1988ef1aa2e14c7b0a4d6ed46e10f6f1e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727044"
---
# <a name="debugging-deployed-aspnet-applications"></a>Ladění nasazených aplikací ASP.NET
Chcete-li použít nástroj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k ladění nasazené aplikace, je nutné se připojit k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu a zajistit, aby ladicí program měl přístup ke symbolům pro aplikaci. Je také nutné vyhledat a otevřít zdrojové soubory aplikace. Další informace naleznete v tématu [určení symbolu (PDB) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)a [systémových požadavků](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Pokud se připojíte k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu pro ladění a dostanete zarážku, veškerý spravovaný kód v pracovním procesu se zastaví. Zastavení veškerého spravovaného kódu v pracovním procesu může způsobit přerušení práce pro všechny uživatele na serveru. Než začnete ladit na provozním serveru, vezměte v úvahu potenciální dopad na produkční práci.

Proces pro připojení k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovnímu procesu je stejný jako připojení k jinému vzdálenému procesu. Pokud jste připojeni, pokud nemáte otevřený správný projekt, zobrazí se dialogové okno při přerušení aplikace. V tomto dialogovém okně se zobrazí výzva k zadání umístění zdrojových souborů aplikace. Název souboru, který zadáte v dialogovém okně, se musí shodovat s názvem souboru zadaným v symbolech ladění na webovém serveru. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Pokud chcete nastavit vzdálené ladění ve službě IIS, přečtěte si téma [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Mnoho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací odkazuje na knihovny DLL, které obsahují obchodní logiku nebo jiný užitečný kód. Takový odkaz kopíruje knihovnu DLL z místního počítače do složky \Bin virtuálního adresáře webové aplikace při nasazení aplikace. Při ladění nezapomeňte, že vaše webová aplikace odkazuje na tuto kopii knihovny DLL a nikoli na kopii na místním počítači.

## <a name="see-also"></a>Viz také
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: Povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)