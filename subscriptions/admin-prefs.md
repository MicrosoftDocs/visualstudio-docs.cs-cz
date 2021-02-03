---
title: Nastavení předvoleb smlouvy na portálu pro správu
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 10/22/2020
ms.topic: conceptual
description: Přečtěte si, jak nastavit předvolby pro jazyky, kontakty, úroveň předplatného a další na portálu pro správu.
ms.openlocfilehash: bdb6a5bc1160c75830fe9f1473222155d8fad781
ms.sourcegitcommit: d124123528776993eb5e7461dae8da3975d11d0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2021
ms.locfileid: "99511342"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Nastavení předvoleb pro vaše smlouvy na portálu pro správu
Super správci můžou nastavit určité Předvolby na portálu pro správu (portál pro správu), které se použijí globálně pro každou smlouvu.  Tyto preference automaticky naplní podrobnosti předplatného pro vaše správce, když přidávají předplatitele a můžou je upravovat jenom globálně správci super.  

## <a name="access-preferences"></a>Předvolby přístupu
Abyste mohli zobrazit nebo upravit předvolby, musíte být přihlášeni k [portálu pro správu](https://manage.visualstudio.com) pomocí přihlašovacího ID, které má práva správce k této smlouvě.  

Nastavení předvoleb:
1. Přihlaste se k portálu pro správu s ID, které má oprávnění superuživatele.
2. V levém podokně klikněte na ikonu nastavení.
   > [!div class="mx-imgBorder"]
   > ![Tlačítko Předvolby správce](_img/admin-prefs/admin-prefs-button.png "Kliknutím na Správa správců a pak na Předvolby smlouvy zobrazíte předvolby.")

3. Klikněte na **Předvolby smlouvy**.
Otevře se panel na levé straně a zobrazí se vaše dostupné předvolby. 

   > [!div class="mx-imgBorder"]
   > ![Dialogová okna Předvolby pro správu](_img/admin-prefs/admin-prefs-flyout.png "Nastavte předvolby a klikněte na Uložit.")

## <a name="set-your-preferences"></a>Nastavit předvolby
Pojďme prozkoumat všechny dostupné předvolby a jejich účinky. 

### <a name="agreement"></a>Smlouva
Pokud máte více smluv, pro které jste nadřízeného, budete moci zvolit požadovanou smlouvu v rozevíracím seznamu napravo od panelu Rozšířená nastavení.  Předvolby, které nastavíte, se použijí jenom pro danou smlouvu.  Při přiřazování předplatných můžou jednotliví správci potlačit některé z těchto předvoleb na základě případu. 

Pokud je k e-mailové adrese, kterou jste použili k přihlášení, přidružená jenom jedna smlouva, zobrazí se napravo od rozbaleného panelu nastavení a rozevírací seznam se zakáže. 

### <a name="contact-email-address"></a>Kontaktní e-mailová adresa
Tato předvolba nabízí způsob, jak vašim předplatitelům získat přístup ke správcům prostřednictvím tlačítka **kontaktujte správce** na [stránce Předplatná](https://my.visualstudio.com/subscriptions) na portálu pro předplatitele.  Pokud je tato předvolba prázdná, zprávy předplatitele se předají všem správcům a nadsprávcům této smlouvy.  K přizpůsobení cílové skupiny pro tento kontaktní e-mail doporučujeme použít e-mailový alias skupiny nebo skupinu zabezpečení. Můžete také zvolit zadání e-mailové adresy jednotlivce, pokud dáváte přednost.

> [!NOTE]
> E-mailová adresa, kterou tady uvedete, se zákazníkům neposkytne.  Když předplatitel odešle na portál odběratele žádost o **kontakt my admin** , zpráva se přepošle na alias, aniž by ji vystavil odběratel. 

### <a name="default-subscription-level"></a>Výchozí úroveň předplatného
Pomocí tohoto nastavení můžete určit, která z úrovní předplatného zahrnutých ve vaší smlouvě je standardně vybraná, když se k uživateli přiřadí předplatné.  Správci můžou toto nastavení změnit na libovolnou úroveň předplatného ve vaší smlouvě – to stačí, když nebudete muset opakovaně dělat nejběžnější volbu. 

### <a name="default-communication-preferences"></a>Výchozí předvolby komunikace
Nastavení výchozího komunikačního jazyka a národního prostředí může zjednodušit proces přiřazování předplatných.  Pokud je váš vývojový tým založen například na jiné zemi, než je váš tým pro správu, můžete nastavit předvolby nejvhodnější pro umístění předplatitelů. Tato nastavení může i nadále měnit všichni správci pro jednotlivé předplatitele. 

### <a name="default-external-subscribers-setting"></a>Nastavení výchozích externích odběratelů
Tato předvolba vám umožní rozhodnout, jestli správci můžou přidat předplatitele mimo tenanta nebo tenant vaší organizace.  Pokud tuto možnost vypnete, nepovolí se žádní externí předplatitelé.  Pokud ji povolíte a správce se pokusí přidat mimo předplatitele, zobrazí se jim výzva k potvrzení výběru a bude jim povoleno přiřadit předplatné. Správci nemohou přepsat toto nastavení. 

### <a name="default-downloads-setting"></a>Výchozí nastavení stahování
Povolení tohoto nastavení, které je ve výchozím nastavení zapnuté, umožní předplatitelům přístup ke stažení, když správci vytvoří nové předplatné.  Správci stále můžou zakázat stahování na základě jednotlivých předplatných.  Zakázáním přístupu ke stažení také zakážete přístup k klíčům Product Key.  


## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>Otázka: můžu zakázat **kontaktní e-mailovou adresu** , aby předplatitelé nemohly kontaktovat správce?
Odpověď: ne. Pokud chcete určit, kteří správci budou kontaktováni pomocí skupiny zabezpečení, e-mailového aliasu nebo jednotlivé e-mailové adresy, funkce se nedá zakázat.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Otázka: když odpovím na e-mail předplatitele, budou mít e-mailovou adresu?
Odpověď: vzhledem k tomu, že vaše odpověď přijde z libovolného e-mailového klienta, který používáte, zobrazí odpověď, kterou předplatitel obdrží, na základě jakékoli e-mailové adresy, kterou používáte.  Pokud tedy budete reagovat z aliasu skupiny, uvidí se alias skupiny.  Pokud odpovíte z vlastní e-mailové adresy, uvidí to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Otázka: kde se mohu dozvědět více o funkci **kontakt my admin** na portálu odběratele?
Odpověď: Podívejte se na náš [Kontakt na svého správce](contact-my-admin.md) . 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Otázka: Pokud nedokončíte **kontaktní e-mailovou adresu** a předplatitel používá funkci **kontaktujte my admin** , která obdrží svoji žádost?
Odpověď: Pokud v předvolbách **kontaktní e-mailová** adresa není nastavená žádná konkrétní e-mailová adresa, žádost obdrží všichni správci smlouvy. 

## <a name="resources"></a>Zdroje informací
- [Podpora správy a předplatných sady Visual Studio](https://my.visualstudio.com/gethelp)

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