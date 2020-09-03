---
title: 'Postupy: ladění webových aplikací | Microsoft Docs'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205406"
---
# <a name="how-to-debug-web-applications"></a>Postupy: Ladění webových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] je primární technologie pro vývoj webových aplikací v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ladicí program poskytuje výkonné nástroje pro ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webových aplikací lokálně nebo na vzdáleném serveru. Toto téma popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projekt během vývoje. Informace o tom, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, která je již nasazena na provozním serveru, naleznete v tématu [ladění nasazených webových aplikací](../debugger/debugging-deployed-web-applications.md).  
  
 Ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace:  
  
- Musíte mít požadovaná oprávnění. Další informace najdete v části [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ladění musí být povoleno ve **vlastnostech projektu**.  
  
- Konfigurační soubor aplikace (Web.config) musí být nastaven na režim ladění. Režim ladění způsobí [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] generování symbolů pro dynamicky generované soubory a umožňuje ladicímu programu připojit se k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikaci. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tuto sadu nastaví automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.  
  
- Další informace najdete v tématu [Postup: povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Ladění webové aplikace během vývoje  
  
1. V nabídce **ladit** klikněte na **Spustit** a začněte ladit webovou aplikaci.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestaví projekt webové aplikace, nasadí aplikaci v případě potřeby, spustí vývojový server ASP.NET, pokud provádíte ladění místně a připojíte se k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovnímu procesu.  
  
2. Použijte ladicí program k nastavení a vymazání zarážek, krokování a provádění dalších operací ladění, stejně jako u libovolné aplikace.  
  
     Další informace najdete v tématu [Základy ladicího programu](../debugger/debugger-basics.md).  
  
3. V nabídce **ladění** kliknutím na možnost **Zastavit ladění** ukončete relaci ladění, nebo v nabídce **soubor** v aplikaci Internet Explorer klikněte na tlačítko **Zavřít**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací a skriptů](../debugger/debugging-web-applications-and-script.md)   
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Postupy: Povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
