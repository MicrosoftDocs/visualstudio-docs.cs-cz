---
title: 'Postupy: krokování se službami WCF | Microsoft Docs'
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
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176521"
---
# <a name="how-to-step-into-wcf-services"></a>Postupy: Krokování s vnořením služeb WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] můžete vstoupit do služby WCF. Pokud je služba WCF ve stejném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení jako klient, můžete ve službě WCF narazit zarážky.  
  
 Pro krokování v práci je nutné povolit ladění v souboru app.config nebo Web.config. Informace o tom, jak povolit ladění a omezení pro krokování služby WCF, najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Postup pro krokování se službou WCF  
  
1. Vytvořte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje projekt WCF i projekty služby WCF.  
  
2. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt klienta WCF a pak klikněte na **nastavit jako spouštěný projekt**.  
  
3. Povolit ladění v souboru app.config nebo web.config. Další informace najdete v tématu [omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Nastavte zarážku v umístění v klientském projektu, kde chcete začít s krokování. Obvykle to bude těsně před voláním služby WCF.  
  
5. Spusťte ke zarážce a pak začněte krokování. Ladicí program se automaticky přeskočí na službu.  
  
## <a name="see-also"></a>Viz také  
 [Ladění služeb WCF](../debugger/debugging-wcf-services.md)   
 [Omezení pro ladění WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Postupy: Ladění služby WCF s vlastním hostováním](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
