---
title: Vizualizace kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 071048fba8d3663639747ea35dbae4375d101c26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738933"
---
# <a name="visualize-code"></a>Vizualizace kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizualizace a modelování nástroje v sadě Visual Studio můžete použít k vám pomůže pochopit stávající kód a popisují vaši aplikaci. To vám umožní vizuálně zjistit, jak mohou změny ovlivnit kód a pomůže vám to posoudit práci a rizika vyplývající z těchto změn. Příklad:  
  
- Pochopení vztahů v kódu, vizuálně mapování těchto relací.  
  
- K popisu architektury systému a byl kód zachován konzistentní s návrhem, vytváření diagramů vrstev a ověření kódu proti tyto diagramy.  
  
- K popisu třídy, struktury, vytvoření diagramů tříd.  
  
- Model a různé aspekty systému, kreslit diagramy jazyka UML (Unified Modeling). Například lze modelovat součásti systému, typy, interakce a procesy.  
  
  Tyto nástroje také umožňují snadněji komunikovat s lidmi, které jsou součástí vašeho projektu. Například můžete použít diagramy tříd UML vytvoření společný glosář pro diskuze o systém s účastníky projektu, uživateli a členy týmu.  
  
  Které verze sady Visual Studio podporují jednotlivé funkce najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
|||  
|-|-|  
|**Pochopení kódu a jejích vztahů:**<br /><br /> Mapovat vztahy mezi konkrétní části kódu.<br /><br /> Zobrazit přehled vztahů v kódu pro celé řešení.<br /><br /> **Poznámka:**: V této verzi sady Visual Studio, termín *mapy kódu* je použito místo *graf závislosti*.|-   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Principy struktur třídy:**<br /><br /> Vizualizujte strukturu tříd v projektu tak, že vytvoříte diagramů tříd z kódu.|[Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Popis návrhu systému vysoké úrovně a ověření kódu proti tohoto návrhu:**<br /><br /> Vytvořením diagramy vrstev popisují návrh vysoké úrovně systému a jeho zamýšlených závislostí. Ověření kódu proti tohoto návrhu zajistit, aby zůstaly konzistentní s návrhem závislosti v kódu.|-   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|  
|**Komunikaci uživatelských požadavků a architektury:**<br /><br /> Modelování uživatelských požadavků a architektury softwarového systému kreslením následující diagramy UML: aktivita, komponenty, třídy, pořadí a případ použití.|-   [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)<br />-   [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>Externí zdroje  
  
|**Kategorie**|**Odkazy**|  
|------------------|---------------|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogy**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technické články a deníky**|[Architektura fórum MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Viz také  
 [Scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Analýza a modelování vaší architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)   
 [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)   
 [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)



