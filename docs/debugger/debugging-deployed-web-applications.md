---
title: Ladění aplikace nasazené ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b8c7c9ea2f280eaf60f4592f149ed2989d862b9b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472433"
---
# <a name="debugging-deployed-aspnet-applications"></a>Ladění aplikace nasazené ASP.NET
Použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k ladění nasazených aplikací, je nutné se připojit k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní zpracovat a ujistěte se, že ladicí program má přístup k symboly pro aplikaci. Musíte také najít a otevřít zdrojové soubory pro aplikaci. Další informace najdete v tématu [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), a [požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> Pokud připojíte k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces pro ladění a stiskněte klávesu zarážku, všechny spravovaného kódu v zdržovalo proces pracovního procesu. Zastavení všech spravovaného kódu v pracovním procesu může způsobit zastavení práce pro všechny uživatele na serveru. Před ladění na provozním serveru, vezměte v úvahu potenciální dopad na produkční práci. 
  
Proces pro připojení k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu je stejný jako připojení k jiné vzdálený proces. Pokud jste se připojili, pokud nemáte otevřený správný projekt, zobrazí se dialogové okno když dělí aplikace. Toto dialogové okno se žádostí pro umístění zdrojových souborů pro aplikaci. Název souboru, který zadáte v dialogovém okně musí odpovídat názvu souboru, který je zadaný v symboly ladění na webovém serveru. Další informace najdete v tématu [přiřadit běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Vzdálené ladění ve službě IIS, naleznete v tématu [vzdáleného ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  Mnoho [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reference knihovny DLL, které obsahují obchodní logiku nebo další užitečné kódu webové aplikace. Odkazu knihovnu DLL zkopíruje z místního počítače do složky \bin virtuální adresář webové aplikace při nasazení aplikace. Při ladění, mějte na paměti, že webová aplikace je odkazy na tuto kopii této knihovny DLL a nelze zkopírovat do místního počítače. 
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Postupy: povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)