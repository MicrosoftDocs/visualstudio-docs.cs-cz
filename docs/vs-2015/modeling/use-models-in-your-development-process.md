---
title: Použití modelů ve vývojových procesech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 56534483f8b9cda99b756524d87408efbedfe275
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757705"
---
# <a name="use-models-in-your-development-process"></a>Použití modelů ve vývojových procesech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio vám pomůže modelu vám pomůžou pochopit a změnit systému, aplikace nebo komponenty. Model můžete vizualizovat na světě, ve kterém je váš systém funguje, vysvětlení požadavky uživatelů, definovat architektuře systému, analýza kódu a ujistěte se, že váš kód splňuje požadavky. Zobrazit [Video pro kanál 9: zlepšení architektury prostřednictvím modelování](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Které verze sady Visual Studio podporovat každý typ modelu najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="how-to-use-models"></a>Použití modelů  
 Modely můžou pomoct několika způsoby:  
  
- Kreslení diagramů modelování vám objasnění konceptů, které jsou součástí požadavků, architektury a návrhu vysoké úrovně. Další informace najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
- Práce s modely můžete zveřejnit nekonzistence v požadavcích.  
  
- Komunikace s modely vám umožňuje komunikovat, důležité koncepty menší ambiguously přirozeným jazykem. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).  
  
- Modely někdy slouží ke generování kódu nebo jiných artefaktů, jako je například databázová schémata nebo dokumenty. Například modelování součástí [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] se generují z modelu.  Další informace najdete v tématu [vygenerovat a nakonfigurovat aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).  
  
  Modely v nejrůznějších procesy, extreme agility na vysokou procedury můžete použít.  
  
### <a name="use-models-to-reduce-ambiguity"></a>Použití modelů ke snížení nejednoznačnosti  
 Modelovací jazyk je nejednoznačný méně než přirozený jazyk a je určený k vyjádření nápady obvykle vyžadují při vývoji softwaru.  
  
 Pokud váš projekt obsahuje malý tým agilních postupů, můžete použít modely umožňují objasnění uživatelských scénářů. V diskusích u zákazníka o jejich potřebám vytváření modelu můžete generovat užitečné dotazy mnohem rychleji a napříč širším oblasti produktu, než psaní kódu ve špičce nebo spravovat.  
  
 Pokud váš projekt je velká a zahrnuje týmy v různých částech světa, můžete použít modely usnadňují komunikaci požadavcích a architektuře mnohem efektivněji než v prostém textu.  
  
 V obou případech vytváření modelu téměř vždy vede k výraznému snížení nekonzistence a nejednoznačnosti. Různé zúčastněné strany mají často různých porozumění obchodním světě, ve kterém systém funguje, a různí vývojáři často mají různé porozumění fungování systému. Použití modelu jako zaměření diskuse obvykle poskytuje tyto rozdíly. Další informace o tom, jak využít model k snížení nekonzistence, naleznete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
### <a name="use-models-with-other-artifacts"></a>Použití modelů pomocí jiné artefakty  
 Model se sám o sobě specifikace požadavky nebo architekturu. Je nástroj pro větší přehlednost vyjádření některé aspekty těchto věcí, ale ne všechny konceptech vyžadovaných při návrhu softwaru lze vyjádřit. Modely proto je nutné použít spolu s jiným způsobem komunikace, jako jsou stránky v OneNote nebo odstavce, dokumentů Microsoft Office, pracovní položky v [!INCLUDE[esprfound](../includes/esprfound-md.md)], nebo rychlé poznámky na zeď místnosti projektu. Kromě poslední položky všechny tyto typy objektů lze propojit k různým částem prvky modelu.  
  
 Další aspekty specifikace, které se běžně používají společně s modely patří. V závislosti na rozsahu a styl projektu můžete použít některé z těchto aspektů nebo není žádný vůbec používat:  
  
