---
title: 'Postupy: povolení funkce Autostart pro instalace disků CD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153788"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Postupy: Povolení funkce AutoStart pro instalace z média CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když nasadíte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci pomocí vyměnitelného média, jako je například CD-ROM nebo DVD-ROM, můžete povolit `AutoStart` , aby se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace automaticky spustila při vložení média.  
  
 `AutoStart` lze povolit na stránce **publikovat** v **Návrháři projektu**.  
  
### <a name="to-enable-autostart"></a>Povolení autostart  
  
1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. Klikněte na tlačítko **Možnosti** .  
  
     Zobrazí se dialogové okno **Možnosti publikování** .  
  
4. Klikněte na tlačítko **nasazení**.  
  
5. Zaškrtněte políčko **pro instalaci CD, automaticky spustit instalační program při vložení disku CD** .  
  
     Po publikování aplikace bude soubor Autorun. inf zkopírován do umístění pro publikování.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
