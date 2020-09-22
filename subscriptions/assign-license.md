---
title: Přiřazení licencí k předplatným sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Informace o tom, jak můžou správci přiřazovat licence předplatitelům
ms.openlocfilehash: f458e12cd27688f910917842de89e6377675fb69
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006199"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Přiřazení licencí na portálu pro správu předplatných sady Visual Studio
Jako správce předplatných sady Visual Studio můžete použít portál pro správu k přiřazení předplatných jednotlivým uživatelům a skupinám uživatelů.

Pro skupiny uživatelů máte možnosti, jak přiřadíte odběry.  
- Odběry můžete přiřadit v jednom okamžiku.
- Můžete také rychle a snadno odeslat seznamy předplatitelů a informace o jejich předplatném pomocí funkce [hromadného přidání](assign-license-bulk.md) .
- Pokud vaše organizace používá Microsoft Azure Active Directory (Azure AD), můžete k [přiřazení předplatných skupinám uživatelů použít skupiny Azure AD](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) .  


## <a name="add-a-single-subscriber"></a>Přidání jednoho předplatitele
Zde je postup přiřazení předplatného sady Visual Studio novému uživateli, aby mohli získat přístup k výhodám předplatného.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Přihlaste se k [portálu pro správu](https://manage.visualstudio.com).
2. Pokud chcete přiřadit licenci jednomu předplatiteli sady Visual Studio, vyberte v horní části tabulky možnost **Přidat**a pak zvolte **jednotlivé odběratele**.
   > [!div class="mx-imgBorder"]
   > ![Přidání jednoho předplatitele](_img/assign-license-add/add-subscriber-individual.png "Vyberte Přidat a pak zvolte jednotlivé odběratele k přiřazení jednoho předplatného.")
3. Zadejte informace do polí formuláře pro nového předplatitele. Pokud vaše organizace používá Azure Active Directory, pole **název** slouží jako vyhledávací funkce pro hledání osob v aktuálním adresáři, abyste mohli vybrat správného uživatele z výsledků hledání. Po výběru této osoby se automaticky vyplní e-mail s oznámením o přihlášení a oznámení.
   > [!div class="mx-imgBorder"]
   > ![Podrobnosti předplatitele](_img/assign-license-add/subscriber-details.png "Zadejte název předplatitele a další podrobnosti nebo si vyberte ze členů tenanta.")

    > [!NOTE]
    > Aby se členové klienta Azure Active Directory viděli při zadávání názvu předplatitele, musí být správce členem tenanta. 


    Pokud chcete, aby měl tento předplatitel přístup ke stažení softwaru, když se přihlásí na [portál předplatných sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), nezapomeňte v části **Nastavení stahování** ponechat přepínač stahování zapnuto. Pokud se rozhodnete zakázat stahování, uživatel nebude mít přístup ke stažení softwaru.  Přístup k klíčům Product Key bude taky zakázaný.  Předplatitel stále bude mít přístup ke všem dalším výhodám zahrnutým v předplatném.
   > [!div class="mx-imgBorder"]
   > ! [Přístup k souborům ke stažení] (Pokud chcete poskytnout předplatiteli přístup ke stažení softwaru, klikněte na tlačítko ' Media/access-to-downloads.png '.

    Pokud chcete do předplatného přidat vlastní referenční poznámky, můžete to udělat v části **Přidat odkaz** .
   > [!div class="mx-imgBorder"]
   > ![Přidání vlastních referenčních poznámek do každého předplatného](media/add-subscriber-reference-notes.png "V referenčním poli můžete zaznamenat libovolné poznámky k tomuto předplatnému.")

    Po výběru možností a zadání dat pro odběratele zvolte **Přidat** v dolní části **Přidat předplatitele** .
   > [!div class="mx-imgBorder"]
   > ![Klikněte na tlačítko Přidat.](media/add-button.png "Vyberte Přidat a uložte informace a přiřaďte předplatné k odběrateli.")

## <a name="resend-assignment-emails"></a>Znovu odeslat e-maily přiřazení
Po přidání odběratele se e-mail s přiřazením automaticky pošle novému předplatiteli s dalšími pokyny. E-mail s přiřazením můžete kdykoli odeslat, a to tak, že vyberete odběratele a potom v horní nabídce vyberete tlačítko pro **opětovné odeslání** .  Chcete-li znovu odeslat e-maily více uživatelům, podržte při výběru odběratelů klávesu **CTRL** .  Po výběru tlačítka **znovu odeslat** se zobrazí dialogové okno s výzvou, abyste potvrdili, že se těmto předplatitelům chcete znovu odeslat.  

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Další kroky
- Máte spoustu uživatelů, které přidat?  Naučte se, jak přiřadit odběry [více odběratelům](assign-license-bulk.md).
- Potřebujete pomoc?  Obraťte [se na podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).