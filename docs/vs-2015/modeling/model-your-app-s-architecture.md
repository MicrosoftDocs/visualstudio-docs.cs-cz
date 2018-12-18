---
title: Modelování aplikace&#39;architekturu s | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 770f93c0ede93201ee873820d6701356837f4ea9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803848"
---
# <a name="model-your-app39s-architecture"></a>Modelování aplikace&#39;s architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K zajištění, že softwarový systém nebo aplikace splňuje uživatelů potřebuje, si můžete vytvořit modelů v sadě Visual Studio jako součást vaší popis celkovou strukturu a chování softwarového systému nebo aplikace. Použití modelů, může také popisovat vzory, které se používají v návrhu. Tyto modely umožňují pochopit stávající architekturou, změny a jasně komunikovat vaše záměry.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Účel modelu je, abyste snížili nejasnosti, ke kterým dochází v přirozeném jazyce popisy a vy i vaši kolegové vizualizovat návrhu a diskutovat o alternativní návrhy. Model je třeba použít společně s další dokumenty nebo diskusí. Model samostatně, nepředstavuje kompletní specifikaci architektury.  
  
> [!NOTE]
>  V tomto tématu "systém" znamená, že software, který vyvíjíte. Může být velkou kolekci mnoho softwarové a hardwarové součásti, nebo jedné aplikace nebo součást aplikace.  
  
 Architektura systému je možné rozdělit do dvou oblastí:  
  
