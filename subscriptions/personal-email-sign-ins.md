---
title: Osobní e-maily zobrazené v VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Předplatná sady Visual Studio – proč se mi zobrazují adresy služby Hotmail nebo Gmail pro moje předplatitele?
ms.openlocfilehash: c4a3202bfb14246fa8057309de90bdc7c32db5df
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410212"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Předplatná sady Visual Studio – proč se mi zobrazují adresy služby Hotmail nebo Gmail pro moje předplatitele?
Po migraci společností z webu Volume Licensing Service Center (VLSC) na nový [portál pro správu předplatných](https://manage.visualstudio.com)sady Visual Studio byli správci překvapeni, že přihlašovací e-mailová adresa pro některé předplatitele zobrazuje e-mailovou adresu třetí strany, jako je Hotmail, Gmail nebo Yahoo.  Další informace najdete v [tomto videu](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6).

## <a name="cause"></a>Příčina
K tomuto scénáři dochází v důsledku procesů přihlašování, které byly přidruženy k starší verzi služby předplatitele MSDN. Uživatelé byli migrováni z webu Volume License Service Center (VLSC) na portál pro správu předplatných sady Visual Studio bez úprav. Správci možná nebudou vědomi, že uživatelé používali osobní účty pro přístup k výhodám jejich předplatného. Před migrací předplatitele sady Visual Studio, které byly dokončeny v 2016, byly pro úspěšné použití Visual Studio Subscription nutné dvě akce:
1. Správce přiřadil předplatné individuálnímu předplatiteli pomocí své pracovní nebo školní e-mailové adresy.
2. Předplatné je aktivované předplatitelem.

Během procesu aktivace předplatitele se vyžaduje účet Microsoft (MSA), abyste se přihlásili. Pokud se předplatiteli nepovedlo vytvořit pracovní nebo školní účet (například tasha@contoso.com), mohl vytvořit novou MSA nebo využít stávající. Výsledkem je, že se "e-mailová adresa pro přihlášení" liší od jejich "přiřazeno e-mailové adresy".

> [!NOTE]
> Nové prostředí pro předplatitele v [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) podporuje typy identit pracovní/školní a účet Microsoft (MAA).

## <a name="solution"></a>Řešení
Pokud chcete tento problém vyřešit, stačí vybrat tlačítko **připojit e-maily** a systém se pokusí porovnat účty s účty spravované služby stávajícím uživatelům v Azure Active Directory (Azure AD) vaší organizace na základě shody s prvním a posledním jménem. Pokud dojde k chybě, můžete jakoukoli shodu odstranit kliknutím na **X** napravo od shody.  

> [!div class="mx-imgBorder"]
> Tlačítko pro ![připojení k e-mailům](_img/connect-emails/connect-emails-button.png)

Pomocí **adresáře hledání** můžete také opravit chyby nebo vyplnit chybějící informace z Azure AD. Pokud se všechny shody shodují, můžete vybrat možnost "vybrat všechny odpovídající předplatitele" a nemusíte je vybírat po jednom.  

> [!div class="mx-imgBorder"]
> ](_img/connect-emails/connect-emails-flyout.png) ![připojení e-mailů

Potom klikněte na pokračovat, což vás převezme na obrazovce s osnovou změn, které se mají provést. Pokud souhlasíte, klikněte na Uložit a provedou se změny. Předplatitel dostane také zprávu o tom, že se změní při příštím přihlášení ke svému předplatnému.   

> [!div class="mx-imgBorder"]
> Potvrzení e-mailu ![připojení](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Když upravujete e-mailovou adresu pro přihlášení, aktualizuje se e-mail, který se používá pro přihlášení ke svému předplatnému na https://my.visualstudio.com. Pokud už předplatitel aktivoval výhody, jako je Azure nebo Pluralsight, pomocí jiné e-mailové adresy, bude muset tyto e-mailové adresy dál používat pro přístup k nim. Pro všechny nové výhody, ke kterým mají přístup, by měly používat novou e-mailovou adresu. 

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Další kroky
- Pokud jste aktualizovali e-mailové adresy odběratelů, můžete jim sdělit, že se změnily přihlašovací údaje.  Budou také dostávat e-maily s aktualizovanými informacemi.
- Může být užitečné [filtrovat seznam předplatitelů](search-license.md) ve vaší organizaci, aby se hledaly e-mailové adresy, které může být potřeba změnit.  
