---
title: Osobní e-maily zobrazené v VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: Předplatné sady Visual Studio – proč se mi zobrazuje hotmail nebo gmailové adresy pro předplatitele?
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223681"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Předplatná visual studia – proč se u odběratelů zobrazují osobní účty?
Poté, co společnosti migrovaly z Centra multilicenčních služeb (VLSC) na nový [portál správy předplatných](https://manage.visualstudio.com)sady Visual Studio , byli správci překvapeni, že "Přihlašovací e-mailová adresa" pro některé předplatitele zobrazuje osobní e-mailovou adresu, jako je Hotmail nebo Outlook.  

## <a name="cause"></a>Příčina
K tomuto scénáři dochází z důvodu přihlášení procesy, které byly přidruženy ke starším prostředí předplatitele MSDN. Uživatelé byli migrována z Volume License Service Center (VLSC) na portál pro správu předplatných sady Visual Studio bez úprav. Správci si možná nebyli vědomi toho, že uživatelé používali osobní účty k přístupu k výhodám předplatného. Před migracepředplatitele sady Visual Studio, které byly dokončeny v roce 2016, byly k úspěšnému použití předplatného sady Visual Studio vyžadovány dvě akce:
1. Správce "přiřadil" předplatné jednotlivému odběrateli pomocí jeho pracovní nebo školní e-mailové adresy.
2. Účastník "aktivoval" předplatné.

Během procesu aktivace odběratele: K přihlášení byl vyžadován účet Microsoft (MSA). Pokud se předplatitel nepokusil vytvořit svůj pracovní nebo školní tasha@contoso.comúčet (např. ) MSA, mohl by vytvořit nový MSA nebo využít stávající. To mělo za následek, že jejich "přihlašovací e-mailová adresa" se liší od jejich "Přiřazeno k e-mailové adrese".

> [!NOTE]
> Moderní prostředí pro [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) předplatitele podporuje typy identit Work/School i Microsoft Account (MSA).

## <a name="solution"></a>Řešení

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Chcete-li problém vyřešit, jednoduše vyberte tlačítko **Připojit e-maily** a systém se pokusí porovnat účty s MSA s existujícími uživateli ve vaší organizaci Azure Active Directory (Azure AD) na základě odpovídající jméno a příjmení. Pokud dojde k chybě, můžete odstranit libovolnou shodu kliknutím na **X** napravo od shody.  

> [!div class="mx-imgBorder"]
> ![Tlačítko Připojit e-maily](_img/connect-emails/connect-emails-button.png)

Můžete také použít **adresář vyhledávání** opravit chyby nebo vyplnit chybějící informace z Azure AD. Pokud všechny shody vypadají správně, můžete zvolit možnost "Vybrat všechny odpovídající předplatitele", nikoli je vybírat po jednom.  

> [!div class="mx-imgBorder"]
> ![Připojení e-mailů Fly-out](_img/connect-emails/connect-emails-flyout.png)

Další klikněte na "pokračovat", který vás zavede na obrazovku popisující změny, které se mají uskutečnit. Pokud souhlasíte, klikněte na tlačítko "uložit" a změny budou provedeny. Váš odběratel také obdrží zprávu informující o změně při příštím přihlášení k předplatnému.   

> [!div class="mx-imgBorder"]
> ![Připojení potvrzení e-mailů](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Při úpravě přihlašovací e-mailovou adresu to pouze aktualizuje e-mail https://my.visualstudio.compoužívaný účastníkem k přihlášení k jejich předplatné na . Pokud předplatitel již aktivoval výhody, jako je Azure nebo Pluralsight pomocí jiné e-mailové adresy, bude muset nadále používat tyto e-mailové adresy pro přístup k nim. Pro všechny nové výhody, které mají přístup, by měli použít novou e-mailovou adresu. 

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Další kroky
- Pokud jste aktualizovali e-mailovou adresu odběratele(y), můžete je upozornit, že se změnily jejich přihlašovací údaje.  Obdrží také e-mail s aktualizovanými informacemi.
- Může být užitečné [filtrovat seznam odběratelů](search-license.md) ve vaší organizaci a vyhledat všechny přihlašovací e-mailové adresy, které může být nutné změnit.  
