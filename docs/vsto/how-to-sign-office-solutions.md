---
title: 'Postupy: podepisování řešení pro systém Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 23afc171fd97620b3e6801b8d199da6890198d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545753"
---
# <a name="how-to-sign-office-solutions"></a>Postupy: podepisování řešení pro systém Office
  Pokud podepíšete řešení, můžete k řešení důvěřovat pomocí certifikátu jako legitimace. Stejný certifikát můžete použít pro více řešení a všechna řešení budou důvěryhodná bez dalších aktualizací zásad zabezpečení.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pokud ručně upravíte manifesty aplikace a nasazení pomocí Manifest Generation and Editing Tool (*mage.exe* a *mageui.exe*), musíte manifest znovu podepsat předtím, než je můžete použít. Další informace najdete v tématu [Postup: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Podepsat pomocí certifikátu
 Certifikát je soubor, který obsahuje jedinečný klíč a identitu vydavatele řešení. Můžete koupit certifikáty od certifikační autority nebo vytvořit vlastní certifikát a vlastnit si ho certifikační autorita.

 Sada Visual Studio podepisuje řešení pro Office s dočasným certifikátem pro povolení ladění. V nasazených řešeních jako legitimace byste neměli používat dočasný certifikát.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Podepsání řešení Office pomocí certifikátu

1. V nabídce **projekt** klikněte _na příkaz_**Vlastnosti vlastností**.

2. Klikněte na kartu **podepisování** .

3. Vyberte **podepsat manifesty ClickOnce**.

4. Vyhledejte certifikát kliknutím na **vybrat ze Storu** nebo **výběrem ze souboru** a přechodem na certifikát.

5. Chcete-li ověřit, zda je používán správný certifikát, klikněte na tlačítko **Další podrobnosti** a zobrazte informace o certifikátu.

## <a name="see-also"></a>Viz také

- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md)
- [Stránka Podepisování, návrhář projektu (C#)](../ide/reference/signing-page-project-designer.md)
