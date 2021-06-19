---
title: Strukturujte svá řešení modelování
description: Naučte se schéma modelování pro rozdělení aplikace do různých částí, které odpovídají vrstvám v celkovém diagramu vrstvení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54275c55d3d7a80dc2df1721585bc6c39ba8b06e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385484"
---
# <a name="structure-your-modeling-solution"></a>Strukturujte svá řešení modelování

Aby mohli členové týmu efektivně používat modely ve vývojovém projektu, musí být schopni pracovat současně na modelech různých částí projektu. Toto téma navrhuje schéma pro rozdělení aplikace do různých částí, které odpovídají vrstvám v celkovém diagramu vrstvení.

Pokud chcete rychle začít s projektem nebo dílčím projektem, je užitečné mít šablonu projektu, která dodržuje strukturu projektu, kterou jste zvolili. Toto téma popisuje, jak takovou šablonu vytvořit a použít.

Toto téma předpokládá, že pracujete na projektu, který je dostatečně velký, aby vyžadoval několik členů týmu a možná má několik týmů. Kód a modely projektu jsou uloženy v systému správy zdrojového kódu, například [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] . Alespoň někteří členové týmu používají Visual Studio k vývoji modelů a jiní členové týmu mohou modely zobrazit pomocí jiných Visual Studio verzí.

