---
title: Vývoj testů z modelu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e1fd3b1cd19efa9032b7b92576a489e3b17373db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919328"
---
# <a name="develop-tests-from-a-model"></a>Vývoj testů z modelu
Požadavky a architektury modely můžete pomoci vám organizovat testy systému a jeho součástí. Tento postup pomáhá zajistit, že testování požadavků, které jsou důležité pro uživatele a další zainteresované uživatele, a pomůže vám rychle aktualizovat testů při změně požadavků. Pokud používáte [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], můžete také zachovat propojení mezi modely a testy.

 Které verze sady Visual Studio podporují tyto funkce najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Systému a subsystému testování
 *Systémové testování,* označované také jako *akceptační testování*, testování, zda byly splněny požadavky uživatelů prostředky. Tyto testy, které jsou zajímá externě viditelného chování systému namísto vnitřního návrhu.

 Systémové testy jsou velmi užitečné, když rozšíření nebo změna návrhu systému. Mohou pomoci vyhnout vzniku chyb při změně kódu.

 Pokud máte v úmyslu změnit ani rozšíření do systému, je užitečné začít se sadou systémové testy, které běží ve stávajícím systému. Potom můžete rozšířit nebo upravit testy pro nové požadavky na testovací, proveďte požadované změny pro kód a znovu spusťte kompletní sadu testů.

 Při vývoji nového systému můžete začít ihned vývoj vytvořit testy. Definováním testů předtím, než při vývoji jednotlivých funkcí, můžete zachytit požadavky na diskuse velmi určitým způsobem.

 Subsystém testování platí stejné zásady pro hlavní součásti systému. Jednotlivé komponenty se testovali odděleně od jiných komponent. Subsystém testuje zaměřit se na chování viditelné v součásti uživatelského rozhraní nebo rozhraní API.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Odvozování systémových testů z modelu požadavky
 Můžete vytvořit a Udržovat vztah mezi testy systému a model požadavků. K navázání tohoto vztahu, psaní testů, které odpovídají hlavních prvků model požadavků. Visual Studio pomáhá udržovat relace umožňují vytvářet propojení mezi testy a součástí modelu. Další informace o modelech požadavky najdete v části [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Zápis testů pro každý případ použití
 Pokud používáte [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], můžete vytvořit skupinu testů pro každý případ použití, který jste definovali ve vašem modelu požadavky. Například pokud máte případu použití objednávka jídla, která zahrnuje vytvoření objednávky a přidat položku pořadí, můžete vytvořit testy pro obě celkové a podrobnější tyto případy použití.

 Tyto pokyny mohou být užitečné:

-   Každý případ použití by měl mít několik testů pro hlavní cesty a mimořádných výsledků.

-   Když popíšete případ použití v modelu požadavky, je důležitější k definování jeho neplatná následná, to znamená, cíl, který je dosaženo, než k podrobnému popisu, postupy uživatel sleduje, aby bylo možné dosáhnout. Neplatná následná objednávky pokrmu může být například, který restaurace připravuje pokrmu zákazníka a že má zákazník zaplatí. Neplatná následná je kritérium, které testy by měly ověřit.

-   Základní samostatných testů na samostatné klauzulí neplatná následná. Například vytvořte samostatné testy pro oznamování restaurace pořadí a pro provádění platby od zákazníka. Toto oddělení má tyto výhody:

    -   Změny v různých aspektů požadavky dochází často nezávisle na sobě. Oddělením testů na různé aspekty tímto způsobem můžete usnadnit Neaktualizovat testy při změně požadavků.

    -   Pokud plán vývoje implementuje jeden aspekt jejich případu použití dříve než jiné, můžete povolit testy samostatně v průběhu vývoje.

-   Při návrhu testy oddělte od kódu nebo skript, který určuje, zda bylo dosaženo neplatná následná volba testovací data. Například může být zkoušku jednoduchou funkci aritmetické: vstup 4; Ověřte, zda výstup je 2. Místo toho navrhnout skript jako: Zvolte vstupní; vynásobit výstup samostatně a ověřte, že výsledek je původní vstup. Tento styl umožňuje měnit testovací vstupy beze změny hlavní části testu.

#### <a name="linking-tests-to-use-cases"></a>Propojení testy s případy použití
 Pokud používáte [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] k navrhování a spuštění testů, můžete uspořádat testy v rámci požadavků, případu použití nebo uživatelské scénáře pracovních položek. Můžete propojit tyto pracovní položky s případy použití v modelu. To vám umožní rychle trasování požadavky na změny na testy a umožňuje sledovat průběh každého případu použití.

###### <a name="to-link-tests-to-a-use-case"></a>Propojení případu použití testy

1. V [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], vytvořit požadavek a základní sadu testů v něm.

    Je požadavek, který vytvoříte pracovní položku v [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Může to být uživatelský scénář, požadavek nebo případ použití pracovní položky, v závislosti na šabloně procesu, který váš projekt používá s Team Foundation. Další informace najdete v tématu [o agilní nástroje a agilní řízení projektů](/azure/devops/boards/backlogs/overview?view=vsts).

2. Propojte pracovní položky požadavku na jeden nebo více případy použití v modelu.

    Diagram případu použití, klikněte pravým tlačítkem na případu použití a pak klikněte na **odkaz na pracovní položku**.

3. Přidejte do testovací sady, testovací případy, které ověřují případy použití.

   Obvykle každé uživatelské scénáře nebo požadavky pracovní položky se propojit několik případů použití ve vašem modelu a každý případ použití se propojit s několika uživatelské scénáře nebo požadavky. Je to proto, že každý uživatelský scénář nebo požadavek zahrnuje sadu úloh, které vývoj několik případů použití. V rané fázi iterace projektu, byste třeba vytvořit základní uživatelský scénář, ve kterém můžete vybrat položky z katalogu a ho doručit zákazník. V pozdější iterace může být sdělení, že uživatel platí při dokončení pořadí a dodavatel obdrží peněz po odešle zboží.  Každý scénář přidá klauzuli neplatná následná případu použití pořadí zboží.

   Můžete vytvořit samostatné odkazy z požadavky do klauzule neplatná následná napsáním těchto klauzulí v samostatných komentáře na diagramu případu použití. Můžete každý komentář k propojení s pracovní položkou požadavku a propojit komentář v diagramu případu použití.

### <a name="base-tests-on-the-requirements-types"></a>Základní testy na typy požadavků
 Typy, které je, třídy, rozhraní a výčty, požadavky na modelu popisují koncepty a vztahy z hlediska jak myslíte, že uživatelé a komunikovat o své firmě. Vyloučí typy týká pouze interních návrhu systému.

 Návrh testy z hlediska tyto typy požadavků. Tento postup vám pomůže zajistit, že když jsou popsány změny požadavky, je snadné se vztahují změny potřebné změnám v testech. To umožňuje prodiskutovat testy a jejich zamýšlený výsledky přímo s koncovým uživatelům a další zainteresované uživatele. To znamená, že uživatelů potřebuje lze udržovat mimo proces vývoje a zabraňuje nechtěnému návrhu testy kolem možné chyby v návrhu.

 U ručních testů zahrnuje tento postup týkajícími se slovník model požadavků v testovacích skriptech. Pro automatizované testy zahrnuje tento postup pomocí diagramů tříd požadavky jako základ pro váš testovací kód a vytvoření přístupového objektu a aktualizační funkce k propojení požadavků modelu kódu.

 Například požadavky, které mohou zahrnovat model typy nabídek, položka nabídky, pořadí a přidružení mezi nimi. Tento model představuje informace, které je uložený a řešil jídla systém objednávek, ale nepředstavuje složitosti jeho implementace. V systému práci může být několik různých realizations každého typu v databázích, v uživatelských rozhraní a rozhraní API. V distribuovaném systému může být několik variant každé instance uložená v různých částí systému ve stejnou dobu.

 K otestování případu použití, jako je například přidat položku pořadí, testovací metoda může obsahovat kód podobný tomuto:

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

 Všimněte si, že tato testovací metoda používá třídy model požadavků. Přidružení a atributy jsou realizovány jako vlastnosti rozhraní .NET.

 Chcete-li tuto práci, vlastnosti třídy musí být definován jako funkce jen pro čtení nebo přístupové objekty, které potřebují přístup k systému k načtení informací o aktuálním stavu. Metody, které simulují případy použití, jako například AddItemToOrder musí řídit systému prostřednictvím jejího rozhraní API nebo vrstvy pod jeho uživatelské rozhraní. Konstruktory test objektů, jako jsou například objednávka a položka nabídky musí také využívat systém k vytvoření odpovídající položky v systému.

 Přístupové objekty a operace Updater již bude k dispozici prostřednictvím rozhraní API normální aplikace. Ale některé další funkce může mít k zapsání Chcete-li povolit testy. Tyto dodatečné přístupové objekty a operace Updater jsou někdy označovány jako 'test instrumentace'. Protože jsou závislé na interní návrhu systému, je odpovědností vývojáře v systému a umožnit jim, že testeři psát kód testy z hlediska model požadavků.

 Při psaní automatizované testy můžete zabalit přístupové objekty a operace Updater obecné testy.

### <a name="tests-for-business-rules"></a>Testy pro obchodní pravidla
 Některé požadavky přímo nesouvisí žádné jeden případ použití. Například obchodní DinnerNow umožňuje zákazníkům vybrat z mnoha nabídky, ale vyžaduje, aby každý mohl, všechny zvolené položky musí být v jediné nabídce. Toto obchodní pravidlo může být vyjádřený jako invariantní o přidružení mezi příkazy, nabídky a položky v třídě modelu požadavky.

 Výchozí pravidlo tohoto druhu se řídí nejen všechny případy použití, které jsou aktuálně definován, ale také všechny ostatní případy použití, které bude obsahovat definici později. Proto je užitečné pro zápis odděleně od případ použití a otestovat samostatně z případů využití.

## <a name="deriving-subsystem-tests-from-models"></a>Odvozování testy subsystému z modelů
 V návrhu vysoké úrovně v rozsáhlém systému je určit, komponenty nebo subsystémů. Představují části, které může být navržena samostatně, nebo jsou umístěné na různých počítačích nebo jsou opakovaně použitelné moduly, které mohou být rekombinované mnoha způsoby.

 Můžete použít pro každou hlavní součást stejné zásady používání pro celý systém. Ve velkých projektech Každá komponenta může mít svůj vlastní model požadavků. V projektech pro menší Architektonický model nebo hlavnímu návrhu vytvořit zobrazíte hlavní součásti a jejich interakce. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).

 V obou případech můžete vytvořit vztah mezi prvků modelu a testy subsystému stejným způsobem, jako byste mezi modelem požadavky a testy systému.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izolace komponenty s poskytovaných a požadovaných rozhraní
 Slouží k identifikaci všechny závislosti, které má součást na ostatní části systému nebo externími službami a k reprezentaci jako požadované rozhraní. V tomto cvičení se obvykle vede k některé přepracování, které se zasílají součást dalšího oddělení a snadno oddělit od zbývající části návrhu.

 Výhodou díky tomuto oddělení je, že komponenty mohou být provedeny pro testování nahrazením mock objektů služby, které se obvykle používá. Toto jsou komponenty, které jsou nastavené pro účely testování. Komponentu mock poskytuje rozhraní, která vyžaduje vaše komponenta odpovídá na dotazy s Simulovaná data. Součástí dokončení testovacího prostředí, se můžete připojit na všechna rozhraní komponenty mock komponenty.

 Výhodou mock testování je, že vám umožní vytvářet vaše komponenta při další komponenty, jejichž služby se bude používat jsou stále ve vývoji.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Údržbu relací mezi testy a Model
 V typickém projektu, který provádí iteraci každých několik týdnů Zkontrolujte požadavky se nachází na začátku každé iterace. Schůzky popisuje funkce, které se doručí do další iterace. Model požadavků lze pomoci diskutovat o koncepty, scénáře a pořadí z akcí, které budou vytvořeny. Zúčastněné obchodní strany priority nastavit, vývojář podá odhady a testeři Ujistěte se, že očekávané chování jednotlivých funkcí jsou zachyceny správně.

 Zápis testů je nejúčinnější způsob, jak definovat požadavek a je také účinný způsob, jak zajistit, že v osoba jistotou určit, co je potřeba. Ale že psaní testů trvá příliš dlouho udělat během seminář o specifikace, vytváření modelů můžete udělat mnohem rychleji.

 Z testování pohledu se dají považovat za zkratka pro testy model požadavků. Proto je důležité zachovat vztah mezi testy a modelu v celém projektu.

## <a name="Attaching"></a> Připojení testovací případy k elementům modelu
 Pokud váš projekt používá [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], testy můžete propojit s prvky v modelu. To vám umožní rychle najít testy ovlivněné změnou v požadavcích a umožňuje sledovat v rozsahu, do které byl proveden požadavek.

 Testy můžete propojit všechny druhy elementu. Následuje několik příkladů:

-   Propojení případu použití s testy výkonu.

-   Zápis klauzule neplatná následná případu použití, nebo cílem, do komentářů, které jsou propojeny s případu použití a propojit testy se všechny komentáře.

-   Zápis invariantní pravidla v komentářích v diagramech tříd nebo diagramy činnosti a propojují se s testy.

-   Propojit testy do diagramu činnosti nebo do jednotlivých aktivit.

-   Součásti či subsystém, který ověřuje propojte testovací sady.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Propojení prvku modelu nebo vztah testy

1. V [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], vytvořit požadavek a základní sadu testů v něm.

    Je požadavek, který vytvoříte pracovní položku v [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Může to být uživatelský scénář, požadavek nebo případ použití pracovní položky, v závislosti na šabloně procesu, který váš projekt používá s Team Foundation. Další informace najdete v tématu [o agilní nástroje a agilní řízení projektů](/azure/devops/boards/backlogs/overview?view=vsts).

2. Propojte pracovní položky požadavku na jeden nebo více prvků ve vašem modelu.

    V diagramu modelování, klikněte pravým tlačítkem na elementu, komentáře nebo relaci a potom klikněte na **odkaz na pracovní položku**.

3. Přidejte do testovací sady, testovací případy, které ověřují požadavek vyjádřené v elementu modelu.

## <a name="see-also"></a>Viz také

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)
- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)