-   Uživatelské scénáře. Uživatelský scénář je krátký popis, popsané s uživateli a další zainteresované uživatele určitý aspekt systému chování, které budou doručeny v jednom projektu iterací. Typické uživatelský scénář začíná "zákazník bude moct..." Uživatelský scénář může způsobit skupinu případy použití, nebo můžete definovat rozšíření případy použití, které byly dříve vytvořeny. Definování nebo rozšíření případy použití pomáhá vytvářet jasnější uživatelský scénář.  
  
-   Žádosti o změnu. Žádost o změnu v formálnější projektu je velmi podobný uživatelského scénáře v projektu aplikace agile. Agilní přístup považuje za všechny požadavky na změny pro co byl vyvinut v předchozími iteracemi.  
  
-   Popis případu použití. Případ použití představuje jeden ze způsobů, ve kterém uživatel pracuje se systémem k dosažení určitého cíle. Úplný popis obsahuje cíl, hlavní a alternativní pořadí událostí a mimořádných výsledků. Diagram případu použití pomáhá shrnout a poskytnout přehled o případy použití.  
  
-   Scénáře. Scénář je poměrně podrobný popis posloupnost událostí znázorňující, jak v systému, uživatelů a jiných systémů společně poskytují hodnotu pro zúčastněné strany. Může trvat formu slide show uživatelského rozhraní nebo prototypu uživatelského rozhraní. To lze popsat jeden případ použití nebo posloupnost případy použití.  
  
-   Glosář. Glosář požadavky projektu popisuje slova, se kterými zákazníci diskutovat o jejich světa. Uživatelské rozhraní a požadavků na modely také používali tyto podmínky. Diagram tříd může pomoci objasnit vztahy mezi většinu těchto podmínek. Vytváření diagramů a glosář pouze snižuje nedorozuměním mezi uživatele a vývojáře, ale také téměř vždy zpřístupňuje nedorozuměním mezi různými obchodními zúčastněnými stranami.  
  
-   Obchodní pravidla. Řada obchodních pravidel může být vyjádřena jako výchozí omezení na přidružení a atributy v třídě modelu požadavky a jako omezení u sekvenčních diagramů.  
  
-   Návrh vysoké úrovně. Popisuje hlavní části a jak je umístit společně. Komponenty, pořadí a interface diagramy jsou hlavní součástí návrhu vysoké úrovně.  
  
-   Vzory návrhu. Popis pravidla návrhu, které jsou sdíleny napříč různými částmi systému.  
  
-   Otestujte specifikace. Testovací skripty a návrhy pro testovací kód můžete velice diagramy činnosti a sekvence pro popis sekvencí testovací kroky. Testy systému by měl být vyjádřen jako model požadavků tak, aby se lze snadno změnit při změně požadavků.  
  
-   Plán projektu. Plánu projektu nebo nevyřízené položky definuje, kdy budou doručeny jednotlivé funkce. Jednotlivé funkce můžete definovat uvedením, co použijete, případy a obchodní pravidla implementuje nebo rozšiřuje. Můžete buď odkazujete i na případy použití a obchodní pravidla přímo v plánu nebo můžete definovat sadu funkcí v samostatných dokumentu a použít názvy funkcí v plánu.  
  
### <a name="use-models-in-iteration-planning"></a>Používání modelů v plánování iterace  
 I když se všechny projekty se liší v jejich škálování a organizaci, obvyklou pro projekty, plánujeme přidat jako řadu iterací mezi dvěma až šest týdnů. Je důležité mít plán dostatek iterace povolit zpětnou vazbu od počáteční iterace, který se má použít k nastavení oboru a plány pro vyšší počet iterací.  
  
 Následující doporučení můžou být užitečné umožňující začít využívat výhod v iterativní projektu modelování.  
  
#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Zdokonalení fokus přístupy každé iterace  
 Při každém blížícím se opakování pomocí modely definovat, co je doručit na konci iterace.  
  
