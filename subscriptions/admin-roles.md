---
title: Role správce super a správce na portálu pro správu
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 09/03/2020
ms.topic: conceptual
description: Přečtěte si o rolích správce superuživatele a správců a postup přiřazení správců.
ms.openlocfilehash: b6c6abc920ff68b6439fe4bff6f813366888a912
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006147"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super správci a správci pro smlouvy o předplatném sady Visual Studio

Na novém portálu pro správu předplatných sady Visual Studio jsou k dispozici dvě různé role pro multilicenční zákazníky. Tyto role jsou jako role primárního/informačního kontaktu a role správce předplatných, které se používají v VLSC.

**Super správci:** Při počátečním nastavování organizace se primární nebo informační kontakt ve výchozím nastavení stal nadtypem správce. Primární nebo informační kontakt se může rozhodnout, že přiřadí další superuživatele nebo správce. Správce Super může přidat a odebrat další správce i předplatitele. Pokud je v systému více než dva Super správci, může nadstraněný správce odstranit všechny kromě poslední dvě pro zabezpečení.

**Správci:** Správce může být přiřazen pouze správci super. Správce může spravovat pouze předplatitele v rámci smluv, ke kterým je správce superuživatele přiřazovat.

Podívejte se na ukázku správy správců. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Přiřazování správců
Přiřazení nových správců (správcům):
1. Přihlaste se k https://manage.visualstudio.com používání e-mailové adresy, která je přiřazená jako nadsprávce na smlouvě, jejímž prostřednictvím bylo předplatné zakoupilo.
2. Klikněte na kartu s názvem **Správa správců**.
3. Klikněte na **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![Přidat správce](_img/admin-roles/add-admins.png "Klikněte na okno spravovat správce a pak kliknutím na Přidat přiřaďte nové správce.")
4. Vyplňte formulář s informacemi o novém Správci.  
   > [!div class="mx-imgBorder"]
   > ![Přidat formulář správce](_img/admin-roles/add-form.png "Zadejte přihlašovací údaje pro nového správce a vyberte, jestli se mají nastavit jako správce super.  Pak klikněte na Přidat.")

   > [!NOTE]
   > Pokud chcete, aby tento správce mohl přiřadit další správce, nezapomeňte zaškrtnout políčko **správce Super** .

5. Když kliknete na **Přidat** a přiřadíte nového správce, obdrží jim e-mail, aby se přihlásil k portálu.  

## <a name="resources"></a>Zdroje informací
- [Podpora správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Další kroky
- Informace o tom, jak [přiřadit odběry](assign-license.md)
- Další informace o plném rozsahu [výhod předplatného](https://visualstudio.microsoft.com/vs/benefits/)
- [Nastavení předvoleb smluv](admin-prefs.md)