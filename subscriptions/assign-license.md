---
title: Přiřazení předplatných sady Visual Studio uživatelům | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Informace o tom, jak můžou správci přiřazovat licence předplatitelům
ms.openlocfilehash: 95e0358a39ccb88ed93f8e5bcee11d2b36d12d48
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863111"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Přiřazení licencí na portálu pro správu předplatných sady Visual Studio
Jako správce předplatných sady Visual Studio můžete použít portál pro správu k přiřazení předplatných jednotlivým uživatelům a skupinám uživatelů.

Pro skupiny uživatelů máte možnosti, jak přiřadíte odběry.  
- Odběry můžete přiřadit v jednom okamžiku.
- Můžete také rychle a snadno odeslat seznamy předplatitelů a informace o jejich předplatném pomocí funkce [hromadného přidání](assign-license-bulk.md) .
- Pokud vaše organizace používá Microsoft Azure Active Directory (Azure AD), můžete k [přiřazení předplatných skupinám uživatelů použít skupiny Azure AD](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) .  


## <a name="add-a-single-subscriber"></a>Přidání jednoho předplatitele
Podívejte se na video nebo si přečtěte informace o tom, jak přiřadit předplatné sady Visual Studio novému uživateli, aby mohli získat přístup k výhodám předplatného.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Přihlaste se k [portálu pro správu](https://manage.visualstudio.com).
2. Pokud chcete přiřadit licenci jednomu předplatiteli sady Visual Studio, vyberte v horní části tabulky možnost **Přidat** a pak zvolte **jednotlivé odběratele**.
   > [!div class="mx-imgBorder"]
   > ![Přidání jednoho předplatitele](_img/assign-license-add/add-subscriber-individual.png "Vyberte Přidat a pak zvolte jednotlivé odběratele k přiřazení jednoho předplatného.")
3. Zadejte informace do polí formuláře pro nového předplatitele. Pokud vaše organizace používá Azure Active Directory, pole **název** slouží jako vyhledávací funkce pro hledání osob v aktuálním adresáři, abyste mohli vybrat správného uživatele z výsledků hledání. Po výběru této osoby se automaticky vyplní e-mail s oznámením o přihlášení a oznámení.  Pokud se předplatitel ve vaší organizaci nenajde, e-mail s oznámením se nevyplní automaticky, ale bude k dispozici pro ruční přidání jiné e-mailové adresy, na kterou se budou posílat e-maily související s předplatným.  Pokud vaše e-mailová služba blokuje příchozí e-maily na přihlašovací e-mailové adresy, je důležité zadat jinou e-mailovou adresu oznámení, aby předplatitelé a správci získali důležité e-maily týkající se předplatného Microsoftu.
   > [!div class="mx-imgBorder"]
   > ![Podrobnosti předplatitele](_img/assign-license-add/subscriber-details.png "Zadejte název předplatitele a další podrobnosti nebo si vyberte ze členů tenanta.")

    > [!NOTE]
    > Aby se členové klienta Azure Active Directory viděli při zadávání názvu předplatitele, musí být správce členem tenanta. 


    Pokud chcete, aby měl tento předplatitel přístup ke stažení softwaru, když se přihlásí na [portál předplatných sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), nezapomeňte v části **Nastavení stahování** ponechat přepínač stahování zapnuto. Pokud se rozhodnete zakázat stahování, uživatel nebude mít přístup ke stažení softwaru.  Přístup k klíčům Product Key bude taky zakázaný.  Předplatitel stále bude mít přístup ke všem dalším výhodám zahrnutým v předplatném.
   > [!div class="mx-imgBorder"]
   > ![Přístup k souborům ke stažení](media/access-to-downloads.png "Zvolením možnosti ' Allow ' poskytněte předplatiteli přístup ke stažení softwaru.")

    Pokud chcete do předplatného přidat vlastní referenční poznámky, můžete to udělat v části **Přidat odkaz** .
   > [!div class="mx-imgBorder"]
   > ![Přidání vlastních referenčních poznámek do každého předplatného](media/add-subscriber-reference-notes.png "V referenčním poli můžete zaznamenat libovolné poznámky k tomuto předplatnému.")

    Po výběru možností a zadání dat pro odběratele zvolte **Přidat** v dolní části **Přidat předplatitele** .
   > [!div class="mx-imgBorder"]
   > ![Klikněte na tlačítko Přidat.](media/add-button.png "Vyberte Přidat a uložte informace a přiřaďte předplatné k odběrateli.")

## <a name="why-use-a-different-notification-email-address"></a>Proč používat jinou e-mailovou adresu pro oznámení?
Některé organizace nastavily své e-mailové služby na blokování příchozích e-mailů z jiných domén.  Blokování příchozích e-mailů znamená, že předplatitelé a správci nebudou přijít o důležitou komunikaci:
- Předplatitelům se nezobrazí oznámení o tom, že k nim bylo přiřazeno předplatné.  Tím se jim taky zabrání v aktivaci některých výhod, které přináší.  
- Předplatitelé, kteří mají přiřazená předplatná sady Visual Studio s GitHubem Enterprise, neobdrží pozvánku k připojení k vaší organizaci GitHubu, což znamená, že pozvánku nepůjde přijmout. Aby mohli získat přístup k vaší organizaci GitHubu, musí přijmout e-mailem pozvánku. 
- Správci nebudou upozorňováni, když budou přidáni do smlouvy, obdrží měsíční příkazy správce nebo oznámení o změnách funkcí, které mají vliv na způsob správy předplatných.

Pomocí e-mailové adresy pro oznámení můžete svým předplatitelům dovolit získat důležitou komunikaci o jejich předplatných, aniž byste museli měnit funkčnost jejich e-mailových přihlašovacích adres.  

## <a name="resend-assignment-emails"></a>Znovu odeslat e-maily přiřazení
Po přidání odběratele se e-mail s přiřazením automaticky pošle novému předplatiteli s dalšími pokyny. E-mail s přiřazením můžete kdykoli odeslat, a to tak, že vyberete odběratele a potom v horní nabídce vyberete tlačítko pro **opětovné odeslání** .  Chcete-li znovu odeslat e-maily více uživatelům, podržte při výběru odběratelů klávesu **CTRL** .  Po výběru tlačítka **znovu odeslat** se zobrazí dialogové okno s výzvou, abyste potvrdili, že se těmto předplatitelům chcete znovu odeslat.  



## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Další kroky
- Máte spoustu uživatelů, které přidat?  Naučte se, jak přiřadit odběry [více odběratelům](assign-license-bulk.md).
- Potřebujete pomoc?  Obraťte [se na podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).