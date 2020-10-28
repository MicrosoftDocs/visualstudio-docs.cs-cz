---
title: Jak používat připojené identity v předplatných sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 10/28/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Naučte se pracovat s připojenými účty Microsoft a Azure Active Directorymi identitami.
ms.openlocfilehash: a4c7b72c91c4c1180a5fd888e3afd0a33fa2d81b
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904029"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Jak používat připojené identity v předplatných sady Visual Studio
Pokud obdržíte předplatné sady Visual Studio prostřednictvím svého pracovního nebo školního účtu a k přihlášení použijete účet Microsoft (MSA), může správce předplatných vaši MSA připojit k vaší identitě v Azure Active Directory (Azure AD) vaší organizace.  Tím se změní způsob přístupu k některým výhodám, které jsou součástí vašeho předplatného. 

## <a name="overview-of-connected-ids"></a>Přehled připojených identifikátorů
Organizace se stále častěji pohybují na identity založené na službě Azure AD a poskytují lepší zabezpečení a podporu automatizované správy předplatných.  Pokud vaše předplatné používá MSA jako @outlook.com nebo jinou osobní e-mailovou adresu, může správce změnit přihlašovací e-mail na vaši identitu Azure AD.  Tím se změní způsob přihlašování k portálu pro předplatitele, https://my.visualstudio.com ale nemusí se měnit způsob přístupu ke všem výhodám.  

Pokud váš správce připojí vaše identity MSA a Azure AD, obdržíte e-mail s informací, jak začít přistupovat k předplatnému sady Visual Studio s vaší identitou Azure AD, a ne vaším MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Jak získat přístup k výhodám pomocí identit Azure AD
Až správce připojí vaše MSA k vaší identitě Azure AD, budete se muset přihlásit k portálu předplatitele na https://my.visualstudio.com základě identity Azure AD, abyste měli přístup k výhodám, které spoléhají na Azure AD.  Mezi ně patří:
- Visual Studio – sada IDE
- Azure DevOps
- Individuální kredit v Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Jak získat přístup k výhodám pomocí MSA
Pro mnohé z výhod nabízených v předplatných sady Visual Studio, jako jsou Pluralsight, LinkedIn, CloudPilot a další, můžete ve skutečnosti vytvářet uživatelské účty na webech partnerů.  Pro tyto účty byste měli dál používat identitu, kterou jste použili při vytváření účtu.  Pokud jste třeba aktivovali Pluralsight výhodu pomocí svého MSAu, měli byste při provádění školení Pluralsight dál používat MSA, a to bez ohledu na identitu, kterou používáte pro přihlášení na portál pro předplatitele.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Použití alternativní identity pro přístup k vašemu předplatnému
Přidáním alternativního účtu k předplatnému sady Visual Studio získáte přístup k výhodám předplatného, jako jsou Azure DevOps a Azure, pomocí jiné identity, než ke které je předplatné přiřazené. Tato funkce byla v minulosti k dispozici pouze v případě, že vaše předplatné sady Visual Studio (VS) bylo přiřazeno k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty v Azure Active Directory (Azure AD).  Další informace o používání alternativních účtů najdete v článku o [alternativních identitách](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Otázka: Jak můžu kontaktovat správce?
Odpověď: Další informace o tom, jak kontaktovat správce, najdete v článku [kontaktujte správce předplatných](contact-my-admin.md) .  

### <a name="q-im-an-admin--how-do-i-use-this"></a>Otázka: jsem správce.  Návody použít?
Odpověď: implementace připojených identit je jednoduchá.  Další informace najdete v [tomto článku](personal-email-sign-ins.md) . 

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Po připojení vašeho správce k účtům Azure AD a MSA doporučujeme ověřit, že se můžete úspěšně přihlásit k [portálu předplatného](https://my.visualstudio.com?wt.mc_id=o~msft~docs) a získat přístup k výhodám, jako je Azure DevOps, Visual Studio a váš jednotlivý kredit Azure DevTest.