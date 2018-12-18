---
title: 'Příprava ladění: Webové aplikace ASP.NET | Dokumentace Microsoftu'
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
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59f4f3e1db92c5f7b46a9bb9e1e164fc25b01010
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730678"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Příprava ladění: webové aplikace technologie ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Webu šablona vytvoří aplikaci webového formuláře. Při vytváření webu pomocí této šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vytvoří výchozí nastavení pro ladění. V **vlastnosti projektu** dialogovém okně můžete zadat, zda chcete webové stránky na úvodní stránku. Při spuštění ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]webové stránky s těmito nastaveními výchozí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí aplikaci Internet Explorer a připojuje se ladicí program [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovního procesu (aspnet_wp.exe nebo w3wp.exe). Další informace najdete v tématu [požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Vytvoření aplikace webových formulářů  
  
1.  Na **souboru** nabídce zvolte **nový web**.  
  
2.  V **nový web** dialogu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **webu**.  
  
3.  Klikněte na tlačítko **OK**.  
  
### <a name="to-debug-your-web-form"></a>Chcete-li ladit webový formulář  
  
1.  Nastavte jednu nebo více zarážek ve funkcích a obslužné rutiny událostí.  
  
     Další informace najdete v tématu [zarážky a sledované body](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Při dosažení zarážky, krokovat kód uvnitř funkce. Sledujte provádění kódu, dokud problém.  
  
     Další informace najdete v tématu [krokování](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) a [ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Změna výchozí konfigurace  
 Pokud chcete změnit výchozí ladění a vydání konfigurace vytvořil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete to udělat. Další informace najdete v tématu [postupy: nastavení ladění a konfiguraci vydání](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Chcete-li změnit výchozí konfigurace ladění  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na webovou stránku a vybrat **stránky vlastností** otevřít **stránky vlastností** dialogové okno.  
  
2.  Klikněte na tlačítko **možnosti spuštění**.  
  
3.  Nastavte **spustit akci** na webovou stránku, který by měl být zobrazen jako první.  
  
4.  V části **ladicí programy**, ujistěte se, že **ladění ASP.NET** zaškrtnuto.  
  
     Další informace najdete v tématu [nastavení stránek vlastností pro webové projekty](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)



