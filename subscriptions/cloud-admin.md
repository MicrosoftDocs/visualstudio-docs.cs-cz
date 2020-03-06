---
title: Nastavení správců pro měsíční odběry | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Nastavení správců pro měsíční předplatná
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78289838"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Nastavení měsíčních předplatných pro správce sady Visual Studio

Měsíční předplatná sady Visual Studio spravuje správci. Tito uživatelé můžou přiřazovat předplatná, upravovat přiřazení, přidávat nebo odstraňovat předplatná a provádět další úlohy správy předplatných.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Vlastníkem předplatného Azure je první správce.

Při nákupu měsíčních předplatných sady Visual Studio se jako vlastník předplatného Azure, který se používá k nákupu, automaticky nastaví jako správce těchto předplatných.

Můžete si koupit měsíční předplatná prostřednictvím [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)nebo kontaktovat poskytovatele Cloud Solution Provider. Pokud si koupíte Visual Studio Marketplace na konci nákupu, budete mít k dispozici možnost spravovat uživatele. Výběrem této možnosti přejdete na portál pro správu předplatných sady Visual Studio – [https://manage.visualstudio.com](https://manage.visualstudio.com).

Po zakoupení předplatných můžete kdykoli navštívit [portál pro správu portálu](https://manage.visualstudio.com) . Stačí se přihlásit k portálu a vybrat příslušné předplatné Azure v levém horním rohu.

Jako vlastník předplatného Azure, který se používá k nákupu měsíčních předplatných, můžete také přiřadit další správce.

## <a name="add-administrators"></a>Přidat správce

Přidání správců:

1. Připojte se k webu Azure Portal na adrese [Portal.Azure.com](https://portal.azure.com).
2. Přihlaste se pomocí účtu, který jste použili k nákupu měsíčních předplatných sady Visual Studio.
3. V části **služby Azure**vyberte **cost management + fakturace**.
   > [!div class="mx-imgBorder"]
   > ![zvolit Cost Management a fakturaci pod službami Azure](_img/cloud-admin/azure-cost-billing.png)
4. V seznamu **Moje předplatné** vyberte předplatné Azure, které jste použili k nákupu.
   > [!div class="mx-imgBorder"]
   > ![zvolit předplatné](_img/cloud-admin/subscription-list.png)
5. Klikněte na **řízení přístupu (IAM)** , které se nachází poblíž horní části seznamu v levém navigačním podokně.
6. V horní části stránky klikněte na kartu **Přidat** .
7. Klikněte na **Přidat přiřazení role**.
   > [!div class="mx-imgBorder"]
   > ![zvolit řízení přístupu, přidat, přidat přiřazení role](_img/cloud-admin/access-control-add.png)
8. V podokně rozletět na pravé straně klikněte v horní části podokna na rozevírací nabídku **role** , přejděte dolů a vyberte **Správce přístupu uživatele**.
9. V seznamu uživatelů se posuňte dolů k uživateli, který chcete nastavit jako správce, a vyberte je. 
   > [!div class="mx-imgBorder"]
   > ![zvolit role, správce přístupu uživatele](_img/cloud-admin/add-role-user-access-admin.png)
10. Klikněte na **Uložit**.
11. Kliknutím na kartu **přiřazení rolí** ověřte, že uživatel, který jste vybrali, se teď zobrazí jako správce přístupu uživatele.

Nový správce se teď může přihlásit k [portálu pro správu](https://manage.visualstudio.com), vybrat stejné předplatné Azure, které se použilo k nákupu měsíčních předplatných ze seznamu v levém horním rohu stránky a začít spravovat tato předplatná.

> [!NOTE]
> Pokud se zobrazí uživatelé s přístupem k úpravám měsíčních předplatných, která jste nevytvořili jako správci, můžou mít v předplatném Azure příslušné role, které jim umožní spravovat předplatná. Mezi tyto role patří: vlastník, přispěvatel, správce služeb nebo spolusprávce. Další informace najdete na webu [Přidání správců fakturace](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Informace o měsíčních předplatných sady Visual Studio najdete v [přehledu](vscloud-overview.md) v části nákup předplatných. Měsíční předplatná sady Visual Studio si můžete koupit na Visual Studio Marketplace [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)



