---
title: Nastavení předvoleb na portálu pro správu předplatných sady Visual Studio
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 05/18/2021
ms.topic: conceptual
description: Přečtěte si, jak nastavit předvolby pro jazyky, kontakty, úroveň předplatného a další na portálu pro správu.
ms.openlocfilehash: 348febd6b964feec54053cff4a3d50cc02eba3d0
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "110018507"
---
# <a name="set-preferences-for-your-agreements-in-the-admin-portal"></a>Nastavení předvoleb pro vaše smlouvy na portálu pro správu
Super správci můžou nastavit určité Předvolby na portálu pro správu (portál pro správu), které se použijí globálně pro každou smlouvu.  Tyto preference automaticky naplní podrobnosti předplatného pro vaše správce, když přidávají předplatitele a můžou je upravovat jenom globálně správci super.  

## <a name="access-preferences"></a>Předvolby přístupu
Abyste mohli zobrazit nebo upravit předvolby, musíte být přihlášeni k [portálu pro správu](https://manage.visualstudio.com) pomocí přihlašovacího ID, které má práva správce k této smlouvě.  

Nastavení předvoleb:
1. Přihlaste se k portálu pro správu s ID, které má oprávnění superuživatele.
2. V levém podokně klikněte na ikonu nastavení.
   > [!div class="mx-imgBorder"]
   > ![Tlačítko Předvolby správce](_img/admin-preferences/admin-preferences-button.png "Kliknutím na Spravovat správce a potom na Předvolby smlouvy zobrazte předvolby.")

3. Klikněte na **Předvolby smlouvy**.
Otevře se panel na levé straně a zobrazí se vaše dostupné předvolby. 

   > [!div class="mx-imgBorder"]
   > ![Dialogová okna Předvolby pro správu](_img/admin-preferences/admin-preferences-flyout-2.png "Nastavte předvolby a klikněte na Uložit.")

## <a name="set-your-preferences"></a>Nastavit předvolby
Pojďme prozkoumat všechny dostupné předvolby a jejich účinky. 

### <a name="agreement"></a>Smlouva
Pokud máte více smluv, pro které jste nadřízeného, budete moci zvolit požadovanou smlouvu v rozevíracím seznamu napravo od panelu Rozšířená nastavení.  Předvolby, které nastavíte, se použijí jenom pro danou smlouvu.  Při přiřazování předplatných můžou jednotliví správci potlačit některé z těchto předvoleb na základě případu. 

Pokud je k e-mailové adrese, kterou jste použili k přihlášení, přidružená jenom jedna smlouva, zobrazí se napravo od rozbaleného panelu nastavení a rozevírací seznam se zakáže. 

### <a name="contact-email-address"></a>Kontaktní e-mailová adresa
Tato předvolba umožňuje předplatitelům kontaktovat správce pomocí tlačítka  Kontaktovat správce na [](https://my.visualstudio.com/subscriptions) stránce předplatných na portálu pro předplatitele.  Pokud je tato předvolba prázdná, zprávy odběratele se předá všem správcům a superschůdkům ve smlouvě.  K přizpůsobení cílové skupiny pro tento kontaktní e-mail doporučujeme použít skupinový e-mailový alias nebo skupinu zabezpečení. Pokud chcete, můžete také zadat e-mailovou adresu jednotlivce.

> [!NOTE]
> E-mailová adresa, kterou tady vypište, NEBUDE předplatitelům poskytnuta.  Když odběratel odešle  žádost Kontaktujte mého správce na portálu pro předplatitele, zpráva se předá aliasu, aniž by ji předplatitelovi vystavil. 

### <a name="default-subscription-level"></a>Výchozí úroveň předplatného
Pomocí tohoto nastavení můžete určit, které úrovně předplatného zahrnuté ve vaší smlouvě jsou ve výchozím nastavení vybrány, když je předplatné přiřazeno uživateli.  Správci mohou toto nastavení změnit na libovolnou úroveň předplatného ve vaší smlouvě – stačí, když se opakovaně vyhoníte ze své nejčastější volby. 

### <a name="default-communication-preferences"></a>Výchozí předvolby komunikace
Nastavení výchozího komunikačního jazyka a národního prostředí může zjednodušit proces přiřazování předplatných.  Pokud je například váš vývojový tým umístěný v jiné zemi než váš tým pro správu, můžete nastavit předvolby, které jsou pro umístění odběratelů nejlepší. Tato nastavení mohou i nadále měnit všichni správci pro jednotlivé odběratele. 

### <a name="default-external-subscribers-setting"></a>Výchozí nastavení externích odběratelů
Tato předvolba umožňuje rozhodnout, jestli správci mohou přidávat předplatitele mimo tenanta nebo adresář vaší organizace.  Pokud tuto možnost vypnete, nebudou povoleni žádní externí odběratelé.  Pokud ho povolíte a správce se pokusí přidat externího předplatitele, zobrazí se mu dotaz, jestli má potvrdit svou volbu, a bude mu povoleno předplatné přiřadit. Správci nemohou toto nastavení přepsat. 

### <a name="default-downloads-setting"></a>Výchozí nastavení stahování
Povolením tohoto nastavení, které je ve výchozím nastavení povoleno, budou mít předplatitelé přístup ke stahování, když správci vytvoří nová předplatná.  Správci mohou stále zakázat stahování pro jednotlivá předplatná.  Zakázáním přístupu ke stažení se také zakáže přístup ke klíčům Product Key.  

### <a name="overallocation-notification"></a>Oznámení o přemísťování 
Výslovný souhlas s obdržením e-mailu, když se přiřazení ve smlouvě přetítí. Toto e-mailové oznámení se pošle na kontaktní [e-mailovou](admin-preferences.md#contact-email-address)adresu nebo na všechny správce ve vaší smlouvě, pokud neexistuje žádná kontaktní e-mailová adresa. Pomocí rozevírací nabídky můžete nakonfigurovat prahovou hodnotu, při které chcete být upozorněni. 

 
## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>Otázka: Můžu kontaktní e-mailovou **adresu zakázat,** aby předplatitelé nekontaktovali správce?
O: Ne– i když můžete určit, kteří správci jsou kontaktování pomocí skupiny zabezpečení, e-mailového aliasu skupiny nebo individuální e-mailové adresy, tuto funkci nelze zakázat.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Otázka: Pokud odpovím na e-mail odběratele, bude mít uživatel moji e-mailovou adresu?
Odpověď: Vzhledem k tomu, že vaše odpověď pochází z jakéhokoli e-mailového klienta, který používáte, odpověď, kterou odběratel obdrží, zobrazí e-mailovou adresu, kterou používáte.  Pokud tedy reagujete z aliasu skupiny, uvidí alias skupiny.  Pokud odpovíte z vlastní e-mailové adresy, uvidí ji.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Otázka: Kde najdu další informace o funkci **Kontaktovat** správce na portálu pro předplatitele?
O: Podívejte se na náš [článek Kontaktování správce.](contact-my-admin.md) 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Otázka: Pokud nevyplníme  kontaktní e-mailovou  adresu a odběratel použije funkci Kontaktovat správce, kdo obdrží žádost?
O: Pokud v předvolbě Kontaktní  e-mailová adresa není nastavená žádná konkrétní e-mailová adresa, obdrží žádost všichni správci ve smlouvě. 

## <a name="resources"></a>Zdroje informací
- [Visual Studio správy a předplatných](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Viz také
- [Visual Studio dokumentace](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Microsoft 365 dokumentace](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o Visual Studio předplatných.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení několika předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)