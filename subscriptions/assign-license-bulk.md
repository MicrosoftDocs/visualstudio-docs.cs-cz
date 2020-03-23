---
title: Přiřazení licencí skupinám uživatelů pro předplatná sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Zjistěte, jak mohou správci přiřazovat licence více odběratelům pomocí funkce Hromadné přidání nebo skupin služby Microsoft Azure Active Directory.
ms.openlocfilehash: 3a4a6c400a17d52cdd67391a45ba088cdbb7af01
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988492"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Přiřazení předplatných více uživatelům
Portál správy předplatných umožňuje přidávat uživatele jednou za čas nebo ve velkých skupinách.  Informace o přidání jednotlivých uživatelů naleznete v tématu [Přidání jednotlivých uživatelů](assign-license.md).

Chcete-li přidat velké skupiny uživatelů, můžete použít funkci hromadného přidání, nebo pokud vaše organizace používá službu Microsoft Azure Active Directory (Azure AD), můžete použít skupiny Azure AD. Tento článek vysvětlí proces pro obě možnosti. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Přiřazení předplatných pomocí hromadného přidání
1. Přihlaste se k portálu https://manage.visualstudio.compro správu předplatných sady Visual Studio na adrese .

2. Pokud chcete přidat víc odběratelů najednou, přejděte na **Add** kartu **Spravovat odběratele.** **Bulk add**  

