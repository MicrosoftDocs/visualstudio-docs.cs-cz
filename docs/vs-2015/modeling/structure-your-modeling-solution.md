---
title: Strukturování řešení modelování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0c001ec8310759309c88c49c37050516b110b81
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850807"
---
# <a name="structure-your-modeling-solution"></a>Strukturujte svá řešení modelování

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li efektivně používat modely ve vývojovém projektu, členové týmu musí být schopni pracovat na modelech různých částí projektu ve stejnou dobu. Toto téma navrhuje schéma pro rozdělení aplikace do různých částí, které odpovídají vrstvám v rámci celkového diagramu vrstev.

Chcete-li spustit projekt nebo dílčí projekt rychle, je vhodné mít šablonu projektu, která následuje za strukturou projektu, kterou jste si zvolili. Toto téma popisuje, jak vytvořit a používat takovou šablonu.

Toto téma předpokládá, že pracujete na projektu, který je dostatečně velký, aby vyžadoval několik členů týmu a možná má několik týmů. Kód a modely projektu jsou uloženy v systému správy zdrojového kódu, jako je například [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Aspoň někteří členové týmu používají Visual Studio k vývoji modelů a jiní členové týmu mohou zobrazit modely pomocí jiných verzí sady Visual Studio.

Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé funkce nástrojů a modelování, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struktura řešení

Ve středních nebo rozsáhlých projektech je struktura týmu založena na struktuře aplikace. Každý tým používá řešení sady Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Rozdělení aplikace do vrstev

1. Základem struktury vašich řešení ve struktuře aplikace, například webové aplikace, aplikace služby nebo aplikace klasické pracovní plochy. Celá řada běžných architektur je popsána v tématu [Application archetypes v průvodci architekturou aplikací Microsoftu](https://docs.microsoft.com/previous-versions/msp-n-p/ee658107(v=pandp.10)?redirectedfrom=MSDN).

2. Vytvořte řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], které budeme volat na řešení architektury. Toto řešení se použije k vytvoření celkového návrhu systému. Bude obsahovat modely, ale žádný kód.

    Přidejte Diagram vrstev do tohoto řešení. V diagramu vrstev nakreslete architekturu, kterou jste zvolili pro vaši aplikaci. Diagram může například zobrazit tyto vrstvy a závislosti mezi nimi: prezentace; Obchodní logika; a data.

    Diagram vrstev a nové řešení sady Visual Studio můžete vytvořit současně pomocí příkazu **Nový UML nebo diagram vrstvy** v nabídce **Architektura** .

3. Přidejte do modelů architektury UML model, které představují důležité obchodní koncepty, a případy použití, na které se říká návrh všech vrstev.

4. Vytvořte samostatné řešení sady Visual Studio pro každou vrstvu v diagramu vrstvy architektury.

    Tato řešení budou použita pro vývoj kódu vrstev.

5. Vytvořte modely UML, které budou představovat návrhy vrstev, a koncepce, které jsou společné pro všechny vrstvy. Uspořádejte modely tak, aby se všechny modely mohly zobrazit z řešení architektury, a příslušné modely se z jednotlivých vrstev dají zobrazit.

    Toho můžete dosáhnout pomocí některého z následujících postupů. První alternativa vytvoří samostatný projekt modelování pro každou vrstvu a druhá vytvoří jeden projekt modelování, který je sdílen mezi vrstvami.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Použití samostatného projektu modelování pro každou vrstvu

1. Vytvořte projekt modelování v každém řešení vrstev.

    Tento model bude obsahovat diagramy UML, které popisují požadavky a návrh této vrstvy. Může také obsahovat diagramy vrstev, které zobrazují vnořené vrstvy.

    Nyní máte model pro každou vrstvu a model pro architekturu aplikace. Každý model je obsažen ve vlastním řešení. Díky tomu mohou členové týmu pracovat na vrstvách současně.

2. Do řešení architektury přidejte projekt modelování jednotlivých řešení vrstev. Provedete to tak, že otevřete řešení architektury. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel řešení, přejděte na Přidat a pak klikněte na **existující projekt**. V jednom řešení vrstvy přejděte do projektu modelování (. modelproj).

    Každý model je teď viditelný ve dvou řešeních: jeho "domovské" řešení a řešení architektury.

3. Do projektu modelování každé vrstvy přidejte Diagram vrstev. Začněte s kopií diagramu vrstev architektury. Můžete odstranit části, které nejsou závislé na diagramu vrstev.

    Můžete také přidat diagramy vrstev, které představují podrobnou strukturu této vrstvy.

    Tyto diagramy slouží k ověření kódu, který je vyvíjen v této vrstvě.

4. V řešení architektury upravte požadavky a navrhněte modely všech vrstev pomocí sady Visual Studio.

    V každém řešení vrstev vytvořte kód pro tuto vrstvu, který odkazuje na model. Pokud máte obsah pro vývoj bez použití stejného počítače k aktualizaci modelu, můžete si model přečíst a vyvíjet kód pomocí verzí sady Visual Studio, které nemohou vytvářet modely. Můžete také vygenerovat kód z modelu v těchto verzích.

    Tato metoda zaručuje, že vývojáři, kteří upravují modely vrstev současně, neprojeví žádné rušivé zásahy.

    Vzhledem k tomu, že modely jsou oddělené, je obtížné si vykázat běžné koncepty. Každý model musí mít svou vlastní kopii prvků, na které je závislý z jiných vrstev a architektury. Diagram vrstev v každé vrstvě musí být udržován v synchronizaci s diagramem vrstev architektury. Je obtížné zachovat synchronizaci, když se tyto prvky změní, i když byste mohli vyvinout nástroje, které to mají udělat.

###### <a name="to-use-a-separate-package-for-each-layer"></a>Použití samostatného balíčku pro každou vrstvu

1. V řešení pro každou vrstvu přidejte projekt modelování architektury. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel řešení, přejděte na **Přidat**a pak klikněte na **existující projekt**. K jednomu projektu modelování se teď dá dostat z každého Řešení: projekt architektury a vývojový projekt pro každou vrstvu.

2. Ve sdíleném modelu UML vytvořte balíček pro každou vrstvu: v Průzkumník řešení vyberte projekt modelování. V Průzkumníku modelů UML klikněte pravým tlačítkem na kořenový uzel modelu, přejděte na **Přidat**a pak klikněte na **balíček**.

    Každý balíček bude obsahovat diagramy UML, které popisují požadavky a návrh odpovídající vrstvy.

3. V případě potřeby přidejte místní diagramy vrstev pro vnitřní strukturu jednotlivých vrstev.

    Tato metoda umožňuje, aby prvky návrhu jednotlivých vrstev odkazovaly přímo na vrstvy a společnou architekturu, na které závisí.

    I když souběžná práce na různých balíčcích může způsobit některé konflikty, je poměrně snadné ji spravovat, protože balíčky jsou uloženy v samostatných souborech. Hlavní potíže jsou způsobeny odstraněním elementu, na který je odkazováno ze závislého balíčku. Další informace najdete v tématu [Správa modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md).

## <a name="creating-architecture-templates"></a>Vytváření šablon architektury

V praxi nebudete současně vytvářet všechna vaše řešení sady Visual Studio, ale můžete je přidat jako průběh projektu. V budoucích projektech pravděpodobně budete používat také stejnou strukturu řešení.  K rychlému vytváření nových řešení můžete vytvořit šablonu řešení nebo projektu. Můžete zachytit šablonu v rozšíření integrace sady Visual Studio (VSIX), aby bylo možné je snadno distribuovat a nainstalovat do jiných počítačů.

Například pokud často používáte řešení, která mají prezentační, obchodní a datové vrstvy, můžete nakonfigurovat šablonu, která vytvoří nová řešení, která mají tuto strukturu.

#### <a name="to-create-a-solution-template"></a>Vytvoření šablony řešení

1. Pokud jste to ještě neudělali, [Stáhněte a nainstalujte Průvodce exportem šablony](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Vytvořte strukturu řešení, kterou chcete použít jako výchozí bod pro budoucí projekty.

3. V nabídce **soubor** klikněte na položku **Exportovat šablonu jako VSIX**. Otevře se **Průvodce Exportovat šablonu jako VSIX** .

4. Podle pokynů v průvodci vyberte projekty, které chcete zahrnout do šablony, zadejte název a popis šablony a zadejte umístění výstupu.

> [!NOTE]
> Materiál v tomto tématu je abstraktní a paraphrased z pokynů k nástrojům architektury sady Visual Studio, které jsou vytvořené pomocí sady Visual Studio ALM, což je spolupráce mezi nejnáročnějšími specialisty (MVP), službami Microsoftu a Visual Studiem. produktový tým a zapisovače. [Kliknutím sem si stáhněte kompletní balíček s pokyny.](https://archive.codeplex.com/?p=vsarchitectureguide)

## <a name="related-materials"></a>Související materiály

[Organizování a Správa modelů](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models) – video Clint Edmondson.

[Pokyny k nástrojům architektury sady Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md) – další pokyny pro správu modelů v týmu

## <a name="see-also"></a>Viz také

[Správa modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)
[používání modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md)
