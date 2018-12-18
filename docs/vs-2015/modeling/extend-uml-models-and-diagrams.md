---
title: Rozšíření modelů a diagramů UML | Dokumentace Microsoftu
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
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 74f3c518682997dca57a630c6f084437f7175d80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794761"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozšíření modelů a diagramů UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma shrnuje různé způsoby, ve kterém můžete rozšířit nástroje, které jsou součástí sady Visual Studio pomocí modelování UML. Které verze sady Visual Studio podporují každého typu modelu a nástroj, najdete v sekci [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 V následujícím ukázkovém scénáři Fabrikam navrhuje a nainstaluje letiště sobě systémy zpracování. Z projektu jedno letiště na další jsou v základní vybavení a software, který ovládacích prvků, je mnoho podobností. Existují však také několika různými faktory, které se liší běžně, jako např. konfigurace dopravní pásy, portál vrácení se změnami, přihrádky úložiště a dalších kontejner objektů a dat zpracování zařízení.  
  
 Při spuštění nového projektu, tým společnosti Fabrikam vytvoří model UML, aby to pomohl ostatním tyto požadavky mezi sebou a s jejich zákazníků. Diagramy činnosti používají k vyjádření tok kontejnery objektů a dat, s uzly objektu představující každého jednotlivého zařízení. UML model přímo nepředstavuje kód v systému.  
  
 Tým společnosti Fabrikam nástroje dosáhne řadu vylepšení pomáhají vývojové týmy. Následující části popisují různé druhy rozšíření, které můžete definovat. Některé z následujících postupů můžete zkombinovat do jedné rozšíření sady Visual Studio.  
  
 Další informace najdete v tématu toto video: ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")[MSDN How do I řadu: nástroje UML a rozšiřitelnost](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
