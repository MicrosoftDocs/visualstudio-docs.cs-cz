---
title: Spuštění pracovního procesu v rámci uživatelského účtu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47aefcb73fd20dcc82b19ed6200fec5fd57dd486
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067813"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Postupy: Spuštění pracovního procesu v rámci uživatelského účtu
Nastavení počítače tak, aby mohly běžet [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovního procesu (aspnet_wp.exe nebo w3wp.exe) v rámci uživatelského účtu, postupujte podle těchto kroků.  

 > [!IMPORTANT]
 > Od verze Windows Server 2008 R2, doporučujeme používat [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako identitu pro každý fond aplikací.
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Ke spuštění aspnet_wp.exe uživatelského účtu  
  
1. Otevřete soubor machine.config, umístěný ve vašem počítači ve složce Konfigurace na cestě, kam jste nainstalovali modul runtime.  
  
2. Najít &lt;processModel&gt; a u atributů uživatele a heslo pro jméno a heslo uživatelského účtu, který chcete, aby aspnet_wp.exe ke spuštění v rámci.  
  
3. Uložte soubor machine.config.  
  
4. Na [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)], ve výchozím nastavení je nainstalována služba IIS 6.0. Odpovídající pracovní proces je w3wp.exe.To v režimu aspnet_wp.exe jako pracovní proces služby IIS 6.0, postupujte takto:  
  
   1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **nástroje pro správu** a klikněte na tlačítko **Internetová informační služba**.  
  
   2.  V **Internetová informační služba** dialogové okno, klikněte pravým tlačítkem na **weby** složky a vyberte **vlastnosti**.  
  
   3.  V **webové servery – vlastnosti** dialogového okna zvolte **služby**.  
  
   4.  Vyberte **spustit webovou službu v izolovaném režimu IIS6.0**.  
  
   5.  Zavřít **vlastnosti** dialogové okno a **Správce služeb Internetu**.  
  
5. Otevřete příkazový řádek Windows a obnovení serveru spuštěním:  
  
   ```cmd
   iisreset  
   ```  
   – nebo –  
  
   ```cmd
   net stop iisadmin /y  
   net start w3svc  
   ```  
  
6. Najít dočasný [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] soubory složky, která by měla být ve stejné cestě jako složku konfigurace. Klikněte pravým tlačítkem na dočasný [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] soubory složky a vyberte **vlastnosti** v místní nabídce.  
  
7. V **dočasné soubory vlastnosti ASP.NET** dialogové okno, klikněte na tlačítko **zabezpečení** kartu.  
  
8. Klikněte na tlačítko **Advanced**.  
  
9. V **Upřesnit nastavení zabezpečení pro dočasné soubory ASP.Net** dialogové okno, klikněte na tlačítko **přidat**.  
  
    **Dialogové okno Vybrat uživatele, počítač nebo skupinu** se zobrazí.  
  
10. Zadejte uživatelské jméno v **zadejte název objektu k výběru** pole a potom klikněte na tlačítko **OK**. Uživatelské jméno musí mít tento formát: Název_domény\uživatelské_jméno.  
  
11. V **položka oprávnění pro dočasné soubory ASP.NET** dialogové okno pole a sdělte mu **úplné řízení**a potom klikněte na tlačítko **OK** zavřete **položku pro dočasné ASP Soubory služby .NET** dialogové okno.  
  
12. A **zabezpečení** dialogové okno se zobrazí a požádá, pokud Opravdu chcete změnit oprávnění pro složku systému. Klikněte na tlačítko **Ano**.  
  
13. Klikněte na tlačítko **OK** zavřete **dočasné soubory vlastnosti ASP.NET** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
[Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[Ladění ASP.NET: Systémové požadavky](../debugger/aspnet-debugging-system-requirements.md)  
  
