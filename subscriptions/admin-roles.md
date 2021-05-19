---
title: Role superuživatele a správce pro předplatná sady Visual Studio
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 03/19/2021
ms.topic: conceptual
description: Přečtěte si o rolích správce superuživatele a správců a postup přiřazení správců.
ms.openlocfilehash: 1f107a5bcef9be61c4693549ee8e628a207cc789
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973535"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Služby Super Admins a Admins pro Visual Studio – smlouvy o předplatném

Na novém portálu pro správu předplatných sady Visual Studio jsou k dispozici dvě různé role pro multilicenční zákazníky. Tyto role jsou jako role primárního/informačního kontaktu a role správce předplatných, které se používají v VLSC.

**Super správci:** Při počátečním nastavování organizace se primární nebo informační kontakt ve výchozím nastavení stal nadtypem správce. Primární nebo informační kontakt se může rozhodnout, že přiřadí další superuživatele nebo správce. Správce Super může přidat a odebrat další správce i předplatitele. Pokud je v systému více než dva Super správci, může nadstraněný správce odstranit všechny kromě poslední dvě pro zabezpečení.

**Správci:** Správce může přiřadit pouze správce superuživatelů. Správce může spravovat pouze předplatitele v rámci smluv, ke kterým se správce superuživatele přiřadí.

Podívejte se na ukázku správy správců. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>Přiřazování správců
Přiřazení nových správců (správcům):
1. Přihlaste se k https://manage.visualstudio.com používání e-mailové adresy, která je přiřazená jako nadsprávce na smlouvě, jejímž prostřednictvím bylo předplatné zakoupilo.
2. Klikněte na kartu s názvem **Správa správců**.
3. Klikněte na **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![Přidat správce](_img/admin-roles/add-admins.png "Klikněte na okno Spravovat správce a pak kliknutím na Přidat přiřaďte nové správce.")
4. Vyplňte formulář s informacemi o novém Správci.  
   > [!div class="mx-imgBorder"]
   > ![Přidat formulář správce](_img/admin-roles/add-form.png "Zadejte přihlašovací údaje nového správce a zvolte, jestli se má z nich udělat supers právy správce.  Pak klikněte na Přidat.")

   > [!NOTE]
   > Pokud chcete, aby tento správce mohl přiřadit další správce, nezapomeňte zaškrtnout políčko **správce Super** .

5. Když kliknete na **Přidat** a přiřadíte nového správce, obdrží jim e-mail, aby se přihlásil k portálu.  

## <a name="resources"></a>Zdroje informací
- [Visual Studio správy a předplatných](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Viz také
- [Visual Studio dokumentace](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Microsoft 365 dokumentace](/microsoft-365/)



## <a name="next-steps"></a>Další kroky
- Zjistěte, jak [přiřadit předplatná.](assign-license.md)
- Další informace o celé řadě výhod [předplatného](https://visualstudio.microsoft.com/vs/benefits/)
- [Nastavení předvoleb smluv](admin-preferences.md)