---
title: Nákupy cloudového předplatného sady Visual Studio pro zprostředkovatele CSP
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Informace o poskytovatelích cloudových řešeních, jak koupit a spravovat cloudová předplatná sady Visual Studio pro vaše zákazníky.
ms.openlocfilehash: 7cc5a04a26a3120d88a931dde47c3b249c082791
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851404"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Nákup a Správa cloudových předplatných sady Visual Studio pro vaše zákazníky
Partneři v programu [Cloud Solution Provider (CSP)](https://partner.microsoft.com/cloud-solution-provider) si můžou koupit Visual Studio Enterprise a Visual Studio Professional předplatné cloudu pro své zákazníky.

[Porovnání možností cloudového předplatného](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Společnost Microsoft už nenabízí Visual Studio Professional roční předplatné a Visual Studio Enterprise roční předplatné v cloudových předplatných. Stávající prostředí pro zákazníky se nijak nemění a možnost obnovit, zvýšit, snížit nebo zrušit jejich odběry. Novým zákazníkům doporučujeme přejít na [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) a prozkoumat různé možnosti nákupu sady Visual Studio.

## <a name="prerequisites"></a>Požadavky
Musíte nejdřív nastavit tenanta zákazníka v partnerském centru a vytvořit předplatné Azure pro tohoto tenanta.

[Další informace](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Kdo může koupit předplatné sady Visual Studio?
K nákupu předplatných sady Visual Studio může koupit kdokoli s [přístupem vlastníka nebo přispěvatele](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) k předplatnému Azure.

## <a name="how-to-buy"></a>Jak koupit

1. Přihlaste se k [partnerskému centru Microsoftu](https://partnercenter.microsoft.com).
0. Zvolte **zákazníky** a vyberte zákazníka, pro který chcete koupit.
0. Vyberte možnost **Správa služeb**.
0. Vyberte **Visual Studio Marketplace**.
0. Ujistěte se, že jste customer's jméno v pravém horním rohu.
0. Vyberte **odběry**.
0. Vyberte Enterprise nebo Professional pro Visual Studio.
0. Vyberte **koupit**.
0. Vyberte předplatné Azure, které se bude fakturovat za nákup.
0. Zadejte počet uživatelů, kteří potřebují vaši zákazníci.
0. Zkontrolujte pořadí a **potvrďte** ho.

>[!NOTE]
> Při každém nákupu předplatných sady Visual Studio jako CSP budete muset postupovat podle těchto kroků. V současné době není k dispozici žádné rozhraní API pro automatizaci nákupu.

Po potvrzení nákupu můžete zvolit **Spravovat** a přiřadit k předplatným koncovým uživatelům vašeho zákazníka.  K portálu pro správu předplatného můžete získat přístup také z partnerského centra volbou **Service Management**.  Tady vidíte níže uvedený postup nebo video.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Jak spravovat cloudová předplatná sady Visual Studio pro zákazníka

1. Přihlaste se k [partnerskému centru Microsoftu](https://partnercenter.microsoft.com).
0. Vyberte možnost **zákazníci** a jméno zákazníka.
0. Vyberte možnost **Správa služeb**.
0. Vyberte **spravovat předplatná sady Visual Studio**.

Pokud pro tohoto zákazníka máte více než jedno předplatné Azure, použijte rozevírací nabídku k výběru předplatného Azure, přes které jste provedli nákupy.  V **souhrnu licence** se zobrazí počet přidaných předplatných a kolik je dostupných pro jednotlivé možnosti cloudového předplatného sady Visual Studio.  Souhrn také umožňuje zakoupit další předplatná nebo snížit počet předplatných.

Pokud chcete novému uživateli přiřadit předplatné, klikněte na tlačítko **Přidat** .  Zobrazené aktualizace počtu a koncový uživatel obdrží e-mailové oznámení. Koncový uživatel se pak může přihlásit pomocí e-mailové adresy, kterou jste zadali k aktivaci předplatného sady Visual Studio na [portálu pro předplatitele sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Chcete-li znovu přiřadit předplatné sady Visual Studio jinému uživateli, můžete odstranit aktuálního předplatitele a přidat nového předplatitele.

Pokud předplatitel neaktivoval své předplatné sady Visual Studio, může to být způsobeno tím, že vynechali e-mail s pozvánkou.  Můžete požádat o to, abychom znovu odeslali pozvánku k aktivaci uživateli z portálu pro správu sady Visual Studio.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Zobrazit ceny sady Visual Studio pro partnery CSP
Pokud si chcete zobrazit ceny pro partnery CSP v programu Visual Studio, přihlaste se do [partnerského centra](https://partnercenter.microsoft.com).  V levém navigačním panelu vyberte **ceny a nabídky** .  V pravém horním rohu vyberte soubor s cenami aktuálního měsíce v části **služby založené na používání** . Po stažení excelového listu přejít na **seznam ceníků Azure** a vyfiltrujte sloupec **kategorie měřičů** na **Visual Studio**.

Tady je postup, jak interpretovat, co vidíte v této tabulce:

| Kategorie měřiče    |   Name                 |  Jednotky                                |           Co to je                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Podnikové             |  Předplatné služby                         | Visual Studio Enterprise měsíční předplatné   |
| Visual Studio     | Professional           |  Předplatné služby                         | Visual Studio Professional měsíční předplatné |

Nabízíme 5% slevu na šesté jednotce, kterou koupíte (pro konkrétního zákazníka) každý měsíc každého předplatného sady Visual Studio. To je důvod, proč uvidíte dva řádky pro každou možnost předplatného. V jednom řádku se zobrazuje "minimální hodnota" 0, kterou byste měli interpretovat jako základní cenu za jednotky 1 až 5. V druhém řádku se zobrazuje "minimální hodnota" 5, takže se jedná o 5% slevu, která se vztahuje na jednotky 6 a vyšší.

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Otázka: jak se zpracovávají poplatky za **měsíční** předplatné cloudu?
Odpověď: při prvním nákupu účtujeme průběžné množství, které pokryje zbývající dny v aktuálním měsíci. Pokud se třeba koupí 10 Visual Studio Professional měsíčních předplatných v cloudu 15. dubna, účtujeme 5 jednotek, protože zbývá 15 dní na 30 dnů nebo 50% a jednotky účtované za 50%. Na první z těchto let a potom každý měsíc až do doby, kdy zrušíte, budou se fakturovat celých 10 jednotek.

Po pozdějším zvýšení placeného množství také provedeme průběžné zvyšování počtu zbývajících dnů v aktuálním měsíci. Takže pokud jste si koupili 1 více Visual Studio Professional měsíčního cloudového předplatného 10. května, bude se vám účtovat zhruba 0,677 jednotek (21 dní zbývajících v 31. den).

### <a name="q-how-do-cancellations-work"></a>Otázka: jak zrušení fungují?
Odpověď: Když zrušíte předplatné cloudu sady Visual Studio, zrušíte tím automatické obnovení. Předplatné pokračuje do normálního data obnovení a pak jednoduše vyprší jeho platnost. Po vypršení platnosti nemůže předplatitel sady Visual Studio nadále používat Visual Studio ani jiné výhody z předplatného.

U předplatných v rámci měsíčního cloudu se zrušení projeví na prvním dni příštího měsíce. Pokud zrušíte jenom některé z měsíčních předplatných v rámci vašeho zákazníka, nezapomeňte na první z následujících měsíců odebrat uživatele, abyste měli jistotu, že budou mít přiřazená aktivní předplatná.

Pro roční cloudová předplatná se zrušení projeví v platnost první den v měsíci po uplynutí 12 měsíců od původního nákupu nebo po uplynutí 12 měsíců od poslední roční poplatky za obnovení. Pokud jste například koupili Visual Studio Enterprise roční předplatné cloudu 3. ledna 2018, zůstane aktivní až do 1. února 2019, když se automaticky obnoví na jiný rok. Pokud kdykoli operaci zrušíte od 1. února 2020, platnost předplatného vyprší 1. února 2020. V rámci předplatného s ročním předplatným cloudu není k dispozici žádný Rabat ke zrušení části.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Otázka: Jaký druh množstevních slev je k dispozici pro předplatná sady Visual Studio?
Odpověď: získáte 5% slevu v šesté a všech dalších odběrech *v rámci každého typu* předplatného:
- Visual Studio Professional měsíčně
- Visual Studio Enterprise měsíčně

Pokud třeba koupíte 6 Visual Studio Professional měsíční předplatná a 5 Visual Studio Enterprise měsíční předplatné, platíte běžnou cenu na pět Professional, získáte 5% slevu na šest Professional a platíte běžnou cenu na všech pět Podniková předplatná.

Sleva se vztahuje také na poplatky v daném měsíčním fakturačním období. Takže pokud koupíte 5 Visual Studio Professional ročních předplatných za jeden měsíc a pak si koupíte 5 dalších dalších měsíců, platíte běžnou cenu na všechna deset předplatných.

Tyto slevy se projeví v údajích o cenách v [partnerském centru](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>Otázka: Existují slevy na obnovení?
Odpověď: Ne, ceny pro předplatná sady Visual Studio jsou ploché. Stejná cena se nabízí pro nová předplatná a pokračování v předplatných.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Otázka: jsou k dispozici cenové možnosti pro vývoj/testování Azure pro poskytovatele CSP?
Odpověď: ne v tomto okamžiku. Vaši zákazníci můžou využít [ceny Azure pro vývoj a testování](https://azure.microsoft.com/pricing/dev-test/), ale pro CSP nepoužíváme žádné konkrétní.

