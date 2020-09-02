---
title: Ladění nasazených webových aplikací | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832443"
---
# <a name="debugging-deployed-web-applications"></a>Ladění nasazených webových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud potřebujete ladit webovou aplikaci, která běží na provozním serveru, měli byste to dělat opatrně. Pokud se připojíte k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovnímu procesu pro ladění a zaškrtnete-li se zarážka, například veškerý spravovaný kód v pracovním procesu se zastaví. Zastavení veškerého spravovaného kódu v pracovním procesu může způsobit přerušení práce pro všechny uživatele na serveru. Než začnete ladit na provozním serveru, vezměte v úvahu potenciální dopad na produkční práci.  
  
 Chcete-li použít nástroj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k ladění nasazené aplikace, je nutné se připojit k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovnímu procesu a zajistit, aby ladicí program měl přístup ke symbolům pro aplikaci. Je také nutné vyhledat a otevřít zdrojové soubory aplikace. Další informace naleznete v tématu [určení symbolu (PDB) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)a [systémových požadavků](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> Mnoho [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací odkazuje na knihovny DLL, které obsahují obchodní logiku nebo jiný užitečný kód. Takový odkaz automaticky zkopíruje knihovnu DLL z místního počítače do složky \Bin virtuálního adresáře webové aplikace. Při ladění nezapomeňte, že vaše webová aplikace odkazuje na tuto kopii knihovny DLL a nikoli na kopii na místním počítači.  
  
 Proces pro připojení k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovnímu procesu je stejný jako připojení k jinému vzdálenému procesu. Pokud jste připojeni, pokud nemáte otevřený správný projekt, zobrazí se dialogové okno při přerušení aplikace. V tomto dialogovém okně se zobrazí výzva k zadání umístění zdrojových souborů aplikace. Název souboru, který zadáte v dialogovém okně, se musí shodovat s názvem souboru zadaným v symbolech ladění na webovém serveru. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Ladění webových aplikací a skriptů](../debugger/debugging-web-applications-and-script.md)   
 [Postupy: povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
