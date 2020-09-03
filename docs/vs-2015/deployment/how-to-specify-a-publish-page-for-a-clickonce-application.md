---
title: 'Postupy: určení stránky publikování pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202159"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Postupy: Určení stránky publikování pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je vygenerována a publikována výchozí webová stránka (publish.htm) spolu s aplikací. Tato stránka obsahuje název aplikace, odkaz pro instalaci aplikace a/nebo všechny požadované součásti a odkaz na téma nápovědy popisující [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Vlastnost **Page Publish** pro váš projekt umožňuje zadat název webové stránky pro vaši [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci.  
  
 Po zadání stránky publikování se při příštím publikování zkopíruje do umístění publikování; Při opětovném publikování se nebude přepsat. Pokud chcete přizpůsobit vzhled stránky, můžete tak učinit bez obav o ztrátu vašich změn. Další informace najdete v tématu [Postup: přizpůsobení výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Vlastnost **Publikovat stránku** lze nastavit v dialogovém okně **Možnosti publikování** přístupné z podokna **publikování** v **Návrháři projektu**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Určení vlastní webové stránky pro aplikaci ClickOnce  
  
1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Vyberte podokno **publikování** .  
  
3. Kliknutím na tlačítko **Možnosti** otevřete dialogové okno **Možnosti publikování** .  
  
4. Klikněte na tlačítko **nasazení**.  
  
5. V dialogovém okně **Možnosti publikování** se ujistěte, že je zaškrtnuté políčko **otevřít webovou stránku nasazení po publikování** (mělo by být vybráno ve výchozím nastavení).  
  
6. Na **webové stránce nasazení:** zadejte název webové stránky a potom klikněte na tlačítko **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Zabránění spuštění stránky publikovat při každém publikování  
  
1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Vyberte podokno **publikování** .  
  
3. Kliknutím na tlačítko **Možnosti** otevřete dialogové okno **Možnosti publikování** .  
  
4. Klikněte na tlačítko **nasazení**.  
  
5. V dialogovém okně **Možnosti publikování** zrušte zaškrtnutí políčka **otevřít webovou stránku nasazení po publikování** .  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Postupy: Přizpůsobení výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
