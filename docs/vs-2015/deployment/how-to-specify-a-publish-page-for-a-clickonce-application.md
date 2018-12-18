---
title: 'Postupy: určení stránky publikování pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: c10033f7e3f3a4336177c8c66721bd6b79ba4c71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196687"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Postupy: Určení stránky publikování pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace vygeneruje a publikovat aplikace spolu se výchozí webová stránka (publish.htm). Tato stránka obsahuje název aplikace, odkaz na instalaci aplikace a všechny požadované součásti a odkaz na nápovědu s popisem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. **Publikovat stránku** vlastností projektu můžete zadat název pro webovou stránku pro vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
 Jakmile stránka publikování nebyl zadán, při příštím publikování, bude zkopírován do umístění pro publikování; nesmí být přepsány, pokud znovu publikovat. Pokud chcete přizpůsobit vzhled stránky, činíte tak nemusíme se starat o ztrátu změn. Další informace najdete v tématu [postupy: Úprava výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Publikovat stránku** vlastnost lze nastavit **možnosti publikování** dialogové okno, přístupné **publikovat** podokně **Návrháře projektu**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Chcete-li určit vlastní webové stránky pro aplikaci ClickOnce  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **možnosti** tlačítko Otevřít **možnosti publikování** dialogové okno.  
  
4.  Klikněte na tlačítko **nasazení**.  
  
5.  V **možnosti publikování** dialogové okno pole, ujistěte se, že **publikování otevřít webovou stránku nasazení po** je zaškrtnuto políčko (by se měla vybrat ve výchozím nastavení).  
  
6.  V **webovou stránku nasazení:** pole, zadejte název pro svou webovou stránku a pak klikněte na tlačítko **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Stránka publikovat zabránit spouštění pokaždé, když publikujete  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **možnosti** tlačítko Otevřít **možnosti publikování** dialogové okno.  
  
4.  Klikněte na tlačítko **nasazení**.  
  
5.  V **možnosti publikování** dialogové okno, zrušte **publikování otevřít webovou stránku nasazení po** zaškrtávací políčko.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Postupy: Přizpůsobení výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)



