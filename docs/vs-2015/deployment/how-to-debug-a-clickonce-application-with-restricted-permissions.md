---
title: 'Postupy: ladění aplikace ClickOnce s omezenými oprávněními | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153803"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Postupy: Ladění aplikace ClickOnce s omezenými oprávněními
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jako vývojář máte pravděpodobně spuštěný vývojový počítač s oprávněními s úplným vztahem důvěryhodnosti, takže při ladění aplikace ClickOnce, která se může koncovým uživatelem zobrazit při spuštění s omezenými oprávněními, se neobjeví stejné výjimky zabezpečení.  
  
 Aby bylo možné tyto výjimky zachytit, je nutné ladit aplikaci se stejnými oprávněními jako koncový uživatel. Ladění s omezenými oprávněními lze povolit na stránce **zabezpečení** **Návrháře projektu**.  
  
 Kromě toho při vývoji aplikací, které volají webové služby, se tyto webové služby často nacházejí ve vývojovém počítači. Po nasazení bude koncový uživatel přistupovat k těmto webovým službám z jiné adresy URL. Aby bylo možné emulovat činnost koncového uživatele během ladění, můžete zadat adresu URL a ladicí program bude považovat webové služby, jako kdyby byly volány z této adresy URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Povolení ladění s omezenými oprávněními  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. V **Návrháři projektu**klikněte na kartu **zabezpečení** .  
  
3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** a pak klikněte na tlačítko možnosti **částečně důvěřovat aplikaci** .  
  
4. Klikněte na tlačítko **Upřesnit** .  
  
5. Zaškrtněte políčko **Ladit tuto aplikaci s vybranou sadou oprávnění** a pak klikněte na **OK**.  
  
     Při ladění aplikace se všechny pokusy o přístup k oprávnění, které není součástí sady oprávnění, vyvolá výjimku zabezpečení.  
  
### <a name="to-specify-a-url-for-debugging"></a>Určení adresy URL pro ladění  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. V **Návrháři projektu**klikněte na kartu **zabezpečení** .  
  
3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** a pak klikněte na tlačítko možnosti **částečně důvěřovat aplikaci** .  
  
4. Klikněte na tlačítko **Upřesnit** .  
  
5. Zaškrtněte políčko **Ladit tuto aplikaci s vybranou sadou oprávnění** a pak klikněte na **OK**.  
  
6. V okně **Ladit tuto aplikaci, jako by byla stažena z následujícího textového pole adresy URL** zadejte adresu URL nebo cestu k síti.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
