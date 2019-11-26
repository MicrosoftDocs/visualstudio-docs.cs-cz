---
title: Nejčastější dotazy k fakturaci Visual Studio Enterprise a Visual Studio Professional cloudových předplatných
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Otázky fakturace pro cloudová předplatná.
ms.openlocfilehash: 12ff77a052e54520885642cb3cd6ed1dea31506b
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491271"
---
# <a name="visual-studio-cloud-subscriptions-billing-faq"></a>Nejčastější dotazy k fakturaci pro cloudové předplatné sady Visual Studio
Nezapomeňte porovnat výhody [a ceny cloudového předplatného](https://visualstudio.microsoft.com/vs/pricing/) , abyste porozuměli výhodám každého předplatného sady Visual Studio, s porovnáním předplatných v cloudu a standardním prostředím, podrobnosti o výhodách pro předplatitele a další.

## <a name="general-purchasing-questions"></a>Obecné dotazy k nákupu
### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-using-a-purchase-order"></a>Otázka: mohu koupit cloudová předplatná sady Visual Studio pomocí nákupní objednávky?
Odpověď: Ne. Všechna cloudová předplatná sady Visual Studio musí být zakoupená pomocí předplatného Azure. (Můžete si ho představit jako fakturační účet Azure.)

### <a name="q-what-types-of-azure-subscriptions-can-be-used-to-buy-visual-studio-cloud-subscriptions"></a>Otázka: Jaké typy předplatných Azure je možné použít k nákupu cloudových předplatných sady Visual Studio?
Odpověď: Většina předplatných Azure je možné použít – podporujeme předplatná Azure připojená k vašemu [smlouva Enterprise (EA)](https://azure.microsoft.com/pricing/enterprise-agreement/), předplatná Azure nastavená poskytovateli Cloud Solution Providers (CSP), předplatná Azure se nastavila prostřednictvím prodejců Microsoft Open License a předplatných Azure s průběžnými platbami.

Některé typy předplatných Azure, včetně [bezplatné zkušební verze Azure](https://azure.microsoft.com/pricing/free-trial/) a předplatných, která jsou součástí předplatných sady Visual Studio, se nedají použít.

### <a name="q-am-i-required-to-buy-other-azure-services"></a>Otázka: Potřebuji koupit další služby Azure?
Odpověď: ne vůbec. Pokud chcete jenom koupit cloudová předplatná sady Visual Studio prostřednictvím Azure, můžete to udělat.

## <a name="enterprise-agreement-ea-customers"></a>Zákazníci smlouva Enterprise (EA)
### <a name="q-can-i-use-an-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>Otázka: mohu použít smlouva Enterprise k nákupu cloudových předplatných sady Visual Studio?
Odpověď: Ano, můžete. Musíte být vlastníkem nebo přispěvatelem předplatného Azure, které jste vytvořili pro EA. Ujistěte se prosím, že máte nákupy pro cloudová předplatná sady Visual Studio přímo v Visual Studio Marketplace. Nemůžete koupit cloudová předplatná sady Visual Studio pomocí nákupní objednávky.

### <a name="q-how-can-i-tell-whether-i-have-the-necessary-privileges-to-buy-services-in-the-visual-studio-marketplace-through-my-organizations-enterprise-agreement"></a>Otázka: Jak můžu zjistit, jestli mám potřebná oprávnění k nákupu služeb v Visual Studio Marketplace prostřednictvím smlouva Enterprise mojí organizace?
Odpověď: Nejjednodušší způsob, jak zjistit, jestli máte správná oprávnění, je kliknout na tlačítko **koupit** pro službu nabízenou v Visual Studio Marketplace.
Musíte vybrat předplatné Azure (což je fakturační účet) z prezentovaného seznamu předplatných Azure, která jsou aktuálně propojená s vaším účtem.
Vzhledem k tomu, že se název předplatného Azure nastaví jako výchozí typ fakturačního účtu ("průběžné platby", "smlouva Enterprise" atd.), často je jasné, jestli je předplatné Azure součástí vaší smlouva Enterprise.

Další možností je zkusit navštívit [Azure Enterprise Portal](https://ea.azure.com).  Pokud se k tomu budete moct úspěšně připojit, pak už máte roli správce podniku nebo vlastníka účtu. V smlouva Enterprise můžou vytvořit nové fakturační účty Azure jenom vlastníci účtu. Pokud nemůžete získat přístup k Azure Enterprise Portal, zeptejte se ve své organizaci, jestli je to váš podnikový správce, a požádejte ji, aby vás přidala jako vlastníka účtu v rámci Azure Enterprise Portal.  Pokud tuto osobu nemůžete najít, můžete [Odeslat lístek podpory](https://aka.ms/AzureEntSupport) a požádat o kontaktní údaje.  Pro lístek podpory budete potřebovat název vaší organizace a smlouva Enterprise číslo registrace.

### <a name="q-can-i-use-the-azure-monetary-commitment-funds-from-my-enterprise-agreement-to-buy-visual-studio-cloud-subscriptions"></a>Otázka: můžu použít prostředky peněžních závazků Azure z mého smlouva Enterprise k nákupu cloudových předplatných sady Visual Studio?
Odpověď: Ne, tyto předplacené prostředky nemají nárok na zakoupení cloudových předplatných sady Visual Studio. Když zvolíte předplatné Azure, které jste vytvořili pro EA, abyste si mohli koupit cloudové předplatné sady Visual Studio, poplatky se zobrazí ve vaší další faktuře za nadlimitní využití. Obvykle se jedná o každý měsíc, ale kvůli historickým pravidlům pro některé zákazníky EA se faktura za nadlimitní využití nemusí vydávat několik měsíců. Pokud potřebujete zjistit, kolik dalších nákupů (nákupů, které nejsou způsobilé pro prostředky peněžních závazků Azure), obraťte se na odborníka na licencování pro vašeho EA.

## <a name="how-charges-are-processed"></a>Jak se zpracovávají poplatky
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Otázka: jak se zpracovávají poplatky za **měsíční** předplatné cloudu?
Odpověď: při prvním nákupu účtujeme průběžné množství, které pokryje zbývající dny v aktuálním měsíci. Pokud se třeba koupí 10 Visual Studio Professional měsíčních předplatných cloudu od 15. dubna, účtujeme 5 jednotek, protože 50% v měsíci zůstane (15 dní 30 dnů na měsíc).
Na první z těchto let a potom každý měsíc až do doby, kdy zrušíte, budou se fakturovat celých 10 jednotek.

Po pozdějším zvýšení placeného množství také provedeme průběžné zvyšování počtu zbývajících dnů v aktuálním měsíci. Takže pokud jste si koupili 1 více Visual Studio Professional měsíčního cloudového předplatného 10. května, bude se vám účtovat zhruba 0,677 jednotek (21 dní zbývajících v 31. den).

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>Otázka: jak se zpracovávají poplatky za **roční** cloudové předplatné?
Odpověď: u každého nákupu účtujeme okamžitě celé množství nákupu. Poplatky nejsou rozdělené po rocích a neexistují žádné hodnocení. Pokud si koupíte roční předplatné v cloudu v různou dobu v roce, budete mít předplatné v různých měsících obnovování. V rámci nákupu multilicenční smlouvy s Microsoftem není vše pro roční předplatné v cloudu coterminous.

### <a name="q-how-do-cancelations-work"></a>Otázka: Jak může zrušení fungovat?
Odpověď: Když zrušíte předplatné cloudu sady Visual Studio, zrušíte tím automatické obnovení. Předplatné pokračuje do normálního data obnovení a pak jednoduše vyprší jeho platnost.
Po vypršení platnosti nemůže předplatitel sady Visual Studio nadále používat Visual Studio ani jiné výhody z předplatného.

U předplatných v rámci měsíčního cloudu se zrušení projeví na prvním dni příštího měsíce. Pokud zrušíte jenom některé z měsíčních předplatných cloudu, nezapomeňte odebrat uživatele na první z následujících měsíců, abyste měli jistotu, že budou mít přiřazená aktivní předplatná.

Pro roční cloudová předplatná se zruší platnost prvního dne v měsíci po uplynutí 12 měsíců od původního nákupu nebo po uplynutí 12 měsíců od poslední roční poplatky za obnovení. Pokud jste například koupili Visual Studio Professional roční předplatné cloudu 3. ledna 2018, zůstane aktivní až do 1. února 2019, když se automaticky obnoví na jiný rok. Pokud kdykoli operaci zrušíte od 1. února 2020, platnost předplatného vyprší 1. února 2020. V rámci předplatného s ročním předplatným cloudu není k dispozici žádný Rabat ke zrušení části.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Otázka: Jaký druh množstevních slev je k dispozici pro předplatná sady Visual Studio?
Odpověď: získáte 5% slevu v šesté a všech dalších odběrech *v rámci každého typu* předplatného:

* Visual Studio Professional měsíčně
* Visual Studio Professional roční
* Visual Studio Enterprise měsíčně
* Visual Studio Enterprise roční

Pokud třeba koupíte 6 Visual Studio Professional měsíčních předplatných a 5 Visual Studio Enterprise měsíčních předplatných, platíte běžnou cenu 5 Professional, získáte 5% slevu na šest Professional a platíte běžnou cenu na všech 5 Enterprise odběru.

Sleva se vztahuje také na poplatky v daném měsíčním fakturačním období. Takže pokud koupíte 5 Visual Studio Professional ročních předplatných za jeden měsíc a pak si koupíte 5 dalších dalších měsíců, platíte běžnou cenu na všechna 10 předplatných.

> [!NOTE]
> Společnost Microsoft už nenabízí Visual Studio Professional roční předplatné a Visual Studio Enterprise roční předplatné v cloudových předplatných. Stávající prostředí pro zákazníky se nijak nemění a možnost obnovit, zvýšit, snížit nebo zrušit jejich odběry. Novým zákazníkům doporučujeme přejít na [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) a prozkoumat různé možnosti nákupu sady Visual Studio.

## <a name="other-questions"></a>Další otázky
### <a name="q-can-i-use-the-monthly-azure-devtest-individual-credit-as-a-visual-studio-subscriber-to-buy-more-visual-studio-cloud-subscriptions"></a>Otázka: můžu použít měsíční kredit Azure DevTest jako předplatitele sady Visual Studio k nákupu dalších cloudových předplatných sady Visual Studio?
Odpověď: Ne, nemůžete použít svůj [měsíční kredit Azure DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) jako předplatitele sady Visual Studio k placení za Visual Studio Marketplace nákup. Jakékoli nákupy cloudových předplatných sady Visual Studio budou Fakturovatelné na platební kartu.
Než začnete nakupovat, budete muset [Odebrat limit útraty](https://azure.microsoft.com/pricing/spending-limits/).

### <a name="q-whats-the-difference-between-annual-and-monthly-cloud-subscriptions"></a>Otázka: Jaký je rozdíl mezi ročním a měsíčním předplatným cloudu?
Odpověď: měsíční předplatné cloudu zahrnuje sadu Visual Studio plus použití Azure DevOps Services a TFS. Tato roční cloudová předplatná mají tuto roli moc, ale také zahrnují výhody pro předplatitele, včetně použití Windows a dalšího softwaru Microsoftu k instalaci a spuštění pro vývoj a testování, měsíční kredit Azure DevTest, který se použije pro experimentování s Azure. služby a vývoj a testování v cloudu, školení, podpora a mnoho dalšího.
[Porovnání výhod a cen cloudových předplatných](https://visualstudio.microsoft.com/vs/pricing/)

### <a name="q-do-i-get-new-versions-of-visual-studio-if-i-buy-a-visual-studio-cloud-subscription"></a>Otázka: Chci dostávat nové verze sady Visual Studio, pokud si koupíte cloudové předplatné sady Visual Studio?
Odpověď: Ano. Při vydání nových verzí je můžete stáhnout a spustit. Navíc můžete i nadále spouštět předchozí verze.

### <a name="q-can-i-buy-visual-studio-cloud-subscriptions-from-my-software-reseller"></a>Otázka: Můžu si koupit cloudová předplatná sady Visual Studio z mého prodejce softwaru?
Odpověď: Ano, pokud se prodejce účastní programu Cloud Solution Provider (CSP). Stačí se zeptat.

## <a name="related-resources"></a>Související prostředky
- [Portál pro správu předplatných sady Visual Studio](https://manage.visualstudio.com/)
- [Podpora předplatných sady Visual Studio](https://visualstudio.microsoft.com/vs/support/)
- [Nákupy cloudového předplatného sady Visual Studio pro zprostředkovatele CSP](vscloud-csp.md)

## <a name="next-steps"></a>Další kroky
Zakupte si předplatné cloudu hned teď
- [Visual Studio Professional měsíčně](https://marketplace.visualstudio.com/items?itemName=ms.vs-professional-monthly)
- [Visual Studio Enterprise měsíčně](https://marketplace.visualstudio.com/items?itemName=ms.vs-enterprise-monthly)