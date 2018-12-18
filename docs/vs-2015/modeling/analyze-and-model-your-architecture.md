---
title: Analýza a modelování vaší architektury | Dokumentace Microsoftu
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
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b7d7f9f478e85229eaa72ab04d12b6b542cbab5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781033"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zajistěte, aby že vaše aplikace splňuje požadavky uživatelů pomocí sady Visual Studio architektura a modelování nástroje pro návrh a modelování vaší aplikace. Snadněji pochopit stávající kód programu pomocí sady Visual Studio můžete vizualizovat strukturu kódu, chování a vztahy.  
  
 Vytvářejte modely s různými úrovněmi detailů v průběhu životního cyklu aplikací v rámci vašeho vývojového procesu. Sledujte požadavky, úkoly, testovací případy, chyby a další práci související s vašimi modely propojením prvků modelu s pracovními položkami serveru Team Foundation Server a váš plán vývoje. Zobrazit [scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Které verze sady Visual Studio podporují jednotlivé funkce najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="to"></a>Chcete-li  
  
|||  
|-|-|  
|**Vizualizace kódu**:<br /><br /> – Podívejte organizaci a vztahy kódu vytvořením map kódu. Vizualizace závislostí mezi sestavení, oborů názvů, třídy, metody a tak dále.<br />– Podívejte na strukturu třídy a členy pro konkrétní projekt tak, že vytvoříte diagramů tříd z kódu.<br />-Vyhledání konfliktů mezi kódu a jeho návrhu tak, že vytvoříte diagramy vrstev pro ověření kódu.<br /><br /> **Poznámka:**: V této verzi sady Visual Studio, termín *mapy kódu* je použito místo *graf závislosti*. Termín *grafu* při použití samostatného obvykle odkazuje na diagram orientovaného grafu nebo jazyka DGML (nebo dokumentu). Mapy kódu se speciálním typem DGML diagram.|-   [Vizualizace kódu](../modeling/visualize-code.md)<br />-   [Práce s třídami a ostatními typy (návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Pochopení závislostí kódu až po vizualizaci (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Vizualizujte dopad změn (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Popsat a sdělovat požadavky uživatelů**:<br /><br /> -Objasnění uživatelských scénářů, obchodní pravidla a další požadavky a pomáhají zajistit jejich konzistence kreslením diagramy UML, jako je například případ použití, aktivity a diagramy tříd.|-   [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)<br />-   [Video: Vylepšení architektury prostřednictvím modelování (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Definice architektury**:<br /><br /> – Modelování ve velkém měřítku strukturu softwarového systému a vzory návrhu kreslením Komponenta UML, třídy a sekvenční diagramy.<br />-Definovat a vynucovat omezení závislosti mezi komponentami váš kód tak, že vytvoříte diagramy vrstev.|-   [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Vylepšení architektury prostřednictvím modelování (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Použijte diagramy vrstev k navrhování a ověřování architektury (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Ověřování systému s požadavky a určené návrhu:**<br /><br /> -Definujte akceptační testy nebo testy systému podle požadavků na modely. Tím se vytvoří silný vztah mezi testy a požadavky vašich uživatelů a umožňuje snadno aktualizovat systém další při změně požadavků.<br />-Validate závislostí kódu pomocí diagramů vrstev, které popisují zamýšlenou architekturu a Neumožnit změny, které může být v konfliktu s návrhem.|-   [Ověřování systému během vývoje.](../modeling/validate-your-system-during-development.md)<br />-   [Video: Použijte diagramy vrstev k navrhování a ověřování architektury (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Sdílení modelů, diagramy a map kódu pomocí správy verzí Team Foundation**:<br /><br /> -Umístěte map kódu, modelování projekty, diagramy UML a diagramy vrstev v systému správy verzí Team Foundation, můžete je sdílet.|Pokud máte více uživatelů, kteří pracují s následujícími položkami v rámci správy verzí Team Foundation, abyste se vyhnuli problémy s verzí ovládacího prvku použijte tyto pokyny:<br /><br /> -   [Správa modelů a diagramů pomocí správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Vytvořit nebo nakonfigurovat částí aplikace z UML nebo jazyky specifickými pro doménu**:<br /><br /> – Ujistěte se, návrhu rychlejší reakce na požadavky na změny a snadno proměnné v řadě produktů.|-   [Generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Přizpůsobení modelů a diagramů**:<br /><br /> -Adaptace modelů a jak váš projekt je využívá tak, že definujete další vlastnosti pro prvky UML, omezení ověření, abyste měli jistotu, že vaše modely souladu s firemní pravidla a další příkazy a položky panelu nástrojů.<br />-Vytvořte vlastní jazyky specifickými pro doménu.|-   [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Generování textu s použitím šablony T4**:<br /><br /> – Použijte textové bloky a logiky ovládacího prvku uvnitř šablony pro vygenerování souborů založený na textu.|-   [Generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Typy modelů a jejich použití  
  
|**Typ modelu a typické používá**|  
|-------------------------------------|  
|**Mapy kódu**<br /><br /> Mapy kódu vám umožní zjistit, organizaci a vztahy v kódu.<br /><br /> Obvyklá využití:<br /><br /> – Zkontrolujte kód programu to vám umožní lépe pochopit jeho strukturu a její závislosti, jak ji aktualizovat a odhad nákladů na navrhované změny.<br /><br /> Další informace:<br /><br /> -   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagram vrstvy**<br /><br /> Diagramy vrstev vám umožní definovat struktury aplikace jako sada vrstvy nebo bloky s explicitní závislosti. Můžete spustit ověření ke zjišťování konfliktů mezi závislostmi v kódu a závislostmi popsané na diagramu vrstvy.<br /><br /> Obvyklá využití:<br /><br /> – Stabilizace struktury aplikace pomocí množství změn průběhu své životnosti.<br />-Zjišťování konfliktů nechtěné závislosti před vrácením se změnami kódu.<br /><br /> Další informace:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|  
|**UML model**<br /><br /> UML model obsahuje několik zobrazení, včetně třídy, komponenty, případ použití, aktivity a sekvenční diagramy. Můžete přizpůsobit UML tak, aby vyhovovala vaší domény aplikace. Například můžete připojit značky, další informace a omezení s prvky modelu. Můžete také definovat nástroje, které pracují na modely. Zobrazit [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).<br /><br /> Obvyklá využití:<br /><br /> – Popis požadavků a návrhu. UML lze rychle použít k vývoji jakékoli aplikace. Zobrazit [použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md).<br />-Vytvořit nebo nakonfigurovat testy nebo částí aplikace. Úkony je nutné přizpůsobit zápis a vývoj generování šablon nebo konfigurovat aplikace. Zobrazit [vygenerovat a nakonfigurovat aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).<br />-Pro obecný popis a pro generování kódu nebo konfigurace v menších projektů.|  
|**Jazyka specifického pro doménu (DSL)**<br /><br /> DSL je zápis, který návrh pro konkrétní účel. V sadě Visual Studio má obvykle grafickou podobu.<br /><br /> Obvyklá využití:<br /><br /> -Vygeneruje nebo nakonfigurovat částí aplikace. Práce je vyžadována k vývoji zápisem a nástroje. Výsledkem může být lepší vhodný k vaší doméně než přizpůsobení UML.<br />-Pro velké projekty nebo řádky produktů, kde se investice do vývoje DSL a jeho nástrojů vrácený jeho použití ve více než jeden projekt.<br /><br /> Další informace:<br /><br /> -   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Kde lze získat další informace?  
  
|||  
|-|-|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Viz také  
 [Co je nového](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps a správa životního cyklu aplikací](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



