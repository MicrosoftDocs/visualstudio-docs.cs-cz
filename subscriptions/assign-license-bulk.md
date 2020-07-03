---
title: Přiřazení licencí skupinám uživatelů pro předplatná sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 05/10/2020
ms.topic: how-to
description: Přečtěte si, jak můžou správci přiřazovat licence k několika předplatitelům pomocí funkce hromadného přidání nebo skupin Microsoft Azure Active Directory.
ms.openlocfilehash: 459220c7fb2103da05f15607787390963863e622
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903276"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Přiřazení předplatných více uživatelům
Portál pro správu předplatných umožňuje přidat uživatele v jednom okamžiku nebo ve velkých skupinách.  Chcete-li přidat jednotlivé uživatele, přečtěte si téma [přidání jednotlivých uživatelů](assign-license.md).

Pokud chcete přidat velké skupiny uživatelů, můžete použít funkci hromadného přidání, nebo pokud vaše organizace používá Microsoft Azure Active Directory (Azure AD), můžete použít skupiny Azure AD. Tento článek vysvětluje postup pro obě možnosti. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Použití hromadného přidání k přiřazení předplatných
1. Přihlaste se na portál pro správu předplatných sady Visual Studio na adrese <https://manage.visualstudio.com> .

1. Pokud chcete najednou přidat víc předplatitelů, přejděte na kartu **Spravovat předplatitele** . Zvolte kartu **Přidat** a pak v rozevíracím seznamu vyberte **hromadné přidání** .  

1. Hromadné přidání používá šablonu Microsoft Excelu k nahrání informací o odběrateli. V dialogovém okně nahrát několik předplatitelů klikněte na **Stáhnout** a stáhněte šablonu.
   > [!div class="mx-imgBorder"]
   > ![Stáhněte si excelovou šablonu pro nahrání více odběratelů.](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Vždy stáhnout nejnovější verzi této šablony. Pokud používáte starší verzi, může hromadné nahrání selhat.

1. V tabulce aplikace Excel vyplňte pole informacemi pro jednotlivce, ke kterým chcete přiřadit odběry. (*Odkaz* je volitelné pole.) Uložte soubor místně, až budete hotovi.

    > [!NOTE]
    > Jedno z polí v šabloně umožňuje správcům povolit nebo zakázat stahování softwaru pro předplatitele.  Zakázání stahování také zakáže přístup k klíčům Product Key.

   Pro zajištění hladkého nahrávání si dodržujte následující osvědčené postupy:

    - Ujistěte se, že žádné z polí formuláře neobsahuje čárky.
    - Odstraňte mezery na začátku a konci polí formuláře.
    - Ujistěte se, že názvy uživatelů neobsahují nadbytečné mezery mezi dvěma částmi jména a příjmení (například pokud má osoba jméno se dvěma částmi, například "Maggie květen"), měla by být zadána jako "MaggieMay", protože systém neořízne nadbytečné místo.)
    - Ujistěte se, že jsou dokončená všechna povinná pole. 
    - Podívejte se na sloupec **chybová zpráva** .  Pokud jsou uvedeny nějaké chyby, vyřešte je před pokusem o nahrání souboru. 

1. Vraťte se na portál pro správu předplatných sady Visual Studio. V dialogovém okně **nahrát několik předplatitelů** klikněte na **Procházet**.
   > [!div class="mx-imgBorder"]
   > ![Pokud chcete nahrát několik předplatitelů, přejděte k uložené šabloně.](media/bulk-add-browse-saved-template.png)

