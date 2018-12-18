---
title: Omezení ladění WCF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 001393a856dc374d92e11ff2d4707346a35aea12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887420"
---
# <a name="limitations-on-wcf-debugging"></a>Omezení ladění WCF
Existují tři způsoby, můžete začít ladění služby WCF:  
  
- Ladění procesu klienta, která volá službu. Ladicí program do služby. Služba nemusí být ve stejném řešení jako klientské aplikace.  
  
- Ladění procesu klienta, který odešle požadavek do služby. Služba musí být součástí vašeho řešení.  
  
- Použijete **připojit k procesu** k připojení ke službě, na kterém aktuálně běží. Ladění začíná v službě.  
  
  Toto téma popisuje omezení na uvedené scénáře.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Omezení krokování s vnořením do služby  
 Chcete-li do služby z klientských aplikací, které ladíte, musí být splněny následující podmínky:  
  
-   Klient musí volat službu pomocí synchronního klientského objektu.  
  
-   Kontrakt operace nemůže být jednosměrná.  
  
-   Pokud je server asynchronní, nelze zobrazit úplného zásobníku volání, zatímco spouštíte kód uvnitř služby.  
  
-   Pomocí následujícího kódu v souboru Web.config nebo app.config musí být povoleno ladění:  
  
    ```xml
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Tento kód jenom musí být přidán jednou. Tento kód můžete přidat úpravou souboru .config nebo připojením ke službě s použitím **připojit k procesu**. Při použití **připojit k procesu** službu, ladění kódu se automaticky přidá do souboru .config. Potom můžete ladit a Krokovat s vnořením služby bez nutnosti upravovat soubor .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Omezení krokování mimo službu  
 Krokování mimo službu a zpět do klienta má stejná omezení pro krokování s vnořením do služby. Kromě toho ladicí program musí být připojené ke klientovi. Pokud ladíte klienta a krokování s vnořením do služby, zůstane připojený ke službě ladicí program. Je hodnota true Určuje, zda jste spustili klienta s použitím **spustit ladění** nebo připojené ke klientovi pomocí **připojit k procesu**. Pokud jste začali ladění pomocí připojení ke službě, není dosud připojen ladicí program ke klientovi. V takovém případě Pokud máte krok ze služby a zpět klientovi, musíte nejprve použít **připojit k procesu** ručně připojit ke klientovi.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Omezení na automatické připojení ke službě  
 Automatické připojení ke službě má následující omezení:  
  
- Služba musí být součástí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] řešení ladění.  
  
- Musí být služba hostována. Může být součástí projektu webové stránky (systém souborů a HTTP), projekt webové aplikace (systém souborů a HTTP) nebo projekt knihovny služby WCF. Projekty knihovny služby WCF může být služba knihovny nebo knihovny služby pracovního postupu.  
  
- Služba musí být vyvolána z klienta WCF.  
  
- Pomocí následujícího kódu v souboru Web.config nebo app.config musí být povoleno ladění:  
  
  ```xml
  <system.web>  
    <compilation debug="true" />  
  <system.web>  
  ```  
  
## <a name="self-hosting"></a>S vlastním hostováním  
 A *služby v místním prostředí* je služba WCF, která není spuštěna služba IIS, hostitel služby WCF nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojový Server. Informace o tom, jak ladit v místním prostředí služby najdete v tématu [postupy: ladění služby WCF s místním](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>S vlastním hostováním  
 Chcete povolit ladění [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace 3.0 nebo 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 nebo 3.5, musí být nainstalována před [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] je nainstalována. Pokud [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] je nainstalována před [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 nebo 3.5, dojde k chybě při pokusu o ladění [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace 3.0 nebo 3.5. Je chybová zpráva "nelze automaticky krokovat do serveru." Chcete-li tento problém vyřešit, použijte Windows **ovládací panely** > **programy a funkce** opravit vaše [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] instalace.  
  
## <a name="see-also"></a>Viz také  
 [Ladění služeb WCF](../debugger/debugging-wcf-services.md)   
 [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
