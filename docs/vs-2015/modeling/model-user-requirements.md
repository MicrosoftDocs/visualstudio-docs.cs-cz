---
title: Požadavky na model uživatele | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d70a7c8b7dbf6015e992cfabb5204f3b307238a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844919"
---
# <a name="model-user-requirements"></a>Modelování uživatelských požadavků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio vám pomůže pochopit, diskutovat a sdělovat potřeby vašich uživatelů vykreslením diagramů o jejich aktivitách a části vašeho systému, který pomáhá dosahovat svých cílů. Model požadavků je sada těchto diagramů, z nichž každá se zaměřuje na jiný aspekt potřeb uživatelů. Ukázku videa najdete v tématu [modelování obchodní domény](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

 Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé typy modelů, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Model požadavků vám pomůže:

- Soustřeďte se na externí chování systému, a to odděleně od jeho interního návrhu.

- Popište požadavky uživatelů a zúčastněných stran s mnohem menší nejednoznačnější, než můžete v přirozeném jazyce.

- Definujte konzistentní Glosář termínů, které mohou používat uživatelé, vývojáři a testery.

- Snižte mezery a nekonzistence v požadavcích.

- Zmenšete práci potřebnou k reakci na změny požadavků.

- Naplánujte pořadí, ve kterém budou funkce vyvíjeny.

