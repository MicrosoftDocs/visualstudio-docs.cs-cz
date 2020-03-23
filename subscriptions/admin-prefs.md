---
title: Nastavení předvoleb smlouvy na portálu pro správu
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: Přečtěte si, jak nastavit předvolby pro jazyk, kontakty, úroveň předplatného a další na portálu pro správu.
ms.openlocfilehash: cbcf532620e958ca408d43295d2d4200d12ee0cd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508755"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>Nastavení předvoleb pro vaše smlouvy na portálu pro správu
Super správci mohou nastavit určité předvolby na portálu pro správu (portál pro správu), které budou použity globálně pro každou smlouvu.  Tyto předvolby automaticky vyplní podrobnosti o předplatném pro správce při přidávání odběratelů a mohou být změněny pouze globálně super správci.  

## <a name="access-preferences"></a>Předvolby přístupu
Abyste mohli zobrazit nebo upravit předvolby, musíte být k [portálu pro správu](https://manage.visualstudio.com) přihlášeni pomocí přihlašovacího ID, které má práva super správců ke smlouvě.  

Nastavení předvoleb:
1. Přihlaste se k portálu pro správu pomocí ID, které má oprávnění super správce.
2. Klikněte na kartu **Spravovat správce.**
   > [!div class="mx-imgBorder"]
   > ![Tlačítko Předvolby správce](_img/admin-prefs/admin-prefs-button.png)

3. Klikněte na **Předvolby smlouvy**.
Vpravo se otevře panel a zobrazí se vaše dostupné předvolby. 

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Předvolby správce](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Nastavení předvoleb
Podívejme se na každou z dostupných předvoleb a jejich efekty. 

### <a name="agreement"></a>Smlouva
Pokud máte více smluv, pro které jste super admin, budete moci vybrat požadovanou smlouvu v rozevíracím seznam.  Předvolby, které nastavíte, se budou vztahovat pouze na tuto smlouvu.  Jednotliví správci mohou přepsat některé z těchto předvoleb případ od případu při přiřazování předplatných. 

Pokud je k e-mailové adrese, kterou jste použili k přihlášení, přidružena pouze jedna smlouva, zobrazí se a rozevírací seznam bude zakázán. 

### <a name="contact-email-address"></a>Kontaktní e-mailová adresa
Tato předvolba umožňuje vašim odběratelům oslovit správce pomocí tlačítka **Kontaktujte správce** na [stránce odběrů](https://my.visualstudio.com/subscriptions) na portálu odběratelů.  Pokud je tato předvolba ponechána prázdná, budou zprávy odběratelů předány všem správcům a super správcům smlouvy.  Doporučujeme použít skupinový e-mailový alias nebo skupinu zabezpečení k přizpůsobení okruhu uživatelů pro tento kontaktní e-mail. Pokud dáváte přednost, můžete také zadat e-mailovou adresu jednotlivce.

> [!NOTE]
> E-mailová adresa, kterou zde uvádíte, nebude poskytnuta odběratelům.  Když odběratel odešle žádost **Kontaktujte mého správce** na portálu odběratele, zpráva bude předána aliasu, aniž by ji vystavil odběrateli. 

### <a name="default-external-subscribers-setting"></a>Výchozí nastavení externích odběratelů
Tato předvolba umožňuje rozhodnout, zda správci mohou přidávat předplatitele mimo klientnebo adresář vaší organizace.  Pokud tuto možnost vypnete, nebudou povoleni žádní externí odběratelé.  Pokud ji povolíte a správce se pokusí přidat externího odběratele, bude požádán o potvrzení své volby a bude moci přiřadit předplatné. Správci nemohou toto nastavení přepsat. 

### <a name="default-downloads-setting"></a>Výchozí nastavení stahování
Povolení tohoto nastavení, které je ve výchozím nastavení zapnuto, umožní odběratelům přístup ke stahování při vytváření nových předplatných správci.  Správci stále mohou zakázat stahování na základě individuálního předplatného.  

### <a name="default-subscription-level"></a>Výchozí úroveň předplatného
Toto nastavení můžete použít k určení, která z úrovní předplatného zahrnutých ve vaší smlouvě je vybrána ve výchozím nastavení, když je předplatné přiřazeno uživateli.  Správci mohou změnit nastavení na libovolnou úroveň předplatného ve vaší smlouvě – To jen zabrání nutnosti opakovaně provádět nejběžnější volbu. 

### <a name="default-communication-preferences"></a>Výchozí předvolby komunikace
Nastavení výchozího komunikačního jazyka a národního prostředí může zjednodušit proces přiřazování předplatných.  Pokud má například váš vývojový tým sídlo v jiné zemi než váš tým správce, můžete nastavit předvolby, které nejlépe odpovídají poloze odběratelů. Tato nastavení mohou stále měnit všichni správci pro jednotlivé předplatitele. 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>Otázka: Mohu zakázat **kontaktní e-mailovou adresu,** aby odběratelé nemohli kontaktovat správce?
Odpověď: Ne - zatímco můžete určit, kteří správci jsou kontaktováni pomocí skupiny zabezpečení, skupinového e-mailového aliasu nebo jednotlivé e-mailové adresy, tuto funkci nelze zakázat.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>Otázka: Pokud odpovím na e-mail účastníka, bude mít mou e-mailovou adresu?
Odpověď: Vzhledem k tomu, že vaše odpověď bude pocházet z jakéhokoli e-mailového klienta, který používáte, odpověď, kterou odběratel obdrží, zobrazí jakoukoli e-mailovou adresu, kterou používáte.  Takže pokud odpovídáte z aliasu skupiny, uvidí alias skupiny.  Pokud odpovíte z vlastní e-mailové adresy, uvidí to.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>Otázka: Kde se můžu dozvědět více o funkci **Kontaktujte mého správce** na portálu pro předplatitele?
A: Podívejte se na náš [kontakt můj admin](contact-my-admin.md) článek. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>Otázka: Pokud nedokončíme **kontaktní e-mailovou adresu** a odběratel použije funkci **Kontaktovat mého správce,** kdo obdrží jejich žádost?
A: Pokud není v předvolbě **Kontaktní e-mailová adresa** nastavena žádná konkrétní e-mailová adresa, všichni správci smlouvy obdrží žádost. 

## <a name="resources"></a>Zdroje informací
- [Podpora správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

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



