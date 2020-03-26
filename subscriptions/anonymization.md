---
title: Anonymizace údajů o předplatitelích sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 02/20/2020
ms.topic: conceptual
description: Zjistěte, jak jsou data odběratelů anonymizována při ztrátě přístupu k předplatným.
ms.openlocfilehash: b65673d2fe61f62bf9e7731d20763bcd8c6f74bf
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232741"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymizace informací o předplatiteli sady Visual Studio
Pokud dojde k události, která blokuje použití předplatného účastníkem, například vypršení platnosti předplatného nebo odstranění přihlašovacího účtu odběratele, osobní údaje uživatele, jako je jméno a přihlašovací účet, jsou v podstatě kódované k vykreslení nepoužitelné.  To se provádí k ochraně osobních údajů účastníka.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kdy dochází k anonymizaci?
Události, které vykreslují odběr nepoužitelný pro odběratele spustí anonymizaci.  Jak rychle dojde k anonymizaci, závisí na typu předplatného a aktivační události. Další informace najdete v následující tabulce.

| Typ předplatného (Subscription Type)                                                                                                                       | Událost spouštějící anonymizaci                                                                                                     | Když dojde k anonymizaci |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Účastník se odhlásí z programu nebo nepřijme podmínky použití                                    | 30 dní               |
| Předplatná Visual Studia zakoupená v obchodě Microsoft Store (maloobchod)                                                                      | Platnost předplatného vyprší nebo není aktivována                                                                   | 360 dní                  |
| Předplatná sady Visual Studio získaná prostřednictvím hromadné licence, webu Visual Studio Marketplace (cloudová předplatná) nebo programů, jako je mpn | Platnost předplatného vyprší nebo není přiřazeno uživateli.                                                          | 180 dnů                  |
| Všechna předplatná                                                                                                                       | Účet Azure Active Directory nebo účet Microsoft (MSA) používaný k přihlášení k předplatnému se zavře. | Okamžitě               |
| Všechna předplatná                                                                                                                       | Odběratel je odebrán z tenanta, který je přidružený k účtu Azure Active Directory                                | Okamžitě               |

## <a name="faq"></a>Nejčastější dotazy
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Otázka: Způsobuje anonymizace osobních údajů účastníka ztrátu přístupu k předplatnému?
A: Ne.  Anonymizace je v reakci na událost, která způsobuje ztrátu přístupu k předplatnému, ale nezpůsobuje nedostatek přístupu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Otázka: Jsem správcem předplatných organizace.  Pokud je jedna z informací o odběrateli anonymizována, může být toto předplatné znovu přiřazeno jinému uživateli?
A: Ano – Dokud předplatné nevypršela, může být znovu přiřazeno jinému odběrateli.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Otázka: Jak lze zabránit anonymizaci způsobené odstraněním přihlašovací e-mailové adresy?
A: Existují dva způsoby, jak zabránit problému:
- Nasazení jednoho systému správy identit – buď MSA nebo AAD – ale ne obojí.  
- Přidružte identity AAD a MSA prostřednictvím klienta. 

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Naučte se, jak zabránit anonymizaci [asociací identit MSA a AAD](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).


