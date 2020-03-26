---
title: Úpravy předplatných na portálu pro správu | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: Přečtěte si, jak můžou správci upravovat přiřazení předplatného.
ms.openlocfilehash: d145d556467b4eecec787fe409b4faa45945bec0
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232555"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Úprava přiřazení předplatného sady Visual Studio
Jako správce předplatného můžete provádět změny v předplatných přiřazených jednotlivcům ve vaší organizaci.  Tento článek popisuje typy změn, které můžete provést, a poskytuje nezbytné kroky.

   > [!NOTE]
   > Pokud potřebujete změnit podrobnosti o předplatném pro odběratele přiřazené prostřednictvím skupiny Azure Active Directory, budete je muset odebrat ze skupiny a přidat je na portál pro správu jednotlivě.  

## <a name="change-subscriber-information"></a>Změna informací o odběrateli
Můžete upravit informace o odběrateli a opravit chyby nebo aktualizovat informace.

Chcete-li upravit odběratele, vyberte tři tečky (...), které se zobrazí vedle e-mailové adresy odběratele, když na něj najedete myší. Zobrazí se rozevírací soubor.  Vyberte **Upravit,** chcete-li upravit podrobnosti odběratele. 
> [!div class="mx-imgBorder"]
> ![Vyberte odběratele, který chcete upravit.](_img/edit-license/select-subscriber.png)

Můžete aktualizovat jméno odběratele, příjmení, úroveň předplatného, e-mailovou adresu, zemi, jazyk, soubory ke stažení a referenční pole. Upravte informace o odběrateli a klepněte na tlačítko **Uložit**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Úprava více odběratelů pomocí hromadných úprav
Pomocí procesu hromadných úprav můžete upravovat více odběratelů najednou. Tato funkce se používá především pro organizace, které procházejí změnami firemních e-mailových adres nebo pokud se organizace rozhodla omezit přístup ke stahování.

   > [!IMPORTANT]
   > Úrovně předplatného (tj. podnikové, profesionální atd.) a identifikátory GUID předplatného nelze změnit pomocí hromadné úpravy.  Pokud potřebujete přiřadit uživatelům identifikátory GUID konkrétního předplatného, použijte proces pro přidání uživatelů výběrem ID předplatného. Pokud se pokusíte o nahrání s těmito položkami změněnými v šabloně hromadné úpravy, nahrávání se nezdaří.

1. Chcete-li upravit více odběratelů najednou, přejděte na kartu Odběratelé. Na pásu karet nahoře klikněte na **Hromadné úpravy**.

2. Hromadné úpravy používají šablonu Aplikace Excel k úpravám informací o odběrateli. V poli Hromadné úpravy klikněte na **Exportovat tuto excelovou** položku a stáhněte si aktuální seznam odběratelů včetně všech jejich informací.
   > [!div class="mx-imgBorder"]
   > ![Úprava licence – export seznamu hromadných úprav](_img/edit-license/edit-license-bulk-edit-export.png)

3. Dále uložte soubor místně, abyste jej mohli snadno najít a provést potřebné změny před jeho nahráním. Chcete-li zajistit úspěšné nahrání, **neupravujte úroveň předplatného nebo identifikátor GUID předplatného** v souboru hromadné úpravy, protože to způsobí selhání nahrávání.

4. Vraťte se na portál správy předplatných sady Visual Studio a v dialogovém okně Hromadné úpravy klepněte na **tlačítko Procházet**. Vyberte uložený excelový soubor a klepněte na **OK**. Průběh nahrávání uvidíte na obrazovce.
   > [!div class="mx-imgBorder"]
   > ![Úprava licence – hromadné úpravy nahrání souboru](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Po nahrání souboru se zobrazí oznámení, že byl úspěšný. V tomto okamžiku se vaše úpravy projeví v informacích o odběrateli.

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Potřebujete přiřadit konkrétní ID předplatného? Přečtěte si přečtěte si o přiřazení ID předplatného. 
- Nápovědu k vyhledání konkrétního předplatného najdete [v rozhledě v hledání předplatného](search-license.md).
- Potřebujete vytvořit seznam všech vašich předplatných?  Podívejte se na [exportní odběry](exporting-subscriptions.md).


