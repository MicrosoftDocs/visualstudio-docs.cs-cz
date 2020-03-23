---
title: Role super správců a správců na portálu pro správu
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Přečtěte si o rolích super správců a správců a o tom, jak přiřadit správce.
ms.openlocfilehash: ef0ba479c099bf1e34fe871386984297b130ffd6
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "78234818"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super správci a správci pro smlouvy o předplatném Visual Studia

V novém portálu pro správu předplatných visual studia pro zákazníky s multilicenčním číslem existují dvě různé role. Tyto role jsou jako primární/oznámení kontaktní role a role Správce odběrů, které existovaly v VLSC.

**Super správci:** Když je organizace původně nastavena, primární kontakt nebo kontakt oznámení se ve výchozím nastavení stane super správcem. Primární kontakt nebo kontakt s oznámeními může přiřadit další super správce nebo správce. Super admin může přidávat a odebírat další správce, stejně jako předplatitelé. Pokud existuje více než dva super adminy v systému, super-admin může odstranit všechny, ale poslední dva pro bezpečnost.

**Správci:** Správce může přiřadit pouze super správce. Správce může spravovat pouze předplatitele ve smlouvách, které jim super správce přiřadí.

## <a name="assigning-administrators"></a>Přiřazení správců
Přiřazení nových správců (správců):
1. Přihlaste https://manage.visualstudio.com se k používání e-mailové adresy, která je přiřazena jako super správce smlouvy, přes kterou byla předplatná zakoupena.
2. Klikněte na kartu s názvem **Spravovat správce**.
3. Klikněte na **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![Přidání správců](_img/admin-roles/add-admins.png)
4. Vyplňte formulář s informacemi nového správce.  
   > [!div class="mx-imgBorder"]
   > ![Přidání formuláře správce](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Pokud chcete, aby tento správce mohl přiřadit další správce, nezapomeňte zaškrtnout políčko **Super Admin.**

5. Po kliknutí na **přidat** přiřadíte nového správce, obdrží e-mail s výzvou k přihlášení k portálu.  

## <a name="resources"></a>Zdroje informací
- [Podpora správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Další kroky
- Přečtěte si, jak [přiřadit předplatná.](assign-license.md)
- Další informace o celé řadě [výhod předplatného](https://visualstudio.microsoft.com/vs/benefits/)
- [Nastavení předvoleb smluv](admin-prefs.md) 


