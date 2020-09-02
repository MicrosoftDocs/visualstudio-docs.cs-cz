---
title: 'Příprava ladění: ASP.NET webové aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691465"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Příprava ladění: webové aplikace technologie ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Šablona webu vytvoří aplikaci webového formuláře. Když vytvoříte web pomocí této šablony, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vytvoří se výchozí nastavení pro ladění. V dialogovém okně **Vlastnosti projektu** můžete určit, zda má být webová stránka stránkou po spuštění. Když spustíte ladění webu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] s těmito výchozími nastaveními, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí aplikace Internet Explorer a připojí ladicí program k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovnímu procesu (aspnet_wp.exe nebo w3wp.exe). Další informace najdete v části [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Vytvoření aplikace webového formuláře  
  
1. V nabídce **soubor** vyberte možnost **Nový web**.  
  
2. V dialogovém okně **Nový web** vyberte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Web**.  
  
3. Klikněte na **OK**.  
  
### <a name="to-debug-your-web-form"></a>Ladění webového formuláře  
  
1. Nastavte jednu nebo více zarážek ve vašich funkcích a obslužných rutinách událostí.  
  
     Další informace naleznete v tématu [zarážky a trasováním](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Když je dosaženo zarážky, krokovat kód uvnitř funkce. Sledujte provádění kódu, dokud neizolujete problém.  
  
     Další informace naleznete v tématu [krokování](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) a [ladění webových aplikací a skriptů](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Změna výchozích konfigurací  
 Pokud chcete změnit výchozí konfiguraci ladění a vydaných verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kterou vytvořil, můžete to udělat. Další informace najdete v tématu [Postupy: nastavení ladění a konfigurací vydání](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Změna výchozí konfigurace ladění  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na web a výběrem **stránky vlastností** otevřete dialogové okno **stránky vlastností** .  
  
2. Klikněte na možnost **Spustit**.  
  
3. Nastavte **akci spustit** na webovou stránku, která se má zobrazit jako první.  
  
4. V části **Debuggery**se ujistěte, že je vybraná možnost **ladění v ASP.NET** .  
  
     Další informace naleznete v tématu [nastavení stránek vlastností pro webové projekty](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