Informace o tom, které verze Visual Studio podporují jednotlivé nástroje a funkce modelování, najdete v tématu [Podpora verzí pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="solution-structure"></a>Struktura řešení

Ve středním nebo velkém projektu je struktura týmu založená na struktuře aplikace. Každý tým používá Visual Studio řešení.

### <a name="to-divide-an-application-into-layers"></a>Rozdělení aplikace do vrstev

1. Založit strukturu vašich řešení na struktuře vaší aplikace, jako je webová aplikace, aplikace služby nebo desktopová aplikace. Celou řadu běžných architektur je popsána v článku [Archetypy aplikací v příručce Microsoft Application Architecture Guide](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Vytvořte Visual Studio řešení, které budeme nazývat Řešení architektury. Toto řešení se použije k vytvoření celkového návrhu systému. Bude obsahovat modely, ale žádný kód.

   Přidejte do tohoto řešení diagram závislostí. V diagramu závislostí nakreslete architekturu, kterou jste pro svou aplikaci zvolili. Diagram může například zobrazit tyto vrstvy a závislosti mezi nimi: Prezentace; Obchodní logika; a Data.

4. Vytvořte samostatné řešení Visual Studio pro každou vrstvu v diagramu závislostí Architektury.

   Tato řešení se budou používat k vývoji kódu vrstev.

5. Vytvářejte modely, které představují návrhy vrstev a koncepty, které jsou společné pro všechny vrstvy. Uspořádejte modely tak, aby byly z řešení Architektury vidět všechny modely, a příslušné modely můžete vidět z každé vrstvy.

   Toho můžete dosáhnout pomocí jednoho z následujících postupů. První alternativa vytvoří samostatný projekt modelování pro každou vrstvu a druhá vytvoří jeden projekt modelování, který je sdílen mezi vrstvami.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Použití samostatného projektu modelování pro každou vrstvu

1. Vytvořte projekt modelování v každé vrstvě řešení.

   Tento model bude obsahovat diagramy, které popisují požadavky a návrh této vrstvy. Může také obsahovat diagramy závislostí, které zobrazují vnořené vrstvy.

   Teď máte model pro každou vrstvu a navíc model pro architekturu aplikace. Každý model je součástí vlastního řešení. To umožňuje členům týmu pracovat na vrstvách současně.

2. Do řešení Architektura přidejte projekt modelování každého řešení vrstev. To můžete udělat tak, že otevřete řešení Architektura. V Průzkumník řešení klikněte pravým tlačítkem na uzel řešení, přejděte na Přidat **a** pak klikněte na **Existující projekt.** V jednom řešení vrstvy přejděte do projektu modelování (.modelproj).

   Každý model je teď viditelný ve dvou řešeních: ve svém "domovském" řešení a v řešení architektura.

3. Do projektu modelování každé vrstvy přidejte diagram závislostí. Začněte kopií diagramu závislostí Architektury. Můžete odstranit části, které nejsou závislostmi diagramu závislostí.

   Můžete také přidat diagramy závislostí, které představují podrobnou strukturu této vrstvy.

   Tyto diagramy slouží k ověření kódu vyvinutého v této vrstvě.

4. V řešení Architektura upravte požadavky a modely návrhu všech vrstev pomocí Visual Studio.

   V každé vrstvě řešení vyvíjet kód pro tuto vrstvu odkazující na model. Pokud jste obsahem při vývoji bez použití stejného počítače k aktualizaci modelu, můžete si model přečíst a vyvíjet kód pomocí verzí Visual Studio které nelze vytvářet modely. V těchto verzích můžete také vygenerovat kód z modelu.

   Tato metoda zaručuje, že vývojáři, kteří upravují modely vrstev současně, nebudou způsobovat žádnou interferenci.

   Vzhledem k tomu, že modely jsou oddělené, je obtížné odkazovat na běžné koncepty. Každý model musí mít vlastní kopii prvků, na kterých je závislý na jiných vrstvách a architektuře. Diagram závislostí v každé vrstvě musí být synchronizované s diagramem závislostí Architektury. Synchronizace je obtížné udržovat, když se tyto prvky změní, i když k tomu můžete vyvíjet nástroje.

#### <a name="use-a-separate-package-for-each-layer"></a>Pro každou vrstvu použijte samostatný balíček.

1. V řešení pro každou vrstvu přidejte projekt modelování architektury. V **Průzkumník řešení** klikněte pravým tlačítkem na uzel řešení, přejděte na **Přidat** a pak klikněte na **Existující projekt.** K jednomu projektu modelování je teď možné přistupovat z každého řešení: projektu architektury a vývojového projektu pro každou vrstvu.

2. Ve sdíleném modelu vytvořte balíček pro každou vrstvu: **V Průzkumník řešení** vyberte projekt modelování. V **Průzkumníku modelů UML** klikněte pravým tlačítkem na kořenový uzel modelu, přejděte na **Přidat** a potom klikněte na **Balíček**.

   Každý balíček bude obsahovat diagramy, které popisují požadavky a návrh odpovídající vrstvy.

3. V případě potřeby přidejte místní diagramy závislostí pro interní strukturu každé vrstvy.

   Tato metoda umožňuje, aby prvky návrhu každé vrstvy odkazují přímo na vrstvy a běžnou architekturu, na které závisí.

   I když souběžná práce na různých balíčcích může způsobit určité konflikty, je poměrně snadné je spravovat, protože balíčky jsou uložené v samostatných souborech.

## <a name="create-architecture-templates"></a>Vytváření šablon architektury

V praxi nevytváříte všechna vaše řešení Visual Studio současně, ale přidáte je v průběhu projektu. V budoucích projektech budete pravděpodobně používat stejnou strukturu řešení. Abyste mohli rychle vytvářet nová řešení, můžete vytvořit řešení nebo šablonu projektu. Šablonu můžete zachytit v rozšíření Visual Studio (VSIX), aby se snadno distribuuje a instaluje na jiných počítačích.

Pokud například často používáte řešení s prezentačními, obchodními a datovými vrstvami, můžete nakonfigurovat šablonu, která vytvoří nová řešení, která mají tuto strukturu.

### <a name="to-create-a-solution-template"></a>Vytvoření šablony řešení

1. [Stáhněte a nainstalujte Průvodce exportem šablony.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard)

2. Vytvořte strukturu řešení, kterou chcete použít jako výchozí bod pro budoucí projekty.

3. V nabídce **File (Soubor)** klikněte **na Export Template as VSIX (Exportovat šablonu jako VSIX).**

   Otevře **se Průvodce exportem šablony jako VSIX.**

4. Podle pokynů v průvodci vyberte projekty, které chcete zahrnout do šablony, zadejte název a popis šablony a zadejte umístění výstupu.

## <a name="watch-a-video"></a>Přehrát video

[Uspořádání a správa modelů](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Viz také

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
