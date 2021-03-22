---
title: Úprava předplatných sady Visual Studio na portálu pro správu | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/21/2021
ms.topic: how-to
description: Přečtěte si, jak můžou správci upravovat přiřazení předplatného.
ms.openlocfilehash: b1779b80cc295e680ff1856181be42a6390fe25b
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776867"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Upravit přiřazení předplatných sady Visual Studio
Jako správce předplatného můžete provádět změny v předplatných přiřazených jednotlivcům ve vaší organizaci.  Tento článek popisuje typy změn, které lze provést, a poskytuje potřebné kroky.

   > [!NOTE]
   > Pokud potřebujete změnit podrobnosti předplatného pro předplatitele přiřazený prostřednictvím skupiny Azure Active Directory, budete je muset ze skupiny odebrat a přidat na portál pro správu jednotlivě.  

## <a name="change-subscriber-information"></a>Změna informací o odběrateli
Můžete upravit informace předplatitele a opravit chyby nebo aktualizovat informace.

Pokud chcete odběratele upravit, vyberte tři tečky (...), které se zobrazí vedle e-mailové adresy předplatitele, když na ni najedete myší. Zobrazí se rozevírací seznam.  Výběrem **Upravit** upravíte podrobnosti odběratele. 
> [!div class="mx-imgBorder"]
> ![Vyberte odběratele, kterého chcete upravit.](_img/edit-license/select-subscriber.png "Klikněte na tlačítko se třemi tečkami a vyberte možnost Upravit.")

Můžete aktualizovat křestní jméno, příjmení, úroveň předplatného, e-mailovou adresu, zemi, jazyk, soubory ke stažení a referenční pole. Upravte informace o odběrateli a klikněte na **Uložit**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Úprava více odběratelů pomocí hromadné úpravy

Pomocí procesu hromadného úprav můžete upravovat více předplatitelů najednou. Tato funkce se primárně používá pro organizace, které procházejí se změnami firemních e-mailových adres, nebo pokud se organizace rozhodla omezit přístup k souborům ke stažení.

Podívejte se na toto video nebo si přečtěte, kde se dozvíte, jak upravit více předplatitelů pomocí hromadné úpravy. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> V šabloně neměňte identifikátory GUID předplatného. Přečtěte si prosím náš článek o [přiřazování konkrétních identifikátorů GUID předplatného](assign-guid.md).

1. Chcete-li upravit více předplatitelů najednou, přejděte na kartu předplatitelé. Na pásu karet nahoře klikněte na **Hromadná úprava**.

2. Hromadná úprava používá excelovou šablonu k provádění úprav informací o odběrateli. V poli Hromadná úprava klikněte na **exportovat tento Excel** a Stáhněte si aktuální seznam předplatitelů včetně všech jejich informací.
   > [!div class="mx-imgBorder"]
   > ![Úprava seznamu hromadných úprav pro export licencí](_img/edit-license/edit-license-bulk-edit-export.png "Kliknutím na exportovat tento Excel vytvořte seznam aktuálních předplatných.")

3. Potom uložte soubor místně, abyste ho mohli snadno najít a provést potřebné změny před jeho odesláním. 

4. Vraťte se na portál pro správu předplatných sady Visual Studio a v dialogovém okně hromadné úpravy klikněte na **Procházet**. Vyberte excelový soubor, který jste uložili, a klikněte na **OK**. Na obrazovce se zobrazí průběh nahrávání.
   > [!div class="mx-imgBorder"]
   > ![Úprava nahrávání souboru s hromadnou úpravou licencí](_img/edit-license/edit-license-bulk-file-upload1.png "Přejděte do umístění dokončeného souboru aplikace Excel, vyberte jej a klikněte na tlačítko OK.")

5. Po nahrání souboru se zobrazí oznámení o tom, že bylo úspěšné. V tomto okamžiku se vaše úpravy projeví v informacích o odběrateli.

## <a name="resources"></a>Zdroje informací
- [Podpora předplatných](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Potřebujete přiřadit konkrétní ID předplatného? Podívejte se na přiřazení ID předplatného. 
- Nápovědu k vyhledání konkrétního předplatného najdete v tématu [hledání předplatného](search-license.md).
- Potřebujete vytvořit seznam všech vašich předplatných?  Podívejte se na [Export předplatných](exporting-subscriptions.md).