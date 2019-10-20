---
title: Modelování architektury aplikace&#39;| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41dbb7b996c32af10010694935cbd3660b462f73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609634"
---
# <a name="model-your-app39s-architecture"></a>Modelování architektury aplikace&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby bylo zajištěno, že váš softwarový systém nebo aplikace vyhovují potřebám vašich uživatelů, můžete vytvořit modely v aplikaci Visual Studio jako součást popisu celkové struktury a chování softwarového systému nebo aplikace. Pomocí modelů můžete také popsat vzory používané v celém návrhu. Tyto modely vám pomůžou pochopit stávající architekturu, diskutovat o změnách a jasně sdělit své záměry.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Účelem modelu je snížit nejednoznačnosti, ke kterým dochází v popisech v přirozeném jazyce, a pomáhat vám a vašim kolegům vizualizovat návrh a diskutovat o alternativních návrzích. Model by se měl používat společně s ostatními dokumenty nebo diskuzemi. Sám o sobě model nepředstavuje úplnou specifikaci architektury.

> [!NOTE]
> V celém tomto tématu označuje "systém" software, který vyvíjíte. Může se jednat o velkou kolekci mnoha softwarových a hardwarových komponent nebo o jednu aplikaci nebo součást aplikace.

 Architektura systému může být rozdělena do dvou oblastí:

