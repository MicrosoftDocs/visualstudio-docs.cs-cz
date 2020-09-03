---
title: Spuštění pracovního procesu v rámci uživatelského účtu | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac5bee0ffa05aa275782c57fc9b7b1c369bf65d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349403"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Postupy: Spuštění pracovního procesu v rámci uživatelského účtu
Chcete-li nastavit počítač tak, aby bylo možné spustit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pracovní proces (aspnet_wp.exe nebo w3wp.exe) v rámci uživatelského účtu, postupujte podle následujících kroků.

 > [!IMPORTANT]
 > Počínaje systémem Windows Server 2008 R2 doporučujeme použití [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako identity pro každý fond aplikací.

## <a name="procedure"></a>Postup

#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>Spuštění aspnet_wp.exe pod uživatelským účtem

1. Otevřete soubor machine.config, který se nachází v počítači ve složce CONFIG v cestě, kam jste nainstalovali modul runtime.

2. Vyhledejte &lt; část processModel &gt; a změňte atributy uživatele a hesla na jméno a heslo uživatelského účtu, na kterém chcete spustit aspnet_wp.exe.

3. Uložte soubor machine.config.

4. V systému [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] je služba IIS 6,0 standardně nainstalována. Odpovídající pracovní proces je w3wp.exe. Chcete-li spustit v režimu IIS 6,0 s aspnet_wp.exe jako pracovní proces, je nutné provést následující kroky:

   1. Klikněte na tlačítko **Start**, klikněte na položku **Nástroje pro správu** a potom zvolte možnost **Internetová informační služba**.

   2. V dialogovém okně **Internetová informační služba** klikněte pravým tlačítkem myši na složku **webové stránky** a vyberte možnost **vlastnosti**.

   3. V dialogovém okně **vlastnosti webů** vyberte **Služba**.

   4. **V režimu izolace služby IIS 6.0 vyberte spustit webovou službu**.

   5. Zavřete dialogové okno **vlastnosti** a **Správce služeb Internetu**.

5. Otevřete příkazový řádek systému Windows a obnovte server spuštěním příkazu:

   ```cmd
   iisreset
   ```

   ani

   ```cmd
   net stop iisadmin /y
   net start w3svc
   ```

6. Vyhledejte složku dočasných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] souborů, která by měla být ve stejné cestě jako konfigurační složka. Klikněte pravým tlačítkem na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] složku Dočasné soubory a v místní nabídce vyberte **vlastnosti** .

7. V dialogovém okně **dočasné vlastnosti souborů ASP.NET** klikněte na kartu **zabezpečení** .

8. Klikněte na tlačítko **Upřesnit**.

9. V dialogovém okně **Upřesnit nastavení zabezpečení pro dočasné soubory ASP.NET** klikněte na **Přidat**.

    Zobrazí se **dialogové okno Vybrat uživatele, počítač nebo skupinu** .

10. Do pole **Zadejte název objektu k výběru** zadejte uživatelské jméno a pak klikněte na **OK**. Uživatelské jméno musí být v následujícím formátu: DomainName\UserName.

11. V dialogovém okně **Položka oprávnění pro dočasné soubory ASP.NET** Udělte uživateli **úplný ovládací prvek**a kliknutím na tlačítko **OK** zavřete dialogové okno **záznam dočasných souborů ASP.NET** .

12. Zobrazí se dialogové okno **zabezpečení** a zobrazí se dotaz, jestli opravdu chcete změnit oprávnění pro systémovou složku. Klikněte na **Ano**.

13. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti dočasných souborů ASP.NET** .

## <a name="see-also"></a>Viz také
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Ladění ASP.NET: požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)
