---
title: Přiřazení licencí k předplatným sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Informace o tom, jak můžou správci přiřazovat licence předplatitelům
ms.openlocfilehash: 8785d4d4253fa3217341c8200a94dab923ae4a5f
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797367"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Přiřazení licencí na portálu pro správu předplatných sady Visual Studio
Jako správce předplatných sady Visual Studio můžete použít portál pro správu k přiřazení předplatných jednotlivým uživatelům a skupinám uživatelů.

Pro skupiny uživatelů můžete k nim přiřadit odběry po jednom, nebo můžete použít funkci [hromadného přidání](assign-license-bulk.md) k rychlému a snadnému nahrávání seznamů předplatitelů a informací o jejich předplatném.

## <a name="add-a-single-subscriber"></a>Přidání jednoho předplatitele
Zde je postup přiřazení předplatného sady Visual Studio novému uživateli, aby mohli získat přístup k výhodám předplatného.

1. Přihlaste se k [portálu pro správu](https://manage.visualstudio.com).
2. Pokud chcete přiřadit licenci jednomu předplatiteli sady Visual Studio, vyberte v horní části tabulky možnost **Přidat**.
   > [!div class="mx-imgBorder"]
   > ![přidání jednoho předplatitele](media/add-single-subscriber.png)
3. Zadejte informace do polí formuláře pro nového předplatitele. Pokud vaše organizace používá Azure Active Directory, pole **název** slouží jako vyhledávací funkce pro hledání osob v aktuálním adresáři, abyste mohli vybrat správného uživatele z výsledků hledání. Po výběru této osoby se automaticky vyplní e-mail s oznámením o přihlášení a oznámení.
   > [!div class="mx-imgBorder"]
   > Podrobnosti o předplatiteli ![](_img/assign-license-add/subscriber-details.png)

    Pokud chcete, aby měl tento předplatitel přístup ke stažení softwaru, když se přihlásí na [portál předplatných sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), nezapomeňte v části **Nastavení stahování** ponechat přepínač stahování zapnuto. Pokud se rozhodnete zakázat stahování, uživatel nebude mít přístup ke stažení softwaru, ale stále bude mít přístup ke všem dalším výhodám zahrnutým v předplatném.
   > [!div class="mx-imgBorder"]
   > ![přístup k souborům ke stažení](media/access-to-downloads.png)

       If you'd like to add your own reference notes to the subscription, you can do so in the **Add reference** section.
   > [!div class="mx-imgBorder"]
   > ![do každého předplatného přidat svoje vlastní referenční poznámky](media/add-subscriber-reference-notes.png)

    Po výběru možností a zadání dat pro odběratele zvolte **Přidat** v dolní části **Přidat předplatitele** .
   > [!div class="mx-imgBorder"]
   > ![klikněte na tlačítko Přidat](media/add-button.png)

## <a name="resend-assignment-emails"></a>Znovu odeslat e-maily přiřazení
Po přidání odběratele se e-mail s přiřazením automaticky pošle novému předplatiteli s dalšími pokyny. E-mail s přiřazením můžete kdykoli odeslat, a to tak, že vyberete odběratele a kliknete na tlačítko **znovu odeslat** v horní nabídce.  Chcete-li znovu odeslat e-maily více uživatelům, podržte při výběru odběratelů klávesu **CTRL** .  Po kliknutí na tlačítko **znovu odeslat** se zobrazí dialogové okno s výzvou, abyste potvrdili, že chcete tomuto předplatiteli znovu odeslat.  

## <a name="next-steps"></a>Další kroky
- Máte spoustu uživatelů, které přidat?  Naučte se, jak přiřadit odběry [více odběratelům](assign-license-bulk.md).
- Potřebujete pomoc?  Obraťte [se na podporu správy a předplatných sady Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

