---
title: Obsluha nadlimitních licencí v předplatných sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 05/18/2021
ms.topic: conceptual
description: Informace o tom, jak můžou správci vyřešit přetížená předplatná
ms.openlocfilehash: 533ce71e8795e89bcb21fd437da6bea91db291f4
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973392"
---
# <a name="over-allocated-subscriptions"></a>Přetížená předplatná
V některých případech se po přidání předplatitelů mění objednávky, což může vést k většímu počtu přiřazených předplatných než k licencím vlastněných vaší společností. Tato možnost se nazývá "přepřidělování".  

Chcete-li zobrazit přidělení předplatného, klikněte na ikonu nahoře vlevo a otevřete podokno přidělení.  

> [!NOTE]
> Převzetí služeb při selhání není v programech Open License povolené.  Další programy můžou tyto informace na portálu zobrazit jinak.
>
> [!div class="mx-imgBorder"]
> ![Oznámení o vyhodnocených předplatných](_img/over-claimed/over-claimed-alert.png "Počet předělků je uvedený v přehledu a reprezentuje ho pruh hash v grafu pro každý typ předplatného.")

Všimněte si, že zobrazení používá hashový pruh k označení přetížených předplatných.  Počet nadlimitních přidělení napříč všemi typy předplatného je zahrnutý v části Přehled v horní části a každá úroveň předplatného zobrazuje taky svůj vlastní stav přidělení.  

## <a name="receive-notifications-when-over-allocations-occur"></a>Dostávat oznámení, když dojde k převzetí služeb při selhání
Můžete určit e-mailovou adresu pro příjem oznámení v případě, že dojde k přetížení, a nastavit prahovou hodnotu, která musí být překročena před odesláním oznámení.  Přečtěte si další informace o [Nastavení předvoleb pro vaše smlouvy](admin-preferences.md) na portálu pro správu.

## <a name="resolve-over-allocated-subscriptions"></a>Řešení přetížených předplatných
Existuje několik způsobů, jak převádět více prostředků:
- Pokud si chcete koupit další odběry, obraťte se na svého prodejce.
- Počkejte prosím, než se dokončí vaše roční období, a platíte za předem přidělené předplatné v daném okamžiku. 
- Odstraňte některá přiřazení předplatného.  (To nebrání tomu, aby platba při ročním pravdivosti, která je pravdivá, jako pravdivá, byla založená na maximálním počtu přidaných předplatných v průběhu roku.)

## <a name="billing-and-true-up"></a>Fakturace a true-up
Pokud má vaše organizace předplatné smlouva Enterprise (EA), mohou správci přiřazovat předplatná bez jejich nákupu a platit za ně později prostřednictvím procesu odsouhlasení, který se označuje jako "pravdivé".  Když přidělíte více prostředků, bude se vaší organizaci účtovat maximální počet předplatných přiřazených uživatelům během "true-up".  To platí i v případě, že už nemáte přiřazený maximální počet předplatných v době, kdy probíhá true-up.  Další informace o monitorování maximálního využití najdete v [tématu Maximální](maximum-usage.md) využití.


## <a name="see-also"></a>Viz také
- [Visual Studio dokumentace](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Microsoft 365 dokumentace](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Další informace o správě [Visual Studio předplatných pomocí GitHub Enterprise](assign-github.md).
- Pokud chcete pomoc s prodejem, předplatným, účty a fakturací pro Předplatná sady Visual Studio, kontaktujte Visual Studio [podpory předplatných.](https://aka.ms/vsadminhelp)