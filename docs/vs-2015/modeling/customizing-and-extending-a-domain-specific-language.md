---
title: Přizpůsobení a rozšíření jazyka specifického pro doménu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d5b55a9b9a55d00cbfb7928295699c254f72639
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180684"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Přizpůsobení a rozšíření jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio modelování a vmsdk následující (sada SDK vizualizace položky) nabízí několik úrovní, ve kterém můžete definovat nástrojů pro modelování:  
  
1.  Definice jazyka specifického pro doménu (DSL) pomocí diagramem definice DSL. Můžete rychle vytvořit DSL s graficky zápis, čitelné formě XML a základní nástroje, které jsou nutné ke generování kódu a další artefakty.  
  
     Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Vylaďte DSL pomocí pokročilejších funkcí definici DSL. Například můžete provést další odkazy zobrazí, když uživatel vytvoří element. Tyto postupy jsou většinou dosáhnout v definici DSL a některé vyžadují pár řádků kódu programu.  
  
3.  Rozšíření nástrojů pro modelování pomocí kódu programu. Vmsdk následující položky je navržená speciálně pro usnadnění integrace vašich rozšíření s kódem, který je generován z definice DSL.  Další informace najdete v tématu [psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Po aktualizaci souboru definic DSL, nezapomeňte kliknout na **Transformovat všechny šablony** na panelu nástrojů Průzkumník řešení před opětovné sestavování svého řešení.  
  
##  <a name="customShapes"></a> V této části  
  
|Tohoto efektu dosáhnete tak|Přečtěte si toto téma|  
|----------------------------|-------------------------|  
|Umožní uživateli nastavit vlastnosti barvu a styl v tvaru.|Pravým tlačítkem myši na obrazec nebo spojnici třídy, přejděte na **přidat vystavený**a klikněte na položku.<br /><br /> Zobrazit [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|  
|Různé třídy prvku modelu vypadat podobně jako v diagramu, vlastnosti, jako je počáteční výška a šířka, barvy, popisky pro sdílení obsahu.|Použití dědičnosti mezi tvarů nebo konektor třídy. Mapování mezi odvozené tvary a odvozené doménové třídy dědit podrobnosti mapování z rodičů.<br /><br /> Nebo mapování jinou doménu tříd na stejnou třídu tvaru.|  
|Třída elementu, model se zobrazí při různých tvarů kontexty.|Map – třída více než jeden tvar do stejné doménové třídy. Při sestavování řešení postupujte podle zprávy o chybách a zadejte požadovaný kód se rozhodnout, jaký tvar, který má použít.|  
|Barva obrazce nebo jiné funkce, jako je písmo označují aktuální stav.|Zobrazit [aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Vytvoření pravidla, která aktualizuje vlastnosti zveřejněné. Zobrazit [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Nebo použijte OnAssociatedPropertyChanged() k aktualizaci není vystavený funkce, jako je písmo nebo odkaz šipky.|  
|Ikona ve tvaru změny k označení stavu.|Nastavte viditelnost dekoratéru mapování v okně podrobností DSL. Vyhledejte několik dekoratéry bitové kopie na stejné pozici. Zobrazit [aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Nebo přepsat `ImageField.GetDisplayImage()`. Viz příklad v <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Nastavit obrázek pozadí na žádný obrazec|Přepište InitializeInstanceResources() přidat ukotvené ImageField. Zobrazit [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|  
|Vnořování obrazců do libovolné hloubky|Nastavte rekurzivní vložení stromu. Definujte BoundsRules tak, aby obsahovala tvary. Zobrazit [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|  
|Připojte konektory na pevnou bodů na hranice prvku.|Definování vložené terminálu prvky reprezentována malé porty v diagramu. Použití BoundsRules opravit porty na místě. Zobrazit ukázku diagramu okruh v [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Textové pole zobrazí hodnotu odvozenou z jiných hodnot.|Mapování dekoratéru text na doménovou vlastnost počítané nebo vlastní úložiště. Další informace najdete v tématu [vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md).|  
|Šíří změny mezi prvky modelu, nebo obrazce|Zobrazit [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).|  
|Šíří změny prostředky, jako jsou jiné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření mimo úložiště.|Zobrazit [obslužné rutiny události šířící změny mimo Model](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Vlastnost okně zobrazí vlastnosti související elementu.|Nastavte vlastnost předávání. Zobrazit [přizpůsobení okna vlastnosti](../modeling/customizing-the-properties-window.md).|  
|Kategorie vlastností|V okně Vlastnosti je rozdělený do částí názvem kategorie. Nastavte **kategorie** vlastností vaší domény. Vlastnosti se stejným názvem kategorie se zobrazí ve stejném oddílu. Můžete také nastavit **kategorie** role vztahu.|  
|Řízení přístupu uživatelů k vlastnosti domény|Nastavte **je Prohlížitelná** hodnotu false, aby doménová vlastnost, která povolí, v okně Vlastnosti v době běhu. Můžete je stále namapovat na dekoratéry textu.<br /><br /> **Je uživatelské rozhraní jen pro čtení** zabraňuje uživatelům možnost měnit doménové vlastnosti.<br /><br /> Přístup k doménové vlastnosti programu nemá vliv.|  
|Změňte název, ikonu a viditelnost uzly v Průzkumníku modelu vašeho kódu DSL.|Zobrazit [přizpůsobení Průzkumníka modelů](../modeling/customizing-the-model-explorer.md).|  
|Povolit kopírování, vyjmutí a vložení|Nastavte **povolit kopírování vkládání** vlastnost **Editor** uzel v Průzkumník DSL.|  
|Kopie referenčních odkazů a jejich cíle pokaždé, když se zkopíruje element. Například zkopírujte komentáře připojené k položce.|Nastavte **šíří kopírování** vlastnost zdrojové role (reprezentovaný identifikátorem řádek na jedné straně doménový vztah v diagramem definice DSL).<br /><br /> Napsání kódu pro přepsání ProcessOnCopy k dosažení složitějšího účinky.<br /><br /> Zobrazit [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|  
|Odstranit, změnit nadřazenou položku nebo znovu propojit souvisejících prvků po odstranění prvku.|Nastavte **šíří odstranit** hodnotu role vztahu. Pro složitější efekty přepsat `ShouldVisitRelationship` a `ShouldVisitRolePlayer` metody v `MyDslDeleteClosure` třídy definované v **DomainModel.cs**<br /><br /> Zobrazit [přizpůsobení chování odstranění](../modeling/customizing-deletion-behavior.md)|  
|Zachovat obrazce rozložení a vzhled na kopírování a přetažení.|Přidání obrazců a konektorů k zkopírovaný `ElementGroupPrototype`. Je nejvhodnější metodu pro přepsání `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Zobrazit [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|  
|Vkládání obrazců do zvoleného umístění, jako je aktuální pozice kurzoru.|Přepsat `ClipboardCommandSet.ProcessOnCopy()` použije umístění konkrétní verzi `ElementOperations.Merge().` naleznete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|  
|Vytvoření další odkazy na vložení|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Povolit přetažení z diagramu, jiné DSL nebo UML diagramů a prvky Windows|Zobrazit [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Povolit tvar nebo nástroj přetahovat do podřízené obrazce, jako je port, jako kdyby byly přetahovat do nadřazené.|Definujte direktiva sloučení elementů na cílovou třídu objektu, předat přetažený objekt Nadřazený. Zobrazit [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).|  
|Povolit nástroj přetáhnout na obrazec a další odkazy tvaru nebo nebo objekty vytvořené. Chcete-li například povolit komentář, který má být přetaženy položku, ke kterému se chcete propojit.|Definování direktiva sloučení elementů ve třídě cílové domény a definování odkazů, které chcete vygenerovat. Ve složitých případech můžete přidat vlastní kód. Zobrazit [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).|  
|Vytvořte skupinu prvky pomocí jednoho nástroje. Například komponenta s pevnou sadu portů.|Potlačí metodu inicializace sady nástrojů v ToolboxHelper.cs. Vytvoření prvek skupiny prototypu (EGP) obsahující prvky a jejich vztahů odkazů. Zobrazit [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Zahrnout obrazce instančního objektu a port EGP nebo definovat BoundsRules umístit obrazce portu při vytváření instance EGP. Zobrazit [umístění a velikost obrazce omezení BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Použijte jeden nástroj pro připojení k vytvoření instance několik typů vztahu.|Přidání direktivy odkazu připojení (LCD) do Tvůrce připojení, který je vyvolán nástroj. Monitorů LCD určit typ vztahu z typů dvou prvků. Chcete-li to závisí na stavy prvků, můžete přidat vlastní kód. Zobrazit [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).|  
|Rychlé nástroje – uživateli můžete dvakrát kliknout na libovolný nástroj k vytvoření mnoha tvary a konektory v daný okamžik.|Průzkumník modelu DSL, vyberte `Editor` uzlu. V okně Vlastnosti nastavte **používá jako vždy navrchu položky panelu nástrojů**.|  
|Definujte příkazy nabídky|Zobrazit [postupy: úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Omezit model s ověřovací pravidla|Zobrazit [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md)|  
|Generování kódu, konfigurační soubory nebo dokumenty ze DSL.|[Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Vlastní nastavení jak modely se ukládají do souboru.|Zobrazit [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Modely uložte do databáze nebo jiného média.|Přepsat *YourLanguage*DocData<br /><br /> Zobrazit [přizpůsobení souborového úložiště a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrace několik DSL tak, aby fungovaly jako součást jedné aplikace.|Zobrazit [integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Povolit vašeho DSL prodloužit třetími stranami a ovládací prvek rozšíření.|[Rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Sdílení tříd mezi jazyky specifickými pro doménu (DSL) pomocí knihovny DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definování zásady zamykání pro vytváření segmentů jen pro čtení](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Viz také  
 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)   
 [Psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)



