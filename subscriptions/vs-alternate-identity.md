---
title: Identit pro předplatitele sady Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Přidání alternativní identity pro vaše předplatné sady Visual Studio a pro Azure DevOps a Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 68ce5c2a19797b827f1ed6304107ac62ef82623f
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858149"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identit pro předplatitele sady Visual Studio

Při aktivaci předplatného sady Visual Studio, odkaz na identitu (nebo přihlášení), který jste použili při aktivaci s předplatným Visual Studia. Tímto způsobem můžete Uvědomujeme můžete na [portál pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)v Azure DevOps a v Azure.

V Azure DevOps jsme zkontrolujte stav předplatného sady Visual Studio pokaždé, když se přihlásíte a udělit funkce automaticky v rámci každé organizace, ve kterém jsou členy.
Vzhledem k tomu, že tyto funkce jsou zahrnuty jako výhodu předplatitele, je pro vás přidal jako člena v jakékoli organizaci Azure DevOps při použití identitu, která je propojena k vašemu předplatnému sady Visual Studio zdarma.

V Azure, můžeme zkontrolujte stav předplatného sady Visual Studio při aktivaci vaší [měsíční kredit Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) , který je výhodu předplatitele.

V rámci [portál pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), je možné přidat **alternativní identity** --kromě identity použité při aktivaci. Dnes jsme vám umožní přidat alternativní identity, pokud jste použili k aktivaci předplatného účtu Microsoft. Tento způsob, jak můžete také přidat pracovní nebo školní účet (který budete používat při přihlašování do sady Visual Studio, Office 365 nebo firemní nebo školní síti), umožňuje přístup k Azure DevOps s využitím svůj pracovní nebo školní účet i osobní účet.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Přidání alternativního účtu předplatného sady Visual Studio

Přidání alternativního účtu předplatného sady Visual Studio umožňuje přístup k výhodám předplatného, jako je Azure DevOps a Azure, s jinou identitou než ke které je přiřazeno předplatné. Tato funkce byla v minulosti k dispozici pouze v případě, že vaše předplatné Visual Studio (VS) byl přiřazen k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty v Azure Active Directory (Azure AD).

To neposkytuje kopii tohoto předplatného na jiný účet; pouze poskytuje možnost využít dvě výhody s alternativní účet.

Pro všechna předplatná můžete přidat "pracovní nebo školní účet", abyste mohli používat tento účet se výhody, které vyžadují přihlašovací údaje (VS IDE, Azure DevOps a Azure).


### <a name="add-the-alternate-account"></a>Přidání alternativního účtu


1. Přihlaste se k portálu pro předplatitele sady Visual Studio pomocí účtu Microsoft (https://my.visualstudio.com).

2. Přejděte na **předplatná**.

    > [!div class="mx-imgBorder"]
    > ![Přidání alternativního účtu – přejít na předplatná na portálu VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Zvolte **přidat alternativní účet**.
    > [!div class="mx-imgBorder"]
    > ![Zvolte možnost přidat alternativní účet ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Přidejte svůj pracovní nebo školní účet.
    > [!div class="mx-imgBorder"]
    > ![Přidat pracovní nebo školní účet](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Používáte pracovní nebo školní účet pro přihlášení k Azure DevOps (https://{youraccount}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Použít pracovní nebo školní účet](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Alternativní účet se přidá k předplatnému sady Visual Studio, umožní obou identit, které využívají výhod předplatného, které vyžadují, abyste se přihlaste pomocí alternativního účtu (integrované vývojové prostředí, Azure DevOps a Azure).

## <a name="faq"></a>Nejčastější dotazy

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Otázka: Proč Azure DevOps nerozpozná mi jako předplatitel sady Visual Studio?

Odpověď: azure DevOps by měl automaticky rozpoznat vaše předplatné při přihlášení pomocí primární nebo alternativní identity. Pokud ne, můžete vyzkoušet pár věcí:

* Zkontrolujte, že máte aktivní předplatné sady Visual Studio, který [zahrnuje Azure DevOps jako výhoda](vs-azure-devops.md).

* Potvrďte, že používáte přihlášení/identitou, která je buď primární nebo alternativní identity pro vaše předplatné sady Visual Studio.

* Přejděte [portál pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) alespoň jednou před přihlášení k Azure DevOps.

Pokud Azure DevOps ještě nerozpoznal vaše předplatné [obraťte se na podporu](https://visualstudio.microsoft.com/team-services/support/)