-   Model není vše podrobně v počátečních iteracích. V první iteraci vytvoření diagramu tříd pro hlavní položky v glosáři uživatele, nakreslit diagram případy použití hlavní a nakreslete obrázek hlavní součásti. Nepopisují všechny z nich najdete v úplných podrobností, protože později v projektu se změní podrobnosti. Pomocí podmínky definované v tomto modelu vytvořit seznam funkcí nebo hlavní uživatelské scénáře. Funkce přiřadíte k iteracím tak, aby přibližně vyvážit zatížení odhadované během celého projektu. Tato přiřazení se změní později v projektu.  
  
-   Zkuste implementovat zjednodušená verze všech vašich nejdůležitějších případy použití v rané fázi iterace. Rozšíření jsou případy použití ve vyšším počtu iterací. Tento přístup pomáhá snížit riziko zjistit chyby v požadavcích nebo na architekturu příliš pozdě v projektu se nic dělat.  
  
-   Na konci každé iterace stiskněte a podržte požadavky na seminář k definování podrobně požadavky nebo uživatelskými scénáři, které budou vytvořeny v další iteraci. Pozvěte uživatele a zúčastněné obchodní strany, kteří se můžete rozhodnout, priority, jakož i vývojářům a testerům systému. Umožňují definovat požadavky pro iterace 2 týden tři hodiny.  
  
-   Cílem tohoto pracoviště je pro každého souhlas, co všechno zvládneme na konci další iteraci. Abychom to osvětlili požadavky použijte modely jako jeden z nástrojů. Iterace backlogu je výstup seminář: to znamená, že seznam vývoj úkoly v [!INCLUDE[esprfound](../includes/esprfound-md.md)] a testovací sady v [!INCLUDE[TCMext](../includes/tcmext-md.md)].  
  
-   Workshop požadavky diskutovat o návrhu, pouze pokud podle musíte určit odhady pro úlohy vývoje. Jinak použijte diskusi chování systému, který uživatelé budou moci využívat přímo. Zachovat model požadavků nezávisle na architektuře modelu.  
  
-   Běžné uživatele zúčastněné strany mají obvykle bez problémů Principy diagramy UML, s pokyny od vás.  
  
#### <a name="link-model-to-work-items"></a>Odkaz modelu s pracovními položkami  
 Po seminář požadavky vypracování podrobností model požadavků a propojit úkoly vývoje modelu. Můžete to provést pomocí propojení pracovních položek v [!INCLUDE[esprfound](../includes/esprfound-md.md)] na prvky v modelu. Zjistěte, jak to provést, najdete v článku [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).  
  
 Můžete propojit libovolný prvek s pracovními položkami, ale jsou nejužitečnější prvky následujícím způsobem:  
  
-   Případy použití. Propojení případu použití pro vývoj pro úkoly, které provede.  
  
-   Použití rozšíření případu. Pokud pouze jeden aspekt jejich případu použití se provádí v iteraci, můžete ho rozdělte do případu základní použití spolu s jedno nebo více rozšíření. Rozšíření jsou případy použití, které jsou připojeny na základní případ "rozšíření" vztah. Další informace o rozšíření případu použití, naleznete v tématu [diagramy případu použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md).  
  
-   Komentář popisující obchodních pravidel nebo kvality požadavků na služby. Další informace najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
#### <a name="link-model-to-tests"></a>Odkaz modelu testů  
 Pomocí modelu požadavky na návrh předávací testy. Vytvořte tyto testy současně vývojové práce.  
  
 Další informace o této techniky najdete v tématu [vývoj testů z modelu](../modeling/develop-tests-from-a-model.md).  
  
#### <a name="estimate-remaining-work"></a>Odhad zbývající práce  
 Model požadavků může pomoct s odhadem celkovou velikost ve vztahu k velikost každé iterace projektu. Hodnocení počtem a složitostí na případy použití a třídy, pomůže vám při odhadování vývojové práce, která se bude vyžadovat. Když jste dokončili prvních několika iteracích, porovnání požadavky popsané a požadavky stále k pokrytí můžete udělit přibližné zlomek nákladů a rozsah zbytku projektu.  
  
 Na konci každé iterace zkontrolujte přiřazení požadavků k budoucím iteracím. Může být užitečné k vyjádření stavu vašeho softwaru na konci každé iterace jako subsystém v diagramu případu použití. V diskusích můžete přesunout případy použití a pomocí rozšíření případu z jednoho z těchto subsystémů na jiný.  
  
