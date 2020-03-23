---
title: Jak používat připojený účet Microsoft a identity Služby Azure Active Directory | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Přečtěte si, jak pracovat s připojenými účty Microsoft a identitami Azure Active Directory
ms.openlocfilehash: 3dcb41a26f27e5135962edf7ff933de40ccefe5e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508976"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Použití připojených identit v předplatných Sady Visual Studio
Pokud obdržíte předplatné Visual Studia prostřednictvím práce nebo školy a pomocí svého účtu Microsoft (MSA) se přihlásíte, správce předplatných může připojit vaši MSA k vaší identitě ve službě Azure Active Directory (Azure AD) vaší organizace.  Tím se změní způsob přístupu k některým výhodám zahrnutým v předplatném. 

## <a name="overview-of-connected-ids"></a>Přehled připojených ID
Organizace se stále více přesouvají k identitám založeným na Azure AD, aby poskytovaly lepší zabezpečení a podporu pro automatizovanou správu předplatných.  Pokud vaše předplatné používá MSA, jako je například @outlook.com nebo jiné osobní e-mailovou adresu, správce může změnit přihlašovací e-mail na identitu Azure AD.  To změní způsob přihlášení k portálu https://my.visualstudio.com odběratelů na adrese, ale nemusí změnit způsob, jakým máte přístup ke všem vašim výhodám.  

Pokud správce propojí vaše identity MSA a Azure AD, obdržíte e-mail s upozorněním, že můžete začít přistupovat k předplatnému Visual Studia s vaší identitou Azure AD namísto msa. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Jak získat přístup k výhodám pomocí identit Azure AD
Poté, co váš správce propojí msa k vaší identitě Azure AD, https://my.visualstudio.com budete se muset přihlásit k portálu předplatitelů pomocí identity Azure AD, abyste získali přístup k výhodám, které jsou závislé na Azure AD.  Mezi ně patří:
- Visual Studio – sada IDE
- Azure DevOps
- Individuální kredit v Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Jak získat přístup k výhodám pomocí msa
Pro mnoho výhod nabízených v předplatných Sady Visual Studio, jako je Pluralsight, LinkedIn, CloudPilot a další, ve skutečnosti vytváříte uživatelské účty na webových stránkách partnerů.  U těchto účtů byste měli nadále používat identitu, kterou jste použili při vytváření účtu.  Pokud jste například aktivovali výhodu Pluralsight pomocí msa, měli byste pokračovat v používání msa při přijímání školení Pluralsight, bez ohledu na identitu, kterou používáte k přihlášení do portálu odběratelů.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Přístup k předplatnému pomocí alternativní identity
Přidání alternativního účtu do předplatného sady Visual Studio umožňuje přístup k výhodám předplatného, jako je Azure DevOps a Azure, s jinou identitou, než ke které je předplatné přiřazeno. V minulosti byla tato funkce dostupná pouze v případě, že vaše předplatné sady Visual Studio (VS) bylo přiřazeno k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty ve službě Azure Active Directory (Azure AD).  Další informace o používání alternativních účtů najdete v článku [Alternativní identity.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Otázka: Jak se mohu obrátit na svého správce o tom?
A: Přečtěte si prosím náš článek [Kontaktujte správce předplatných,](contact-my-admin.md) kde najdete informace o kontaktování správce.  

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Po připojení vašeho účtu Azure AD a MSA doporučujeme ověřit, že se můžete úspěšně přihlásit k [portálu předplatného](https://my.visualstudio.com?wt.mc_id=o~msft~docs) a získat přístup k výhodám, jako je Azure DevOps, Visual Studio a váš individuální kredit Azure DevTest. 