---
title: Anonymita dat předplatitele sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Přečtěte si, jak se data předplatitelů při ztrátě přístupu k předplatným nezdařila.
ms.openlocfilehash: d15fce8d5e1a64066a42cea69b770f55c9607f06
ms.sourcegitcommit: 02acadb912faced7eaffe27c2c19104bf0428bcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936917"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymita informací předplatitele sady Visual Studio
Když dojde k události, která blokuje použití předplatného předplatitele, jako je například vypršení platnosti předplatného nebo odstranění přihlašovacího účtu odběratele, osobní údaje uživatele, například jméno a přihlašovací účet, jsou v podstatě zakódované pro vykreslování. nepoužitelné.  Tento postup slouží k ochraně osobních údajů předplatitele.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Kdy dojde k anonymitě?
Události, které vygenerují předplatné nepoužité pro předplatitele, aktivují anonymitu.  Jak rychle probíhá, závisí na typu předplatného a události triggeru. Další informace najdete v následující tabulce.

| Typ předplatného                                                                                                                       | Událost aktivující anonymitu                                                                                                     | Když dojde k anonymitě |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Předplatitelský výslovný z programu nebo nepřijímá podmínky použití                                    | 30 dní               |
| Předplatná sady Visual Studio zakoupená prostřednictvím Microsoft Store (maloobchodní)                                                                      | Předplatné vyprší nebo není aktivované.                                                                   | 360 dní                  |
| Předplatná sady Visual Studio získaná prostřednictvím multilicenčního programu, Visual Studio Marketplace (odběry cloudu) nebo programy jako MPN | Předplatné vyprší nebo není přiřazeno uživateli.                                                          | 180 dní                  |
| Všechna předplatná                                                                                                                       | Zavře se účet Azure Active Directory nebo účet Microsoft (MSA), který se používá k přihlášení k předplatnému. | Hned               |
| Všechna předplatná                                                                                                                       | Předplatitel se odebere z klienta, který je přidružený k Azure Active Directorymu účtu.                                | Hned               |

## <a name="faq"></a>Nejčastější dotazy
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Č  Způsobuje anonymita osobních údajů předplatitele ztrátu přístupu k předplatnému?
O:  Ne.  Anonymita je v reakci na událost, která způsobuje ztrátu přístupu k předplatnému, ale nezpůsobí přístup k tomuto předplatnému.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Č  Jsem správcem předplatných mojí organizace.  Pokud je jedna z informací o mém předplatiteli anonymá, může se předplatné znovu přiřadit jinému uživateli?
O:  Ano – Pokud platnost předplatného nevypršela, je možné ji přiřadit jinému předplatiteli.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>Č Jak lze zabránit tomu, aby se odstranila e-mailová adresa pro přihlášení?
O:  Neexistují dva způsoby, jak zabránit problému:
- Nasaďte jeden systém pro správu identit – buď MSA, nebo AAD, ale ne obojí.  
- Přidružte identity AAD a MSA prostřednictvím tenanta. 

## <a name="next-steps"></a>Další kroky
Přečtěte si, jak se vyhnout anonymitě pomocí [přidružení identit MSA a AAD](/azure/active-directory/b2b/add-users-administrator).
