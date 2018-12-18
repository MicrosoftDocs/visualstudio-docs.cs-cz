---
title: Strukturujte svá řešení modelování
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2c279da9aed4a11799004a38004f8b82dca65174
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966710"
---
# <a name="structure-your-modeling-solution"></a>Strukturujte svá řešení modelování

V projektu vývoje modelů efektivně používat, musí být členy týmu moct pracovat s modely z různých částí projektu ve stejnou dobu. Toto téma navrhne schéma dělení aplikaci do různých částí, které odpovídají vrstvy tak celkovou diagram vrstev.

Ke spuštění v projektu nebo dílčí projekt rychle, je užitečné mít šablony projektu, která odpovídá struktuře projektu, který jste zvolili. Toto téma popisuje, jak vytvořit a použít tyto šablony.

Toto téma předpokládá, že pracujete na projektu, který je dostatečně velký, aby vyžadovat několik členů týmu a pravděpodobně má několik týmů. Kód a modely projektu jsou uloženy v systému správy zdrojového kódu, jako [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Alespoň někteří členové týmu vývoje modelů pomocí sady Visual Studio a ostatní členové týmu mohou zobrazit modely pomocí jiných verzí sady Visual Studio.

Které verze sady Visual Studio podporují jednotlivé funkce nástroje a modelování najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struktury řešení

V projektu střední a velké struktura tým se na základě struktury aplikace. Každý tým používá řešení sady Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>K rozdělení aplikace do vrstvy

1. Základní struktura svoje řešení na struktuře aplikace, například webové aplikace, aplikace služby nebo aplikace klasické pracovní plochy. Celou řadu běžných architektur je podrobněji popsána [Archetypes aplikaci do Průvodce architekturou aplikací Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Vytvoření řešení sady Visual Studio, který nazveme architekturu řešení. Toto řešení se použije k vytvoření celkového návrhu systému. Bude obsahovat modely, ale žádný kód.

   Přidejte do závislostí diagram tohoto řešení. Na diagram závislostí nakreslete architektura, kterou jste zvolili pro vaši aplikaci. Například může zobrazit diagram těchto vrstev a závislostí mezi nimi: prezentaci. Obchodní logika; a Data.

4. Vytvoření samostatné řešení Visual Studio pro každou vrstvu Diagram závislostí architektury.

   Tato řešení se použije k vývoji kódu vrstvy.

5. Vytvářejte modely, které představují návrhy vrstvy a koncepty, které jsou společné pro všechny vrstvy. Uspořádejte modely tak, aby všechny modely můžete zobrazit z architektury řešení a relevantní modely můžete zobrazit z každé vrstvy.

   Můžete dosáhnout pomocí některé z následujících postupů. V prvním případě vytvoří samostatné modelování projektu pro každou vrstvu a objekt IErrorInfo vytvoří jeden modelování projektu, jež jsou sdílena mezi vrstvami.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Použití samostatné modelování projektu pro každou vrstvu

1. Vytvoření projektu modelování v každé vrstvě řešení.

   Tento model bude obsahovat diagramy, které najdete popis požadavků a návrh vrstvy. Může také obsahovat diagramů závislostí, které ukazují vnořených vrstev.

   Teď máte model pro každou vrstvu, a navíc modelu pro architekturu aplikace. Každý model je součástí vlastní řešení. To umožňuje členům týmu. budou fungovat na vrstvách ve stejnou dobu.

2. Architektura řešení přidejte projekt modelování z každé vrstvy řešení. Provedete to tak, otevřete řešení architektury. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, přejděte na Přidat a potom klikněte na tlačítko **existující projekt**. Přejděte do projektu modelování (.modelproj) v jedné vrstvě řešení.

   Každý model se teď zobrazují dvě řešení: jeho "domovskou" řešení a jeho architektura.

3. Do projektu modelování každou vrstvu přidejte diagram závislostí. Začněte s kopii diagram závislostí architektury. Můžete odstranit části, které nejsou závislosti diagram závislostí.

   Můžete také přidat diagramy závislostí, které představují podrobnou strukturu této vrstvy.

   Tyto diagramy se používají k ověření kódu, který byl vyvinut v této vrstvě.

4. V architektuře řešení upravte požadavků a návrhu modelů vrstvy pomocí sady Visual Studio.

   V každé vrstvě řešení vyvíjejte kód pro tuto vrstvu, odkazuje na model. Pokud se obsah a provádět vývoj bez použití do stejného počítače k aktualizaci modelu, můžete načíst model a vývoj kódu pomocí verze sady Visual Studio, nelze vytvářet modely. Kód můžete vygenerovat také z modelu v těchto verzích.

   Tato metoda zaručuje, že bude bez rušení způsobuje vývojáři, kteří úpravy modelů vrstvy ve stejnou dobu.

   Vzhledem k tomu, že tyto modely jsou oddělené, je však obtížné najdete běžné koncepty. Každý model musí mít vlastní kopii prvky, na kterých je závislá z jiných vrstev a architektury. Diagram závislostí v každé vrstvě musí udržovat synchronizované s diagram závislostí architektury. Je obtížné kvůli zachování synchronizace při změně těchto prvků, i když může vývoj nástrojů k provedení této.

#### <a name="use-a-separate-package-for-each-layer"></a>Používat samostatné balíčky pro každou vrstvu

1. V řešení pro každou vrstvu přidejte projekt modelování architektury. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující projekt**. Jeden modelování projektu je teď přístupná z každé řešení určené pro: architektura projektu a projekt vývoje pro každou vrstvu.

2. Ve sdíleném modelu, vytvořit balíček pro každou vrstvu: V **Průzkumníka řešení**, vyberte projekt modelování. V **Průzkumníku modelů UML**, klikněte pravým tlačítkem na kořenový uzel modelu, přejděte na **přidat**a potom klikněte na tlačítko **balíčku**.

   Každý balíček bude obsahovat diagramy, které popisují požadavky a návrhu odpovídající vrstvy.

3. V případě potřeby přidejte diagramů místní závislostí pro interní strukturu každou vrstvu.

   Tato metoda umožňuje prvky návrhu každé vrstvě odkazovat přímo na ty vrstvy a běžné architektury, na kterém závisí.

   I když souběžnou prací na různých balíčků může způsobit nějaké konflikty, jsou poměrně snadno spravovat, protože balíčky jsou uloženy do samostatných souborů.

## <a name="create-architecture-templates"></a>Vytvoření šablon architektury

V praxi nevytvářejte všech svých řešení sady Visual Studio v době, ale přidat průběhu projektu. Pravděpodobně je budete také použít stejnou strukturu řešení v budoucnu projekty. Můžete rychle vytvořit nová řešení, můžete vytvořit šablonu řešení nebo projektu. Šablony v Visual Studio integrace rozšíření (VSIX) můžete zachytit tak, aby se snadno distribuovat a instalovat na jiné počítače.

Například pokud používáte často řešení, která mají prezentační, obchodní a datové vrstvy, můžete nakonfigurovat šablonu, která se vytvoří nová řešení, které mají danou strukturu.

### <a name="to-create-a-solution-template"></a>Vytvoření šablony řešení

1. [Stáhněte a nainstalujte průvodce exportem šablony](http://go.microsoft.com/fwlink/?LinkId=196686).

2. Vytvoření struktury řešení, které chcete použít jako výchozí bod pro všechny budoucí projekty.

3. Na **souboru** nabídky, klikněte na tlačítko **exportovat šablonu jako VSIX**.

   **Exportovat šablonu jako průvodce VSIX** otevře.

4. Postupujte podle pokynů v průvodci vyberte projekty, které chcete do šablony zahrnout, zadejte název a popis pro šablonu a zadejte umístění výstupu.

## <a name="watch-a-video"></a>Podívejte se na video

[Uspořádání a správě vašich modelů](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Viz také

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Pokyny k nástrojům architektury sady Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)
