---
title: Nastavení správců pro měsíční odběry | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Nastavení správců pro měsíční předplatná
ms.openlocfilehash: a5d7c6e9442efd70ea3e7c2b7e7da4239e226aa2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "78289838"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Nastavení správců měsíčních předplatných sady Visual Studio

Měsíční předplatná sady Visual Studio spravují správci. Tito jednotlivci mohou přiřazovat předplatná, upravovat přiřazení, přidávat nebo odstraňovat odběry a provádět další úlohy správy předplatného.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Vlastník předplatného Azure je první správce

Když si koupíte měsíční předplatné Visual Studia, jako vlastník předplatného Azure použitého k nákupu, budete automaticky nastaveni jako správce pro tato předplatná.

Měsíční předplatné si můžete zakoupit na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)nebo kontaktováním poskytovatele cloudových řešení. Pokud nakupujete prostřednictvím webu Visual Studio Marketplace, budete mít na konci nákupního prostředí možnost spravovat uživatele. Výběrem této možnosti přejdete na portál [https://manage.visualstudio.com](https://manage.visualstudio.com)pro správu předplatných sady Visual Studio - .

Po zakoupení předplatného můžete kdykoli navštívit [portál pro správu.](https://manage.visualstudio.com) Stačí se přihlásit k portálu a vybrat příslušné předplatné Azure v levém horním rohu.

Jako vlastník předplatného Azure použitého k nákupu měsíčních předplatných můžete také přiřadit další správce.

## <a name="add-administrators"></a>Přidání správců

Přidání správců:

1. Připojte se k portálu Azure na [portal.azure.com](https://portal.azure.com).
2. Přihlaste se pomocí účtu, který jste použili k nákupu měsíčních předplatných Sady Visual Studio.
3. V části **Služby Azure**zvolte **Správa nákladů + Fakturace**.
   > [!div class="mx-imgBorder"]
   > ![Zvolte Správa nákladů + Fakturace v rámci služeb Azure](_img/cloud-admin/azure-cost-billing.png)
4. V seznamu **Moje předplatná** vyberte předplatné Azure, které jste použili k nákupu.
   > [!div class="mx-imgBorder"]
   > ![Zvolte předplatné](_img/cloud-admin/subscription-list.png)
5. Klepněte na **položku Řízení přístupu (IAM),** která se nachází v horní části seznamu v levém navigačním podokně.
6. Klikněte na kartu **Přidat** v horní části stránky.
7. Klepněte na tlačítko **Přidat přiřazení role**.
   > [!div class="mx-imgBorder"]
   > ![Zvolte řízení přístupu, Přidat, přidat přiřazení role.](_img/cloud-admin/access-control-add.png)
8. V rozbalovacím podokně vpravo klikněte na rozevírací **seznam Role** v horní části podokna, posuňte se dolů a vyberte **Správce přístupu uživatelů**.
9. V seznamu uživatelů přejděte dolů k uživateli, který chcete vytvořit správce, a vyberte ho. 
   > [!div class="mx-imgBorder"]
   > ![Zvolte Role, správce přístupu uživatele](_img/cloud-admin/add-role-user-access-admin.png)
10. Klikněte na **Uložit**.
11. Kliknutím na kartu **Přiřazení rolí** ověřte, zda se vybraný uživatel nyní zobrazuje jako správce přístupu uživatelů.

Nový správce se teď může přihlásit k [portálu pro správu](https://manage.visualstudio.com), vybrat stejné předplatné Azure, které bylo použito k nákupu měsíčních předplatných ze seznamu v levém horním rohu stránky, a začít tato předplatná spravovat.

> [!NOTE]
> Pokud se zobrazí uživatelé s přístupem k úpravám měsíčních předplatných, které jste nevytvořili jako správci, mohou mít role v podkladovém předplatném Azure, které jim umožňují spravovat předplatná. Mezi tyto role patří: vlastník, přispěvatel, správce služby nebo spolusprávce. Další informace naleznete v nápovědě [k připojovacím manažerům](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Informace o měsíčních předplatných Sady Visual Studio najdete v části [Přehled](vscloud-overview.md) v části Nákup předplatných. Chcete-li zakoupit měsíční předplatná sady Visual [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Studio, navštivte tržiště Sady Visual Studio na adrese .

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úpravy předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)