##  <a name="Requirements"></a> Požadavky  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
-   [Sada Modeling SDK for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profily  
 Profily umožňují definovat Stereotypy a další vlastnosti u elementů UML.  
  
 Nástroj pro vývojáře společnosti Fabrikam definovat Stereotypy na uzly objektu stránky diagramů činností, jako je například "dopravní pás" a "vrátit se změnami podpory". Když člen týmu vytvoří sobě zpracování schématu pomocí diagramu činnosti, mohou nyní nastavit Stereotypy označující typ zařízení představuje každý uzel. Nástroj pro vývojáře definovat další vlastnosti u některých Stereotypy, tak, aby uživatelé zaznamenat hodnoty, jako je kapacita dopravní pás a uchopení pera stolu vrácení se změnami.  
  
 Další informace najdete v tématu [definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Vlastní panel nástrojů položkami  
 Vlastní položku sady nástrojů vytvoří element nebo skupinu elementů z prototypu, který definujete v diagramu. Můžete například vytvořit nástroj, který vytvoří v určité barvy nebo stereotyp nebo skupinu tříd a přidružení, která představuje vzor návrhu případy použití. Můžete přidat tyto položky panelu nástrojů na rozšíření sady Visual Studio a distribuovat ostatním uživatelům.  
  
 Další informace najdete v tématu [definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Ověřování  
 Můžete definovat pravidla pro zajištění, že UML model odpovídá zadaným omezením.  
  
 Nástroj pro vývojáře společnosti Fabrikam definovat pravidla, která pomůže členům týmu se vyhnuli omylům jednoduché v sobě zpracování modelů. Například oddělení vrácení se změnami nemůže být připojen přímo k bin úložiště. Mezi nimi musí být alespoň běžícím pásu.  
  
 Další informace najdete v tématu [definovat omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Příkazy nabídky  
 Můžete definovat příkazy, které uživatelé můžete vyvolat kliknutím pravým tlačítkem myši prvků v diagramu UML. Příkazy můžete aktualizovat modelu a diagramů nebo provádění jiných operací v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Společnost Fabrikam definuje příkazy nabídky automatizaci často prováděnými operací, jako například vytvořit helpdesku vrácení se změnami a připojení k vybrané dopravní pás nebo uspořádat diagram podle pravidel rozložení vaší společnosti.  
  
 Zobrazit [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Gesta  
 Můžete definovat příkazy, které umožňuje uživatelům zahájit dvojitým kliknutím elementu diagramu nebo přetažením do diagramu nebo prvku v diagramu. Můžete definovat příkazy, které můžete vyřešit položky přetáhnout z ostatních diagramů UML, z jiných částí sady Visual Studio nebo z jiných aplikací nebo Průzkumníka Windows (nebo Průzkumníka souborů.  
  
 Členové týmu společnosti Fabrikam můžete přidružit soubor jako je specifikace libovolnému prvku modelu, jeho přetažením z plochy Windows. Nástroj pro vývojáře definice stereotypu, který poskytuje vlastnost Cesta k souboru a gesta, která nastavuje stereotyp a cesta k souboru, když je soubor přetaženy element libovolný element.  
  
 Další informace najdete v tématu [definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Reagování na změny  
 Můžete napsat kód, který reaguje na změny v modelu, zda způsobeno akcí uživatele nebo jiný programový kód.  
  
 Vývojáři společnosti Fabrikam vytvořit kód, který se automaticky nastaví závisí na jeho stereotyp barvy elementu. To usnadňuje uživatelům rozlišit různé role, které hrají prvky v modelech.  
  
 Další informace najdete v tématu [postupy: reakce na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Sběrnice modelu  
 Model Service Bus vám umožní přistupovat k formuláři modelu nebo diagramu z jiného diagramu nebo z jiného [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření. Mimo jiné to umožňuje rozprostřít informace napříč více než jeden model tak, aby několik lidí může pracovat na kombinovaný model ve stejnou dobu.  
  
 Společnost Fabrikam pomocí elementů v diagramech činnosti představují sobě zpracování zařízení. Každá položka zařízení může mít podrobnější specifikace do jiného diagramu, který může být v jiném modelu. Omezení ověření v diagramu toku sobě můžete načíst relevantní vlastnosti zařízení z ostatních diagramů. Odkazy na ostatní diagramy jsou uloženy v další vlastnosti definované v stereotypy.  
  
 Další informace najdete v tématu [modely UML integrovat s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Generování  
 Z modelu můžete generovat kód programu, skripty, konfigurace, dokumenty, nové modely nebo jiné artefakty.  
  
 V sobě systémy, které navrhuje společnosti Fabrikam velkou část kódu programu je stejný z jednoho projektu do druhého. Hlavní proměnné aspektem je plán toku sobě kolem letiště. Po návrh tým měl zkušeností svých prvních několik projektů, vývojáři nástroj vytvořit šablonu, která generuje z modelu toku sobě velká část kódu proměnné programu a další soubory, jako jsou dokumenty uživatele. To významně snižuje rychlost vývoje čas a chyba pro každý projekt.  
  
 Další informace najdete v tématu [generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server Integration  
 Můžete propojit pracovní položky k prvkům modelu a programový přístup k připojené položky.  
  
 Vývojáři společnosti Fabrikam nástroj psát nástroj, který generuje plán práce pro každý projekt letiště. Pracovní položky v plánu jsou propojeny s prvky modelu.  
  
 Další informace najdete v tématu [definování obslužné rutiny odkazu pracovní položky](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Nástroje, které aktualizace modelů  
 Můžete vytvořit samostatné aplikace a rozšíření sady Visual Studio, které můžete načíst modely UML.  
  
 Vývojáři společnosti Fabrikam vytvořte nástroj, který čte model a generuje sestavy průběhu práce na každý prvek modelu.  
  
 Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Jazyky specifickými pro doménu  
 Pokud používáte často určitý typ modelu, může být užitečné k vytvoření jazyka specifického pro doménu. To můžete provést podle vašich potřeb firmy lépe než modelu UML, ale vyžaduje další úsilí k jejich vytváření a údržbu. Další informace najdete v tématu [sada Modeling SDK for Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Externí zdroje  
  
|**Kategorie**|**Odkazy**|  
|------------------|---------------|  
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How do I řadu: nástroje UML a rozšiřitelnost](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML pomocí sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogy**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technické články a deníky**|[Centrum architektury MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)   
 [Referenční dokumentace k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)



