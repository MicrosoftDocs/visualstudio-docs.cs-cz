---
title: 'Postupy: spuštění pracovního procesu v rámci uživatelského účtu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5d9e9cbadd2b7154eeb84bad99239e0b026eecd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734462"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Postupy: Spuštění pracovního procesu v rámci uživatelského účtu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení počítače tak, aby mohly běžet [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovního procesu (aspnet_wp.exe nebo w3wp.exe) v rámci uživatelského účtu, postupujte podle těchto kroků.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Ke spuštění aspnet_wp.exe uživatelského účtu  
  
1.  Otevřete soubor machine.config, umístěný ve vašem počítači ve složce Konfigurace na cestě, kam jste nainstalovali modul runtime.  
  
2.  Najít &lt;processModel&gt; a u atributů uživatele a heslo pro jméno a heslo uživatelského účtu, který chcete, aby aspnet_wp.exe ke spuštění v rámci.  
  
3.  Uložte soubor machine.config.  
  
4.  Na [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], ve výchozím nastavení je nainstalována služba IIS 6.0. Odpovídající pracovní proces je w3wp.exe.To v režimu aspnet_wp.exe jako pracovní proces služby IIS 6.0, postupujte takto:  
  
    1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **nástroje pro správu** a klikněte na tlačítko **Internetová informační služba**.  
  
    2.  V **Internetová informační služba** dialogové okno, klikněte pravým tlačítkem na **weby** složky a vyberte **vlastnosti**.  
  
    3.  V **webové servery – vlastnosti** dialogového okna zvolte **služby**.  
  
    4.  Vyberte **spustit webovou službu v izolovaném režimu IIS6.0**.  
  
    5.  Zavřít **vlastnosti** dialogové okno a **Správce služeb Internetu**.  
  
5.  Otevřete příkazový řádek Windows a obnovení serveru spuštěním:  
  
    ```  
    iisreset  
    ```  
    – nebo –  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Najít dočasný [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] soubory složky, která by měla být ve stejné cestě jako složku konfigurace. Klikněte pravým tlačítkem na dočasný [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] soubory složky a vyberte **vlastnosti** v místní nabídce.  
  
7.  V **dočasné soubory vlastnosti ASP.NET** dialogové okno, klikněte na tlačítko **zabezpečení** kartu.  
  
8.  Klikněte na tlačítko **Advanced**.  
  
9. V **Upřesnit nastavení zabezpečení pro dočasné soubory ASP.Net** dialogové okno, klikněte na tlačítko **přidat**.  
  
    **Dialogové okno Vybrat uživatele, počítač nebo skupinu** se zobrazí.  
  
10. Zadejte uživatelské jméno v **zadejte název objektu k výběru** pole a potom klikněte na tlačítko **OK**. Uživatelské jméno musí mít tento formát: Název_domény\uživatelské_jméno.  
  
11. V **položka oprávnění pro dočasné soubory ASP.NET** dialogové okno pole a sdělte mu **úplné řízení**a potom klikněte na tlačítko **OK** zavřete **položku pro dočasné ASP Soubory služby .NET** dialogové okno.  
  
12. A **zabezpečení** dialogové okno se zobrazí a požádá, pokud Opravdu chcete změnit oprávnění pro složku systému. Klikněte na tlačítko **Ano**.  
  
13. Klikněte na tlačítko **OK** zavřete **dočasné soubory vlastnosti ASP.NET** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
[Ladění ASP.NET: Systémové požadavky](../debugger/aspnet-debugging-system-requirements.md)  
  




