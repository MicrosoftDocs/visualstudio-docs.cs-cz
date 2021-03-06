---
title: Nastavování správců pro měsíční předplatná sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 02/18/2021
ms.topic: how-to
description: Nastavení správců pro měsíční předplatná
ms.openlocfilehash: c018dbc3437c03c6d029a98c84e0b6cceaef9e2c
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249541"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Nastavení pro měsíční předplatná sady Visual Studio pro správce

Měsíční předplatná sady Visual Studio spravuje správci. Tito uživatelé můžou přiřazovat předplatná, upravovat přiřazení, přidávat nebo odstraňovat předplatná a provádět další úlohy správy předplatných.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Vlastníkem předplatného Azure je první správce.

Při nákupu měsíčních předplatných sady Visual Studio se jako vlastník předplatného Azure, který se používá k nákupu, automaticky nastaví jako správce pro tato předplatná.

Můžete si koupit měsíční předplatná prostřednictvím [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)nebo kontaktovat poskytovatele Cloud Solution Provider. Pokud si koupíte Visual Studio Marketplace na konci nákupu, budete mít k dispozici možnost spravovat uživatele. Výběrem této možnosti přejdete na portál pro správu předplatných sady Visual Studio – [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Po zakoupení předplatných můžete kdykoli navštívit [portál pro správu portálu](https://manage.visualstudio.com) . Stačí se přihlásit k portálu a vybrat příslušné předplatné Azure v levém horním rohu.

Jako vlastník předplatného Azure, který se používá k nákupu měsíčních předplatných, můžete také přiřadit další správce.

## <a name="add-admins"></a>Přidat správce

Přidání správců:

1. Připojte se k Azure Portal na adrese [Portal.Azure.com](https://portal.azure.com).
2. Přihlaste se pomocí účtu, který jste použili k nákupu měsíčních předplatných sady Visual Studio.
3. V části **služby Azure** vyberte **cost management + fakturace**.
   > [!div class="mx-imgBorder"]
   > ![Výběr možnosti Cost Management + fakturace pod službami Azure](_img/cloud-admin/azure-cost-billing.png "Výběr Cost Management ze skupiny služeb Azure")
4. V seznamu **Moje předplatné** vyberte předplatné Azure, které jste použili k nákupu.
   > [!div class="mx-imgBorder"]
   > ![Zvolit předplatné](_img/cloud-admin/subscription-list.png "Vyberte předplatné Azure, které chcete použít k nákupu.")
5. Klikněte na **řízení přístupu (IAM)**, které se nachází poblíž horní části seznamu v levém navigačním podokně.
6. V horní části stránky klikněte na kartu **Přidat** .
7. Klikněte na **Přidat přiřazení role**.
   > [!div class="mx-imgBorder"]
   > ![Zvolit řízení přístupu, přidat, přidat přiřazení role](_img/cloud-admin/access-control-add.png "V seznamu na levé straně vyberte řízení přístupu a pak zvolte Přidat.")
8. V podokně rozletět na pravé straně klikněte v horní části podokna na rozevírací nabídku **role** , přejděte dolů a vyberte **Správce přístupu uživatele**.
9. V seznamu uživatelů se posuňte dolů k uživateli, který chcete nastavit jako správce, a vyberte je. 
   > [!div class="mx-imgBorder"]
   > ![Zvolit roli, správce přístupu uživatele](_img/cloud-admin/add-role-user-access-admin.png "Zvolte role, vyberte Správce přístupu uživatele a pak vyberte jméno uživatele, abyste ho mohli nastavit jako správce.")
10. Klikněte na **Uložit**.
11. Kliknutím na kartu **přiřazení rolí** ověřte, že uživatel, který jste vybrali, se teď zobrazí jako správce přístupu uživatele.

Nový správce se teď může přihlásit k [portálu pro správu](https://manage.visualstudio.com), vybrat stejné předplatné Azure, které se použilo k nákupu měsíčních předplatných ze seznamu v levém horním rohu stránky, a začít spravovat tato předplatná.

> [!NOTE]
> Pokud se zobrazí uživatelé s přístupem k úpravám měsíčních předplatných, která jste nevytvořili jako správci, můžou mít role v předplatném Azure, které jim umožní spravovat předplatná. Mezi tyto role patří: vlastník, přispěvatel, správce služeb nebo spolusprávce. Další informace najdete na webu [Přidání správců fakturace](/azure/devops/organizations/billing/add-backup-billing-managers).

Informace o měsíčních předplatných sady Visual Studio najdete v [přehledu](vscloud-overview.md) v části nákup předplatných. Pokud si chcete koupit měsíční předplatná sady Visual Studio, navštivte Visual Studio Marketplace na adrese [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="resources"></a>Zdroje informací
- [Podpora předplatných](https://visualstudio.microsoft.com/subscriptions/support/)


## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)