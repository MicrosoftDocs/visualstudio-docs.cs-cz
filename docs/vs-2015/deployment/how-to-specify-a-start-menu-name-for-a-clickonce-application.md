---
title: 'Postupy: určení názvu nabídky Start pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149757"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Postupy: Určení názvu úvodní nabídky pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] je aplikace nainstalována pro online i offline použití, přidá se do nabídky **Start** položka a seznam **Přidat nebo odebrat programy** . Ve výchozím nastavení je zobrazované jméno stejné jako název sestavení aplikace, ale můžete změnit název zobrazení nastavením **názvu produktu** v dialogovém okně **Možnosti publikování** .  
  
 **Název produktu** se zobrazí na stránce publish.htm; v případě nainstalované offline aplikace se jedná o název položky v nabídce **Start** a také na název, který se zobrazí v nabídce **Přidat nebo odebrat programy**.  
  
 **Název vydavatele** se zobrazí na stránce publish.htm nad **názvem produktu**a v případě nainstalované offline aplikace bude také názvem složky, která obsahuje ikonu aplikace v nabídce **Start** .  
  
 Vlastnosti **název produktu** a **název vydavatele** můžete nastavit v dialogovém okně **Možnosti publikování** , které je k dispozici na stránce **publikovat** v **Návrháři projektu**.  
  
### <a name="to-specify-a-start-menu-name"></a>Určení názvu nabídky Start  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. Kliknutím na tlačítko **Možnosti** otevřete dialogové okno **Možnosti publikování** .  
  
4. Klikněte na **Popis**.  
  
5. V dialogovém okně **Možnosti publikování** zadejte název, který se zobrazí v poli **název produktu**.  
  
6. V případě potřeby můžete zadat název vydavatele v **názvu vydavatele**.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