2. Hromadné přidání používá k nahrání informací o odběrateli šablonu aplikace Microsoft Excel. V dialogovém okně Nahrát více odběratelů klikněte na **Stáhnout** a stáhněte si šablonu.
   > [!div class="mx-imgBorder"]
   > ![Stažení maské šablony pro nahrání více odběratelů](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Vždy si stáhněte nejnovější verzi této šablony. Pokud používáte starší verzi, může dojít k selhání hromadného nahrávání.

3. V excelové tabulce vyplňte pole s informacemi o jednotlivcích, kterým chcete předplatná přiřadit. (*Reference* je volitelné pole.) Po dokončení uložte soubor místně.

   Chcete-li zajistit hladké nahrávání, dodržujte následující doporučené postupy:

    - Ujistěte se, že žádné z polí formuláře neobsahuje čárky.
    - Odeberte mezery před a za polemi formuláře.
    - Ujistěte se, že jména uživatele neobsahují další mezery mezi dvěma částmi křestního jména nebo příjmení (například pokud má osoba dvoudílné křestní jméno, například "Maggie May", měla by být zadána jako "MaggieMay", protože systém nebude oříznout další mezeru.)
    - Zkontrolujte, zda jsou vyplněna všechna povinná pole. 
    - Zkontrolujte sloupec **Chybová zpráva.**  Pokud jsou uvedeny nějaké chyby, vyřešte je před pokusem o nahrání souboru. 

4. Vraťte se na portál správy předplatných sady Visual Studio. V dialogovém okně **Nahrát více odběratelů** klepněte na **tlačítko Procházet**.
   > [!div class="mx-imgBorder"]
   > ![Přejděte do uložené šablony a nahrajte více odběratelů.](media/bulk-add-browse-saved-template.png)

5. Přejděte na uložený soubor aplikace Excel a klepněte na tlačítko **OK**.
   > [!div class="mx-imgBorder"]
   > ![Nahrání excelové šablony pro nahrání více odběratelů](media/bulk-upload-subscribers.png)

    Zobrazí se dialogové okno průběhu nahrávání.

    Pokud šablona obsahuje chyby, nahrávání se nezdaří a zobrazí se chyby, takže můžete šablonu opravit a pokusit se o hromadné nahrání znovu.
   > [!div class="mx-imgBorder"]
   > ![Chybová zpráva, pokud se nezdaří nahrávání více odběratelů](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Pokud narazíte na selhání, postupujte takto:
   1. Otevřete soubor aplikace Excel, který jste vytvořili, opravte problémy a uložte soubor.
   0. Vraťte se na portál Adminstration a zvolte **Přidat**.
   0. Vyberte **Hromadné přidání**.
   0. Vzhledem k tomu, že již máte uložený soubor aplikace Excel, nemusíte šablonu stahovat.  Klepněte na **tlačítko Procházet**, vyhledejte soubor, který jste právě uložili, a klepněte na **tlačítko Otevřít**.
   0. Klikněte na tlačítko **OK**.


    Po úspěšném nahrání se zobrazí seznam odběratelů a potvrzovací zpráva.
   > [!div class="mx-imgBorder"]
   > ![Potvrzovací zpráva, pokud je úspěšné nahrání více odběratelů](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Přiřazení předplatných pomocí skupin služby Azure Active Directory 
Použití této funkce usnadňuje možnost i nadále se přibližovat přiřazením předplatného. Skupiny zabezpečení Služby Azure Active Directory můžete přidat na portál u správy předplatných, který zajistí, že všem jednotlivcům ve skupině bude přiřazeno předplatné. A aby to bylo jednodušší, když jednotlivci opustí vaši organizaci a odeberou se ze služby Azure Active Directory, jejich přístup k předplatným se také odebere. 


> [!IMPORTANT]
>
> Použití skupin Azure AD je povoleno ve fázích.  Nemusí se okamžitě zobrazit funkce povolená pro vaši smlouvu(y).
>
> Následující omezení platí pro použití skupin Azure AD pro přidávání odběratelů:
> - Skupiny musí obsahovat alespoň jeden člen.  Prázdné skupiny nejsou podporovány.
> - Skupiny musí mít méně než 1 000 uživatelů. 
> - Všichni uživatelé musí být v nejvyšší úrovni skupiny.  Vnořené skupiny nejsou podporovány.
> - Podporovány jsou pouze důvěryhodné smlouvy.
> - Všichni členové skupiny musí mít e-mailovou adresu přidruženou k účtu Azure AD.
> - Samostatné e-mailové adresy pro oznámení nejsou podporovány pro odběry přidané pomocí skupin Azure AD.  

1. Přihlaste se k portálu [https://manage.visualstudio.com](https://manage.visualstudio.com)pro správu předplatných sady Visual Studio na adrese .

2. Chcete-li přidat více odběratelů najednou, přejděte na kartu **Spravovat odběratele.**

3. V rozevíracím seznamu zvolte kartu **Přidat** a v rozevíracím seznamu vyberte **skupinu Azure Active Directory.**  

   > [!div class="mx-imgBorder"]
   > ![Volba hromadného přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad.png)

4. Začněte zadávat název skupiny Azure AD, kterou chcete přidat do pole formuláře. To bude prohledávat dostupné skupiny Azure AD ve vaší organizaci. 

5. Když vyberete skupinu, pole se automaticky naplní názvem skupiny. Před přidáním budete mít možnost zobrazit uživatele v této skupině. Dále můžete zvolit úroveň předplatného, práva ke stažení a předvolby komunikace pro skupinu. Pokud chcete, můžete do referenčního pole přidat podrobnosti. 

   > [!div class="mx-imgBorder"]
   > ![Volba hromadného přidání pomocí Azure AD](_img/assign-license-bulk/bulk-add-aad-details.png)

6. Klepněte na tlačítko **Přidat** a potom **na potvrdit**. 

7. Chcete-li přidanou skupinu zobrazit, přejděte na konec seznamu uživatelů.  

8. Výběrem **možnosti Zobrazit odběratele** zobrazíte členy skupiny. Můžete zobrazit podrobnosti o odběratelích ve skupině, ale nelze provádět žádné úpravy odběratelů nebo předplatných, které jsou přiřazeny.    

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>Otázka: Můžu si vybrat více úrovní předplatného, které se mají přiřadit v rámci skupiny Azure AD? 
A: Ne -- všichni ve skupině obdrží stejné předplatné. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>Otázka: Můžu upravit podrobnosti o odběrateli jednotlivců přidaných ve skupině Azure AD?  
Odpověď: Ne -- Chcete-li upravit informace pro jednotlivé předplatitele, budete muset odebrat ze skupiny zabezpečení Azure AD a přiřadit jim předplatné jednotlivě.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>Otázka: Někoho jsem přidal do skupiny zabezpečení Azure AD, ale nevidím ho přidané ho na portálu pro správu předplatných a nemají předplatné. Proč ne?  
A: V závislosti na tom, jak vaše organizace nakonfigurovala Azure AD, může zobrazit zpoždění až 24 hodin před přidáním uživatele. Pokud je to delší než 24 hodin, [obraťte se na podporu](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Chcete přidat pouze jednoho nebo dva odběratele?  Rezervovat [Přidat jednotlivé uživatele](assign-license.md)
- Potřebujete pomoc? Obraťte se na [podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).
