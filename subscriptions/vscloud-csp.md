---
title: Nákup předplatného visual studia cloud pro poskytovatele služeb na uspono
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Informace pro poskytovatele cloudových řešení o tom, jak nakupovat a spravovat předplatná cloudu sady Visual Studio pro vaše zákazníky.
ms.openlocfilehash: 7cc5a04a26a3120d88a931dde47c3b249c082791
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "75851404"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Nákup a správa cloudových předplatných Sady Visual Studio pro vaše zákazníky
Partneři v programu [Zprostředkovatel cloudových řešení (CSP)](https://partner.microsoft.com/cloud-solution-provider) mohou zakoupit předplatná cloudu Visual Studio Enterprise a Visual Studio Professional pro své zákazníky.

[Porovnání možností předplatného cloudu](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Microsoft už nenabízí roční předplatná Visual Studio Professional a roční předplatná Visual Studia Enterprise v předplatných cloudu. Stávající zákazníci se nezmění a možnost obnovit, zvýšit, snížit nebo zrušit jejich odběry. Noví zákazníci se [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) doporučuje přejít na prozkoumat různé možnosti nákupu Visual Studio.

## <a name="prerequisites"></a>Požadavky
Nejprve musíte nastavit klienta zákazníka v Partnerském centru a vytvořit předplatné Azure pro tohoto klienta.

[Další informace](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Kdo si může koupit předplatná Visual Studia?
Předplatné Visual Studia si může zakoupit kdokoli, kdo má [přístup vlastníka nebo přispěvatele](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) k předplatnému Azure.

## <a name="how-to-buy"></a>Možnosti nákupu

1. Přihlaste se do [centra microsoft partnercenter](https://partnercenter.microsoft.com).
0. Vyberte **zákazníka** a vyberte zákazníka, pro který chcete koupit.
0. Zvolte **Správa služeb**.
0. Zvolte **Visual Studio Marketplace**.
0. Ujistěte se, že vaše jméno zákazníka je v pravém horním rohu.
0. Zvolte **Předplatná**.
0. Zvolte Enterprise nebo Professional pro Visual Studio.
0. Zvolte **Koupit**.
0. Zvolte předplatné Azure pro fakturování za nákup.
0. Zadejte počet uživatelů, které zákazníci potřebují.
0. Zkontrolujte objednávku a **potvrďte** ji.

>[!NOTE]
> Budete muset postupovat podle těchto kroků při každém nákupu předplatných Sady Visual Studio jako csp. V tuto chvíli neexistuje žádné rozhraní API pro automatizaci nákupu.

Po potvrzení nákupu můžete zvolit **Spravovat** a přiřadit předplatná koncovým uživatelům zákazníka.  K portálu správy předplatného můžete také přistupovat z Partnerského centra výběrem **správy služeb**.  Odtud viz kroky nebo video níže.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Jak spravovat předplatná cloudu sady Visual Studio pro zákazníka

1. Přihlaste se do [centra microsoft partnercenter](https://partnercenter.microsoft.com).
0. Zvolte **Zákazníci** a jméno zákazníka.
0. Zvolte **Správa služeb**.
0. Zvolte **Spravovat předplatná sady Visual Studio**.

Pokud máte pro tohoto zákazníka více než jedno předplatné Azure, vyberte pomocí rozevírací nabídky předplatné Azure, přes které jste provedli nákupy.  **Souhrn licencí** zobrazuje počet předplatných, která byla přiřazena, a počet, kolik je k dispozici pro každou možnost předplatného cloudu sady Visual Studio.  Souhrn také umožňuje zakoupit další předplatná nebo snížit počet předplatných.

Zvolte **přidat,** chcete-li přiřadit předplatné novému uživateli.  Zobrazený počet se aktualizuje a koncový uživatel obdrží e-mailové oznámení. Koncový uživatel se pak může přihlásit pomocí e-mailové adresy, kterou jste zadali, a aktivovat tak své předplatné sady Visual Studio na [portálu předplatitelů sady Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Chcete-li znovu přiřadit předplatné sady Visual Studio jinému uživateli, můžete odstranit aktuálního odběratele a přidat nového odběratele.

Pokud předplatitel neaktivoval své předplatné sady Visual Studio, může to být proto, že zmeškal e-mail s pozvánkou.  Můžete požádat, abychom znovu odeslali pozvánku k aktivaci uživateli z portálu pro správu Visual Studia.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Zobrazit ceny visual studia pro partnery CSP
Chcete-li zobrazit ceny sady Visual Studio pro partnery CSP, přihlaste se do [Centra partnerů](https://partnercenter.microsoft.com).  Zvolte **Ceny a nabídky** z levého nav.  V pravém horním části zvolte aktuální soubor cen za měsíc v části **Služby založené na využití.** Po stažení excelové tabulky přejděte na list **Ceníku Azure** a filtrujte sloupec **Kategorie měřiče** do **Sady Visual Studio**.

Postup interpretace toho, co vidíte v této tabulce:

| Kategorie měřiče    |   Name (Název)                 |  Jednotky                                |           Co to je                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Enterprise             |  Předplatné                         | Měsíční předplatné Visual Studio Enterprise   |
| Visual Studio     | Professional           |  Předplatné                         | Měsíční předplatné Visual Studio Professional |

Nabízíme 5% slevu na šestou jednotku, kterou si koupíte (pro daného zákazníka) každý měsíc každého předplatného sady Visual Studio. To je důvod, proč se zobrazí dva řádky pro každou možnost předplatného. Jeden řádek zobrazuje "Minimální hodnota" 0, kterou byste měli interpretovat jako základní cenu pro jednotky 1 až 5. Druhý řádek zobrazuje "minimální hodnotu" 5, takže se jedná o 5% diskontní cenu, která se vztahuje na jednotky 6 a vyšší.

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Otázka: Jak **se** zpracovávají měsíční poplatky za předplatné cloudu?
A: Při prvním nákupu účtujeme poměrné množství, které pokrývá zbývající dny v aktuálním měsíci. Pokud například 15. dubna byl proveden nákup 10 měsíčních cloudových předplatných Visual Studio Professional, účtovali bychom 5 jednotek, protože v 30denním měsíci zbývá 15 dní nebo 50 % a jednotky účtované 50 %. Prvního května a poté každý měsíc, dokud jej nezrušíte, bude účtováno celých 10 jednotek.

Když později zvýšíte placené množství, zvýšíme také zvýšené jednotky, abychom pokryli zbývající dny v aktuálním měsíci. Pokud jste si tedy 1 další měsíční předplatné cloudu Visual Studio Professional koupili 10. května, vyfakturovali bychom zhruba 0,677 jednotek (v měsíci květen 31 dnů zbývá 21 dní).

### <a name="q-how-do-cancellations-work"></a>Otázka: Jak zrušení fungují?
A: Když zrušíte předplatné cloudu Sady Visual Studio, stornujete automatické obnovení. Předplatné pokračuje až do svého normálního data obnovení a pak jednoduše vyprší. Po vypršení platnosti předplatitele sady Visual Studio již nelze použít Visual Studio nebo jiné výhody z předplatného.

S měsíčními předplatnými cloudu se zrušení projeví první den následujícího měsíce. Pokud zrušíte jenom některá měsíční cloudová předplatná zákazníka, nezapomeňte odebrat uživatele prvního příštího měsíce, abyste zajistili, že správným lidem budou i nadále přiřazena aktivní předplatná.

U ročních předplatných cloudů se zrušení projeví první den měsíce následujícího po 12 měsících od původního nákupu nebo 12 měsíců od posledního ročního poplatku za obnovení. Pokud jste například 3. Pokud předplatné zrušíte kdykoli mezi 1. Neexistuje žádná sleva za zrušení části cesty přes rok předplatného s ročním icloudpředplatného.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Otázka: Jaký druh množstevních slev je k dispozici pro předplatná sady Visual Studio?
A: Získáte 5% slevu na 6th a všechny následné předplatné *v rámci každého typu* předplatného:
- Visual Studio Professional měsíčně
- Visual Studio Enterprise měsíčně

Pokud si například koupíte měsíční předplatné 6 Visual Studio Professional a 5 měsíčních předplatných sady Visual Studio Enterprise, zaplatíte běžnou cenu za pět hodin, získáte 5% slevu na 6. Podnikové předplatná.

Sleva se také vztahuje pouze na poplatky v daném měsíčním fakturačním období. Takže pokud si koupíte 5 Visual Studio Professional roční předplatné v jednom měsíci, a pak si koupíte 5 více příští měsíc, budete platit běžnou cenu na všech deset předplatných.

Tyto slevy se projeví v cenových datech v rámci [Partnerského centra](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>Otázka: Existují slevy na obnovení?
A: Ne, ceny pro předplatná sady Visual Studio jsou ploché. Stejná cena je nabízena pro nová předplatná a pokračující předplatná.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Otázka: Existují možnosti azure dev/test cen pro csp?
A: Ne v tomto okamžiku. Vaši zákazníci mohou využít [ceny Azure pro vývoj a testování](https://azure.microsoft.com/pricing/dev-test/), ale pro csp nemáme nic konkrétně.

