---
title: Přiřazení licencí skupinám uživatelů pro předplatná sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/26/2020
ms.topic: conceptual
description: Přečtěte si, jak můžou správci přiřazovat licence k několika předplatitelům pomocí funkce hromadného přidání nebo skupin Microsoft Azure Active Directory.
ms.openlocfilehash: a9bb8e1d96b3448a4ba803b7e6348057635950b4
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634608"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Přiřazení předplatných více uživatelům
Portál pro správu předplatných umožňuje přidat uživatele v jednom okamžiku nebo ve velkých skupinách.  Chcete-li přidat jednotlivé uživatele, přečtěte si téma [přidání jednotlivých uživatelů](assign-license.md).

Pokud chcete přidat velké skupiny uživatelů, můžete použít funkci hromadného přidání, nebo pokud vaše organizace používá Microsoft Azure Active Directory (Azure AD), můžete použít skupiny Azure AD. Tento článek vysvětluje postup pro obě možnosti. 


## <a name="use-bulk-add-to-assign-subscriptions"></a>Použití hromadného přidání k přiřazení předplatných
1. Přihlaste se na portál pro správu předplatných sady Visual Studio na https://manage.visualstudio.com.

2. Pokud chcete najednou přidat víc předplatitelů, přejděte na kartu **Spravovat předplatitele** . Zvolte kartu **Přidat** a pak v rozevíracím seznamu vyberte **hromadné přidání** .  

2. Hromadné přidání používá šablonu Microsoft Excelu k nahrání informací o odběrateli. V dialogovém okně nahrát několik předplatitelů klikněte na **Stáhnout** a stáhněte šablonu.
   > [!div class="mx-imgBorder"]
   > ![stáhnout excelovou šablonu pro nahrání více předplatitelů](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Vždy stáhnout nejnovější verzi této šablony. Pokud používáte starší verzi, může hromadné nahrání selhat.

3. V tabulce aplikace Excel vyplňte pole informacemi pro jednotlivce, ke kterým chcete přiřadit odběry. (*Odkaz* je volitelné pole.) Uložte soubor místně, až budete hotovi.

   Pro zajištění hladkého nahrávání si dodržujte následující osvědčené postupy:

    - Zajistěte, aby žádná pole formuláře neobsahovala čárky.
    - Odebrat mezery před a za poli formuláře.
    - Ujistěte se, že názvy uživatelů neobsahují nadbytečné mezery mezi dvěma částmi jména a příjmení (například pokud má osoba jméno se dvěma částmi, například "Maggie květen"), měla by být zadána jako "MaggieMay", protože systém neořízne nadbytečné místo.)
    - Ujistěte se, že jsou dokončená všechna povinná pole. 
    - Podívejte se na sloupec **chybová zpráva** .  Pokud jsou uvedeny nějaké chyby, vyřešte je před pokusem o nahrání souboru. 

4. Vraťte se na portál pro správu předplatných sady Visual Studio. V dialogovém okně **nahrát několik předplatitelů** klikněte na **Procházet**.
   > [!div class="mx-imgBorder"]
   > ![vyhledejte uloženou šablonu a nahrajte více předplatitelů](media/bulk-add-browse-saved-template.png)

5. Přejděte do excelového souboru, který jste uložili, a pak klikněte na **OK**.
   > [!div class="mx-imgBorder"]
   > ![nahrát excelovou šablonu pro nahrání více předplatitelů](media/bulk-upload-subscribers.png)

    Zobrazí se dialogové okno s průběhem nahrávání.

    Pokud šablona obsahuje chyby, nahrávání se nezdaří a zobrazí se chyby, abyste mohli šablonu opravit a znovu se pokusit o hromadné nahrání.
   > [!div class="mx-imgBorder"]
   > ![chybová zpráva, pokud nahrávání více předplatitelů neproběhne úspěšně](media/bulk-add-template-failed.png)

    Po úspěšném nahrání se zobrazí seznam předplatitelů a potvrzovací zpráva.
   > [!div class="mx-imgBorder"]
   > ![potvrzující zprávu, pokud je nahrávání více předplatitelů úspěšné](media/bulk-add-template-success.png)

