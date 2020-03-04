---
title: Role správce super a správce na portálu pro správu
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Přečtěte si o rolích správce superuživatele a správců a postup přiřazení správců.
ms.openlocfilehash: ef0ba479c099bf1e34fe871386984297b130ffd6
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78234818"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super správci a správci pro smlouvy o předplatném sady Visual Studio

Na novém portálu pro správu předplatných sady Visual Studio jsou k dispozici dvě různé role pro multilicenční zákazníky. Tyto role jsou jako role primárního/informačního kontaktu a role správce předplatných, které se používají v VLSC.

**Super správci:** Při počátečním nastavování organizace se primární nebo informační kontakt ve výchozím nastavení stal nadtypem správce. Primární nebo informační kontakt se může rozhodnout, že přiřadí další superuživatele nebo správce. Správce Super může přidat a odebrat další správce i předplatitele. Pokud je v systému více než dva Super správci, může nadstraněný správce odstranit všechny kromě poslední dvě pro zabezpečení.

**Správci:** Správce může být přiřazen pouze správci super. Správce může spravovat pouze předplatitele v rámci smluv, ke kterým je správce superuživatele přiřazovat.

## <a name="assigning-administrators"></a>Přiřazování správců
Přiřazení nových správců (správcům):
1. Přihlaste se k https://manage.visualstudio.com s použitím e-mailové adresy, která je přiřazená jako správce Super u smlouvy, přes kterou se předplatné zakoupilo.
2. Klikněte na kartu s názvem **Správa správců**.
3. Klikněte na **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![přidat správce](_img/admin-roles/add-admins.png)
4. Vyplňte formulář s informacemi o novém Správci.  
   > [!div class="mx-imgBorder"]
   > ![Přidání formuláře správce](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Pokud chcete, aby tento správce mohl přiřadit další správce, nezapomeňte zaškrtnout políčko **správce Super** .

5. Když kliknete na **Přidat** a přiřadíte nového správce, obdrží jim e-mail, aby se přihlásil k portálu.  

## <a name="resources"></a>Zdroje
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


