---
title: 'Postupy: určení stránky publikování pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 265c1d777da7703dbaa0dd7146a3142e8b7ddffa
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077978"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Postupy: určení stránky publikování pro aplikaci ClickOnce
Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace vygeneruje a publikovat aplikace spolu se výchozí webová stránka (publish.htm). Tato stránka obsahuje název aplikace, odkaz na instalaci aplikace a všechny požadované součásti a odkaz na nápovědu s popisem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Publikovat stránku** vlastností projektu můžete zadat název pro webovou stránku pro vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.  
  
 Jakmile stránka publikování nebyl zadán, při příštím publikování, bude zkopírován do umístění pro publikování; nesmí být přepsány, pokud znovu publikovat. Pokud chcete přizpůsobit vzhled stránky, činíte tak nemusíme se starat o ztrátu změn. Další informace najdete v tématu [postupy: Úprava výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Publikovat stránku** vlastnost lze nastavit **možnosti publikování** dialogové okno, přístupné **publikovat** podokně **Návrháře projektu**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Chcete-li určit vlastní webové stránky pro aplikaci ClickOnce  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **možnosti** tlačítko Otevřít **možnosti publikování** dialogové okno.  
  
4.  Klikněte na tlačítko **nasazení**.  
  
5.  V **možnosti publikování** dialogové okno pole, ujistěte se, že **publikování otevřít webovou stránku nasazení po** je zaškrtnuto políčko (by se měla vybrat ve výchozím nastavení).  
  
6.  V **webovou stránku nasazení** pole, zadejte název pro svou webovou stránku a pak klikněte na tlačítko **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Stránka publikovat zabránit spouštění pokaždé, když publikujete  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **možnosti** tlačítko Otevřít **možnosti publikování** dialogové okno.  
  
4.  Klikněte na tlačítko **nasazení**.  
  
5.  V **možnosti publikování** dialogové okno, zrušte **publikování otevřít webovou stránku nasazení po** zaškrtávací políčko.  
  
## <a name="see-also"></a>Viz také:  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Postupy: Úprava výchozí webové stránky ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)