1. Přejděte do excelového souboru, který jste uložili, a pak klikněte na **OK**.
   > [!div class="mx-imgBorder"]
   > ![Nahrání excelové šablony pro nahrání více předplatitelů](media/bulk-upload-subscribers.png)

    Zobrazí se dialogové okno s průběhem nahrávání.

    Pokud šablona obsahuje chyby, nahrávání se nezdaří a zobrazí se chyby, abyste mohli šablonu opravit a znovu se pokusit o hromadné nahrání.
   > [!div class="mx-imgBorder"]
   > ![Chybová zpráva, pokud nahrávání více předplatitelů neproběhne úspěšně](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Pokud dojde k selhání, postupujte podle následujících kroků:
   1. Otevřete excelový soubor, který jste vytvořili, opravte problémy a uložte soubor.
   0. Vraťte se na portál pro správu a vyberte **Přidat**.
   0. Vyberte **hromadné přidání**.
   0. Vzhledem k tomu, že už máte excelový soubor uložený, nemusíte stahovat šablonu.  Klikněte na **Procházet**, vyhledejte soubor, který jste právě uložili, a klikněte na **otevřít**.
   0. Klikněte na **OK**.


    Po úspěšném nahrání se zobrazí seznam předplatitelů a potvrzovací zpráva.
   > [!div class="mx-imgBorder"]
   > ![Zpráva s potvrzením úspěšného odeslání více předplatitelů](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Přiřazení předplatných pomocí skupin Azure Active Directory 
Díky této funkci se můžete snadno soustředit na přiřazení předplatného. Na portálu pro správu předplatných můžete přidat skupiny zabezpečení Azure Active Directory, které zajistí, že se k odběru všech jednotlivců ve skupině přiřadí předplatné. A aby bylo snazší, když jednotlivci opustí vaši organizaci a jsou odstraněné z Azure Active Directory, odeberou se také jejich přístup k předplatným. 


> [!IMPORTANT]
>
> Následující omezení se vztahují na použití skupin Azure AD pro přidávání předplatitelů:
> - Správce musí být členem tenanta AAD, když se poprvé přidá skupina na portál pro správu.  Po přidání skupiny nebudou změny členství ve skupinách vyžadovat zapojení správce. 
> - Skupiny musí obsahovat alespoň jeden člen.  Prázdné skupiny se nepodporují.
> - Skupiny musí mít méně než 1 000 uživatelů. 
> - Všichni uživatelé musí být na nejvyšší úrovni skupiny.  Vnořené skupiny se nepodporují.
> - Podporovány jsou pouze důvěryhodné smlouvy.
> - Všichni členové skupiny musí mít e-mailovou adresu přidruženou ke svému účtu Azure AD.
> - Samostatné e-mailové adresy pro oznámení se nepodporují u předplatných přidaných pomocí skupin Azure AD.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Přihlaste se na portál pro správu předplatných sady Visual Studio na adrese [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Pokud chcete najednou přidat víc odběratelů, přejděte na kartu **Spravovat předplatitele** .

3. Zvolte kartu **Přidat** a pak v rozevíracím seznamu vyberte **Azure Active Directory skupina** .  

   > [!div class="mx-imgBorder"]
   > ![Volba hromadného přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Začněte zadáním názvu skupiny Azure AD, kterou chcete přidat do pole formuláře. Tato akce vyhledá dostupné skupiny Azure AD v rámci vaší organizace. 

5. Když vyberete skupinu, pole se automaticky vyplní názvem skupiny. Budete mít možnost Zobrazit uživatele v této skupině, než je přidáte. V dalším kroku můžete zvolit úroveň předplatného, práva ke stažení a předvolby komunikace pro skupinu. Pokud chcete, můžete do pole Reference přidat podrobnosti. 

   > [!div class="mx-imgBorder"]
   > ![Volba hromadného přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Klikněte na **Přidat** a **potvrďte**. 

7. Pokud chcete zobrazit přidanou skupinu, posuňte se do dolní části seznamu uživatelů.  

8. Vyberte **Zobrazit předplatitele** k zobrazení členů skupiny. Můžete zobrazit podrobnosti o předplatitelích ve skupině, ale nemůžete provádět žádné úpravy odběratelů nebo předplatných, ke kterým se přiřadí.    

> [!NOTE]
> Pokud jste již odběry přiřadili uživatelům, kteří jsou následně přidáni jako součást skupiny Azure AD, budou přidány jako součást skupiny a nebudou již uvedeny jednotlivě. Pokud je však individuální předplatné pro jinou úroveň předplatného, budou mít dvě předplatná.  Příklad: Pokud má uživatel individuální Visual Studio Professional předplatné a je členem skupiny, ke které přiřadíte Visual Studio Enterprise předplatných, budou mít obě.  


## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Otázka: mohu vybrat více úrovní předplatného, které mají být přiřazeny v rámci skupiny Azure AD? 
Odpověď: ne – všichni ve skupině obdrží stejné předplatné. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Otázka: mohu upravit podrobnosti odběratele jednotlivců přidaných ve skupině Azure AD?  
Odpověď: ne. Pokud chcete upravit informace pro jednotlivé odběratele, budete je muset odebrat ze skupiny zabezpečení Azure AD a přiřadit jim předplatné individuálně.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Otázka: jsem přidal uživatele do skupiny zabezpečení Azure AD, ale nevidím ho na portálu pro správu předplatných a nemá předplatné. Proč ne?  
Odpověď: v závislosti na tom, jak vaše organizace nakonfigurovala Azure AD, se může zobrazit zpoždění až 24 hodin, než se uživatel přidá. Pokud je delší než 24 hodin, obraťte se na [podporu](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Chcete přidat jenom jednoho nebo dva předplatitele?  Podívejte se na [přidat jednotlivé uživatele](assign-license.md) .
- Potřebujete pomoc? Obraťte [se na podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