- Použijte modely jako základ pro systémové testy a vytvořte tak jasný vztah mezi testy a požadavky. Když se požadavky změní, tento vztah vám pomůže správně aktualizovat testy. Tím se zajistí, že systém splňuje nové požadavky.

  Model požadavků poskytuje nejvyšší výhody, pokud ho používáte k zaměření diskusí s uživateli nebo jejich zástupci a na začátku každé iterace. Před psaním kódu ho nemusíte podrobně doplňovat. Částečně funkční aplikace, a to i v případě, že je velmi zjednodušená, všeobecně tvoří základ pro diskuzi o požadavcích s uživateli. Model představuje efektivní způsob sumarizace výsledků těchto diskusí. Další informace najdete v tématu [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> V těchto tématech "systém" znamená systém nebo aplikaci, kterou vyvíjíte. Může se jednat o velkou kolekci mnoha softwarových a hardwarových komponent. nebo jedna aplikace; nebo softwarová součást v rámci většího systému. V každém případě model požadavků popisuje chování, které je viditelné mimo váš systém bez ohledu na to, jestli jde o uživatelské rozhraní nebo rozhraní API.

## <a name="common-tasks"></a>Běžné úkoly
 Můžete vytvořit několik různých zobrazení požadavků uživatelů.  Každé zobrazení poskytuje konkrétní typ informací.  Když vytváříte tato zobrazení, je nejlepší je často přesunout z jedné do druhé. Můžete začít z libovolného zobrazení.

|Diagram nebo dokument|Jak popisuje model požadavků|Část|
|-------------------------|-----------------------------------------------|-------------|
|Použití diagramu případu|Kdo používá systém a co s ním dělat.|[Popis způsobu použití systému](#UseCases)|
|Diagram koncepční třídy|Glosář typů, které se používají k popisu požadavků; typy viditelné v rozhraní systému.|[Definování podmínek používaných k popisu požadavků](#RequirementsClasses)|
|Diagram činnosti|Tok práce a informace mezi aktivitami prováděnými uživateli a systémem nebo jeho částmi.|[Zobrazuje se pracovní postup mezi uživateli a vaším systémem.](#Workflow)|
|Sekvenční diagram|Sekvence interakcí mezi uživateli a systémem nebo jeho částmi. Alternativní zobrazení diagramu činnosti.|[Zobrazení interakcí mezi uživateli a systémem](#Sequences)|
|Další dokumenty nebo pracovní položky|Kritéria pro výkon, zabezpečení, použitelnost a spolehlivost.|[Popisující požadavky na službu Quality of Service](#QoSRequirements)|
|Další dokumenty nebo pracovní položky|Omezení a pravidla nespecifická pro konkrétní případ použití|[Zobrazení obchodních pravidel](#BusinessRules)|

 Všimněte si, že většinu typů diagramů lze použít pro jiné účely. Přehled typů diagramů najdete v tématu [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md). Základní informace o diagramech kreslení najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="UseCases"></a>Popis způsobu použití systému
 Vytvářejte diagramy případů použití, abyste popsali, kdo používá systém a k čemu ho používají. Případ použití představuje cíl uživatele systému a postup, který provádí k dosažení tohoto cíle.

 Například systém pro online stravování musí zákazníkům dovolit, aby si z nabídky zvolili položky, a musí dovolit restauracím aktualizovat nabídku. To můžete shrnout v diagramu případu použití:

 ![Případy použití pro zákazníky a restaurace](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Můžete také zobrazit, jak se případ použití skládá z menších případů. Například řazení moučky je součástí nákupu moučky, která zahrnuje také platby a doručování:

 ![Systém se účastní platby, ale neposkytuje doručení.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Můžete také zobrazit, které případy použití jsou zahrnuty v oboru systému, který vyvíjíte. Například systém na ilustraci se nepodílí na případu použití v rámci služby Delivery moučky. To pomáhá nastavit kontext pro vývojovou práci. (V diagramu případu použití lze kontejnery subsystémů použít k reprezentaci systému nebo jeho součástí.)

 Pomáhá týmu také diskutovat o tom, co bude zahrnuto v po sobě následujících verzích. Můžete například diskutovat, jestli v počáteční verzi systému platí, že se platíte za moučku přímo mezi restaurace a zákazníkem, a ne přes systém. V takovém případě můžete pro počáteční verzi přesunout platbu za moučku mimo rámec systému večeře Now.

 Diagram případu použití poskytuje pouze souhrn případů použití. Chcete-li zadat podrobnější popis, můžete propojit případy použití v diagramu k oddělení dokumentů a dalším diagramům. Další informace o tom, jak to provést, najdete v tématu [propojení případu použití s dokumenty a diagramy](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Vykreslení diagramu případu použití pomáhá vašemu týmu:

- Zaměřte se na to, co uživatelé očekávají se systémem, aniž by se museli odvolávat podrobnostmi implementace.

- Prodiskutujte rozsah systému nebo konkrétní verze systému.

  Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Podrobnější informace o tom, jak vytvořit případy použití|[Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|
|Prvky v diagramu případu použití|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|
|Postup vývoje kódu z případů použití|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="RequirementsClasses"></a>Definování podmínek používaných k popisu požadavků
 Diagramy tříd UML můžete použít k vytvoření konzistentního slovníku obchodních konceptů používaných pro následující účely:

- Vlastními uživateli projednávat podnikání, ve kterém systém pracuje.

- K popisu potřeb uživatelů, například v popisech případů použití, obchodních pravidel a uživatelských scénářů.

- Typy informací, které jsou vyměňovány v rozhraní API systému nebo prostřednictvím uživatelského rozhraní.

- Popisy systémových nebo přijímacích testů.

  Při použití k tomuto účelu se obsah diagramu tříd UML nazývá diagram koncepční třídy. (Označuje se také jako model *domény* nebo *model třídy analýzy*.)

  V diagramu koncepční třídy zobrazíte pouze ty třídy, které jsou potřeba v popisech požadavků, a to bez zobrazení jakýchkoli podrobností interního návrhu systému. Diagram nezobrazuje žádné podrobnosti interního návrhu systému. Nebudete obvykle zobrazovat operace nebo rozhraní pro koncepční třídy.

  Například můžete vykreslit tyto koncepční třídy pro systém večeře Now:

  ![Nabídka třídy, pořadí, položka nabídky, položka objednávky.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Diagram koncepční třídy poskytuje slovní druh termínů, které můžete použít v rámci modelu požadavků. Například v podrobném popisu objednávky případu použití můžete napsat:

  Zákazník zvolí *nabídku* , ze které *se má vytvořit* *objednávka*, a pak v *nabídce*vytvoří *položky objednávek* kliknutím na *položku nabídky* .

  Všimněte si, jak jsou výrazy používané v tomto popisu názvy tříd v modelu. Diagram odstraňuje nejednoznačnosti z vztahů mezi těmito třídami. Zobrazuje se například jasně, že je každá objednávka přidružená pouze k jedné nabídce.

  Nesrozumitelnější požadavky uživatelů je často možné trasovat tak, aby nerozuměly podrobným významům slov. Například většina restaurací bude mít sdílený význam nabídky podmínek a objednávek, ale rozdíl mezi položkou v objednávce a položkou v nabídce je méně jasný. V případě, že jsou požadavky popsány u obchodních účastníků, je důležité tyto rozdíly zveřejnit. Diagram tříd je užitečný nástroj, který vám může pomoct objasnit výrazy a jejich vztahy.

  Model koncepční třídy může tvořit základní slovník, podle kterého lze popsat obchodní logiku systému. Avšak třídy v softwaru budou obvykle mnohem složitější než koncepční model, protože implementace musí brát v úvahu problémy, jako je například výkon, distribuce, flexibilita a další faktory. Několik různých implementací koncepční třídy je často nalezeno v jednom systému.

  Například objednávky mohou být reprezentovány v jazyce XML, SQL, HTML a C# v různých částech systému a v různých rozhraních mezi částmi. Přidružení mezi objednávkou a nabídkou může představovat mnoho různých způsobů, jako jsou například odkazy v rámci C# kódu, relace v databázi nebo ID křížového odkazu v XML. I přes tyto odchylky poskytují koncepční model důležité informace, které jsou v každé části softwaru pravdivé. Diagram tříd v příkladu oznamuje, že v každé implementaci bude k jednotlivým objednávkám přidružena pouze jedna nabídka.

  Vykreslení diagramu tříd požadavků pomáhá týmu:

- Definujte a standardizacte základní výrazy používané při diskusích o potřebách uživatelů.

- Vyjasněte vztahy mezi těmito podmínkami.

  Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Podrobnější informace o hledání tříd požadavků|[Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Prvky v diagramu koncepční třídy|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|
|Vývoj kódu z koncepčních tříd|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

 V diagramu koncepční třídy není obvykle vhodné umístit šipky na přidružení, aby představovaly schopnost navigace. Důvodem je, že diagram nepředstavuje implementaci. Asociace představuje vztahy mezi objekty reálného světa. Následující rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nastaví nesměrující se šipky výchozí: [Ukázka: funkce modelování domén UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples).

## <a name="BusinessRules"></a>Zobrazení obchodních pravidel
 Obchodní pravidlo je požadavek, který není přidružený k určitému případu použití, a měl by být pozorován v celém systému.

 Mnoho obchodních pravidel je omezení pro vztahy mezi koncepčními třídami. Tato *statická obchodní pravidla* můžete zapsat jako komentáře přidružené k příslušným třídám v diagramu koncepční třídy. Příklad:

 ![Pravidlo v komentáři připojené ke třídě Order](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 *Dynamická obchodní pravidla* omezí možné posloupnosti událostí. Například můžete použít diagram sekvence nebo aktivity k zobrazení, že se uživatel musí přihlásit před provedením dalších operací v systému.

 Mnoho dynamických pravidel ale může být efektivnější a obecně řečeno jejich nahrazením statickými pravidly. Například můžete přidat logický atribut "přihlášen" do třídy v modelu koncepční třídy. Přidali jste přihlášeni jako následná podmínka v případu použití protokolu a přidáte ho jako podmínku pro většinu ostatních případů použití. Tento přístup vám umožní vyhnout se definování všech možných kombinací posloupnosti událostí. Je také pružnější, pokud pro model potřebujete přidat nové případy použití.

 Všimněte si, že zvolený postup je o tom, jak definujete požadavky a že je nezávisle na tom, jak implementujete požadavky v kódu programu.

 Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Podrobnější informace o hledání a záznamu statických obchodních pravidel|[Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Prvky v diagramu koncepční třídy|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|
|Postup vývoje kódu, který dodržuje obchodní pravidla|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="QoSRequirements"></a>Popisující požadavky na službu Quality of Service
 Existuje několik kategorií požadavků na kvalitu služeb. Mezi tyto typy patří:

- Výkon

- Zabezpečení –

- Použitelnost

- Spolehlivost

- Robustnost

  Některé z těchto požadavků můžete zahrnout do popisu konkrétního případu použití. Jiné požadavky nejsou specifické pro případy použití a jsou efektivně napsány v samostatném dokumentu. Když můžete, je vhodné dodržovat slovník definovaný modelem požadavků. V následujícím příkladu si všimněte, že hlavní slova použitá v požadavku jsou názvy objektů Actor, případy použití a třídy v předchozí ilustraci:

  Pokud restaurace odstraní položku nabídky, když zákazník seřazení moučky, položka objednávky, která odkazuje na tuto položku nabídky, se zobrazí červeně.

  Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Připojení dalších dokumentů k případům použití|[Propojení případu použití s dokumenty a diagramy](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Postup vývoje kódu, který dodržuje požadavky na kvalitu služeb|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="Workflow"></a>Zobrazuje se pracovní postup mezi uživateli a vaším systémem.
 Diagram aktivity můžete použít k zobrazení toku práce mezi různými případy použití. Je často vhodné začít model požadavků vykreslením diagramu činností, který znázorňuje hlavní úkoly, které uživatelé provádějí – v systému i mimo něj.

 Příklad:

 ![Aktivita se třemi akcemi a smyčkou.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Můžete nakreslit diagramy případů použití a diagramy aktivit k zobrazení různých zobrazení stejných informací.  Diagram případu použití je efektivnější při zobrazení vnořování menších akcí v rámci větší aktivity, ale nezobrazuje tok práce. Příklad:

 ![Případy použití pro předchozí akce](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Všimněte si, že můžete také použít diagramy aktivit k zobrazení algoritmů v rámci vašeho softwaru, ale když použijete diagramy pro obchodní proces, zaměříte se na akce, které jsou viditelné mimo systém.

 Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Další informace o tom, jak definovat pracovní toky|[Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|
|Prvky v diagramu činnosti|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|
|Vývoj kódu z diagramů činností|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="Sequences"></a>Zobrazení interakcí mezi uživateli a systémem
 Sekvenční diagram můžete použít k zobrazení výměny zpráv mezi systémem a externími aktéry nebo mezi částmi systému. To poskytuje zobrazení kroků v případu použití, které znázorňují jasně sekvenci interakcí. Sekvenční diagramy jsou užitečné hlavně v případě, že je v případu použití několik vzájemně komunikujících stran a také v případě, kdy má váš systém rozhraní API.

 Příklad:

 ![Sekvenční diagram se systémem a objekty Actors.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Jednou z výhod sekvenčních diagramů je, že je snadné zjistit, jaké zprávy přicházejí do systému, který vytváříte. Chcete-li navrhnout systém, můžete nahradit jedinou životnost systému samostatným životností pro každou jeho součást a pak zobrazit interakce mezi nimi v reakci na každou příchozí zprávu.

 Další informace najdete v následujících tématech:

|Další informace|Číst|
|--------------------|----------|
|Další informace o tom, jak definovat interakce|[Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Prvky v sekvenčním diagramu|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|
|Postup vývoje kódu z sekvenčních diagramů|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Snížení nekonzistencí pomocí modelu
 Vytvoření modelu obvykle vede k výraznému snížení nekonzistencí a nejednoznačnosti v požadavcích uživatelů. Různí účastníci mají často různé porozumění obchodnímu světě, ve kterém systém pracuje. Proto je vaším prvním úkolem vyřešit tyto rozdíly mezi vašimi klienty.

 Zjistíte, že mnohé otázky týkající se obchodní domény vzniknou přirozeně při vytváření modelu. Vložením těchto otázek uživatelům omezíte potřebu změn v pozdější fázi projektu. Tady jsou některé konkrétní otázky, které si můžete nejdřív zeptat a pak pokládat zúčastněným účastníkům, pokud odpověď není jasná:

- Pro každou třídu v modelu požadavků požádejte ", který případ použití vytvoří instance této třídy?" Například v online službě pro objednávání se můžete zeptat, jaký případ použití vytvoří instance třídy nabídky restaurace?. To by vedlo k diskusi o tom, jak je nová restaurace zaregistrovaná do služby, a přispívání do příslušné nabídky. Můžete klást podobné otázky ohledně toho, co vytváří nebo mění atributy a přidružení.

- Pro každý případ použití v modelu požadavků se pokuste popsat výsledek nebo následná podmínka každého případu použití ve slovech poskytovaných diagramy tříd. Je často užitečné zobrazit efekt případu použití pomocí náčrtace instancí tříd před a po výskytu případu použití. Například pokud se v případu použití následná podmínka říká, že se položka nabídky přidá do objednávky zákazníka, "instance skicy tříd objednávek a položek nabídky. Zobrazení efektů případu použití, jako je například nový odkaz nebo nový objekt, v jiné barvě nebo v novém výkresu. To často vede k diskusi o tom, jaké informace jsou v modelu nutné. I když se třídy požadavků přímo netýkají implementace, popisují informace, které bude systém potřebovat pro uložení a přenos.

- Zeptejte se omezení atributů a přidružení, zejména omezení týkajících se více než jednoho atributu nebo asociace.

- Seznamte se s platnými a neplatnými sekvencemi případů použití, diagramů sekvence nebo diagramů aktivit k jejich ilustraci.

  Prozkoumáním vztahů mezi zobrazeními, které různé diagramy poskytují, můžete rychle porozumět hlavním koncepcím, se kterými uživatelé pracují, a pomáhat jim pochopit, co potřebují ze systému. Také se dostanete k lepšímu porozumění požadavkům, o které mají účastníci aspoň určité informace. Můžete naplánovat vývoj těchto funkcí, alespoň ve zjednodušené podobě, v rané fázi projektu, a dovolit uživatelům experimentovat s nimi.

## <a name="see-also"></a>Viz také
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [vyvíjejí testy z modelu](../modeling/develop-tests-from-a-model.md) [použití modelů v modelu procesu vývoje](../modeling/use-models-in-your-development-process.md) [](../modeling/model-your-app-s-architecture.md) [. Ukázka vs Extension: funkce Modelování domény UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [Ukázka vs: barva prvků UML podle typu stereotypu](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) vs. rozšíření: [propojte elementy UML s diagramy, soubory a dalšími prvky](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [Ukázka vs Extension: zarovnání obrazců na video diagramu UML](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [: modelování obchodní domény](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
