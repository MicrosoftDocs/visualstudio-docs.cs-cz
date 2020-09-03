---
title: Vývoj testů z modelu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2981d510b5f56b89a2cb68d1a6bee93222d71b3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596655"
---
# <a name="develop-tests-from-a-model"></a>Vývoj testů z modelu
Můžete použít požadavky a modely architektury, které vám pomůžou organizovat testy vašeho systému a jeho součástí. Tento postup pomáhá zajistit, že budete testovat požadavky, které jsou důležité pro uživatele a další zúčastněné strany, a pomůže vám rychle aktualizovat testy v případě změny požadavků. Pokud používáte [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] , můžete také zachovat propojení mezi modely a testy.

 Chcete-li zjistit, které verze aplikace Visual Studio podporují tyto funkce, přečtěte si téma [podpora verzí pro architektury a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Testování systému a subsystému
 *Testování systému,* označované také jako *testování přijetí*, znamená testování, jestli jsou požadavky uživatelů splněné. Tyto testy se týkají externě viditelného chování systému místo interního návrhu.

 Systémové testy jsou velmi užitečné při rozšiřování nebo přenavrhování systému. Pomůžou vám vyhnout se vkládání chyb při změně kódu.

 Při plánování jakékoli změny nebo rozšíření systému je vhodné začít se sadou systémových testů, které jsou spuštěny ve stávajícím systému. Pak můžete roztáhnout nebo upravit testy pro otestování nových požadavků, provést změny v kódu a znovu spustit úplnou sadu testů.

 Při vývoji nového systému můžete začít vytvářet testy hned po zahájení vývoje. Definováním testů před vývojem jednotlivých funkcí můžete zachytit diskuze požadavků velmi specifickým způsobem.

 Testování subsystému používá stejné principy pro hlavní součásti systému. Jednotlivé komponenty jsou testovány odděleně od jiných komponent. Testy subsystému se zaměřují na chování viditelné v uživatelském rozhraní nebo rozhraní API součásti.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Odvození systémových testů z modelu požadavků
 Můžete vytvořit a udržovat vztah mezi systémovými testy a modelem požadavků. Chcete-li vytvořit tuto relaci, zapište testy, které odpovídají hlavním prvkům modelu požadavků. Visual Studio pomáhá udržovat tento vztah tím, že vám umožní vytvořit propojení mezi testy a částmi modelu. Další informace o modelech požadavků najdete v článku [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Zápis testů pro každý případ použití
 Pokud používáte [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] , můžete vytvořit skupinu testů pro každý případ použití, který jste definovali v modelu požadavků. Například pokud máte v pořadí případů použití moučku, která zahrnuje vytvoření objednávky a přidání položky do objednávky, můžete vytvořit testy pro celkové i podrobnější informace v těchto případech použití.

 Tyto pokyny můžou být užitečné:

- Každý případ použití by měl mít několik testů pro hlavní cesty a výjimečné výsledky.

- Když popíšete případ použití v modelu požadavků, je důležitější definovat jeho následná podmínka, to znamená, že je dosaženo cíle, než aby bylo podrobně popsané postupy, které uživatel sleduje, aby bylo možné dosáhnout cíle. Například následná podmínka z objednávky může být, že restaurace připraví jídlo pro zákazníka a že se zákazník zaplatí. Následná podmínka je kritérium, které by testy měly ověřit.

- Základní samostatné testy na samostatné klauzule následná podmínka. Můžete například vytvořit samostatné testy pro oznamování restaurace objednávky a pro platbu od zákazníka. Toto oddělení má tyto výhody:

  - Změny v různých aspektech požadavků často vznikají nezávisle. Oddělením testů do různých aspektů tímto způsobem usnadňujete aktualizaci testů v případě změny požadavků.

  - Pokud plán vývoje implementuje jeden aspekt případu použití před jiným, můžete testy povolit samostatně jako průběh vývoje.

- Při návrhu testů oddělte výběr testovacích dat z kódu nebo skriptu, který určuje, zda byl dosažen následná podmínka. Například test jednoduché aritmetické funkce může být: vstup 4; Ověřte, zda je výstup 2. Místo toho Navrhněte skript jako: volba vstupu; vynásobte výstup samotným a ověřte, zda je výsledkem původní vstup. Tento styl vám umožní měnit vstupy testu bez změny hlavního těla testu.

#### <a name="linking-tests-to-use-cases"></a>Propojování testů s případy použití
 Pokud používáte [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] k návrhu a spuštění testů, můžete své testy uspořádat v pracovních položkách požadavky, případ použití nebo uživatelský scénář. Tyto pracovní položky můžete propojit s případy použití v modelu. To vám umožní rychle sledovat změny požadavků testů a pomáhá sledovat průběh každého případu použití.

###### <a name="to-link-tests-to-a-use-case"></a>Propojení testů s případem použití

1. V portálu [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] vytvořte požadavek a založte na něm testovací sadu.

    Požadavek, který vytvoříte, je pracovní položka v [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] . Může to být uživatelský scénář, požadavek nebo pracovní položka případu použití, v závislosti na šabloně procesu, kterou projekt používá s Team Foundation. Další informace najdete v tématu [o agilních nástrojích a agilních řízeních projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts).

2. Propojte pracovní položku požadavku s jedním nebo více případy použití v modelu.

    V diagramu případu použití klikněte pravým tlačítkem myši na případ použití a pak klikněte na **odkaz na pracovní položku**.

3. Přidejte do testovací sady, testovací případy, které ověřují případy použití.

   Každý uživatelský scénář nebo pracovní položka požadavku se obvykle připojí k několika případům použití v modelu a každý případ použití se připojí k několika uživatelským scénářům nebo požadavkům. Důvodem je to, že každý uživatelský scénář nebo požadavek se týká sady úloh, které vyvíjejí několik případů použití. Například v prvotní iteraci projektu můžete vyvinout základní uživatelský scénář, ve kterém může zákazník vybrat položky z katalogu a dodat je. V pozdější iteraci může příběh znamenat, že uživatel platí při dokončení objednávky a dodavatel obdrží peníze po odeslání zboží.  Každý příběh přidá klauzuli do následná podmínkay případu použití zboží objednávky.

   Můžete vytvořit samostatné odkazy z požadavků na klauzule následná podmínka tak, že tyto klauzule zapíšete do samostatných komentářů v diagramu případu použití. Každý komentář můžete propojit s pracovní položkou požadavku a připojit komentář k případu použití v diagramu.

### <a name="base-tests-on-the-requirements-types"></a>Základní testy na typech požadavků
 Typy, které jsou třídy, rozhraní a výčty modelu požadavků, popisují koncepty a vztahy v souvislosti s tím, jak si uživatelé myslí a sdělí své podnikání. Vylučuje dotyčné typy pouze s interním návrhem systému.

 Navrhněte testy v souvislosti s těmito typy požadavků. Tento postup vám pomůže zajistit, že při změnách požadavků, je snadné spojit změny v nezbytných změnách v testech. Umožňuje projednávat testy a jejich zamýšlené výsledky přímo s koncovými uživateli a dalšími zúčastněnými stranami. To znamená, že potřeby uživatelů je možné spravovat mimo proces vývoje a vyhnout se nechtěnému návrhu testů s možnými nedostatky v návrhu.

 V případě manuálních testů zahrnuje tento postup dodržení slovníku modelu požadavků v testovacích skriptech. Pro automatizované testy tento postup zahrnuje použití diagramů tříd požadavků jako základu pro testovací kód a vytváření funkcí přistupujícího a aktualizačního programu pro propojení modelu požadavků s kódem.

 Model požadavků může například zahrnovat nabídky typů, položky nabídky, pořadí a přidružení mezi nimi. Tento model představuje informace, které jsou uloženy a zabývá se systémem pro objednávání v jídlo, ale nepředstavuje složitosti jeho implementace. V pracovním systému může existovat několik různých rozdílnosti každého typu, v databázích, v uživatelských rozhraních a na rozhraních API. V distribuovaném systému může existovat několik variant každé instance uložené v různých částech systému současně.

 Chcete-li otestovat případ použití, například přidat položku k seřazení, může metoda testu zahrnovat kód podobný tomuto:

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Všimněte si, že tato testovací metoda používá třídy modelu požadavků. Přidružení a atributy jsou realizovány jako vlastnosti rozhraní .NET.

 Aby bylo možné tuto práci provést, vlastnosti třídy musí být definovány jako funkce nebo přistupující objekty jen pro čtení, které mají přístup k systému, aby bylo možné načíst informace o jeho aktuálním stavu. Metody, které simulují případy použití, jako je například AddItemToOrder, musí řídit systém prostřednictvím jeho rozhraní API nebo přes vrstvu pod svým uživatelským rozhraním. Konstruktory testovacích objektů, například Order a MenuItem, musí také řídit systém, aby vytvořil odpovídající položky v rámci systému.

 Řada přístupových objektů a jejich přidaných nástroje již bude k dispozici prostřednictvím normálního rozhraní API aplikace. Některé další funkce ale může být nutné zapsat, aby bylo možné testy povolit. Tyto další přistupující objekty a aktualizace se někdy označují jako "zkušební instrumentace". Vzhledem k tomu, že jsou závislé na interním návrhu systému, je odpovědností vývojářů systému poskytnout jim, zatímco testeri zapisují kód testů z podmínek modelu požadavků.

 Při psaní automatizovaných testů můžete použít obecné testy k zabalení přístupových objektů a aktualizovatelných.

### <a name="tests-for-business-rules"></a>Testy pro obchodní pravidla
 Některé požadavky přímo nesouvisejí s žádným případem použití. Například DinnerNow Business umožňuje zákazníkům vybírat z mnoha nabídek, ale vyžaduje, aby všechny zvolené položky byly v jedné nabídce. Toto obchodní pravidlo lze vyjádřit jako invariantní o přidruženích mezi objednávkami, nabídkami a položkami v modelu třídy požadavků.

 Invariantní pravidlo tohoto druhu řídí nejen všechny aktuálně definované případy použití, ale také všechny další případy použití, které budou definovány později. Proto je vhodné ho napsat samostatně z jakéhokoli případu použití a testovat ho odděleně z případů použití.

## <a name="deriving-subsystem-tests-from-models"></a>Odvození testů subsystému z modelů
 V rámci vysokého návrhu velkého systému můžete identifikovat součásti nebo subsystémy. Tyto prvky představují části, které mohou být samostatně navržené nebo umístěné na různých počítačích, nebo jsou opakovaně použitelné moduly, které se dají v mnoha ohledech znovu kombinovat.

 Pro každou hlavní komponentu se dá použít stejný princip jako u kompletního systému. Ve velkém projektu mohou mít jednotlivé komponenty vlastní model požadavků. V menších projektech lze vytvořit model architektury nebo návrh na nejvyšší úrovni, aby se zobrazily hlavní komponenty a jejich interakce. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).

 V obou případech můžete vytvořit relaci mezi prvky modelu a testy subsystému stejným způsobem jako mezi modelem požadavků a systémovými testy.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izolace součástí pomocí poskytovaných a požadovaných rozhraní
 Je vhodné identifikovat všechny závislosti, které má součást v jiných částech systému nebo externích služeb, a reprezentovat je jako požadovaná rozhraní. Toto cvičení obvykle vede k nějakému přepracování, který ponechá součást mnohem více oddělenou a snadno se oddělit od ostatních vašich návrhů.

 Výhodou tohoto odkládání je, že komponentu lze spustit pro testování nahrazením objekty typu, které obvykle používá. Jedná se o komponenty, které jsou nastaveny pro účely testování. Přípravou součást poskytuje rozhraní, které vaše komponenta vyžaduje, a reaguje na dotazy se simulovanými daty. Naformátované komponenty tvoří součást kompletního testovacího svazku, který se můžete připojit ke všem rozhraním komponenty.

 Výhodou takového testování je, že můžete vyvíjet komponentu, zatímco ostatní komponenty, jejichž služby se budou používat, jsou stále ve vývoji.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Udržování vztahů mezi testy a modelem
 V typickém projektu, který provádí iteraci každé pár týdnů, se na začátku každé iterace podrží revize požadavků. Schůzka se zabývá funkcemi, které se mají doručit v další iteraci. Model požadavků se dá použít k pojednání o konceptech, scénářích a sekvencích akcí, které se budou vyvíjet. Obchodní účastníci nastavili priority, vývojáři vytvářejí odhady a testeri ověří, že očekávané chování jednotlivých funkcí je správně zachyceno.

 Psaní testů je nejúčinnější způsob, jak definovat požadavek, a je také účinný způsob, jak zajistit, aby osoba měla jasné porozumění tomu, co je potřeba. Vzhledem k tomu, že během specifikace dílny trvá zápis testů příliš dlouho, vytváření modelů je možné provést mnohem rychleji.

 Z hlediska testování je možné model požadavků zobrazit jako zkrácený pro testy. Proto je důležité udržovat vztah mezi testy a modelem v celém projektu.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Připojení testovacích případů k prvkům modelu
 Pokud váš projekt používá [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] , můžete propojit testy s prvky v modelu. To vám umožní rychle najít testy ovlivněné změnou požadavků a pomůže vám sledovat rozsah, do kterého byl požadavek realizován.

 Testy můžete propojit se všemi druhy prvků. Tady je několik příkladů:

- Propojit případ použití s testy, které ji vykonávají.

- Zapište klauzule případu použití následná podmínka nebo cíl, do komentářů, které jsou propojeny s případem použití, a pak propojte testy s každým komentářem.

- Zapište invariantní pravidla v komentářích k diagramům tříd nebo diagramům aktivit a propojte je s testy.

- Propojte testy s diagramem činnosti nebo jednotlivými aktivitami.

- Propojte sadu testů s komponentou nebo podsystémem, který testuje testy.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Propojení testů s prvkem modelu nebo vztahu

1. V portálu [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] vytvořte požadavek a založte na něm testovací sadu.

    Požadavek, který vytvoříte, je pracovní položka v [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] . Může to být uživatelský scénář, požadavek nebo pracovní položka případu použití, v závislosti na šabloně procesu, kterou projekt používá s Team Foundation. Další informace najdete v tématu [o agilních nástrojích a agilních řízeních projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts).

2. Propojte pracovní položku požadavku s jedním nebo více prvky v modelu.

    V diagramu modelování klikněte pravým tlačítkem myši na prvek, komentář nebo vztah a pak klikněte na **odkaz na pracovní položku**.

3. Přidejte do testovací sady, testovací případy, které ověřují požadavek vyjádřený v prvku modelu.

## <a name="see-also"></a>Viz také

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)
- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)
