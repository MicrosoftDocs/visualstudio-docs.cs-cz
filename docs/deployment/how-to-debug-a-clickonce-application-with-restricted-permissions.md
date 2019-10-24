---
title: Ladit aplikaci ClickOnce s omezenými oprávněními
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d942c41aac873b775566efa4e128651a8830e92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727953"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Postupy: ladění aplikace ClickOnce s omezenými oprávněními
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

## <a name="see-also"></a>Viz také:
- [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Zabezpečené aplikace ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [Zabezpečené aplikace ClickOnce](../deployment/securing-clickonce-applications.md)