---
title: 'Postupy: podepisování řešení pro Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 161c175b6bb37ece93559f0378bbaf8e5e16d170
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776130"
---
# <a name="how-to-sign-office-solutions"></a>Postupy: podepisování řešení pro Office
  Pokud podepíšete řešení, můžete udělit důvěryhodnosti řešení pomocí certifikátu prokázat. Můžete použít stejný certifikát pro více řešení, a všechna řešení budou důvěryhodné žádné další aktualizace zásad.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Když ručně upravíte aplikace a manifesty nasazení s použitím Manifest Generation and Editing Tool (*mage.exe* a *mageui.exe*), musíte znovu podepsat manifesty, abyste mohli používat. Další informace najdete v tématu [postupy: Opětovné podepisování manifestů aplikace a nasazení](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="sign-by-using-a-certificate"></a>Podepsat pomocí certifikátu  
 Certifikát je soubor, který obsahuje jedinečný klíč a identita vydavatele řešení. Můžete koupit certifikáty od certifikační autority, nebo vytvořit svůj vlastní certifikát a nechat podepsat certifikační autority.  
  
 Visual Studio podepíše řešení pro systém Office s dočasný certifikát pro povolení ladění. Dočasný certifikát byste neměli používat v nasazeném řešení jako důkaz.  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>K podepisování řešení pro Office s použitím certifikátu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko _SolutionName_**vlastnosti**.  
  
2.  Klikněte na tlačítko **podepisování** kartu.  
  
3.  Vyberte **podepsat manifesty ClickOnce**.  
  
4.  Vyhledejte certifikát kliknutím **vybírat Store** nebo **vybrat ze souboru** a přejdete k certifikátu.  
  
5.  Chcete-li ověřit, jestli se používá správný certifikát, klikněte na tlačítko **další podrobnosti** zobrazíte informace o certifikátu.  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Zajistit jeho důvěryhodnost do řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md)   
 [Stránka Podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)  
  
  