## <a name="levels-of-abstraction"></a>Úrovní abstrakce  
 Modely mají celou řadu abstrakce ve vztahu k softwaru. Většina konkrétní modely přímo představují programového kódu a nejvíce abstraktní modely představují obchodních konceptů, jež mohou nebo nemusí být zastoupeny v kódu.  
  
 Model lze zobrazit pomocí několika druhů diagramů. Informace o modelů a diagramů naleznete v tématu [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).  
  
 Různé druhy diagramu jsou užitečné pro popis návrhu na různých úrovních, abstrakce. Mnoho typů diagramu jsou užitečné na více než jedné úrovni. Tato tabulka ukazuje, jak je možné každý typ diagramu.  
  
|Úroveň návrh|Typy diagramů|  
|------------------|-------------------|  
|Obchodního procesu<br /><br /> Díky porozumění kontextu, ve kterém se použije váš systém pomáhá zjistit, co uživatelé musíte z něj.|– Aktivity diagramy popisují postup mezi lidmi a systémy pro dosažení obchodních cílů.<br />– Diagramy tříd koncepční popisují obchodní koncepty používané v rámci obchodního procesu.|  
|Požadavky na uživatele<br /><br /> Definice uživatelé musí z vašeho systému.|– Použijte diagramy případu pro shrnutí interakcí, které uživatelé a dalších externích systémů mají s systému, které vyvíjíte. Další dokumenty, které můžete připojit na každý případ použití pro podrobně popisují.<br />– Diagramy tříd UML popisují typy informací, které uživatelé a systém komunikovat o.<br />-Obchodní pravidla a kvalitu služeb požadavků lze popsat v samostatných dokumentech.|  
|Návrh vysoké úrovně<br /><br /> Celkovou strukturu systému: hlavní součásti a jak se spojit dohromady.|– Diagramy vrstev popisují struktury systému do vzájemně závislé součásti. Můžete ověřit kód programu proti diagramy vrstev k zajištění, že bude odpovídat architektuře.<br />-Diagramy komponent zobrazí rozhraní částí, určení zpráv a služeb, které jsou k dispozici a vyžadované jednotlivých komponent.<br />– Sekvenční diagramy ukazují, jak sdělit implementovat každý případ použití komponenty.<br />– Diagramy tříd UML popisují rozhraní komponenty a typy dat předávaných mezi komponentami.|  
|Vzory návrhu<br /><br /> Vytváření a způsoby řešení problémů návrhu, které se používají ve všech částech návrhu|– Diagramy tříd UML popisují struktury vzoru<br />-Pořadí nebo zobrazit diagramy činnosti interakce a algoritmy|  
|Analýza kódu<br /><br /> Několik typů diagramu se dá vygenerovat na kód.|-Sekvenční diagramy zobrazit interakce mezi objekty v kódu.<br />-Diagramy vrstev zobrazit závislosti mezi třídami. Může být ověřen aktualizovaný kód proti diagramu vrstev.<br />– Diagramy tříd zobrazit třídy v kódu.|  
  
## <a name="external-resources"></a>Externí zdroje  
  
|**Kategorie**|**Odkazy**|  
|------------------|---------------|  
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How do I video: postup vytvoření a použití modelů a diagramů UML (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML sadou Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How do I řadu: nástroje UML a rozšíření (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogy**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technické články a deníky**|[Centrum architektury MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Pokyny k nástrojům architektury sady Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)|  
  
## <a name="see-also"></a>Viz také  
 [Použití modelů v Agilním vývoji](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)   
 [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)   
 [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)   
 [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)   
 [Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)



