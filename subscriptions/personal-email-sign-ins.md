---
title: Osobní e-maily zobrazené v VLSC
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: Předplatná sady Visual Studio – proč se mi zobrazují adresy služby Hotmail nebo Gmail pro moje předplatitele?
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81223681"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Předplatná sady Visual Studio – proč se mi zobrazují osobní účty pro moje předplatitele?
Po migraci společností z webu Volume Licensing Service Center (VLSC) na nový [portál pro správu předplatných](https://manage.visualstudio.com)sady Visual Studio byli správci překvapeni, že "přihlašovací e-mailová adresa" pro některé předplatitele zobrazuje osobní e-mailovou adresu, jako je Hotmail nebo Outlook.  

## <a name="cause"></a>Příčina
K tomuto scénáři dochází v důsledku procesů přihlašování, které byly přidruženy k starší verzi služby předplatitele MSDN. Uživatelé byli migrováni z webu Volume License Service Center (VLSC) na portál pro správu předplatných sady Visual Studio bez úprav. Správci možná nebudou vědomi, že uživatelé používali osobní účty pro přístup k výhodám jejich předplatného. Před migrací předplatitele sady Visual Studio, které byly dokončeny v 2016, byly pro úspěšné použití Visual Studio Subscription nutné dvě akce:
1. Správce přiřadil předplatné individuálnímu předplatiteli pomocí své pracovní nebo školní e-mailové adresy.
2. Předplatné je aktivované předplatitelem.

Během procesu aktivace předplatitele se vyžaduje účet Microsoft (MSA), abyste se přihlásili. Pokud se předplatitel nepokusí svůj pracovní nebo školní účet (např. tasha@contoso.com ) MSA, mohl vytvořit nový MSA nebo využít stávající. Výsledkem je, že se "e-mailová adresa pro přihlášení" liší od jejich "přiřazeno e-mailové adresy".

> [!NOTE]
> Moderní prostředí pro předplatitele v systému [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) podporuje typy identit pracovní/školní a účet Microsoft (MSA).

## <a name="solution"></a>Řešení

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Pokud chcete tento problém vyřešit, stačí vybrat tlačítko **připojit e-maily** a systém se pokusí porovnat účty s účty spravované služby stávajícím uživatelům v Azure Active Directory (Azure AD) vaší organizace na základě shody s prvním a posledním jménem. Pokud dojde k chybě, můžete jakoukoli shodu odstranit kliknutím na **X** napravo od shody.  

> [!div class="mx-imgBorder"]
> ![Tlačítko připojit emaily](_img/connect-emails/connect-emails-button.png)

Pomocí **adresáře hledání** můžete také opravit chyby nebo vyplnit chybějící informace z Azure AD. Pokud se všechny shody shodují, můžete vybrat možnost "vybrat všechny odpovídající předplatitele" a nemusíte je vybírat po jednom.  

> [!div class="mx-imgBorder"]
> ![Připojení k e-mailu](_img/connect-emails/connect-emails-flyout.png)

Potom klikněte na pokračovat, což vás převezme na obrazovce s osnovou změn, které se mají provést. Pokud souhlasíte, klikněte na Uložit a provedou se změny. Předplatitel dostane také zprávu o tom, že se změní při příštím přihlášení ke svému předplatnému.   

> [!div class="mx-imgBorder"]
> ![Potvrzení připojení e-mailů](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Když upravujete e-mailovou adresu pro přihlášení, aktualizuje se jenom e-mail, který předplatitel používá pro přihlášení ke svému předplatnému https://my.visualstudio.com . Pokud už předplatitel aktivoval výhody, jako je Azure nebo Pluralsight, pomocí jiné e-mailové adresy, bude muset tyto e-mailové adresy dál používat pro přístup k nim. Pro všechny nové výhody, ke kterým mají přístup, by měly používat novou e-mailovou adresu. 

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Další kroky
- Pokud jste aktualizovali e-mailové adresy odběratelů, můžete jim sdělit, že se změnily přihlašovací údaje.  Budou také dostávat e-maily s aktualizovanými informacemi.
- Může být užitečné [filtrovat seznam předplatitelů](search-license.md) ve vaší organizaci, aby se hledaly e-mailové adresy, které může být potřeba změnit.  
