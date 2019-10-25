---
title: Identity pro předplatitele sady Visual Studio
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Jak přidat alternativní identitu pro předplatné sady Visual Studio, která se má použít pro Azure DevOps a Azure
ms.openlocfilehash: e19774f2314280b2e5a995a7d83336f1403682a4
ms.sourcegitcommit: bcdab788085bd9931d73883fe70cd5831317dca2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72816556"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identity pro předplatitele sady Visual Studio
Při aktivaci předplatného sady Visual Studio propojíme identitu (nebo přihlášení), kterou jste použili během aktivace v rámci předplatného sady Visual Studio. Tímto způsobem můžeme na [portálu pro předplatitele Visual studia](https://my.visualstudio.com?wt.mc_id=o~msft~docs), v Azure DevOps a v Azure.

V Azure DevOps zkontrolujeme stav předplatného sady Visual Studio pokaždé, když se přihlásíte, a automaticky vám poskytnete funkce v rámci každé organizace, které jste členem.
Vzhledem k tomu, že tyto funkce jsou zahrnuté jako zvýhodnění pro předplatitele, je při použití identity, která je propojená s vaším předplatným sady Visual Studio, nemůžete ji přidat jako člena v jakékoli organizaci Azure DevOps.

V Azure zkontrolujeme stav předplatného sady Visual Studio, když aktivujete svůj [měsíční kredit Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) , který je výhodou pro předplatitele.

V rámci [portálu pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)můžete přidat **alternativní identitu** – kromě identity, kterou jste použili během aktivace. Umožňuje přidat alternativní identitu, pokud jste použili účet Microsoft k aktivaci svého předplatného. Tímto způsobem můžete také přidat pracovní nebo školní účet (který použijete při přihlašování do sady Visual Studio, Office 365 nebo firemní nebo školní síť), což vám umožní přístup k Azure DevOps pomocí vašeho osobního účtu i vašeho pracovního nebo školního účtu.

## <a name="add-an-alternate-account-to-your-subscription"></a>Přidání alternativního účtu do předplatného
Přidání alternativního účtu do předplatného sady Visual Studio vám umožní získat přístup k výhodám předplatného, jako je Azure DevOps a Azure, s jinou identitou, než ke které je předplatné přiřazeno. Tato funkce byla v minulosti k dispozici pouze v případě, že vaše předplatné sady Visual Studio (VS) bylo přiřazeno k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty v Azure Active Directory (Azure AD).

To neposkytuje kopii předplatného pro druhý účet; poskytuje jenom možnost přístupu ke dvěma výhodám pomocí alternativního účtu.

U všech předplatných můžete přidat pracovní nebo školní účet, abyste mohli použít tento účet s výhodami, které vyžadují přihlášení (IDE, Azure DevOps a Azure).

### <a name="add-the-alternate-account"></a>Přidání alternativního účtu
1. Přihlaste se k portálu předplatitele sady Visual Studio pomocí účet Microsoft (https://my.visualstudio.com).
2. Klikněte na kartu **předplatná** .
3. Vyberte **Přidat alternativní účet**.
4. Přidejte svůj pracovní nebo školní účet.
    > [!div class="mx-imgBorder"]
    > ![přidat pracovní nebo školní účet](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Použijte svůj pracovní nebo školní účet pro přihlášení k Azure DevOps (https://{youraccount}. VisualStudio. com).
    > [!div class="mx-imgBorder"]
    > ![použít svůj pracovní nebo školní účet](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Váš alternativní účet se přidá do předplatného sady Visual Studio, což umožňuje, aby obě identity využily výhod předplatného, které vyžaduje, abyste se přihlásili pomocí alternativního účtu (IDE, Azure DevOps a Azure).

## <a name="faq"></a>Nejčastější dotazy

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>Otázka: Proč Azure DevOps nerozpozná mě jako předplatitel sady Visual Studio?

Odpověď: Azure DevOps by měl automaticky rozpoznat vaše předplatné, když se přihlásíte pomocí primární nebo alternativní identity. Pokud ne, můžete zkusit pár věcí:

* Ověřte, že máte aktivní předplatné sady Visual Studio, které zahrnuje [Azure DevOps](vs-azure-devops.md#eligibility) jako výhodu.

* Ověřte, že používáte přihlašovací údaje nebo identitu, které jsou buď primární, nebo jinou identitou pro vaše předplatné sady Visual Studio.

* Než se přihlásíte ke službě Azure DevOps, navštivte [portál pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) aspoň jednou.

Pokud Azure DevOps ještě nerozpozná vaše předplatné, obraťte se na [podporu Azure DevOps](https://azure.microsoft.com/support/devops/).
