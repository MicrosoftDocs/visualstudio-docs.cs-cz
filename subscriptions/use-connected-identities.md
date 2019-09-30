---
title: Jak používat připojené účet Microsoft a Azure Active Directory identity | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: Naučte se pracovat s připojenými účty Microsoft a Azure Active Directorymi identitami.
ms.openlocfilehash: d0d30092f34a3cb17b41455612cd336af3e58d30
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682156"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Jak používat připojené identity v předplatných sady Visual Studio
Pokud obdržíte předplatné sady Visual Studio prostřednictvím svého pracovního nebo školního účtu a k přihlášení použijete účet Microsoft (MSA), může správce předplatných vaši MSA připojit k vaší identitě v Azure Active Directory (Azure AD) vaší organizace.  Tím se změní způsob přístupu k některým výhodám, které jsou součástí vašeho předplatného. 

## <a name="overview-of-connected-ids"></a>Přehled připojených identifikátorů
Organizace se stále častěji pohybují na identity založené na službě Azure AD a poskytují lepší zabezpečení a podporu automatizované správy předplatných.  Pokud vaše předplatné používá MSA, například @outlook.com nebo jinou osobní e-mailovou adresu, může správce změnit přihlašovací e-mail na vaši identitu Azure AD.  Tím se změní způsob přihlašování k portálu předplatitele na @no__t – 0, ale nemusí se měnit způsob přístupu ke všem výhodám.  

Pokud váš správce připojí vaše identity MSA a Azure AD, obdržíte e-mail s informací, jak začít přistupovat k předplatnému sady Visual Studio s vaší identitou Azure AD, a ne vaším MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Jak získat přístup k výhodám pomocí identit Azure AD
Až správce připojí vaše MSA k vaší identitě Azure AD, budete se muset přihlásit k portálu předplatitele na adrese @no__t 0 s vaší identitou Azure AD pro přístup k výhodám, které spoléhají na Azure AD.  Mezi ně patří:
- Visual Studio – sada IDE
- Azure DevOps
- Kredity Azure

## <a name="how-to-access-benefits-using-your-msa"></a>Jak získat přístup k výhodám pomocí MSA
Pro mnohé z výhod nabízených v předplatných sady Visual Studio, jako jsou Pluralsight, LinkedIn, CloudPilot a další, můžete ve skutečnosti vytvářet uživatelské účty na webech partnerů.  Pro tyto účty byste měli dál používat identitu, kterou jste použili při vytváření účtu.  Pokud jste třeba aktivovali Pluralsight výhodu pomocí svého MSAu, měli byste při provádění školení Pluralsight dál používat MSA, a to bez ohledu na identitu, kterou používáte pro přihlášení na portál pro předplatitele.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Použití alternativní identity pro přístup k vašemu předplatnému
Přidání alternativního účtu do předplatného sady Visual Studio vám umožní získat přístup k výhodám předplatného, jako je Azure DevOps a Azure, s jinou identitou, než ke které je předplatné přiřazeno. Tato funkce byla v minulosti k dispozici pouze v případě, že vaše předplatné sady Visual Studio (VS) bylo přiřazeno k účtu Microsoft (MSA). Rozšířili jsme tuto funkci pro pracovní nebo školní účty v Azure Active Directory (Azure AD).  Další informace o používání alternativních účtů najdete v článku o [alternativních identitách](vs-alternate-identity.md) . 

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Č Jak se můžu obrátit na správce?
O:  Informace o tom, jak kontaktovat správce, najdete v článku [kontaktujte správce předplatných](contact-my-admin.md) .  

## <a name="next-steps"></a>Další kroky
Po připojení vašeho správce k účtům Azure AD a MSA doporučujeme ověřit, že se můžete úspěšně přihlásit k [portálu předplatného](https://my.visualstudio.com?wt.mc_id=o~msft~docs) a získat přístup k výhodám, jako je Azure DevOps, Visual Studio a kredity Azure. 