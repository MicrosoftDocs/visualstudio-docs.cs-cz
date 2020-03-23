---
title: Anonymizace údajů o předplatitelích sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Zjistěte, jak jsou data odběratelů anonymizována při ztrátě přístupu k předplatným.
ms.openlocfilehash: 439e53b1c67fde0fbda0666652e29bf396abfee2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "78894408"
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


