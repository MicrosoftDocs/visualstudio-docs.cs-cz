---
title: 'Postupy: ladění aplikace ClickOnce s omezenými oprávněními | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c30766b50692052ec9fdd04c5ec1b156738c47b5
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152968"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Postupy: ladění aplikace ClickOnce s omezenými oprávněními
Jako vývojář pravděpodobně používáte vývojového počítače oprávnění plné důvěryhodnosti, takže neuvidíte stejné výjimky zabezpečení při ladění aplikace ClickOnce, která koncový uživatel může zobrazit při spuštění s omezenými oprávněními.  
  
 Pokud chcete zachytit tyto výjimky, je potřeba ladění aplikace se stejnými oprávněními jako koncový uživatel. Ladění s omezenými oprávněními může být povoleno na **zabezpečení** stránku **Návrháře projektu**.  
  
 Kromě toho při vývoji aplikací, které volají webové služby, tyto webové služby často jsou umístěny ve svém vývojovém počítači. Po nasazení, koncovému uživateli přístup k těmto webovým službám z jinou adresu URL. Pokud chcete emulovat činnost koncového uživatele při ladění, můžete zadat že adresu URL a ladicí program bude považovat webové služby, jako kdyby byly volány z této adresy URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Pokud chcete povolit ladění s omezenými oprávněními  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **zabezpečení** kartu.  
  
3.  Vyberte **povolit nastavení zabezpečení ClickOnce** zaškrtněte políčko a potom klikněte **Toto je aplikace s částečnou důvěryhodností** přepínač.  
  
4.  Klikněte na tlačítko **Upřesnit** tlačítko.  
  
5.  Vyberte **Ladit tuto aplikaci s vybranou sadou oprávnění** zaškrtněte políčko a potom klikněte na tlačítko **OK**.  
  
     Při ladění aplikace, všechny pokusy o přístup k oprávněním, který není součástí sady oprávnění vyvolá výjimka zabezpečení.  
  
### <a name="to-specify-a-url-for-debugging"></a>Zadejte adresu URL pro ladění  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **zabezpečení** kartu.  
  
3.  Vyberte **povolit nastavení zabezpečení ClickOnce** zaškrtněte políčko a potom klikněte **Toto je aplikace s částečnou důvěryhodností** přepínač.  
  
4.  Klikněte na tlačítko **Upřesnit** tlačítko.  
  
5.  Vyberte **Ladit tuto aplikaci s vybranou sadou oprávnění** zaškrtněte políčko a potom klikněte na tlačítko **OK**.  
  
6.  V **Ladit tuto aplikaci, jako kdyby byla stažena z následující adresy URL** textového pole zadejte adresu URL nebo síťovou cestu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)