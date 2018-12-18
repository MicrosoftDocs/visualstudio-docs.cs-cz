---
title: Anonymizace dat předplatitele sady Visual Studio | Dokumentace Microsoftu
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: Zjistěte, jak předplatitelská data jsou anonymní, když se ztratí přístup k předplatným.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4570ff43f946c25c50d298e22de3b0c8a261f870
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810588"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Anonymizace informace předplatitele sady Visual Studio

Při výskytu události, které blokuje předplatitele pomocí předplatného, jako je například vypršení platnosti předplatného nebo odstranění odběratele přihlašovací účet, osobní údaje uživatele, jako je název a přihlašovací účet jsou v podstatě zamíchal k vykreslení je nepoužitelné.  To se provádí na trhu při ochraně osobních údajů předplatitele.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Když dojde k anonymizaci?

Anonymizace se aktivuje události, které nepoužitelná odběr pro odběratele.  Nastane, jak rychle anonymizace závisí na typu předplatného a aktivační událost. Najdete v následující tabulce pro další informace.

| Typ odběru                                                                                                                       | Událost aktivuje anonymizace                                                                                                     | Pokud dojde k anonymizaci |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Předplatitel požádá o mimo program nebo nepřijímá žádné podmínky použití                                    | 30 dní               |
| Předplatná sady Visual Studio koupili prostřednictvím Microsoft Store (prodejní verze)                                                                      | Předplatné vyprší platnost nebo není aktivováno                                                                   | 360 dní                  |
| Předplatná sady Visual Studio získali prostřednictvím multilicence, Visual Studio Marketplace (Cloudová předplatná) nebo programy, jako je MPN | Předplatné vyprší platnost nebo není přiřazená uživateli                                                          | 180 dnů                  |
| Všechna předplatná                                                                                                                       | Zavření účtu služby Azure Active Directory nebo účet Microsoft (MSA) používaná pro přihlášení odběru | Okamžitě               |
| Všechna předplatná                                                                                                                       | Předplatitel se odebere z klienta, která je přidružená k účtu Azure Active Directory                                | Okamžitě               |

## <a name="faq"></a>Nejčastější dotazy

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>Otázka: anonymizace účastníka osobních údajů způsobí, že je přijít o přístup k předplatnému?
Odpověď: Ne.  Je anonymizace v reakci na událost, která způsobí, že dojde ke ztrátě přístupu k předplatnému, ale nezpůsobí zamezení přístupu.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>Otázka: jsem správce předplatného mojí organizace.  Pokud jeden z Moje předplatitele informace jsou anonymní, můžete toto předplatné přiřadit jiný uživatel?
Odpověď: Ano – za předpokladu, nevypršela platnost předplatného, ji můžete přiřadit na jiného předplatitele.

## <a name="next-steps"></a>Další kroky

Naučte se, aby se zabránilo anonymizace podle [propojení identity MSA a AAD](/azure/active-directory/b2b/add-users-administrator).
