---
title: Modelování uživatelských požadavků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab92a08aa7359aa4393b3356384a4ccc352afb27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776483"
---
# <a name="model-user-requirements"></a>Modelování uživatelských požadavků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio vám pomáhá pochopit, diskutovat a sdělovat požadavky uživatelů ve vytvoření diagramů o svých aktivit a části systému hraje v usnadňuje dosáhli svých cílů. Model požadavků je sada tyto diagramy, z nichž každý se zaměřuje na různé aspekty potřebám uživatelů. Video ukázku naleznete v tématu: [modelování obchodní domény](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Které verze sady Visual Studio podporovat každý typ modelu najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Požadavky na modelu vám pomůže:  
  
- Zaměřte se na chování systému externí, odděleně od jeho vnitřní strukturou.  
  
- Popište uživatelů a zúčastněných stran pomocí musí mít mnohem méně nejednoznačnost, než v přirozeném jazyce.  
  
- Definujte konzistentní Glosář termínů, které je možné uživatele, vývojáři a testeři.  
  
- Snížit prostoje a nekonzistence v požadavcích.  
  
- Omezení práce potřebné reakce na změny požadavků.  
  
- Naplánujte pořadí, ve kterém se funkce vyvinuté.  
  
- Pomocí modelu jako základ pro testy systému, což jasný vztah mezi testy a požadavky. Při změně požadavků, tato relace vám pomůže aktualizovat testy správně. Tím je zajištěno, že systém splňuje nové požadavky.  
  
  Požadavky na model poskytuje největší výhody, pokud jej používat k aktivní diskuze s uživateli nebo svých zástupci a opakování na začátku každé iterace. Není nutné pro dokončení podrobně před psaním kódu. Částečně funkční aplikaci, i v případě velmi výrazně zjednodušené, obecně tento balíček je základem nejvíce podporovat diskuzi o požadavky s uživateli. Model je účinný způsob, jak vytvořit souhrn výsledků tyto diskuse. Další informace najdete v tématu [použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  V těchto tématech "systém" znamená, že systém nebo aplikace, kterou vyvíjíte. Rozsáhlá kolekce řadu softwarových a hardwarových součástí; může být nebo si jednu aplikaci; nebo softwarová součást uvnitř větší systému. V každém případě model požadavků popisuje chování, které je viditelné z vnějšku systému prostřednictvím uživatelského rozhraní nebo rozhraní API.  
  
## <a name="common-tasks"></a>Obecné úlohy  
 Můžete vytvořit několik různých zobrazení podle požadavků uživatelů.  Každé zobrazení obsahuje konkrétního typu informací.  Při vytváření těchto zobrazení je nejvhodnější často přesunout na další. Můžete spustit z jakékoli zobrazení.  
  
|Diagram nebo dokumentu|Co se popisuje v modelu požadavky|Oddíl|  
|-------------------------|-----------------------------------------------|-------------|  
|Použití diagramu případu|Kdo používá systém a co dělají s ním.|[Popisující, jak se váš systém používá](#UseCases)|  
|Třída koncepční diagram|Glosář typů, které se používají k popisu požadavků; typy viditelný na rozhraní v systému.|[Definuje termíny používané k popisu požadavků](#RequirementsClasses)|  
|Diagram činnosti|Tok práce a informací mezi aktivity uživatele nebo systému nebo jeho části.|[Zobrazuje pracovní postup mezi uživateli a systému](#Workflow)|  
|Sekvenční diagram|Sekvence interakcí mezi uživateli a systému nebo jeho části. Alternativní zobrazení diagramu činnosti.|[Zobrazení interakce mezi uživateli a systému](#Sequences)|  
|Další dokumenty nebo pracovních položek|Kritéria výkonu, zabezpečení, využitelnost a spolehlivost.|[Popisující kvality požadavků na služby](#QoSRequirements)|  
|Další dokumenty nebo pracovních položek|Omezení a pravidla není specifická pro konkrétní případ použití|[Zobrazení obchodních pravidel](#BusinessRules)|  
  
 Všimněte si, že většina typů diagramu můžete používat pro jiné účely. Přehled typů diagramu, naleznete v tématu [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md). Základní informace o vytvoření diagramů naleznete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
##  <a name="UseCases"></a> Popisující, jak se váš systém používá  
 Vytvořte diagramy případu použití a popisují, kdo používá systém a co využijí ho. Případ použití představuje cíl uživatele systému a postup jejich provést k dosažení cíle.  
  
 Jako příklad online jídla prodej systému musí umožňovat zákazníkům z nabídky vyberte položky a musí umožňovat zadání restaurace aktualizace v nabídce. To lze shrnout v diagramu případu použití:  
  
 ![Případy použití pro zákazník a restaurace](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 Můžete také ukazují, jak případu použití se skládá z menších případů. Například pokrmu je součástí nákupu jídla, která zahrnuje také platby a doručování:  
  
 ![Systém se podílí na platbu, ale ne doručování. ](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 Můžete také zobrazit, které případy použití jsou zahrnuty v rámci systému, které vyvíjíte. Například systém na obrázku neúčastní poskytovat jídla případu použití. Díky tomu nastavte kontext pro vývojové práce. (V diagramu případu použití subsystému kontejnery lze použít k reprezentaci systému nebo její součásti.)  
  
 Pomáhá také váš tým popisují, které budou zahrnuty v následných vydáních. Například může projednat, zda v počáteční verzi systému, platit pro jídla uspořádána přímo mezi restauraci a zákazníků, místo používání přes systém. V takovém případě můžete platit za jídla přesunout mimo systém společnosti Dinner Now rámeček pro počáteční verze.  
  
 Diagram případu použití pouze poskytuje přehled případy použití. Pokud chcete poskytnout podrobné popisy, můžete propojit případy použití v diagramu oddělit jednotlivé dokumenty a k jiným diagramům. Zjistěte, jak to provést, najdete v článku [propojení případu použití s dokumenty a diagramy](../modeling/link-a-use-case-to-documents-and-diagrams.md).  
  
 Náčrt diagramu případu použití pomáhá vašemu týmu:  
  
- Zaměřte se na co očekávat uživatelé dělat s systému, aniž by se odváděna podle podrobnosti implementace.  
  
- Zjistěte rozsah vašeho systému nebo konkrétní verzí systému.  
  
  Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Podrobnější informace o tom, jak vytvářet případy použití|[Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Prvků v diagramu případu použití|[Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)|  
|Postupy při vývoji kódu z případy použití|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> Definuje termíny používané k popisu požadavků  
 Můžete použít diagramy tříd UML a pomohou vám vytvořit konzistentní slovník business koncepty použité k těmto účelům:  
  
- Uživatelé sami fattica firmy, ve kterém systém funguje.  
  
- K popisu potřebám uživatelů, třeba v popisech případy použití, obchodní pravidla a uživatelskými scénáři.  
  
- Typy informací si vyměňují v rozhraní API systému nebo prostřednictvím uživatelského rozhraní.  
  
- Popis systému nebo akceptační testy.  
  
  Při použití pro tento účel, obsah, diagram tříd UML je volána diagramu koncepční tříd. (Je také označován jako *doménový model* nebo *analýzy třídy modelu*.)  
  
  V diagramu tříd koncepční zobrazit pouze tyto třídy potřebné v popisech požadavků, aniž by se zobrazil všech podrobností interního návrhu systému. Diagram nezobrazuje žádné podrobnosti interního návrhu systému. Můžete neukazuje obvykle operace nebo rozhraní na koncepční třídy.  
  
  Například lze nakreslit tyto koncepční třídy pro systém Dinner Now:  
  
  ![Třídy nabídka, objednávka, položka nabídky položka objednávky. ](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
  Koncepční třídy diagram představuje slovník podmínky, které budete používat v celé model požadavků. Například v podrobný popis použití případu objednávka pokrmu, můžete například napsat:  
  
  Zákazník vybere *nabídky* ze kterého se má vytvořit *pořadí*a potom vytvoří *pořadí položek* v *pořadí* tak, že vyberete  *Položky nabídky* z *nabídky*.  
  
  Všimněte si, jak termíny používané v tomto popisu jsou názvy tříd v modelu. Diagram zruší nejednoznačnosti vztahy mezi těmito třídami. Například to, ukazují, že jednotlivé objednávky souvisí s právě jednu nabídku.  
  
  Nedorozuměním o požadavcích uživatelů můžete sledovat často k nedorozuměním o podrobné význam slova. Například většina restaurace budou mít sdílené znalost podmínky nabídky a pořadí, ale je méně jasné rozdíl mezi položky v objednávce a položky v nabídce. Pokud požadavky byly diskutovány s zúčastněné obchodní strany, je důležité ke zveřejnění těchto rozdílů. Diagram tříd je užitečným nástrojem při vysvětlení podmínky a jejich vztahy.  
  
  Třída Koncepční model mohl vytvořit základní slovník, pomocí kterého lze popsat váš systém obchodní logiku. Ale třídy v softwaru obvykle bude mnohem složitější než konceptuální model, protože implementace nutné vzít v úvahu problémy, jako je výkon, distribuce, flexibility a dalších faktorů. Několik různých implementací koncepční třídy se často nacházejí v jednom systému.  
  
  Například můžou být reprezentované objednávky v XML, SQL, HTML a C# v různých částí systému a na různých rozhraní mezi částmi. Přidružení mezi objednávkou a nabídky můžou být reprezentované mnoha různými způsoby, například odkazy v kódu jazyka C#, vztahy v databázi, nebo křížové odkazy. ID ve formátu XML. Ale i přes tyto odchylky Koncepční model poskytuje důležité informace, které platí ve všech součástí softwaru. Diagram tříd v příkladu nás informuje, že v každé implementace bude pouze jeden nabídky spojené s každou pořadí.  
  
  Náčrt diagramu třídy požadavky pomáhá vašemu týmu:  
  
- Definovat a standardizovat základní termínů používaných v diskuzích k žádostem o potřebám uživatelů.  
  
- Vysvětlení vztahy mezi těmito podmínkami.  
  
  Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Podrobnější informace o vyhledání požadavky na třídy|[Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementy diagramu koncepční tříd|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|  
|Postupy při vývoji kódu z koncepční tříd|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
 V diagramu tříd koncepční není obvykle vhodné umístit šipky na přidružení relevantní. Je to proto diagramu nepředstavuje implementace. Asociace reprezentují vztahy mezi objekty reálného světa. Následující [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření nastavit jiné směrové šipky jako výchozí: [vzorku: modelování UML domény funkce](http://go.microsoft.com/fwlink/?LinkId=213849).  
  
##  <a name="BusinessRules"></a> Zobrazení obchodních pravidel  
 Obchodní pravidlo je požadavek, který není spojen s případem použití konkrétní a by měl v celém systému.  
  
 Mnoho obchodní pravidla jsou omezení na vztahy mezi koncepční třídy. Můžete napsat tyto *statické obchodní pravidla* jako komentáře přidružené k příslušné třídy v diagramu tříd koncepční. Příklad:  
  
 ![Pravidlo v komentář připojený na třídu pořadí. ](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 *Dynamické obchodní pravidla* omezit povolený sledů událostí. Například pomocí diagramu pořadí nebo aktivity zobrazíte, že uživatel musí přihlásit, před provedením další operace ve vašem systému.  
  
 Nicméně mnoho dynamická pravidla můžete efektivněji a obecně zobrazovat nahrazením je statická pravidla. Například můžete přidat atribut typu Boolean zaznamenána v na třídu v koncepčním třídy modelu. By přidejte zaznamenána v jako neplatná následná protokolu v případu použití a přidejte ho jako předběžnou podmínku většinu dalších případů použití. Tento přístup umožňuje Vyhněte se definování všech možných kombinací sledů událostí. Je také flexibilnější když budete chtít do modelu přidat nové případy použití.  
  
 Všimněte si, že tady je o tom, jak definovat požadavky a, že se jedná o nezávislé implementace požadavky v kódu programu.  
  
 Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Podrobnější informace o hledání a záznam statický obchodní pravidla|[Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementy diagramu koncepční tříd|[Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)|  
|Postupy při vývoji kódu, který splňuje obchodní pravidla|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Popisující kvality požadavků na služby  
 Existuje několik kategorií kvality služby. Jsou to tyto země:  
  
- Výkon  
  
- Zabezpečení  
  
- Použitelnosti  
  
- Spolehlivost  
  
- Robustnost  
  
  Může obsahovat některé z těchto požadavků v popisech zvláštní případy. Další požadavky nejsou specifická pro případy použití a efektivní zapsány v samostatných dokumentu. Pokud je to možné, je vhodné dodržovat slovník určené model požadavků. V následujícím příkladu Všimněte si, že hlavní slova používaná požadavek na názvy objektů actor, případy použití a třídy v vidět na předchozím obrázku:  
  
  Pokud restaurace odstraní položku nabídky, zatímco zákazník je pokrmu, jakoukoli objednávky položku, který odkazuje na danou položku nabídky se zobrazí červeně.  
  
  Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Podrobnější informace o nahrávání kvality požadavků na služby|[Pokyny pro definování kvality požadavků na služby](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Připojení dalších dokumentů s případy použití|[Propojení případu použití s dokumenty a diagramy](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|Postupy při vývoji kódu, který dodržuje kvality požadavků na služby|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> Zobrazuje pracovní postup mezi uživateli a systému  
 Diagram aktivity můžete použít k zobrazení toku práce mezi různé případy použití. Je často užitečné Začněte model požadavků náčrt diagramu aktivit znázorňující hlavních úloh, které uživatelé provádějí - systémem i mimo něj.  
  
 Příklad:  
  
 ![Aktivita s tři akce a smyčku. ](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 Můžete nakreslit diagramy případů použití a diagramy činnosti k zobrazení různých zobrazení stejné informace.  Diagram případu použití je efektivnější v vnoření menší akce v rámci větší aktivitu, ale nezobrazuje pracovní postup. Příklad:  
  
 ![Případy použití pro předchozí akce](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 Všimněte si, že můžete také použít diagramy činnosti ke znázornění algoritmy v rámci vašeho softwaru, ale při použití diagramy pro obchodní proces, zaměřit se na akce, které jsou viditelné mimo systém.  
  
 Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Další informace o tom, jak definovat obchodní pracovní postupy|[Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|  
|Prvků v diagramu činnosti|[Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)|  
|Postupy při vývoji kódu z diagramů aktivit|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> Zobrazení interakce mezi uživateli a systému  
 Sekvenční diagram můžete použít k zobrazení výměny zpráv mezi systémem a externí aktéry nebo mezi částmi systému. To poskytuje přehled kroky v případu použití, který zobrazuje velmi jasně sekvence interakcí. Sekvenční diagramy jsou zvláště užitečné, pokud existuje, že několik interakci stranami v případu použití a taky Pokud váš systém používá rozhraní API.  
  
 Příklad:  
  
 ![Sekvenční diagram se systémem a objekty actor. ](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 Jednou z výhod sekvenčních diagramů je, že je snadno zjistit, jaké zprávy přicházejí na systém, který se sestavením. Návrhu systému, můžete nahradit jednoho životnost systému samostatné životnosti pro všechny jeho komponenty a pak zobrazení interakce mezi nimi v reakci na příchozí zprávy.  
  
 Další informace naleznete v následujících tématech:  
  
|Další informace o|Číst|  
|--------------------|----------|  
|Další informace o tom, jak definovat interakce|[Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Prvky v sekvenční diagram|[Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)|  
|Postupy při vývoji kódu v sekvenčních diagramů|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>Používání modelu ke snížení nekonzistence  
 Vytvoření modelu obvykle vede k výraznému snížení nekonzistence a nejednoznačnosti v podle požadavků uživatelů. Různé zúčastněné strany mají často různých porozumění obchodním světě, ve kterém systém funguje. Proto je první úkol k vyřešení těchto rozdílů mezi klienty.  
  
 Zjistíte, že mnoho dotazy týkající se obchodní domény vzniknou přirozeně při vytváření modelu. Vložením tyto otázky, které vaši uživatelé budou omezení potřeby změny v pozdější fázi v projektu. Tady jsou některé konkrétní otázky, můžete nejprve položte si otázku a Vyzvěte zúčastněné obchodní strany, pokud je odpověď nejasné:  
  
- Pro každou třídu v modelu požadavky na dotaz "co případ použití vytváří instance této třídy?" Například v objednání jídla služby online, můžete pokládat, "co případ použití vytvoří instance třídy nabídka?" To vedlo k diskusi o tom, jak nové restaurace je zaregistrovaný do služby a přispívá nabídku. Podobné dotazy můžete požádat o co vytvoří nebo změní atributy a asociace.  
  
- Pro každý případ použití v modelu požadavky pokuste popsat, výsledek nebo neplatná následná z každý případ použití v slova poskytované diagramy tříd. Je často užitečné zobrazit vliv případu použití podle navrhování instance tříd, před a po výskytu případu použití. Například když je ve stavu "položka nabídky je přidána do objednávky zákazníka" Neplatná následná pro případ použití, náčrt instance tříd objednávka a položka nabídky. Zobrazte účinky případ použití, jako je například nový odkaz či nový objekt jinou barvou, nebo nový výkres. To často vede k diskuse o tom, jaké informace je nutné v modelu. I když se požadavky na třídy nejsou přímo starosti s implementací, popisují informace, které váš systém potřebovat k ukládání a vysílání.  
  
- Požádejte o omezení pro atributy a asociace, zejména omezení zahrnující více než jeden atribut nebo přidružení.  
  
- Požádejte o platné a neplatné pořadí případy použití, vykreslování diagramů pořadí nebo aktivity pro ilustraci je.  
  
  Prozkoumáním vztahy mezi zobrazení, která poskytují různé diagramy vy tak rychle porozumíte hlavní koncepty, které vaši uživatelé pracovat, a pomohly jim pochopit, co potřebují ze systému. Také dosáhnout lepší představu, jaké požadavky jsou zúčastněné strany některých nejméně o. Můžete naplánovat pro vývoj tyto funkce alespoň ve zjednodušené podobě, v rané fázi projektu, aby uživatelé mohli experimentovat s nimi.  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)   
 [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)   
 [Ukázkové rozšíření VS: Funkce modelování UML domény](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [Ukázka rozšíření VS: Barevné prvky UML podle stereotypu](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Ukázka rozšíření VS: Propojení elementů UML diagramů, soubory a další prvky](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [Ukázka rozšíření VS: Zarovnání tvarů v diagramu UML](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [Video: Modelování obchodní domény](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