-   [Podrobný návrh](#Structure). Popisuje hlavní součásti a jejich vzájemné interakce mezi sebou ke splnění každý požadavek. Pokud systém je velká, může být jednotlivé komponenty vlastní hlavnímu návrhu, který ukazuje, jak se skládají z menších komponent.  
  
-   [Vzory návrhu](#Patterns) a pravidla týkající se používají v návrzích komponenty. Vzor popisuje konkrétní přístup k dosažení cíle programování. Pomocí stejné vzorce v celém návrh váš tým může snížit náklady na provedení změn a vývoji nového softwaru.  
  
##  <a name="Structure"></a> Návrh vysoké úrovně  
 Návrh vysoké úrovně popisuje hlavní součásti systému a jejich vzájemné interakce mezi sebou k dosažení cíle návrhu. Aktivity v následujícím seznamu jsou součástí vývoje nejvyšší úrovni návrhu, i když nemusí nutně jít v určitém pořadí.  
  
 Pokud aktualizujete existující kód, může začít popisuje hlavní součásti. Ujistěte se, že pochopit změny s požadavky uživatele a pak přidat nebo upravit interakce mezi komponentami. Pokud vyvíjíte na nový systém, začněte tím, že vysvětlení si hlavní funkce potřebám uživatelů. Můžete pak prozkoumejte sekvence interakcí pro případy použití hlavní a pak sloučit sekvence na návrh komponent.  
  
 Ve všech případech je užitečné pro vývoj různé aktivity paralelně a pro vývoj kódu a testy v rané fázi. Vyhněte se pokusům o proveďte jeden z těchto aspektů před spuštěním jiného. Obvykle požadavky a pochopíte nejlepší způsob, jak navrhnout systému se změní při psaní a testování kódu. Proto měli byste začít tak, že porozumění a psaní kódu si hlavní funkce požadavky a návrhu. Vyplňte podrobnosti v pozdější iterace projektu.  
  
-   [Principy požadavky](#Requirements). Výchozí bod jakékoli návrhu je pochopili, že potřebám uživatelů.  
  
-   [Vzorech architektury](#BigDecisions). Volby, které jste provedli o základních technologií a prvky architektury systému.  
  
-   [Komponenty a jejich rozhraní](#Components). Můžete kreslit diagramy komponent k zobrazení hlavních částí systému a zobrazit rozhraní, pomocí kterých se vzájemně spolupracují. Rozhraní jednotlivé součásti zahrnují všechny zprávy, které jste identifikovali v sekvenčních diagramech.  
  
-   [Interakce mezi komponentami](#Interactions). Pro každý případ použití, události nebo příchozí zprávy můžete nakreslit sekvenční diagram, který znázorňuje interakci hlavní součásti systému zajistit požadované odpovědi.  
  
-   [Datový Model rozhraní a komponenty](#Data). Je-li nakreslit diagramy tříd k popisu informace, které se ukládají v součásti a předány mezi komponentami.  
  
##  <a name="Requirements"></a> Vysvětlení požadavků  
 Hlavnímu návrhu dokončené aplikace je efektivní vyvinutý spolu s modelem požadavky nebo jiný popis potřebám uživatelů. Další informace o modelech požadavky najdete v části [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
 Pokud systém, který vyvíjíte je součástí větší systému, může být část nebo všechny vaše požadavky shrnuta v programových rozhraní.  
  
 Požadavky na model poskytuje tyto základní údaje:  
  
- Poskytované rozhraní. Poskytované rozhraní obsahuje seznam služeb nebo operací, které systém nebo komponenta musí poskytnout uživatelům, ať už jsou lidské uživatele nebo další softwarové komponenty.  
  
- Požadovaná rozhraní. Požadované rozhraní obsahuje seznam služeb nebo operací, které můžete použít systém nebo komponenty. V některých případech bude možné navrhnout všechny tyto služby jako součást vlastní systému. V ostatních případech zejména v případě, že součást, kterou můžete kombinovat s jinými součástmi v řadě konfigurací, navrhujete požadované rozhraní se nastavit externí aspekty.  
  
- Kvalita požadavků na služby. Výkon, zabezpečení, odolnosti a další cíle a omezení, které musí splnit systému.  
  
  Model požadavků se zapíše z pohledu uživatele vašeho systému, ať už jsou lidé, případně další softwarové komponenty. Které znají nic vnitřní fungování systému. Vaším cílem v architektuře modelu naopak je popíšou vnitřní činnost a ukážou, jak vyhovují uživatelů potřebuje.  
  
  Pokud oddělíte požadavků a architektury modelů je užitečné, protože usnadňuje požadavky s uživateli. Pomáhá také Refaktorovat návrhu a zvážit alternativní architektury, při zachování požadavky beze změny.  
  
  Požadavky a architektury modely můžete oddělit dva alternativní způsoby:  
  
- Uložily do stejného řešení, ale jiné projekty. Zobrazí se jako samostatných modelů v Průzkumníku modelů UML. Různí členové týmu mohou pracovat souběžně na modely. Omezené druhy trasování lze vytvořit mezi modely.  
  
- Vytvořte z nich ve stejném modelu UML, ale v různých balíčcích. To usnadňuje trasování závislosti mezi modely, ale zabrání víc než jedna osoba najednou pracovat v modelu. Kromě toho modelu velmi velké bude trvat déle načíst do sady Visual Studio. Tento přístup je proto méně vhodná pro velké projekty.  
  
  Množství podrobností, které byste měli umístit do požadavky nebo Architektonický model závisí na škálování projektu a velikost a rozmístění týmu. Malý tým na krátké projektu je možné dát další než zobrazení diagramu tříd obchodních konceptů a některé vzory návrhu; velký projekt distribuovat napříč více než jedné oblasti, bude nutné výrazně více podrobností.  
  
##  <a name="BigDecisions"></a> Vzorech architektury  
 V rané fázi vývoje budete muset zvolit hlavní technologie a prvky, na kterých závisí návrhu. Oblasti, ve kterých se musí provádět tyto možnosti patří:  
  
- Základní technologické volby, jako je například výběr mezi databází a systém souborů a možností volby mezi aplikace v síti a webovému klientovi a tak dále.  
  
- Volby architektury, jako je například možností volby mezi Windows Workflow Foundation nebo ADO.NET Entity Framework.  
  
- Integrace metody se nemusíte rozhodovat, například mezi enterprise service bus nebo kanál typu point-to-point.  
  
  Tyto možnosti jsou často určené kvalitu požadavků služby, jako je škálovatelnost a flexibilitu a můžete provést předtím, než jsou známé podrobné požadavky. V rozsáhlém systému se důrazně vzájemně propojené konfigurace hardwaru a softwaru.  
  
  Vámi provedeném výběru vliv na způsob používání a interpretace Architektonický model. Například v systému, která používá databázi, asociace v diagramu tříd může představovat vztahů nebo cizí klíče v databázi, že v systému, který je založen na soubory XML, přidružení může znamenat křížové odkazy, které používají XPath. V distribuovaném systému může představovat zprávy v sekvenčním diagramu zprávy v přenosové; samostatná aplikace může představovat volání funkce.  
  
##  <a name="Components"></a> Komponenty a jejich rozhraní  
 Hlavní doporučení v této části jsou následující:  
  
- Vytvoření diagramů komponent k zobrazení hlavních částí systému.  
  
- Nakreslete závislosti mezi komponentami nebo jejich rozhraní a zobrazit strukturu systému.  
  
- Pomocí rozhraní do komponent k zobrazení služeb, které poskytuje jednotlivé komponenty, nebo vyžaduje.  
  
- Ve velkých návrhu můžete kreslit samostatných diagramech k rozložení jednotlivých komponent do menších částí.  
  
  Tyto body jsou rozpracovaného ve zbytku této části.  
  
### <a name="components"></a>Součásti  
 Střed zobrazení modelu architektury jsou diagramů komponent, které zobrazení hlavních částí systému a jak jsou závislé na sebe navzájem. Další informace o diagramech komponent najdete v tématu [diagramy komponent UML: referenční](../modeling/uml-component-diagrams-reference.md).  
  
 ![Diagram komponenty UML zobrazující částí](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Diagram typické komponent pro velké systém může zahrnovat komponenty, jako jsou tyto:  
  
-   Prezentace. Komponenta, která poskytuje přístup pro uživatele, obvykle běží ve webovém prohlížeči.  
  
-   Součásti webové služby. Poskytuje připojení mezi klienty a servery.  
  
-   Použijte velká řadiči. Chování uživatele provede kroky pro každý scénář.  
  
-   Základní firmy. Obsahuje třídy, které jsou založeny na třídách v modelu požadavky, implementuje klíčové operace a ukládá obchodních omezení.  
  
-   Databáze. Ukládá objekty firmy.  
  
-   Protokolování a komponent pro zpracování chyb.  
  
### <a name="dependencies-between-components"></a>Závislosti mezi komponentami  
 Kromě komponent sami můžete zobrazit závislosti mezi nimi. Šipky závislostí mezi dvě součásti ukazuje, že změny v návrhu jeden můžou ovlivnit návrh druhé. To obvykle dochází, protože jedna komponenta využívá služby nebo funkce, které jsou k dispozici jinou součástí, buď přímo nebo nepřímo.  
  
 Strukturované architektura se vymazat uspořádání závislostí, ve kterých jsou splněny tyto podmínky:  
  
- Neexistují žádné smyčky v mapě kódu.  
  
- Součásti lze uspořádat do vrstev, ve kterých každý závislost přejde z komponenty v jedné vrstvě součásti v dalším. Všechny závislosti mezi jakékoli dvě vrstvy přejděte ve stejném směru.  
  
  Můžete zobrazit závislosti mezi komponentami přímo, nebo můžete zobrazit závislosti mezi povinné a k dispozici rozhraní, které jsou připojené k součástem. To s využitím rozhraní, můžete definovat, jaké operace se používají v jednotlivých závislostí. Obvykle jsou uvedeny závislosti mezi komponentami, když jsou nejprve vykreslit diagramy a pak nahrazuje závislosti mezi rozhraními, jak přidat další informace. Obě verze jsou popsaná níž správný software, ale verze rozhraní poskytuje podrobnější než u předchozí verze.  
  
  Správa závislostí je nejdůležitější pro provozní údržby software. Diagramy součástí by měly odrážet všechny závislosti ve vašem kódu. Pokud kód již existuje, ujistěte se, že všechny závislosti jsou zobrazeny v diagramech. Pokud kód je vyvíjena, ujistěte se, že v diagramu komponent neobsahuje závislosti, které nejsou plánované. Vám pomůžou zjistit závislosti v kódu, můžete vygenerovat diagramy vrstev. Vám pomohou zajistit, že jsou splněné omezení plánované závislosti, můžete ověření kódu oproti diagramům vrstev. Další informace najdete v tématu [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Umístěním rozhraní na vaše komponenty můžete oddělit a pojmenujte hlavních skupin operací, které jsou poskytovány jednotlivých komponent. Součástí webové prodejní systém může mít například rozhraní, přes které zákazníci zakoupit zboží, rozhraní, přes který dodavatelé aktualizaci jejich katalogy a třetí rozhraní prostřednictvím systému spravuje.  
  
 Komponenta může mít libovolný počet poskytovaných a požadovaných rozhraní. Poskytované rozhraní zobrazit služby, které obsahuje komponenty pro jiné komponenty používat. Požadovaná rozhraní zobrazit služeb, které používá komponenty v jiných komponent.  
  
 Pokud definujete i k dispozici a požadovaná rozhraní díky tomu můžete oddělit komponentu přímo od ostatních návrhu, tak, aby tyto postupy můžete použít:  
  
- Umístěte komponentu do testovací prostředí, ve kterém jsou okolního komponenty simulováno testovací prostředí.  
  
- Vývoj vaší komponentě nezávisle na ostatních součástí.  
  
- Znovu použijte komponentu v jiných kontextech párování jeho rozhraní pro různé součásti.  
  
  Pokud chcete definovat seznam operací v rozhraní, můžete vytvořit další zobrazení rozhraní v diagramu tříd UML. Chcete-li to provést, vyhledejte rozhraní v Průzkumníku modelů UML a přetáhnout do diagramu tříd. Pak může přidání operací do rozhraní.  
  
  Operace v rozhraní UML může představovat žádným způsobem, ve kterém může být vyvolána chování součásti. To může představovat požadavek webové služby, signál nebo interakce určitého druhu nebo volání funkce rozhraní běžné programu.  
  
  Pokud chcete zjistit, jaké operace přidat, vytvořte sekvenční diagramy zobrazit, jak komponenty komunikovat mezi sebou. Zobrazit [interakce mezi komponentami](#Interactions). Každá z těchto sekvenčních diagramů ukazuje interakce, ke kterým dochází v případě použití v odlišných. Tímto způsobem můžete postupně přidat na seznam operací v jednotlivých komponent rozhraní při seznamování s případy použití.  
  
### <a name="decomposing-a-component-into-parts"></a>Rozložení komponentu do částí  
 Můžete použít postup popsaný v předchozích částech pro jednotlivé komponenty.  
  
 V rámci jednotlivých komponent můžete zobrazit jeho dílčí komponenty jako částí. Součást je v podstatě atribut své nadřazené komponentě, což je typ třídy. Každá část má svůj vlastní typ, který může být součást. Můžete umístit tuto komponentu v diagramu a zobrazit její části. Další informace najdete v tématu [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).  
  
 Je vhodné použít tuto techniku pro celý systém. Vykreslení jako jedinou komponentu a zobrazit jeho hlavní komponenty jako částí. Toto pomáhá identifikovat jasně rozhraní systému s externí světem.  
  
 Při návrhu pro součást používá jiné komponenty, máte často výběr o tom, jestli reprezentovat ho jako součást nebo jako samostatná součást, ke kterým přístup přes rozhraní se vyžaduje.  
  
 Části použijte v následujících situacích:  
  
- Návrhu nadřazené komponenty musíte vždycky použít typ komponenty na straně. Proto z část je nedílnou součástí návrhu nadřazené komponenty.  
  
- Nadřazené komponenty nemá žádné konkrétní existence své vlastní. Například můžete mít koncepční komponenty s názvem prezentační vrstva, která představuje kolekci skutečné komponent, které zpracovávají zobrazení a interakce uživatelů.  
  
  Použijte samostatné součásti, které jsou přístupné prostřednictvím požadovaná rozhraní v těchto situacích:  
  
- Vyžadování součást je možné kombinovat prostřednictvím svých rozhraní poskytuje různé součásti v době běhu.  
  
- Návrh je tak, aby ho by bylo možné snadno nahradit jiným jednoho poskytovatele.  
  
  Použití požadovaná rozhraní je obvykle vhodnější použít části. I když návrhu může trvat déle, výsledný systému je flexibilnější. Je také usnadňuje testování součástí samostatně. To umožňuje méně párování v jejich vývojových plánů.  
  
##  <a name="Interactions"></a> Interakce mezi součástmi  
 Hlavní doporučení v této části jsou následující:  
  
- Identifikování případů použití vašeho systému.  
  
- Pro každý případ použití kreslit diagramy jeden nebo více zobrazíte jak součástí systému na příjem požadovaného výsledku dosáhnout díky spolupráci mezi sebou a s uživateli. Obvykle se jedná, sekvenční diagramy a diagramy činnosti.  
  
- Pomocí rozhraní můžete určit zprávy přijaté službou jednotlivých komponent.  
  
- Popisuje účinky operací v rozhraní.  
  
- Postup opakujte pro každou komponentu znázorňující způsob interakce jejích částí.  
  
  Například ve webové prodejní systému může být model požadavků definovat nákup zákazníka jako případ použití. Můžete vytvořit sekvenční diagram zobrazíte interakcí, že zákazník má s komponentami v prezentační vrstvě a k zobrazení interakce, ke kterým mají s datového skladu a komponenty monitorování účtů.  
  
### <a name="identifying-the-initiating-events"></a>Identifikace zahájení události  
 Práci prováděnou Většina softwarových systémů můžete pohodlně rozdělit podle odpovědi, které poskytuje různé vstupy nebo události. Zahájení události může být jeden z následujících událostí:  
  
-   První akcí v případu použití. Může zobrazit v modelu požadavky jako krok v případu použití nebo akce v diagramu činnosti. Další informace najdete [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md) a [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
-   Zpráva v programové rozhraní. Pokud systém, který vyvíjíte je součástí větší systému, musí být popsány jako operaci v jednom z rozhraní komponenty. Zobrazit [komponent a jejich rozhraní](#Components).  
  
-   Konkrétní podmínky, který je monitorován pomocí vašeho systému nebo normální událost, jako je například denní dobu.  
  
### <a name="describe-the-computations"></a>Popište výpočtů  
 Nakreslete sekvenční diagramy zobrazit, jak komponenty reagují na počáteční událost.  
  
 Nakreslete životnost pro každou instanci komponenty, která přebírá části typickou postupně. V některých případech může být více než jednu instanci každého typu. Pokud máte popsané celého systému jako jedinou komponentu, musí být jedna životnost pro každou část, kterou obsahuje.  
  
 Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagramy činnosti jsou také užitečné v některých případech. Například pokud vaše komponenty průběžné toku dat, můžete ho popisují jako tok, který objekt. Pokud vaše komponenta obsahuje komplexní algoritmus, můžete ho popsat jako tok řízení. Ujistěte se, abyste vytvořili bylo jasné, jaká součást provádí každou akci, například s použitím komentářů. Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>Určení operací  
 Diagramy popisují operace, které provádí každou komponentu buď reprezentována jako zprávy na akce v diagramu činnosti nebo sekvenčního diagramu.  
  
 Shromažďování těchto operací dohromady pro každou komponentu. Vytvoření rozhraní k dispozici na komponentu a přidání operací do rozhraní. Samostatné rozhraní se obvykle používá u každého typu klienta. Přidání operací se nejsnadněji na rozhraní v **Průzkumníku modelů UML**. Stejným způsobem shromažďovat operace, které používá každá součást od ostatních součástí a umístit je do požadované rozhraní připojené součásti.  
  
 Je užitečné k přidání komentářů do diagramů aktivit nebo pořadí vědět, co bylo dosaženo po každé operaci. Můžete je zapsat také vliv jednotlivých operací ve své **místní neplatná následná** vlastnost.  
  
###  <a name="Data"></a> Datový Model rozhraní a komponenty  
 Definovat parametry a návratové hodnoty pro každou operaci v rozhraní komponenty. Pokud operace představují volání, jako jsou žádosti webové služby, parametry jsou tyto údaje, které jsou odeslány jako součást požadavku. Několik hodnoty jsou vráceny z operace, můžete použít parametry **směr** vlastnost nastavena na hodnotu **si**.  
  
 Každý parametr a návratová hodnota je typu. Můžete definovat tyto typy používání diagramů tříd UML. Nemáte k reprezentaci podrobnosti implementace v těchto diagramů. Například pokud jako XML přenášená data jsou s popisem, můžete použít přidružení pro reprezentaci jakéhokoli vztahu křížových odkazů mezi uzly XML a použít třídy představující uzly.  
  
 Komentáře lze použít k popisu obchodní omezení pro přidružení a atributy. Například pokud prostřednictvím položky z objednávky zákazníka musí pocházet ze stejného dodavatele, je to popisují s odkazem na přidružení mezi pořadí položek a položky v katalogu produktů a mezi položka katalogu a jeho dodavatele.  
  
##  <a name="Patterns"></a> Vzory návrhu  
 Vzor návrhu je přehled toho, jak navrhnout konkrétní aspekt software, hlavně jeden, který se opakuje v různých součástí systému. Přijetím jednotný přístup napříč projektu můžete snížit náklady na návrh, zajistit konzistenci v uživatelském rozhraní a snížit náklady na principy a změny kódu.  
  
 Některé obecné návrhové vzory, třeba pozorovatel jsou dobře známé a široce použitelné. Kromě toho jsou vzorce, které se dají použít jenom pro váš projekt. Například v systému prodejní Web, bude existovat několik operací v kódu ve kterém se změny provedly pořadí na základě. Aby bylo zajištěno, že se v každé fázi přesně zobrazí stav objednávky, musí všechny tyto operace postupujte podle konkrétní protokol k aktualizaci databáze.  
  
 Během práce softwarovou architekturu je nutné určit, co by měl být modely přijatých přes návrhu. To je obvykle probíhající úlohy, protože nová schémata a vylepšení stávajících vzory, bude zjištěno v průběhu projektu. Je vhodné uspořádat plán vývoje tak, aby každý z vašich hlavních návrhové vzory výkonu v rané fázi.  
  
 Většina vzorů návrhu může být částečně shrnuta v kódu rozhraní framework. Součást vzorku lze snížit vyžadováním pro vývojáře pro použití určitých tříd nebo komponenty, jako je například vrstva přístupu k databázi, který zajistí, že je správně zpracovat databázi.  
  
 Vzor návrhu je popsaný v dokumentu a obvykle zahrnuje tyto části:  
  
-   Jméno.  
  
-   Popis kontext, ve které se vztahuje. Jakých kritérií by měl vytvořit vývojář, jestli nebude lepší uplatňovat tento model?  
  
-   Stručné vysvětlení problému, který řeší.  
  
-   Model hlavních částí a jejich vztahy. Může se jednat třídy nebo součásti a rozhraní se přidružení a závislostí mezi nimi. Elementy obvykle spadají do dvou kategorií:  
  
    -   Elementy, které vývojář musí replikovat v každé části kódu, kde se používá vzor. Typy šablon můžete použít k popisu tyto. Další informace najdete v tématu [diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md).  
  
    -   Prvky, který popisuje třídy rozhraní framework, které vývojář by měl používat.  
  
-   Model interakcí mezi částmi, pomocí pořadí nebo aktivita diagramů.  
  
-   Zásady vytváření názvů.  
  
-   Popis jak vzoru byl problém vyřešen.  
  
-   Popis změn, která se můžou vývojáři moci přijmout.  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Vizualizace kódu](../modeling/visualize-code.md)   
 [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)   
 [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)