- [Návrh vysoké úrovně](#Structure). To popisuje hlavní komponenty a jejich vzájemné vzájemné interakce ke splnění jednotlivých požadavků. Pokud je systém velký, může mít každá součást vlastní návrh vysoké úrovně, který ukazuje, jak se skládá z menších součástí.

- [Vzory](#Patterns) a konvence návrhu používané v rámci návrhů komponent. Vzor popisuje konkrétní přístup k dosažení cíle programování. Díky použití stejných vzorů v rámci návrhu může váš tým snížit náklady na provádění změn a vývoj nového softwaru.

## <a name="Structure"></a>Návrh na nejvyšší úrovni
 Návrh vysoké úrovně popisuje hlavní součásti systému a způsob, jak vzájemně komunikují, abyste dosáhli cílů návrhu. Aktivity v následujícím seznamu jsou zapojeny do vývoje vysoké úrovně návrhu, přestože nejsou nutně v konkrétní posloupnosti.

 Pokud aktualizujete existující kód, můžete začít tím, že popisujete hlavní součásti. Ujistěte se, že rozumíte jakýmkoli změnám požadavků uživatelů a pak přidáte nebo upravíte interakce mezi komponentami. Pokud vyvíjíte nový systém, začněte tím, že budete rozumět hlavním funkcím potřeb uživatelů. Pak můžete prozkoumat posloupnosti interakcí pro hlavní případy použití a potom sloučit sekvence do návrhu komponent.

 V každém případě je vhodné vyvíjet různé aktivity paralelně a vyvíjet kód a testy v rané fázi. Vyhněte se pokusu o dokončení některého z těchto aspektů předtím, než začnete s jiným. Při psaní a testování kódu se obvykle změní jak požadavky, tak i vaše porozumění nejlepšímu způsobu návrhu systému. Proto byste měli začít pochopením a kódováním hlavních funkcí požadavků a návrhu. Vyplňte podrobnosti v pozdějších iteracích projektu.

- [Principy požadavků](#Requirements). Výchozím bodem jakéhokoli návrhu je jasné porozumění potřebám uživatelů.

- [Modely architektury](#BigDecisions). Volby, které jste provedli na základních technologiích a prvcích architektury systému.

- [Komponenty a jejich rozhraní](#Components). Můžete nakreslit diagramy komponent a zobrazit tak hlavní části systému a zobrazit rozhraní, přes která vzájemně komunikují. Rozhraní každé součásti obsahují všechny zprávy, které jste identifikovali v sekvenčních diagramech.

- [Interakce mezi komponentami](#Interactions). Pro každý případ použití, událost nebo příchozí zprávu můžete nakreslit sekvenční diagram, který ukazuje, jak hlavní součásti systému spolupracují, aby dosáhli požadované odpovědi.

- [Datový model komponent a rozhraní](#Data). Můžete nakreslit diagramy tříd pro popis informací, které jsou předány mezi komponentami a uloženy v rámci komponent.

## <a name="Requirements"></a>Principy požadavků
 Nejdůležitější návrh kompletní aplikace je nejúčinnější vyvinutý spolu s modelem požadavků nebo jiným popisem potřeb uživatelů. Další informace o modelech požadavků najdete v článku [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

 Pokud je systém, který vyvíjíte, součástí většího systému, část nebo všechny vaše požadavky mohou být součástí programových rozhraní.

 Model požadavků poskytuje tyto podstatné informace:

- Poskytnutá rozhraní. Zadané rozhraní obsahuje seznam služeb nebo operací, které musí systém nebo součást poskytnout svým uživatelům, ať už se jedná o lidské uživatele nebo jiné softwarové komponenty.

- Požadovaná rozhraní. Požadované rozhraní obsahuje seznam služeb nebo operací, které může systém nebo komponenta používat. V některých případech budete moci navrhnout všechny tyto služby jako součást svého vlastního systému. V jiných případech, zejména pokud navrhujete komponentu, kterou je možné zkombinovat s jinými komponentami v mnoha konfiguracích, bude požadované rozhraní nastaveno externími požadavky.

- Požadavky na službu Quality of Service. Výkon, zabezpečení, odolnost a další cíle a omezení, které systém musí splňovat.

  Model požadavků se zapisuje z pohledu uživatelů vašeho systému, ať už jde o osoby nebo jiné softwarové součásti. Neznají žádná interní pracovní prostředí systému. Naopak vaším cílem v modelu architektury je popsat interní pracovní postupy a Ukázat, jak vyhovují potřebám uživatelů.

  Udržování požadavků a modelů architektury je užitečné, protože usnadňuje pojednání s požadavky uživatelů. Pomůže vám taky Refaktorovat návrh a vzít v úvahu alternativní architektury a zároveň zachovat požadavky beze změny.

  Požadavky a modely architektury můžete oddělit dvěma alternativními způsoby:

- Udržujte je ve stejném řešení, ale v různých projektech. Budou se zobrazovat jako samostatné modely v Průzkumníku modelů UML. Různí členové týmu mohou pracovat paralelně na modelech. Mezi modely lze vytvořit omezené druhy trasování.

- Umístěte je do stejného modelu UML, ale do různých balíčků. Díky tomu je snazší sledovat závislosti mezi modely, ale zabrání v tom, aby v modelu pracovala více než jedna osoba. Kromě toho velmi velký model bude trvat déle, než se načte do sady Visual Studio. Tento přístup je proto pro velké projekty méně vhodný.

  Množství podrobností, které byste měli umístit buď do požadavků, nebo do modelu architektury, závisí na rozsahu projektu a velikosti a rozdělení týmu. Malý tým v krátkém projektu může pokračovat bez vytváření náčrtů diagramu tříd obchodních konceptů a některých vzorů návrhu. velký projekt distribuovaný do více než jedné oblasti by vyžadoval podstatně více podrobností.

## <a name="BigDecisions"></a>Modely architektury
 V rané fázi vývoje musíte zvolit hlavní technologie a prvky, na kterých bude návrh záviset. Mezi oblasti, ve kterých se tyto volby musí udělat, patří následující:

- Výběr základních technologií, jako je například volba mezi databází a systémem souborů a volba mezi síťovou aplikací a webovým klientem atd.

- Volby rozhraní, jako je například volba mezi programovací model Windows Workflow Foundation nebo ADO.NET Entity Framework.

- Volby metod integrace, například mezi podnikovou sběrnicí nebo kanálem typu Point-to-Point.

  Tyto možnosti jsou často určeny požadavky na kvalitu služeb, jako je například škálování a flexibilita, a je možné je provést před známými podrobnými požadavky. V rozsáhlých systémech se konfigurace hardwaru a softwaru silně vzájemně souvisí.

  Volby, které provedete, budou mít vliv na způsob používání a interpretace modelu architektury. Například v systému, který používá databázi, může přidružení v diagramu tříd představovat vztahy nebo cizí klíče v databázi, zatímco v systému, který je založen na souborech XML, mohou přidružení značit křížové odkazy, které používají XPath. V distribuovaném systému mohou zprávy v sekvenčním diagramu představovat zprávy na lince. v samostatné aplikaci mohou představovat volání funkcí.

## <a name="Components"></a>Komponenty a jejich rozhraní
 Hlavní doporučení této části jsou následující:

- Vytvořte diagramy komponent pro zobrazení hlavních částí systému.

- Nakreslete závislosti mezi komponentami nebo jejich rozhraním, aby se zobrazila struktura systému.

- Pomocí rozhraní na komponentách můžete zobrazit služby, které jednotlivé komponenty poskytují nebo vyžadují.

- Ve velkém návrhu můžete nakreslit samostatné diagramy a rozložit jednotlivé komponenty na menší části.

  Tyto body jsou vypracované ve zbývající části této části.

### <a name="components"></a>Komponenty
 Centrální zobrazení modelu architektury jsou diagramy komponent, které zobrazují hlavní části systému a vzájemně závislé. Další informace o diagramech komponent najdete v tématu [diagramy komponent UML: referenční informace](../modeling/uml-component-diagrams-reference.md).

 ![Diagram komponenty UML znázorňující části](../modeling/media/uml-barecomponent.png "UML_BareComponent")

 Typický diagram komponent pro velký systém může obsahovat komponenty, jako jsou tyto:

- Vyjádření. Komponenta, která poskytuje přístup k uživateli, který je obvykle spuštěn ve webovém prohlížeči.

- Součásti webové služby. Poskytuje připojení mezi klienty a servery.

- Použijte řadiče případu. Provedete uživatele kroky každého scénáře.

- Obchodní jádro. Obsahuje třídy, které jsou založeny na třídách modelu požadavků, implementuje klíčové operace a ukládá obchodní omezení.

- Databáze. Ukládá obchodní objekty.

- Protokolování a zpracování chyb součástí.

### <a name="dependencies-between-components"></a>Závislosti mezi komponentami
 Kromě samotných komponent můžete zobrazit závislosti mezi nimi. Šipka závislosti mezi dvěma komponentami ukazuje, že změny v návrhu jednoho mohou ovlivnit návrh druhé. K tomu obvykle dochází, protože jedna součást používá služby nebo funkce, které jsou poskytovány jinou komponentou, a to buď přímo, nebo nepřímo.

 Dobře strukturovaná architektura má jasné uspořádání závislostí, ve kterých jsou tyto podmínky splněné:

- Neexistují žádné smyčky na mapě kódu.

- Komponenty lze uspořádat do vrstev, ve kterých každá závislost přechází z komponenty v jedné vrstvě do komponenty v dalším. Všechny závislosti mezi dvěma vrstvami směřují ve stejném směru.

  Závislosti můžete zobrazit přímo mezi komponentami nebo můžete zobrazit závislosti mezi požadovanými a poskytnutými rozhraními, která jsou připojena k součástem. Pomocí rozhraní můžete definovat, jaké operace se mají v každé závislosti používat. V případě, že jsou nejprve vykreslovány diagramy, jsou obvykle zobrazeny závislosti mezi komponentami a poté nahrazeny závislostmi mezi rozhraními, pokud jsou přidány další informace. Obě verze jsou správné popisy softwaru, ale verze s rozhraními poskytují více podrobností než předchozí verze.

  Správa závislostí je nejdůležitější pro produkci udržovatelného softwaru. Diagramy komponent by měly odrážet všechny závislosti ve vašem kódu. Pokud kód již existuje, ujistěte se, že všechny závislosti jsou zobrazeny v diagramech. Pokud je kód vyvíjen, ujistěte se, že nezahrnuje závislosti, které nejsou plánovány v diagramu komponent. Chcete-li zjistit závislosti v kódu, můžete generovat diagramy vrstev. Abyste se ujistili, že jsou splněné vaše plánovaná omezení závislostí, můžete kód ověřit proti diagramům vrstev. Další informace naleznete v tématu [diagramy vrstev: Reference](../modeling/layer-diagrams-reference.md).

### <a name="interfaces"></a>Rozhraní
 Umístěním rozhraní na své komponenty můžete oddělit a pojmenovat hlavní skupiny operací, které jsou k dispozici v jednotlivých součástech. Například komponenty v systémovém prodejním systému můžou mít rozhraní, přes které zákazníci kupují zboží, rozhraní, přes které dodavatelé aktualizují své katalogy, a třetí rozhraní, přes které se systém spravuje.

 Komponenta může mít libovolný počet poskytovaných a požadovaných rozhraní. Poskytnutá rozhraní zobrazují služby, které komponenta poskytuje pro použití pro jiné součásti. Požadovaná rozhraní zobrazují služby, které komponenta používá v jiných součástech.

 Pokud definujete poskytnutá i požadovaná rozhraní, pomůže vám to vyčistit komponentu ze zbytku návrhu, abyste mohli použít tyto techniky:

- Umístěte komponentu do testovacího stroje, ve kterém se okolní součásti simulují pomocí testovacího svazku.

- Rozvinout komponentu nezávisle na ostatních součástech.

- Opětovné použití komponenty v jiných kontextech propojením jejich rozhraní s různými komponentami.

  Pokud chcete definovat seznam operací v rozhraní, můžete vytvořit další zobrazení rozhraní v diagramu tříd UML. Provedete to tak, že vyhledáte rozhraní v Průzkumníku modelů UML a přetáhnete ho do diagramu tříd. Pak můžete do rozhraní přidat operace.

  Operace v rozhraní UML může představovat jakýkoliv způsob, jakým lze vyvolat chování komponenty. Může představovat požadavek webové služby, signál nebo interakci nějakého jiného druhu nebo běžné volání funkce programu.

  Chcete-li určit, jaké operace se mají přidat, vytvořte sekvenční diagramy, abyste viděli, jak komponenty vzájemně komunikují. Viz [interakce mezi komponentami](#Interactions). Každý z těchto sekvenčních diagramů zobrazuje interakce, ke kterým dochází v jiném případu použití. Tímto způsobem můžete postupně přidávat do seznamu operací v rozhraní každé součásti, jak prozkoumáte případy použití.

### <a name="decomposing-a-component-into-parts"></a>Deskládání součásti na části
 Můžete použít postup, který je popsán v předchozích částech každé součásti.

 V rámci každé součásti můžete zobrazit její dílčí komponenty jako části. Část je efektivně atribut své nadřazené komponenty, což je druh třídy. Každá část má svůj vlastní typ, který může být součástí. Tuto součást můžete umístit do diagramu a zobrazit její části. Další informace najdete v tématu [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).

 Tuto techniku je vhodné použít pro celý systém. Nakreslete ji jako jednu komponentu a jako součást si zobrazte její hlavní součásti. To vám pomůže identifikovat jasně rozhraní systému s vnějším světem.

 Pokud váš návrh komponenty používá jinou komponentu, často máte možnost zvolit, zda má být reprezentována jako součást, nebo jako samostatná komponenta, ke které přistupujete prostřednictvím rozhraní, které vyžaduje rozhraní.

 Používejte části v následujících situacích:

- Návrh nadřazené komponenty musí vždy používat typ součásti součásti. Proto je návrh části integrální pro návrh nadřazené komponenty.

- Nadřazená komponenta nemá žádnou konkrétní existenci. Například můžete mít koncepční komponentu s názvem prezentační vrstva, která představuje kolekci skutečných komponent, které zpracovávají zobrazení a interakce s uživateli.

  V těchto situacích použijte samostatné komponenty, ke kterým se přistupovalo prostřednictvím požadovaných rozhraní:

- Komponentu, která vyžaduje součást, může být spojena prostřednictvím svých rozhraní s různými poskytováním komponent za běhu.

- Návrh je takový, že by bylo snadné nahradit jednoho poskytovatele jiným poskytovatelem.

  Použití požadovaných rozhraní je obvykle vhodnější pro použití částí. I když návrh může trvat delší dobu, výsledný systém je flexibilnější. Také je snazší testovat komponenty samostatně. To umožňuje méně propojení ve svých plánech vývoje.

## <a name="Interactions"></a>Interakce mezi součástmi
 Hlavní doporučení této části jsou následující:

- Identifikujte případy použití systému.

- U každého případu použití nakreslete jeden nebo více diagramů, abyste viděli, jak komponenty systému dosáhnou požadovaných výsledků díky spolupráci mezi sebou a s uživateli. Obvykle jsou to sekvenční diagramy nebo diagramy aktivit.

- Pomocí rozhraní můžete určit zprávy přijímané jednotlivými součástmi.

- Popište účinky operací v rozhraních.

- Opakujte postup pro každou komponentu, který ukazuje, jak jeho části pracují.

  Například v rámci webového systému prodeje může model požadavků definovat nákup zákazníka jako případ použití. Můžete vytvořit sekvenční diagram pro zobrazení interakcí, které má zákazník s komponentami v prezentační vrstvě, a zobrazit interakce, které mají s komponentami datového skladu a účetnictví.

### <a name="identifying-the-initiating-events"></a>Určení událostí inicializace
 Práci, kterou provádí většina softwarových systémů, je možné pohodlně rozdělit podle odpovědí, které poskytuje různé vstupy nebo události. Událost iniciace může být jedna z následujících událostí:

- První akce v případu použití. Může se objevit v modelu požadavků jako krok v případu použití nebo v diagramu činnosti. Další informace najdete v [diagramech případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md) a [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

- Zpráva v programovém rozhraní. Pokud je systém, který vyvíjíte, součástí většího systému, měl by být popsán jako operace v jednom z rozhraní komponenty. Viz [komponenty a jejich rozhraní](#Components).

- Konkrétní podmínka, která je monitorována systémem, nebo běžnou událostí, jako je například denní čas.

### <a name="describe-the-computations"></a>Popsat výpočty
 Nakreslete sekvenční diagramy, které ukazují, jak komponenty reagují na počáteční událost.

 Nakreslete životnost pro každou instanci komponenty, která je součástí typické sekvence. V některých případech může existovat více než jedna instance každého typu. Pokud jste si popsali celý systém jako jednu komponentu, měli byste pro každou část, kterou obsahuje, existovat jedna životnost.

 Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagramy činnosti jsou také užitečné v některých případech. Například pokud vaše komponenty mají průběžný tok dat, můžete je popsat jako tok objektu. Pokud má vaše komponenta složitý algoritmus, můžete ho popsat jako tok řízení. Ujistěte se, že nechcete, aby tato součást prováděla jednotlivé akce, například pomocí komentářů. Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

### <a name="specify-the-operations"></a>Zadat operace
 Diagramy znázorňují operace prováděné jednotlivými součástmi, které jsou reprezentované buď jako zprávy v sekvenčním diagramu, nebo akce v diagramu činnosti.

 Shromažďovat tyto operace společně pro jednotlivé komponenty. Vytvořte pro komponentu poskytnutá rozhraní a přidejte operace do rozhraní. Pro každý typ klienta se obvykle používá samostatné rozhraní. Operace jsou nejčastěji přidány do rozhraní v **Průzkumníku modelů UML**. Stejným způsobem Shromážděte operace, které jednotlivé komponenty používají z ostatních komponent, a umístí je do požadovaných rozhraní připojených k komponentě.

 Je vhodné přidat komentáře k aktivitám nebo sekvenčním diagramům, abyste si poznamenali, co bylo dosaženo po každé operaci. Můžete také zapsat účinek každé operace v rámci své místní vlastnosti **následná podmínka** .

### <a name="Data"></a>Datový model komponent a rozhraní
 Definujte parametry a návratové hodnoty každé operace v rozhraní komponenty. V případech, kdy operace představují vyvolání, jako jsou třeba žádosti o webovou službu, jsou parametry tyto informace, které se odesílají v rámci žádosti. Kde se z operace vrátí několik hodnot, můžete použít parametry s vlastností **Direction** nastavenou na **out**.

 Každý parametr a návratová hodnota má typ. Tyto typy můžete definovat pomocí diagramů tříd UML. V těchto diagramech nemusíte zastupovat detaily implementace. Například pokud popisujíte data, která jsou přenášena jako XML, můžete použít přidružení k reprezentaci libovolného druhu křížového odkazu mezi uzly XML a použít třídy pro reprezentaci uzlů.

 Komentáře můžete použít k popisu obchodních omezení u asociací a atributů. Pokud například všechny položky v objednávce zákazníka pocházely od stejného dodavatele, můžete to popsat odkazem na přidružení mezi položkami objednávky a položkami v katalogu produktů a mezi položkou katalogu a jejím dodavatelem.

## <a name="Patterns"></a>Vzory návrhu
 Vzor návrhu je Osnova návrhu konkrétního aspektu softwaru, zejména z toho, který se opakuje v různých částech systému. Přijetím jednotného přístupu v rámci projektu můžete snížit náklady na návrh, zajistit konzistenci v uživatelském rozhraní a snížit náklady na porozumění a změnu kódu.

 Některé obecné vzory návrhu, jako je pozorovatel, jsou dobře známé a často použitelné. Kromě toho existují vzory, které platí pouze pro váš projekt. Například v systému webového prodeje bude v kódu k dispozici několik operací, kde se změny v objednávce zákazníka provedou. Aby se zajistilo, že se stav objednávky přesně zobrazuje v každé fázi, všechny tyto operace musí při aktualizaci databáze postupovat podle konkrétního protokolu.

 Součástí práce softwarové architektury je určit, jaké vzorky by se měly přijmout v rámci návrhu. To je obvykle probíhající úkol, protože nové vzory a vylepšení stávajících vzorů budou zjištěny v průběhu projektu. Je vhodné uspořádat plán vývoje, abyste měli v brzké fázi provádět jednotlivé hlavní vzory návrhu.

 Většina vzorů návrhu může být částečně obsažena v kódu rozhraní. Část vzoru se dá snížit, aby vývojář mohl používat konkrétní třídy nebo komponenty, jako je databázová vrstva přístupu, která zajišťuje správné zpracování databáze.

 Vzor návrhu je popsán v dokumentu a obvykle zahrnuje tyto části:

- Jméno.

- Popis kontextu, ve kterém je možné ho použít. Jaká kritéria by měl vývojář zvážit při použití tohoto vzoru?

- Stručné vysvětlení problému, který řeší.

- Model hlavních částí a jejich vztahů. Můžou to být třídy nebo komponenty a rozhraní s přidruženími a závislostmi mezi nimi. Prvky obvykle spadají do dvou kategorií:

  - Prvky, které musí vývojář replikovat v každé části kódu, kde je použit vzor. K jejich popisu můžete použít typy šablon. Další informace najdete v tématu [Diagramy případů použití UML: referenční informace](../modeling/uml-use-case-diagrams-reference.md).

  - Prvky popisující třídy architektury, které by měl vývojář použít.

- Model interakcí mezi částmi pomocí diagramů sekvence nebo činnosti.

- Zásady vytváření názvů.

- Popis způsobu, jakým vzorek tento problém vyřeší.

- Popis variací, které mohou vývojáři přijmout.

## <a name="see-also"></a>Viz také
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [vizualizace model kódu](../modeling/visualize-code.md) [požadavky uživatelů](../modeling/model-user-requirements.md) [vývoj testů z modelu](../modeling/develop-tests-from-a-model.md) [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md)
