---
title: Role správce super a správce na portálu pro správu
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 04/07/2020
ms.topic: conceptual
description: Přečtěte si o rolích správce superuživatele a správců a postup přiřazení správců.
ms.openlocfilehash: bf10b95d44a960fea50bff6b2fba7b9a8dc98a26
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248447"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super správci a správci pro smlouvy o předplatném sady Visual Studio

Na novém portálu pro správu předplatných sady Visual Studio jsou k dispozici dvě různé role pro multilicenční zákazníky. Tyto role jsou jako role primárního/informačního kontaktu a role správce předplatných, které se používají v VLSC.

**Super správci:** Při počátečním nastavování organizace se primární nebo informační kontakt ve výchozím nastavení stal nadtypem správce. Primární nebo informační kontakt se může rozhodnout, že přiřadí další superuživatele nebo správce. Správce Super může přidat a odebrat další správce i předplatitele. Pokud je v systému více než dva Super správci, může nadstraněný správce odstranit všechny kromě poslední dvě pro zabezpečení.

**Správci:** Správce může být přiřazen pouze správci super. Správce může spravovat pouze předplatitele v rámci smluv, ke kterým je správce superuživatele přiřazovat.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Přiřazování správců
Přiřazení nových správců (správcům):
1. Přihlaste se k https://manage.visualstudio.com používání e-mailové adresy, která je přiřazená jako nadsprávce na smlouvě, jejímž prostřednictvím bylo předplatné zakoupilo.
2. Vyberte kartu s názvem **Správa správců**.
3. Vyberte **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![Přidat správce](_img/admin-roles/add-admins.png "Vyberte okno spravovat správce a pak vyberte Přidat a přiřaďte nové správce.")
4. Vyplňte formulář s informacemi o novém Správci.  
   > [!div class="mx-imgBorder"]
   > ![Přidat formulář správce](_img/admin-roles/add-form.png "Zadejte přihlašovací údaje pro nového správce a vyberte, jestli se mají nastavit jako správce super.  Pak vyberte Přidat.")

   > [!NOTE]
   > Pokud chcete, aby tento správce mohl přiřadit další správce, nezapomeňte zaškrtnout políčko **správce Super** .

5. Když vyberete **Přidat** a přiřadíte nového správce, obdrží jim e-mail, aby se přihlásil k portálu.  

## <a name="resources"></a>Zdroje a prostředky
- [Podpora správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Další kroky
- Informace o tom, jak [přiřadit odběry](assign-license.md)
- Další informace o plném rozsahu [výhod předplatného](https://visualstudio.microsoft.com/vs/benefits/)
- [Nastavení předvoleb smluv](admin-prefs.md) 


