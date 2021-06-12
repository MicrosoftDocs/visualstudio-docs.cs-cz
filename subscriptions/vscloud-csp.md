---
title: Visual Studio cloudových předplatných pro CSP
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: d2ab13ed-ef79-4ef0-8736-eccd04bc6020
ms.date: 03/18/2021
ms.topic: conceptual
description: Informace pro poskytovatele Cloud Solution Providers o tom, jak kupovat Visual Studio spravovat cloudová předplatná pro vaše zákazníky.
ms.openlocfilehash: 09c905d113920a0bb55aed8851d3fb62c92a39bf
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042848"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Nákup a správa Visual Studio cloudových předplatných pro vaše zákazníky
Partneři v [programu Cloud Solution Provider (CSP)](https://partner.microsoft.com/cloud-solution-provider) mohou pro své zákazníky Visual Studio Enterprise a Visual Studio Professional cloudová předplatná.

[Porovnání možností cloudového předplatného](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Microsoft už v cloudových předplatných Visual Studio Professional roční předplatná a Visual Studio Enterprise roční předplatná. Stávající zákazníci nebudou mít žádné změny a možnost prodlužovat, zvyšovat, zmenšovat nebo rušit svá předplatná. Novým zákazníkům doporučujeme, aby [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) prozkoumali různé možnosti nákupu Visual Studio.

## <a name="prerequisites"></a>Požadavky
Nejprve musíte nastavit tenanta zákazníka v Partnerské centrum a vytvořit předplatné Azure pro tohoto tenanta.

[Další informace](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Kdo si může Visual Studio předplatná?
Každý, [kdo má k předplatnému](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) Azure přístup vlastníka nebo přispěvatele, si může Visual Studio předplatná.

## <a name="how-to-buy"></a>Možnosti nákupu

1. Přihlaste se k [webu Microsoft Partnerské centrum](https://partnercenter.microsoft.com).
0. Zvolte **Zákazníci** a vyberte zákazníka, pro který chcete koupit.
0. Zvolte **Správa služeb.**
0. Zvolte **Visual Studio Marketplace**.
0. Ujistěte se, že jméno zákazníka je v pravém horním rohu.
0. Zvolte **Předplatná.**
0. Zvolte Enterprise nebo Professional pro Visual Studio.
0. Zvolte **Koupit.**
0. Zvolte předplatné Azure, které chcete fakturovat za nákup.
0. Zadejte počet uživatelů, které zákazník potřebuje.
0. Zkontrolujte objednávku a **potvrďte** ji.

>[!NOTE]
> Tento postup budete muset provést při každém nákupu předplatného Visual Studio jako CSP. V tuto chvíli neexistuje žádné rozhraní API pro automatizaci nákupu.

Po potvrzení nákupu můžete výběrem možnosti Spravovat přiřadit předplatná koncovým uživatelům zákazníka.   K portálu pro správu předplatného se můžete také Partnerské centrum výběrem možnosti **Správa služeb.**  Odtud se můžete podívat na následující kroky nebo video.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Jak spravovat Visual Studio cloudových předplatných pro zákazníka

1. Přihlaste se k [webu Microsoft Partnerské centrum](https://partnercenter.microsoft.com).
0. Zvolte **Zákazníci** a jméno zákazníka.
0. Zvolte **Správa služeb.**
0. Zvolte **Spravovat Předplatná sady Visual Studio**.

Pokud máte pro tohoto zákazníka více než jedno předplatné Azure, v rozevírací nabídce vyberte předplatné Azure, jehož prostřednictvím jste provedli nákupy.  Souhrn **licencí zobrazuje** počet přiřazených předplatných a počet dostupných předplatných pro každou Visual Studio cloudových předplatných.  Souhrn také umožňuje zakoupit další předplatná nebo snížit počet předplatných.

Zvolte **Přidat** a přiřaďte předplatné novému uživateli.  Zobrazený počet se aktualizuje a koncový uživatel obdrží e-mailové oznámení. Koncový uživatel se pak může přihlásit pomocí e-mailové adresy, kterou jste Visual Studio předplatného na [portálu Visual Studio pro předplatitele.](https://my.visualstudio.com?wt.mc_id=o~msft~docs)

Pokud chcete předplatné Visual Studio jinému uživateli, můžete aktuálního odběratele odstranit a přidat nového odběratele.

Pokud předplatitel neaktivoval své předplatné Visual Studio, může to být tím, že zmeškal e-mail s pozvánkou.  Můžete požádat, abychom uživateli znovu na portálu pro správu Visual Studio pozvánku k aktivaci.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Zobrazení Visual Studio pro partnery CSP
Pokud chcete Visual Studio ceny pro partnery CSP, přihlaste se k [Partnerské centrum](https://partnercenter.microsoft.com).  V **levém navigačním panelu** zvolte Ceny a nabídky.  V části služby založené na využití v pravém horním **rohu** vyberte soubor s cenami pro aktuální měsíc. Po stažení excelové tabulky přejděte na ceník **Azure** a vyfiltrujte sloupec **Meter Category** (Kategorie měřiče) **tak, aby Visual Studio**.

Tady je postup interpretace toho, co vidíte v této tabulce:

| Kategorie měřiče    |   Name                 |  Jednotky                                |           Co to je                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Enterprise             |  Předplatné                         | Visual Studio Enterprise měsíční předplatné   |
| Visual Studio     | Professional           |  Předplatné                         | Visual Studio Professional měsíční předplatné |

Každý měsíc každého předplatného nabízíme 5% slevu na 6. jednotku Visual Studio, kterou si zakoupíte (pro daného zákazníka). Proto se pro každou možnost předplatného zobrazí dva řádky. Jeden řádek zobrazuje "Minimální hodnotu" 0, kterou byste měli interpretovat jako základní cenu pro jednotky 1 až 5. Druhý řádek zobrazuje "Minimální hodnotu" 5, takže se jedná o 5% slevovou cenu, která se vztahuje na jednotky 6 a vyšší.

## <a name="frequently-asked-questions"></a>Nejčastější dotazy
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Otázka: Jak se **zpracovávají měsíční poplatky** za cloudové předplatné?
O: Při prvním nákupu účtujeme přeúčtované množství, které pokryje zbývající dny v aktuálním měsíci. Pokud by například k 15. dubnu došlo k nákupu 10 měsíčních cloudových předplatných, účtili bychom 5 jednotek, protože za 3 Visual Studio Professional 0 dnů v měsíci zbývá 15 dnů, tedy 50 % a poplatky účtujeme ve výši 50 %. 1. května a následně každý měsíc, dokud ji nezrušíte, se vám bude účtovat celých 10 jednotek.

Když placené množství zvýšíte později, také zvýšíme počet jednotek tak, aby pokryje zbývající dny v aktuálním měsíci. Pokud jste tedy 10. května koupili Visual Studio Professional 1 další měsíční cloudové předplatné, fakturovali bychom přibližně 0,677 jednotky (zbývajících 21 dnů v květnovém 31denním měsíci).

### <a name="q-how-do-cancellations-work"></a>Otázka: Jak funguje zrušení?
O: Když zrušíte předplatné Visual Studio, zrušíte automatické prodlužování platnosti. Předplatné bude fungovat dál až do normálního data prodloužení a pak jeho platnost vyprší. Po vypršení platnosti předplatného už předplatitel sady Visual Studio nebude moct využívat sadu Visual Studio ani další výhody, které se s ním pojí.

U měsíčních cloudových předplatných ke zrušení dojde první den následujícího měsíce. Pokud zrušíte jenom některá z měsíčních cloudových předplatných vašich zákazníků, nezapomeňte uživatele odebrat první den následujícího měsíce, abyste zajistili, že budou mít stále přiřazená aktivní předplatná správným lidem.

U ročních cloudových předplatných ke zrušení dojde první den měsíce následujícího 12 měsíců od původního nákupu nebo 12 měsíců od posledního ročního poplatku za prodloužení. Pokud jste si například 3. ledna 2018 koupili roční cloudové předplatné, zůstane aktivní až do 1. února 2019, kdy se automaticky prodlužuje o další rok. Visual Studio Enterprise Pokud kdykoli mezi tímto datem a 1. únorem 2020 předplatné zrušíte, platnost předplatného vyprší 1. února 2020. Za předčasné zrušení ročních cloudových předplatných před uplynutím celého roku není žádná sleva.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Otázka: Jaký druh multilicenčních slev je k dispozici pro Visual Studio předplatná?
O: V rámci každého typu předplatného získáte 5% slevu na 6. a všechna následující *předplatná:*
- Visual Studio Professional měsíčně
- Visual Studio Enterprise měsíčně

Pokud tedy například zakoupíte 6 předplatných Visual Studio Professional měsíčně Visual Studio Enterprise 5 měsíčních předplatných, budete platit běžnou cenu pro pět předplatných Professional, získáte 5% slevu na 6. profesionální předplatné a za všechna pět předplatných Enterprise platíte běžnou cenu.

Sleva se také vztahuje pouze na poplatky v daném měsíčním fakturačním období. Pokud tedy za jeden měsíc zakoupíte 5 Visual Studio Professional ročních předplatných a další 5 za měsíc zakoupíte, za všech deset předplatných zaplatíte běžnou cenu.

Tyto slevy se projeví v datech o cenách v rámci [Partnerské centrum](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>Otázka: Existují slevy za prodloužení?
O: Ne, ceny pro Visual Studio předplatná jsou ploché. Stejná cena se nabízí pro nová předplatná a další předplatná.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Otázka: Existují pro CSP cenové možnosti azure pro vývoj/testování?
O: V tuto chvíli ne. Vaši zákazníci mohou využít výhod cen [Azure pro vývoj a testování,](https://azure.microsoft.com/pricing/dev-test/)ale nemáme nic konkrétního pro CSP.

## <a name="resources"></a>Zdroje informací
- Pomoc s prodejem, předplatným, účty a fakturací pro Předplatná sady Visual Studio najdete v Visual Studio [podpory předplatných.](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Viz také
- [Visual Studio dokumentace](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Microsoft 365 dokumentace](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Odpovědi na [běžné dotazy k](vscloud-billing-faq.yml) fakturaci najdete v nejčastějších dotazech k fakturaci cloudu.