---
title: Identity pro předplatitele sady Visual Studio
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Jak přidat alternativní identitu pro vaše předplatné Visual Studia, které se používá pro Azure DevOps a Azure
ms.openlocfilehash: e19774f2314280b2e5a995a7d83336f1403682a4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "72816556"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identity pro předplatitele sady Visual Studio
Když aktivujete předplatné sady Visual Studio, propojíme identitu (nebo přihlášení), kterou jste použili při aktivaci s předplatným Sady Visual Studio. Tímto způsobem vás poznáme na [portálu předplatitelů Visual Studia](https://my.visualstudio.com?wt.mc_id=o~msft~docs), v Azure DevOps a v Azure.

V Azure DevOps kontrolujeme stav předplatného sady Visual Studio při každém přihlášení a automaticky udělujeme funkce v rámci každé organizace, ve které jste členem.
Vzhledem k tomu, že tyto funkce jsou zahrnuty jako předplatitele výhody, je zdarma přidat jako člen v libovolné organizaci Azure DevOps při použití identity, která je propojená s předplatným Sady Visual Studio.

V Azure kontrolujeme stav předplatného Visual Studia při aktivaci [měsíčního kreditu Azure DevTest,](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) který je výhodou odběratele.

V rámci [portálu předplatitelů sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)můžete kromě **identity,** kterou jste použili při aktivaci, přidat alternativní identitu. Pokud jste k aktivaci předplatného použili účet Microsoft, umožníme vám přidat alternativní identitu. Tímto způsobem můžete také přidat pracovní nebo školní účet (který používáte při přihlášení do Sady Visual Studio, Office 365 nebo podnikové nebo školní sítě), což vám umožní přístup k Azure DevOps pomocí vašeho osobního účtu i pracovního nebo školního účtu.

## <a name="add-an-alternate-account-to-your-subscription"></a>Přidání alternativního účtu k předplatnému
Přidání alternativního účtu do předplatného sady Visual Studio umožňuje přístup k výhodám předplatného, jako je Azure DevOps a Azure, s jinou identitou, než ke které je předplatné přiřazeno. V minulosti byla tato funkce dostupná pouze v případě, že vaše předplatné sady Visual Studio (VS) bylo přiřazeno k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty ve službě Azure Active Directory (Azure AD).

To neposkytuje kopii předplatného na jiný účet; poskytuje pouze možnost přístupu ke dvěma výhodám s alternativním účtem.

Pro všechna předplatná můžete přidat "pracovní nebo školní účet", abyste mohli tento účet používat s výhodami, které vyžadují přihlášení (VS IDE, Azure DevOps a Azure).

### <a name="add-the-alternate-account"></a>Přidání alternativního účtu
1. Přihlaste se k portálu předplatitelůhttps://my.visualstudio.com)Sady Visual Studio pomocí svého účtu Microsoft ( .
2. Klikněte na kartu **Odběry.**
3. Zvolte **Přidat alternativní účet**.
4. Přidejte svůj pracovní nebo školní účet.
    > [!div class="mx-imgBorder"]
    > ![Přidání pracovního nebo školního účtu](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. K přihlášení k Azure DevOps (https://{youraccount}.visualstudio.com) se můžete přihlásit pomocí pracovního nebo školního účtu.
    > [!div class="mx-imgBorder"]
    > ![Použití pracovního nebo školního účtu](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Váš alternativní účet se přidá do předplatného Sady Visual Studio, což umožňuje oběma identitám využívat výhody předplatného, které vyžadují přihlášení pomocí alternativního účtu (IDE, Azure DevOps a Azure).

## <a name="faq"></a>Nejčastější dotazy

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Otázka: Proč mě Azure DevOps nerozpozná jako odběratele Visual Studia?

A: Azure DevOps by měl automaticky rozpoznat vaše předplatné při přihlášení pomocí primární nebo alternativní identity. Pokud ne, můžete zkusit několik věcí:

* Zkontrolujte, zda máte aktivní předplatné Visual Studia, které zahrnuje [Azure DevOps](vs-azure-devops.md#eligibility) jako výhodu.

* Zkontrolujte, zda používáte přihlašovací/identitu, která je primární nebo alternativní identitou pro vaše předplatné sady Visual Studio.

* Než se přihlásíte k Azure DevOps, navštivte [portál předplatitelů Visual Studia](https://my.visualstudio.com?wt.mc_id=o~msft~docs) alespoň jednou.

Pokud Azure DevOps stále nerozpozná vaše předplatné, obraťte se na [podporu Azure DevOps](https://azure.microsoft.com/support/devops/).
