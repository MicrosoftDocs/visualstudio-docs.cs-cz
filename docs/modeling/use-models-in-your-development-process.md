---
title: Použití modelů ve vývojových procesech
description: Seznamte se s tím, že v aplikaci Visual Studio můžete použít model, který vám pomůže pochopit a změnit systém, aplikaci nebo komponentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbc817ca7bdf08c4e5ceee79a1e1113b4dd26e0c
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361427"
---
# <a name="use-models-in-your-development-process"></a>Použití modelů ve vývojových procesech

V aplikaci Visual Studio můžete použít model, který vám pomůže pochopit a změnit systém, aplikaci nebo komponentu. Model vám může přispět k vizualizaci světa, ve kterém váš systém funguje, objasnit potřeby uživatelů, definovat architekturu vašeho systému, analyzovat kód a ujistit se, že váš kód splňuje požadavky. Viz [video o kanálu 9: vylepšení architektury prostřednictvím modelování](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé typy modelů, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Modely vám můžou pomáhat několika způsoby:

- Vytváření diagramů modelování vám pomůže objasnit koncepty, které se týkají požadavků, architektury a návrhu vysoké úrovně. Další informace najdete v tématu [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

- Práce s modely vám může pomáhat odhalit nekonzistence v požadavcích.

- Komunikace s modely vám pomůže sdělit důležité koncepty méně dvojznačnější než u přirozeného jazyka. Další informace najdete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).

- V některých případech můžete použít modely pro generování kódu nebo jiných artefaktů, například schémat databáze nebo dokumentů. Například komponenty modelování sady Visual Studio jsou generovány z modelu. Další informace najdete v tématu [generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).

Modely můžete používat v nejrůznějších procesech, od extrémní agilní až po vysokou procedury.

## <a name="use-models-to-reduce-ambiguity"></a>Použití modelů ke snížení nejednoznačnosti

Jazyk modelování je méně dvojznačný než přirozený jazyk a je navržený tak, aby při vývoji softwaru vyjádřil nápady, které obvykle vyžadují.

Pokud má váš projekt malý tým na základě agilních postupů, můžete použít modely, které vám pomohou objasnit uživatelské scénáře. Při diskusích se zákazníkem na jejich potřeby může vytváření modelu generovat užitečné otázky mnohem rychleji a v širší oblasti produktu, než psát kód špičky nebo prototypy.

Pokud je váš projekt velký a obsahuje týmy v různých částech světa, můžete použít modely, které vám pomohou s tím, že požadavky a architektura budou mnohem efektivnější, než můžete použít prostý text.

V obou případech vytvoření modelu téměř vždy vede k výraznému snížení nekonzistencí a nejednoznačnosti. Různí účastníci mají často různé porozumění obchodnímu světě, ve kterém systém funguje, a různí vývojáři mají často různé informace o tom, jak systém funguje. Použití modelu jako fokusu diskuze obvykle zveřejňuje tyto rozdíly. Další informace o použití modelu ke snížení nekonzistencí najdete v tématu [model uživatelských požadavků](../modeling/model-user-requirements.md).

## <a name="use-models-with-other-artifacts"></a>Použití modelů s jinými artefakty

Model není sám o sobě specifikací požadavků nebo architekturou. Jedná se o nástroj, který vám umožní vyjádřit některé aspekty těchto věcí podrobněji, ale ne všechny koncepty požadované během návrhu softwaru. Modely by se proto měly používat společně s jinými komunikačními prostředky, jako jsou stránky nebo odstavce OneNotu, systém Microsoft Office dokumenty, pracovní položky v Team Foundation nebo rychlé poznámky na stěně projektové místnosti. Kromě poslední položky mohou být všechny tyto typy objektů propojeny s částmi prvků modelu.

Další aspekty specifikace, které se obvykle používají společně s modely, zahrnují následující. V závislosti na měřítku a stylu vašeho projektu můžete použít několik těchto aspektů nebo nepoužívat vůbec:

- Uživatelské scénáře. Uživatelský scénář je krátký popis, který je popsán u uživatelů a dalších zúčastněných stran, z hlediska chování systému, který bude dodán v jednom z iterací projektu. Typický uživatelský scénář začíná "zákazník bude moci..." Uživatelský scénář může představovat skupinu případů použití nebo může definovat rozšíření případů použití, které byly dříve vyvinuty. Definování nebo rozšíření případů použití pomáhá zajistit, aby byl uživatelský scénář jasný.

- Žádosti o změnu. Žádost o změnu v formálním projektu je velmi podobná uživatelskému scénáři v agilním projektu. Agilní přístup zpracovává všechny požadavky jako změny, co bylo vyvinuto v předchozích iteracích.

- Popis případu použití Případ použití představuje jeden způsob, jakým uživatel komunikuje se systémem, aby dosáhl konkrétního cíle. Úplný popis zahrnuje cíl, hlavní a alternativní sekvence událostí a výjimečné výsledky. Diagram případu použití pomáhá shrnout a poskytnout přehled o případech použití.

- Řešení. Scénář je poměrně podrobný popis posloupnosti událostí, která ukazuje, jak systém, uživatelé a další systémy vzájemně spolupracují za účelem poskytování hodnoty zúčastněným stranám. Může mít podobu prezentace uživatelského rozhraní nebo prototypu uživatelského rozhraní. Může popsat jeden případ použití nebo posloupnost případů použití.

- Slovník. Glosář požadavků projektu popisuje slova, se kterými zákazníci projednávají svůj svět. Tyto podmínky by měly používat i modely uživatelských rozhraní a požadavků. Diagram tříd může přispět k objasnění vztahů mezi většinou těchto podmínek. Vytváření diagramů a glosáře nejenom omezuje počet nedorozumění uživatelů a vývojářů, ale i téměř vždy zveřejňuje nepochopení mezi různými obchodními stranami.

- Obchodní pravidla. Mnoho obchodních pravidel lze vyjádřit jako invariantní omezení pro přidružení a atributy v modelu třídy požadavků a jako omezení pro sekvenční diagramy.

- Návrh vysoké úrovně. Popisuje hlavní části a jejich vzájemné přizpůsobení. Diagramy komponent, sekvencí a rozhraní jsou hlavní součástí návrhu vysoké úrovně.

- Vzory návrhu. Popište pravidla návrhu, která jsou sdílena napříč různými částmi systému.

- Specifikace testu. Testovací skripty a návrhy pro testovací kód mohou sloužit k popsání sekvencí testovacích kroků, které popisují sekvence a sekvenční diagramy. Systémové testy by se měly vyjádřit v souvislosti s modelem požadavků, aby je bylo možné snadno změnit při změně požadavků.

- Plán projektu. Plán projektu nebo nevyřízené položky definují, kdy bude každá funkce doručena. Jednotlivé funkce můžete definovat tak, že uvedete, jaké případy použití a obchodní pravidla implementuje nebo rozšiřuje. Můžete buď odkazovat na případy použití a obchodní pravidla přímo v plánu, nebo můžete definovat sadu funkcí v samostatném dokumentu a použít tituly funkcí v plánu.

## <a name="use-models-in-iteration-planning"></a>Použití modelů při plánování iterací

I když se všechny projekty liší ve své škále a organizaci, typický projekt je plánován jako série iterací mezi dvěma a šesti týdny. Je důležité naplánovat dostatek iterací, aby bylo možné použít zpětnou vazbu z počátečních iterací pro úpravu rozsahu a plánů pro pozdější iterace.

Můžete se setkat s následujícími návrhy, které vám pomůžou využít výhody modelování v iterativním projektu.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Zostření se soustředit na jednotlivé přístupy iterace

V rámci každé iterace se používají modely, které vám pomůžou definovat, co se má doručit na konci iterace.

- Nevytvářejte model všeho podrobněji v počátečních iteracích. V první iteraci vytvořte diagram tříd pro hlavní položky v uživatelském glosáři, nakreslete diagram hlavních případů použití a nakreslete diagram hlavních součástí. Nepište žádné z těchto podrobných podrobností, protože podrobnosti se později v projektu změní. Pomocí podmínek definovaných v tomto modelu vytvořte seznam funkcí nebo hlavních uživatelských scénářů. Přiřaďte funkce k iteracím, abyste přibližně vyrovnali odhadované zatížení v celém projektu. Tato přiřazení se později v projektu změní.

- Zkuste implementovat zjednodušené verze všech nejdůležitějších případů použití v předčasném opakování. Rozšíří tyto případy použití v pozdějších iteracích. Tento přístup pomáhá snižovat riziko, že v rámci požadavků zjišťuje chybu nebo v rámci architektury příliš pozdě v projektu.

- Na konci každé iterace si podržíte požadavky Workshop, abyste definovali podrobně požadavky nebo uživatelské scénáře, které budou vyvinuty v další iteraci. Pozvání uživatelů a obchodních účastníků, kteří mohou rozhodnout o prioritách, a také vývojáře a testery systému. Umožňuje třem hodinám definovat požadavky na iteraci na 2 týdny.

- Cílem dílny je, aby všichni souhlasili s tím, co bude provedeno na konci další iterace. Použijte modely jako jeden z nástrojů, které vám pomůžou tyto požadavky vyjasnit. Výstupem dílny je nevyřízené položky iterace: to je seznam vývojářských úloh v Team Foundation a testovacích sadách v [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] .

- V části požadavky Workshop proberte návrh pouze v případě, že potřebujete určit odhady pro úlohy vývoje. V opačném případě ponechte diskuzi na chování systému, které uživatelé můžou pracovat přímo. Model požadavků si ponechte oddělené od modelu architektury.

- Netechničtí účastníci většinou nemají žádné problémy s porozuměním diagramům UML s některými pokyny.

### <a name="link-model-to-work-items"></a>Propojit model s pracovními položkami

Až se požadavky Workshop vyvíjejí, vypracovali Podrobnosti modelu požadavků a propojí model s vývojovými úkoly. To lze provést propojením pracovních položek v rámci serveru Team Foundation s prvky v modelu.

Libovolný prvek můžete propojit s pracovními položkami, ale nejužitečnější prvky jsou následující:

- Komentáře popisující obchodní pravidla nebo požadavky na službu Quality of Service. Další informace najdete v tématu [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

### <a name="link-model-to-tests"></a>Propojit model s testy

Pomocí modelu požadavků můžete obsloužit návrh testů přijetí. Vytvářejte tyto testy souběžně s vývojovou prací.

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
|**Technické články a deníky**|[Centrum architektury MSDN](/previous-versions/dn630665(v=msdn.10))<br /><br /> [Pokyny k nástrojům architektury sady Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Viz také:

- [Používání modelů v agilním vývoji](/previous-versions/ff398061(v=vs.140))
- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)
- [Strukturování řešení modelování](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]