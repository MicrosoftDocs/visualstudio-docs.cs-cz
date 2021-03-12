---
title: Anonymita dat předplatitele sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Přečtěte si, jak se data předplatitelů při ztrátě přístupu k předplatným nezdařila.
ms.openlocfilehash: 69f41232a678a857908b30d63df2ae7f72b79904
ms.sourcegitcommit: 9da787bf5b4281f933dc22083dc0bdeae3bc9461
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2021
ms.locfileid: "103225960"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymita informací předplatitele sady Visual Studio
Když dojde k události, která blokuje použití předplatného předplatitele, jako je například vypršení platnosti předplatného nebo odstranění přihlašovacího účtu odběratele, osobní údaje uživatele, například jméno a přihlašovací účet, jsou v podstatě zakódované, aby je bylo možné vykreslovat.  Tento postup slouží k ochraně osobních údajů předplatitele.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kdy dojde k anonymitě?
Události, které vygenerují předplatné nepoužité pro předplatitele, aktivují anonymitu.  Jak rychle probíhá, závisí na typu předplatného a události triggeru. Další informace najdete v následující tabulce.

| Typ předplatného (Subscription Type)                                                                                                                       | Událost aktivující anonymitu                                                                                                     | Když dojde k anonymitě |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Předplatitelský výslovný z programu nebo nepřijímá podmínky použití                                    | 30 dní               |
| Předplatná sady Visual Studio zakoupená prostřednictvím Microsoft Store (maloobchodní)                                                                      | Předplatné vyprší nebo není aktivované.                                                                   | 360 dní                  |
| Předplatná sady Visual Studio získaná prostřednictvím multilicenčního programu, Visual Studio Marketplace (odběry cloudu) nebo programy jako MPN | Předplatné vyprší nebo není přiřazeno uživateli.                                                          | 180 dnů                  |
| Všechna předplatná                                                                                                                       | Zavře se účet Azure Active Directory nebo účet Microsoft (MSA), který se používá k přihlášení k předplatnému. | Okamžitě               |
| Všechna předplatná                                                                                                                       | Předplatitel se odebere z klienta, který je přidružený k Azure Active Directorymu účtu.                                | Okamžitě               |

## <a name="faq"></a>Časté otázky
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Otázka: při anonymitě osobních údajů předplatitele dojde ke ztrátě přístupu k předplatnému?
Odpověď: ne.  Anonymita je v reakci na událost, která způsobuje ztrátu přístupu k předplatnému, ale nezpůsobí přístup k tomuto předplatnému.

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Otázka: jsem správcem předplatných mojí organizace.  Pokud je jedna z informací o mém předplatiteli anonymá, může se předplatné znovu přiřadit jinému uživateli?
Odpověď: Ano.  Odběry lze znovu přiřadit, pokud jsou splněna tato kritéria:
- Platnost předplatného vypršela.
- Od posledního přiřazení předplatného k odběrateli uplynulo minimálně 90 dní.  Například pokud bylo předplatné přiřazeno k předplatiteli 1. června, nelze ho znovu přiřadit do 30. srpna.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Otázka: Jak mohu zabránit v důsledku odstranění e-mailové adresy pro přihlášení?
Odpověď: Existují dva způsoby, jak zabránit problému:
- Nasaďte jeden systém pro správu identit – buď MSA, nebo AAD, ale ne obojí.  
- Přidružte identity AAD a MSA prostřednictvím tenanta. 

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si, jak se vyhnout anonymitě pomocí [přidružení identit MSA a AAD](/azure/active-directory/b2b/add-users-administrator).