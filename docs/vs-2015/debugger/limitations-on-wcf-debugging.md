---
title: Omezení ladění WCF | Dokumentace Microsoftu
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
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c1d569712547144067cbfcfd894e31e1b41964e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798310"
---
# <a name="limitations-on-wcf-debugging"></a>Omezení ladění WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Tento kód jenom musí být přidán jednou. Tento kód můžete přidat úpravou souboru .config nebo připojením ke službě s použitím **připojit k procesu**. Při použití **připojit k procesu** službu, ladění kódu se automaticky přidá do souboru .config. Potom můžete ladit a Krokovat s vnořením služby bez nutnosti upravovat soubor .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Omezení krokování mimo službu  
 Krokování mimo službu a zpět do klienta má stejná omezení pro krokování s vnořením do služby. Kromě toho ladicí program musí být připojené ke klientovi. Pokud ladíte klienta a krokování s vnořením do služby, zůstane připojený ke službě ladicí program. Je hodnota true Určuje, zda jste spustili klienta s použitím **spustit ladění** nebo připojené ke klientovi pomocí **připojit k procesu**. Pokud jste začali ladění pomocí připojení ke službě, není dosud připojen ladicí program ke klientovi. V takovém případě Pokud máte krok ze služby a zpět klientovi, musíte nejprve použít **připojit k procesu** ručně připojit ke klientovi.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Omezení na automatické připojení ke službě  
 Automatické připojení ke službě má následující omezení:  
  
-   Služba musí být součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení ladění.  
  
-   Musí být služba hostována. Může být součástí projektu webové stránky (systém souborů a HTTP), projekt webové aplikace (systém souborů a HTTP) nebo projekt knihovny služby WCF. Projekty knihovny služby WCF může být služba knihovny nebo knihovny služby pracovního postupu.  
  
-   Služba musí být vyvolána z klienta WCF.  
  
-   Pomocí následujícího kódu v souboru Web.config nebo app.config musí být povoleno ladění:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>S vlastním hostováním  
 A *služby v místním prostředí* je služba WCF, která není spuštěna služba IIS, hostitel služby WCF nebo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový Server. Informace o tom, jak ladit v místním prostředí služby najdete v tématu [postupy: ladění služby WCF s místním](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>S vlastním hostováním  
 Chcete povolit ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace 3.0 nebo 3.5, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 nebo 3.5, musí být nainstalována před [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] je nainstalována. Pokud [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] je nainstalována před [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 nebo 3.5, dojde k chybě při pokusu o ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace 3.0 nebo 3.5. Je chybová zpráva "nelze automaticky krokovat do serveru." Chcete-li tento problém vyřešit, použijte Windows **ovládací panely**, **programy a funkce** opravit vaše [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] instalace.  
  
## <a name="see-also"></a>Viz také  
 [Ladění služeb WCF](../debugger/debugging-wcf-services.md)   
 [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