## <a name="use-azure-ad-groups-to-assign-subscriptions"></a>Přiřazení předplatných pomocí skupin Azure AD 
Díky této funkci se můžete snadno soustředit na přiřazení předplatného. Na portálu pro správu předplatných můžete přidat skupiny zabezpečení Azure AD, které zajistí, že se předplatné přiřadí všem jednotlivcům ve skupině. A aby bylo snazší, když jednotlivci odejdou z vaší organizace a jsou z Azure AD odebráni, odebere se i jejich přístup k předplatným.

> [!NOTE]
> Tato funkce se nasazuje ve fázích, takže nemusí být pro vaši organizaci okamžitě dostupná.   

> [!IMPORTANT]
> Následující omezení se vztahují na použití skupin Azure AD pro přidávání předplatitelů:
> - Skupiny musí obsahovat alespoň jeden člen.  Prázdné skupiny se nepodporují.
> - Skupiny musí mít méně než 1 000 uživatelů.
> - Všichni uživatelé musí být na nejvyšší úrovni skupiny.  Vnořené skupiny se nepodporují.
> - Podporovány jsou pouze důvěryhodné smlouvy.
> - Všichni členové skupiny musí mít e-mailovou adresu přidruženou ke svému účtu Azure AD.


1. Přihlaste se na portál pro správu předplatných sady Visual Studio na [https://manage.visualstudio.com](https://manage.visualstudio.com).

2. Pokud chcete najednou přidat víc odběratelů, přejděte na kartu **Spravovat předplatitele** .

3. Zvolte kartu **Přidat** a pak v rozevíracím seznamu vyberte **Azure Active Directory skupina** .  

   > [!div class="mx-imgBorder"]
   > ![vyberte hromadné přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad.png)


4. Začněte zadáním názvu skupiny Azure AD, kterou chcete přidat do pole formuláře. Tato akce vyhledá dostupné skupiny Azure AD v rámci vaší organizace. 

5. Když vyberete skupinu, pole se automaticky vyplní názvem skupiny. Budete mít možnost Zobrazit uživatele v této skupině, než je přidáte. V dalším kroku můžete zvolit úroveň předplatného, práva ke stažení a předvolby komunikace pro skupinu. Pokud chcete, můžete do pole Reference přidat podrobnosti. 

   > [!div class="mx-imgBorder"]
   > ![vyberte hromadné přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Klikněte na **Přidat** a **potvrďte**. 

7. Pokud chcete zobrazit přidanou skupinu, posuňte se do dolní části seznamu uživatelů.  

8. Vyberte **Zobrazit předplatitele** k zobrazení členů skupiny. Můžete zobrazit podrobnosti o předplatitelích ve skupině, ale nemůžete provádět žádné úpravy odběratelů nebo předplatných, ke kterým se přiřadí.    

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Otázka: mohu vybrat více úrovní předplatného, které mají být přiřazeny v rámci skupiny Azure AD? 
Odpověď: ne – všichni ve skupině obdrží stejné předplatné. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Otázka: mohu upravit podrobnosti odběratele jednotlivců přidaných ve skupině Azure AD?  
Odpověď: ne – Chcete-li upravit informace pro jednotlivé odběratele, budete je muset odebrat ze skupiny zabezpečení Azure AD a přiřadit je k předplatnému jednotlivě.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-add-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Otázka: Přidal (a) jsem někoho do skupiny zabezpečení služby Azure AD, ale nevidím, aby se přidal na portál pro správu předplatných a nemá předplatné. Proč?  
Odpověď: v závislosti na tom, jak vaše organizace nakonfigurovala Azure AD, se může zobrazit zpoždění až 24 hodin, než se uživatel přidá. Pokud je delší než 24 hodin, obraťte se na [podporu](https://visualstudio.microsoft.com/support/support-overview-vs).  


## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Chcete přidat jenom jednoho nebo dva předplatitele?  Podívejte se na [přidat jednotlivé uživatele](assign-license.md) .
- Potřebujete pomoc? Obraťte [se na podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).



