---
title: Strukturování řešení modelování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 995192b372b9c1909ad3a7f164474cfaf63f07bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784452"
---
# <a name="structure-your-modeling-solution"></a>Strukturujte svá řešení modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V projektu vývoje modelů efektivně používat, musí být členy týmu moct pracovat s modely z různých částí projektu ve stejnou dobu. Toto téma navrhne schéma dělení aplikaci do různých částí, které odpovídají vrstvy tak celkovou diagram vrstev.  
  
 Ke spuštění v projektu nebo dílčí projekt rychle, je užitečné mít šablony projektu, která odpovídá struktuře projektu, který jste zvolili. Toto téma popisuje, jak vytvořit a použít tyto šablony.  
  
 Toto téma předpokládá, že pracujete na projektu, který je dostatečně velký, aby vyžadovat několik členů týmu a pravděpodobně má několik týmů. Kód a modely projektu jsou uloženy v systému správy zdrojového kódu, jako [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Alespoň někteří členové týmu vývoje modelů pomocí sady Visual Studio a ostatní členové týmu mohou zobrazit modely pomocí jiných verzí sady Visual Studio.  
  
 Které verze sady Visual Studio podporují jednotlivé funkce nástroje a modelování najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Struktury řešení  
 V projektu střední a velké struktura tým se na základě struktury aplikace. Každý tým používá řešení sady Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>K rozdělení aplikace do vrstvy  
  
1. Základní struktura svoje řešení na struktuře aplikace, například webové aplikace, aplikace služby nebo aplikace klasické pracovní plochy. Celou řadu běžných architektur je podrobněji popsána [Archetypes aplikaci do Průvodce architekturou aplikací Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2. Vytvoření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, který budeme nazývat architekturu řešení. Toto řešení se použije k vytvoření celkového návrhu systému. Bude obsahovat modely, ale žádný kód.  
  
    Přidejte diagram vrstev s tímto řešením. V diagramu vrstev nakreslete architektura, kterou jste zvolili pro vaši aplikaci. Například může zobrazit diagram těchto vrstev a závislostí mezi nimi: prezentaci. Obchodní logika; a Data.  
  
    Diagram vrstev a nové řešení sady Visual Studio můžete vytvořit ve stejnou dobu pomocí **nové UML nebo diagramu vrstev** příkaz **architektura** nabídky.  
  
3. Přidejte do diagramy UML model architektury, které reprezentují důležitých obchodních konceptů a použití případů, které jsou uvedené v návrhu všechny vrstvy.  
  
4. Vytvoření samostatné řešení Visual Studio pro jednotlivé vrstvy v diagramu vrstev architektury.  
  
    Tato řešení se použije k vývoji kódu vrstvy.  
  
5. Vytváření modelů UML, které bude představovat návrhy vrstvy a koncepty, které jsou společné pro všechny vrstvy. Uspořádejte modely tak, aby všechny modely můžete zobrazit z architektury řešení a relevantní modely můžete zobrazit z každé vrstvy.  
  
    Můžete dosáhnout pomocí některé z následujících postupů. V prvním případě vytvoří samostatné modelování projektu pro každou vrstvu a objekt IErrorInfo vytvoří jeden modelování projektu, jež jsou sdílena mezi vrstvami.  
  
   ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Použití samostatné modelování projektu pro každou vrstvu  
  
   1. Vytvoření projektu modelování v každé vrstvě řešení.  
  
       Tento model bude obsahovat diagramy UML, které popisují požadavky a návrh vrstvy. Může také obsahovat diagramy vrstev, které ukazují vnořených vrstev.  
  
       Teď máte model pro každou vrstvu, a navíc modelu pro architekturu aplikace. Každý model je součástí vlastní řešení. To umožňuje členům týmu. budou fungovat na vrstvách ve stejnou dobu.  
  
   2. Architektura řešení přidejte projekt modelování z každé vrstvy řešení. Provedete to tak, otevřete řešení architektury. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel řešení, přejděte na Přidat a potom klikněte na tlačítko **existující projekt**. Přejděte do projektu modelování (.modelproj) v jedné vrstvě řešení.  
  
       Každý model se teď zobrazují dvě řešení: jeho "domovskou" řešení a jeho architektura.  
  
   3. Do projektu modelování každou vrstvu přidejte diagram vrstev. Začněte s kopii diagram vrstev architektury. Můžete odstranit části, které nejsou závislostí v diagramu vrstev.  
  
       Můžete také přidat diagramy vrstev, které představují podrobnou strukturu této vrstvy.  
  
       Tyto diagramy se používají k ověření kódu, který byl vyvinut v této vrstvě.  
  
   4. V architektuře řešení upravte požadavků a návrhu modelů vrstvy pomocí sady Visual Studio.  
  
       V každé vrstvě řešení vyvíjejte kód pro tuto vrstvu, odkazuje na model. Pokud se obsah a provádět vývoj bez použití do stejného počítače k aktualizaci modelu, můžete načíst model a vývoj kódu pomocí verze sady Visual Studio, nelze vytvářet modely. Kód můžete vygenerovat také z modelu v těchto verzích.  
  
      Tato metoda zaručuje, že bude bez rušení způsobuje vývojáři, kteří úpravy modelů vrstvy ve stejnou dobu.  
  
      Vzhledem k tomu, že tyto modely jsou oddělené, je však obtížné najdete běžné koncepty. Každý model musí mít vlastní kopii prvky, na kterých je závislá z jiných vrstev a architektury. Diagram vrstev v každé vrstvě musí udržovat synchronizované s diagramem vrstev architektury. Je obtížné kvůli zachování synchronizace při změně těchto prvků, i když může vývoj nástrojů k provedení této.  
  
   ###### <a name="to-use-a-separate-package-for-each-layer"></a>Chcete-li používat samostatné balíčky pro každou vrstvu  
  
   1. V řešení pro každou vrstvu přidejte projekt modelování architektury. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující projekt**. Jeden modelování projektu je teď přístupná z každé řešení určené pro: architektura projektu a projekt vývoje pro každou vrstvu.  
  
   2. Ve sdíleném modelu UML, vytvořit balíček pro každou vrstvu: V Průzkumníku řešení vyberte projekt modelování. V Průzkumníku modelů UML, klikněte pravým tlačítkem na kořenový uzel modelu, přejděte na **přidat**a potom klikněte na tlačítko **balíčku**.  
  
       Každý balíček bude obsahovat diagramy UML, které popisují požadavky a návrhu odpovídající vrstvy.  
  
   3. V případě potřeby přidejte místní vrstvy diagramy pro interní každou vrstvu.  
  
      Tato metoda umožňuje prvky návrhu každé vrstvě odkazovat přímo na ty vrstvy a běžné architektury, na kterém závisí.  
  
      I když souběžnou prací na různých balíčků může způsobit nějaké konflikty, jsou poměrně snadno spravovat, protože balíčky jsou uloženy do samostatných souborů. Hlavní problémy s dokončením je způsobeno odstranění element, který se odkazuje z závislý balíček. Další informace najdete v tématu [Správa modelů a diagramů pomocí správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md).  
  
## <a name="creating-architecture-templates"></a>Vytváření šablon architektury  
 V praxi nevytvoří všechny vaše řešení sady Visual Studio v době, ale přidat průběhu projektu. Budete pravděpodobně také použít stejnou strukturu řešení v budoucnu projekty.  Můžete rychle vytvořit nová řešení, můžete vytvořit šablonu řešení nebo projektu. Šablony v Visual Studio integrace rozšíření (VSIX) můžete zachytit tak, aby se snadno distribuovat a instalovat na jiné počítače.  
  
 Například pokud používáte často řešení, která mají prezentační, obchodní a datové vrstvy, můžete nakonfigurovat šablonu, která se vytvoří nová řešení, které mají danou strukturu.  
  
#### <a name="to-create-a-solution-template"></a>Vytvoření šablony řešení  
  
1.  [Stáhněte a nainstalujte průvodce exportem šablony](http://go.microsoft.com/fwlink/?LinkId=196686), pokud jste to ještě neudělali.  
  
2.  Vytvoření struktury řešení, které chcete použít jako výchozí bod pro všechny budoucí projekty.  
  
3.  Na **souboru** nabídky, klikněte na tlačítko **exportovat šablonu jako VSIX**. **Exportovat šablonu jako průvodce VSIX** otevře.  
  
4.  Postupujte podle pokynů v průvodci vyberte projekty, které chcete do šablony zahrnout, zadejte název a popis pro šablonu a zadejte umístění výstupu.  
  
> [!NOTE]
>  Materiál v tomto tématu je abstrahovaný a parafrázována z Visual Studio nástrojů doporučení ohledně architektury, autorem Visual Studio ALM Rangers, což je spolupráce mezi největší Vážíme si toho odborníky (MVP), Microsoft Services a sady Visual Studio produktový tým a autory. [Kliknutím sem stáhnete kompletní pokyny k balíčku.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Související materiály  
 [Uspořádání a správě vašich modelů](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) – video od Clint Edmondson.  
  
 [Visual Studio nástrojů doprovodné materiály k architektuře](../modeling/visual-studio-architecture-tooling-guidance.md) – další pokyny týkající se správy modelů v týmu  
  
## <a name="see-also"></a>Viz také  
 [Správa modelů a diagramů pomocí správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)



