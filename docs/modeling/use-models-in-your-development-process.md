---
title: Použití modelů ve vývojových procesech
description: V tomto Visual Studio můžete použít model, který vám pomůže porozumět systému, aplikaci nebo komponentě a změnit je.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095a6f17691d3265320a7b77905f70903bec1cb5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388500"
---
# <a name="use-models-in-your-development-process"></a>Použití modelů ve vývojových procesech

V Visual Studio můžete použít model, který vám pomůže pochopit a změnit systém, aplikaci nebo komponentu. Model vám může pomoct vizualizovat svět, ve kterém váš systém funguje, objasnit potřeby uživatelů, definovat architekturu systému, analyzovat kód a zajistit, aby váš kód splňoval požadavky. Podívejte [se na video Channel 9: Vylepšení architektury prostřednictvím modelování](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

Informace o tom, které Visual Studio podporují jednotlivé typy modelů, najdete v tématu [Podpora verzí pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Modely vám můžou pomoct několika způsoby:

- Kreslení diagramů modelování vám pomůže objasnit koncepty spojené s požadavky, architekturou a návrhem vysoké úrovně. Další informace najdete v tématu [Požadavky na model uživatele.](../modeling/model-user-requirements.md)

- Práce s modely vám může pomoct odhalit nekoistence v požadavcích.

- Komunikace s modely vám pomůže komunikovat důležité koncepty méně nejednoznačně než s přirozeným jazykem. Další informace najdete v tématu [Modelování architektury aplikace.](../modeling/model-your-app-s-architecture.md)

- Modely můžete někdy použít ke generování kódu nebo jiných artefaktů, jako jsou schémata databáze nebo dokumenty. Například komponenty modelování v Visual Studio se generují z modelu. Další informace najdete v tématu [Generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).

Modely můžete používat v široké škále procesů, od extrémní agilní až po vysokou proceduřování.

## <a name="use-models-to-reduce-ambiguity"></a>Použití modelů ke snížení nejednoznačnosti

Modelovací jazyk je méně nejednoznačný než přirozený jazyk a je navržený tak, aby vyjadřovat nápady, které se obvykle při vývoji softwaru vyžaduje.

Pokud má váš projekt malý tým, který postupuje podle agilní postupů, můžete použít modely, které vám pomohou objasnit uživatelské scénáře. V diskuzích se zákazníkem o jejich potřebách může vytvoření modelu generovat užitečné otázky mnohem rychleji a v širší oblasti produktu, než psaní špeku nebo prototypu kódu.

Pokud je váš projekt velký a zahrnuje týmy v různých částech světa, můžete pomocí modelů lépe komunikovat požadavky a architekturu mnohem efektivněji než v prostém textu.

V obou případech vytváření modelu téměř vždy vede k výraznému snížení nekonziferencí a nejednoznačností. Different stakeholders frequently have different understandings of the business world in which the system works, and different developers frequently have different understandings of how the system works. Použití modelu jako zaměření diskuze obvykle tyto rozdíly odhalí. Další informace o použití modelu ke snížení nekonziferencí najdete v tématu Požadavky na [uživatele modelu.](../modeling/model-user-requirements.md)

## <a name="use-models-with-other-artifacts"></a>Použití modelů s jinými artefakty

Model sám o sobě není specifikací požadavků ani architekturou. Jedná se o nástroj, který jasněji vyjadřuje některé aspekty těchto věcí, ale ne všechny koncepty vyžadované během návrhu softwaru je možné vyjádřit. Modely by se proto měly používat společně s jinými komunikačními prostředky, jako jsou stránky nebo odstavce OneNotu, dokumenty systém Microsoft Office, pracovní položky v Team Foundation nebo přilepené poznámky na zdi projektové místnosti. Kromě poslední položky mohou být všechny tyto typy objektů propojeny s částmi prvků modelu.

Mezi další aspekty specifikace, které se obvykle používají společně s modely, patří následující. V závislosti na rozsahu a stylu projektu můžete použít několik z těchto aspektů nebo vůbec žádné použít:

- Uživatelské scénáře. Uživatelský scénář je krátký popis aspektu chování systému, který se bude doručovat v jedné z iterací projektu, probíráme s uživateli a dalšími účastníky. Typický uživatelský scénář začíná "Zákazník bude moct... Uživatelský scénář může představovat skupinu případů použití nebo může definovat rozšíření dříve vyvinutých případů použití. Definování nebo rozšíření případů použití pomáhá srozumitelnějšímu uživatelskému scénáři.

- Žádosti o změnu. Žádost o změnu ve formálnějším projektu je velmi podobná uživatelskému scénáři v agilní projektu. Agilní přístup považuje všechny požadavky za změny toho, co bylo vyvinuto v předchozích iteracích.

- Popis případu použití Případ použití představuje jeden ze způsob, jakým uživatel komunikuje se systémem, aby dosáhl konkrétního cíle. Úplný popis obsahuje cíl, hlavní a alternativní sekvence událostí a mimořádné výsledky. Diagram případu použití pomáhá sumarizovat případy použití a poskytovat přehled o těchto případech.

- Scénáře. Scénář je poměrně podrobný popis posloupnosti událostí, které ukazují, jak systém, uživatelé a další systémy spolupracují, aby zúčastněným stranám poskytovaly hodnotu. Může mít podobu prezentace uživatelského rozhraní nebo prototypu uživatelského rozhraní. Může popisovat jeden případ použití nebo posloupnost případů použití.

- Slovníček. Glosář požadavků projektu popisuje slova, se kterým zákazníci diskutují o svém světě. Tyto termíny by měly používat také modely uživatelského rozhraní a požadavků. Diagram tříd může pomoci objasnit vztahy mezi většinou těchto termínů. Vytváření diagramů a glosáře nejen omezuje nedorozumění mezi uživateli a vývojáři, ale také téměř vždy odhalí nedorozumění mezi různými obchodními účastníky.

- Obchodní pravidla: Mnoho obchodních pravidel lze vyjádřit jako invariantní omezení přidružení a atributů v modelu tříd požadavků a jako omezení v sekvenčních diagramech.

- Návrh na vysoké úrovni. Popisuje hlavní části a jejich prolnutí do sebe. Diagramy komponent, sekvencí a rozhraní jsou hlavní součástí návrhu vysoké úrovně.

- Vzory návrhu. Popis pravidel návrhu, která jsou sdílená v různých částech systému

- Specifikace testů. Testovací skripty a návrhy testovacího kódu mohou dobře využívat diagramy aktivit a sekvencí k popisu posloupností testovacích kroků. Systémové testy by měly být vyjádřeny v modelu požadavků, aby je bylo možné snadno změnit při změně požadavků.

- Plán projektu. Plán projektu nebo backlog definuje, kdy se jednotlivé funkce doručí. Jednotlivé funkce můžete definovat tak, že uvedete, jaké případy použití a obchodní pravidla implementuje nebo rozšiřuje. Na případy použití a obchodní pravidla můžete odkazovat přímo v plánu, nebo můžete definovat sadu funkcí v samostatném dokumentu a používat názvy funkcí v plánu.

## <a name="use-models-in-iteration-planning"></a>Použití modelů při plánování iterací

I když se všechny projekty ve svém rozsahu a organizaci liší, typický projekt se plánuje jako série iterací mezi dvěma a šesti týdny. Je důležité naplánovat dostatek iterací, aby bylo možné použít zpětnou vazbu z počátečních iterací k úpravě rozsahu a plánů pro pozdější iterace.

Následující návrhy vám můžou pomoct realizovat výhody modelování v iterativním projektu.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Zostření fokusu při každé iteraci

S tím, jak se jednotlivé iterace přistupují, použijte modely, které vám pomůžou definovat, co se má na konci iterace doručit.

- V počátečních iteracích nemodelovat všechno podrobně. V první iteraci vytvořte diagram tříd pro hlavní položky v uživatelském glosáře, nakreslete diagram hlavních případů použití a nakreslete diagram hlavních komponent. Žádné z nich podrobně nepopisujete, protože podrobnosti se později v projektu změní. Pomocí termínů definovaných v tomto modelu můžete vytvořit seznam funkcí nebo hlavních uživatelských příběhů. Přiřaďte tyto funkce iteracím, aby se přibližně vyrovnaly odhadované úlohy v rámci celého projektu. Tato přiřazení se později v projektu změní.

- Pokuste se implementovat zjednodušené verze všech nejdůležitějších případů použití v rané iteraci. Rozšiřte tyto případy použití v pozdějších iteracích. Tento přístup pomáhá snížit riziko, že se v projektu objeví chyba v požadavcích nebo architektura příliš pozdě, než aby s ní něco udělal.

- Na konci každé iterace se nachází workshop s požadavky, který podrobně definuje požadavky nebo uživatelské scénáře, které se budou vyvíjet v další iteraci. Pozvěte uživatele a obchodní účastníky, kteří mohou rozhodnout o prioritách, a také vývojáře a testery systému. Po dobu tří hodin můžete definovat požadavky na dvoutýdenní iteraci.

- Cílem workshopu je, aby se všichni shodli na tom, čeho se dosáhne na konci další iterace. Jako jeden z nástrojů použijte modely, které vám pomůžou objasnit požadavky. Výstupem workshopu je backlog iterace, to znamená seznam vývojových úloh v Team Foundation a testovacích sadách v [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] .

- V workshopu o požadavcích proberte návrh pouze v případě, že potřebujete určit odhady pro úkoly vývoje. V opačném případě pokračujte v diskuzi o chování systému, se kterou se uživatelé mohou přímo secházet. Udržujte model požadavků oddělený od modelu architektury.

- Netechnické zúčastněné strany obvykle nemají žádné problémy s pochopením diagramů UML s některými pokyny od vás.

### <a name="link-model-to-work-items"></a>Propojení modelu s pracovními položkami

Po workshopu o požadavcích propracujte podrobnosti modelu požadavků a propoojte ho s úkoly vývoje. Můžete to provést propojením pracovních položek v Team Foundation s prvky v modelu.

S pracovními položkami můžete propojit libovolný prvek, ale nejužitečnější prvky jsou následující:

- Komentáře popisující obchodní pravidla nebo požadavky na kvalitu služeb Další informace najdete v tématu [Požadavky na model uživatele.](../modeling/model-user-requirements.md)

### <a name="link-model-to-tests"></a>Propojení modelu s testy

Pomocí modelu požadavků můžete řídit návrh akceptačních testů. Vytvářejte tyto testy souběžně s vývojovou prací.

Další informace o tomto postupu naleznete v tématu [vývoj testů z modelu](../modeling/develop-tests-from-a-model.md).

### <a name="estimate-remaining-work"></a>Odhad zbývající práce

Model požadavků může přispět k odhadu celkové velikosti projektu ve vztahu k velikosti každé iterace. Vyhodnocení počtu a složitosti případů použití a tříd vám může pomáhat odhadnout vývojovou práci, která se bude vyžadovat. Pokud jste dokončili několik prvních iterací, povýšení požadavků a i nadále pokrytí požadavků může poskytovat přibližnou míru nákladů a rozsahu zbytku projektu.

Na konci každé iterace zkontrolujte přiřazení požadavků k budoucím iteracím. Může být užitečné znázornit stav softwaru na konci každé iterace jako podsystém v diagramu případu použití. V diskusích můžete přesunout případy použití a rozšíření případů použití z jednoho z těchto subsystémů do jiného.

## <a name="levels-of-abstraction"></a>Úrovně abstrakce

Modely mají ve vztahu k softwaru rozsah abstrakce. Nejvíc konkrétní modely představují přímo kód programu a většina abstraktních modelů představuje obchodní koncepty, které mohou nebo nemusí být v kódu zastoupeny.

Model lze zobrazit pomocí několika druhů diagramů. Informace o modelech a diagramech najdete v tématu [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

Různé druhy diagramů jsou užitečné pro popis návrhu na různých úrovních abstrakce. Mnoho typů diagramů je užitečné na více než jedné úrovni. Tato tabulka ukazuje, jak lze použít každý typ diagramu.

|Úroveň návrhu|Typy diagramů|
|-|-|
|Obchodní proces<br /><br /> Pochopení kontextu, ve kterém se váš systém bude používat, vám pomůže pochopit, co uživatelé z něho potřebují.|– Diagramy koncepčních tříd popisují obchodní koncepty používané v rámci obchodního procesu.|
|Požadavky uživatelů<br /><br /> Definice toho, co uživatelé potřebují z vašeho systému.|– Obchodní pravidla a požadavky na kvalitu služeb můžete popsat v samostatných dokumentech.|
|Návrh vysoké úrovně<br /><br /> Celková struktura systému: hlavní komponenty a jejich vzájemná spolupráce.|– Diagramy závislosti popisují, jak je systém strukturovaný, do vzájemně závislých součástí. Pomocí diagramů závislostí můžete ověřit kód programu, aby se zajistilo, že bude vyhovovat architektuře.|
|Analýza kódu<br /><br /> Diagramy lze generovat z kódu.|-Diagramy závislosti znázorňují závislosti mezi třídami. Aktualizovaný kód lze ověřit proti diagramu závislostí.<br />Diagramy tříd zobrazují třídy v kódu.|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|-|-|
|**Videa**|![odkaz na video ](../data-tools/media/playvideo.gif) [MSDN jak mám videa: jak vytvářet a používat modely a diagramy UML (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))<br /><br /> ![odkaz na video ](../data-tools/media/playvideo.gif) [kanál 9: UML se sadou Visual Studio 2010](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![odkaz na video ](../data-tools/media/playvideo.gif) [MSDN postup I série: nástroje a rozšiřitelnost UML (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**Fóra**|- [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogy**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Technické články a deníky**|[Centrum architektury MSDN](/previous-versions/dn630665(v=msdn.10))|

## <a name="see-also"></a>Viz také

- [Používání modelů v agilním vývoji](/previous-versions/ff398061(v=vs.140))
- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)
- [Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]