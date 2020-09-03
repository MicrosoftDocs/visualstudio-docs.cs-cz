---
title: Přizpůsobení a rozšíření jazyka specifického pro doménu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55ec2cf2f2a6ebf4186f81f6f3dd61766acd7958
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918895"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Přizpůsobení a rozšíření jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada Visual Studio Modeling and vizualizace SDK (VMSDK) poskytuje několik úrovní, na kterých můžete definovat nástroje pro modelování:

1. Pomocí diagramu definice DSL definujte jazyk specifický pro doménu (DSL). Můžete rychle vytvořit DSL pomocí zápisu diagramatické, čitelného formuláře XML a základních nástrojů, které jsou nutné k vygenerování kódu a dalších artefaktů.

     Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md).

2. Vyladit DSL pomocí pokročilejších funkcí definice DSL. Můžete například vytvořit další odkazy, když uživatel vytvoří prvek. Tyto techniky se většinou dosahují v definici DSL a některé vyžadují několik řádků programového kódu.

3. Pomocí kódu programu rozšíříte nástroje pro modelování. VMSDK je navržený specificky pro usnadnění integrace vašich rozšíření s kódem, který je vygenerován z definice DSL.  Další informace najdete v tématu [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Po aktualizaci souboru definic DSL nezapomeňte kliknout na možnost **transformovat všechny šablony** na panelu nástrojů Průzkumník řešení před opětovným sestavením řešení.

## <a name="in-this-section"></a><a name="customShapes"></a> V této části

|Pro dosažení tohoto efektu|Informace najdete v tomto tématu.|
|----------------------------|-------------------------|
|Povolí uživateli nastavit vlastnosti barvy a stylu obrazce.|Klikněte pravým tlačítkem myši na obrazec nebo na třídu konektoru, přejděte na **Přidat vystavené**a klikněte na položku.<br /><br /> Viz [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|
|Různé třídy elementu modelu vypadají podobně jako v diagramu, sdílí vlastnosti, jako je počáteční výška a šířka, barva, popisy tlačítek.|Použijte dědičnost mezi tvary nebo třídami konektorů. Mapování mezi odvozenými tvary a odvozenými doménovými třídami dědí Podrobnosti mapování nadřazených objektů.<br /><br /> Nebo můžete mapovat různé třídy domény na stejnou třídu Shape.|
|Třída prvku modelu je zobrazena v různých kontextech tvarů.|Namapujte více než jednu třídu Shape na stejnou doménovou třídu. Když sestavíte řešení, postupujte podle zprávy o chybách a poskytněte požadovaný kód pro rozhodování o tom, jaký tvar chcete použít.|
|Barva obrazce nebo jiné funkce, jako je písmo indikuje aktuální stav.|Viz [aktualizace obrazců a konektorů, aby odrážely model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Vytvoří pravidlo, které aktualizuje vystavené vlastnosti. Viz [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Nebo použijte OnAssociatedPropertyChanged () k aktualizaci nezveřejněných funkcí, jako jsou šipky odkazů nebo písmo.|
|Ikona u obrazce se změní, aby označovala stav.|Nastavte viditelnost mapování dekoratér v okně Podrobnosti DSL. Najděte několik imagí dekoratéry na stejné pozici. Viz  [aktualizace obrazců a konektorů, aby odrážely model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Nebo, přepsat `ImageField.GetDisplayImage()` . Viz příklad v tématu <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Nastavení obrázku na pozadí na jakémkoli obrazci|Přepsat InitializeInstanceResources () pro přidání ukotveného ImageField. Viz [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|
|Vnořování tvarů do libovolné hloubky|Nastavte strom rekurzivního vkládání. Definujte BoundsRules pro zahrnutí tvarů. Viz [přizpůsobení prezentace v diagramu](../modeling/customizing-presentation-on-the-diagram.md).|
|Připojit konektory na hranici elementu v pevně stanovených bodech.|Definujte vložené prvky terminálu reprezentované malými porty v diagramu. Pomocí BoundsRules opravte porty na místě.|
|Textové pole zobrazuje hodnotu odvozenou od jiných hodnot.|Namapujte text dekoratér na vypočítanou nebo vlastní doménovou vlastnost úložiště. Další informace najdete v tématu věnovaném [vypočítaným a vlastním vlastnostem úložiště](../modeling/calculated-and-custom-storage-properties.md).|
|Rozšířit změny mezi prvky modelu nebo mezi tvary|Viz [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).|
|Rozšiřte změny prostředků, jako jsou jiná [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření mimo obchod.|Viz [obslužné rutiny událostí rozšiřují změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Okno vlastností zobrazí vlastnosti souvisejícího prvku.|Nastavte předávání vlastností. Viz [přizpůsobení okna vlastností](../modeling/customizing-the-properties-window.md).|
|Kategorie vlastností|Okno Vlastnosti je rozdělené na oddíly s názvem kategorie. Nastavte **kategorii** vlastností domény. Vlastnosti se stejným názvem kategorie se zobrazí ve stejném oddílu. Můžete také nastavit **kategorii** role vztahu.|
|Řízení přístupu uživatelů k doménovým vlastnostem|Vlastnost **je možné procházet** , aby se zabránilo zobrazování vlastnosti domény v okno Vlastnosti v době běhu. Pořád ho můžete namapovat na text dekoratéry.<br /><br /> **Je uživatelské rozhraní jen pro čtení** , brání uživatelům měnit doménovou vlastnost.<br /><br /> Přístup programu k vlastnosti domény není ovlivněn.|
|Změňte název, ikonu a viditelnost uzlů v Průzkumníku modelů DSL.|Viz [Přizpůsobení Průzkumníka modelů](../modeling/customizing-the-model-explorer.md).|
|Povolit kopírování, vyjmutí a vložení|V Průzkumníku DSL nastavte vlastnost **Povolit kopírování** na uzel **Editor** .|
|Kopírovat odkazy odkazů a jejich cíle při každém zkopírování elementu. Například zkopírujte komentáře připojené k položce.|Nastavte vlastnost **rozšíření kopírování** zdrojové role (reprezentované řádkem na jedné straně relace domény v diagramu definice DSL).<br /><br /> Napíšete kód pro přepsání ProcessOnCopy, abyste dosáhli složitějších efektů.<br /><br /> Viz [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|
|Odstranit, změnit nadřazený prvek nebo znovu propojit související prvky při odstranění elementu.|Nastavte hodnotu **šířit odstranění** role vztahu. Pro složitější efekty, přepsání `ShouldVisitRelationship` a `ShouldVisitRolePlayer` metody ve `MyDslDeleteClosure` třídě definované v **DomainModel.cs**<br /><br /> Viz [přizpůsobení chování při odstraňování](../modeling/customizing-deletion-behavior.md)|
|Zachovat rozložení a vzhled obrazce při kopírování a přetahování myší|Přidejte obrazce a konektory do zkopírovaných `ElementGroupPrototype` . Nejpohodlnější metoda, která se má přepsat, je `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Viz [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|
|Vloží tvary do zvoleného umístění, jako je například aktuální pozice kurzoru.|Přepsáním `ClipboardCommandSet.ProcessOnCopy()` na použití verze specifické pro umístění, `ElementOperations.Merge().` Viz [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).|
|Vytvořit další odkazy při vložení|Přepsat ClipboardCommandSet. ProcessOnPasteCommand ()|
|Povolit přetažení z tohoto diagramu, další DSL nebo diagramy UML a prvky Windows|Viz [Postupy: Přidání obslužné rutiny přetažení myší.](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Umožňuje přetáhnout tvar nebo nástroj na podřízený obrazec, jako je například port, jako by byl přetažen na nadřazený objekt.|Definujte direktivu sloučení elementů pro třídu cílového objektu pro Přeposlání vyřazeného objektu na nadřazený objekt. Viz [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).|
|Umožňuje přetáhnout tvar nebo nástroj na obrazec a vytvořit další odkazy nebo objekty. Například pokud chcete, aby byl komentář vyřazen do položky, na kterou má být propojen.|Definujte direktivu sloučení elementů pro cílovou doménovou třídu a definujte odkazy, které se mají vygenerovat. Ve složitých případech můžete přidat vlastní kód. Viz [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).|
|Vytvořte skupinu prvků s jedním nástrojem. Například součást s pevnou sadou portů.|Přepsat inicializační metodu sady nástrojů v ToolboxHelper.cs. Vytvořte prototyp skupiny elementů (EGP) obsahující elementy a jejich odkazy na relace. Viz [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Buď zahrňte obrazce objektů zabezpečení a port do EGP, nebo definujte BoundsRules pro umístění obrazců portů při vytváření instance EGP. Podívejte [se na umístění a velikost obrazce omezení BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md).|
|Pro vytvoření instance několika typů relací použijte jeden nástroj pro připojení.|Přidejte do Tvůrce připojení direktivy Link Connect (LCD), které nástroj vyvolá. LCDs určuje typ relace z typů těchto dvou prvků. Aby to bylo závislé na stavech prvků, můžete přidat vlastní kód. Viz [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).|
|Nástroje pro rychlé čtení – uživatel může dvakrát kliknout na libovolný nástroj a vytvořit mnoho tvarů nebo konektorů po sobě.|V Průzkumníku DSL vyberte `Editor` uzel. V okno Vlastnosti sada **používá položky sady nástrojů s rychlým**nastavením.|
|Definování příkazů nabídky|Viz [Postupy: Změna standardního příkazu nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Omezení modelu pomocí ověřovacích pravidel|Viz [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)|
|Vygenerujte kód, konfigurační soubory nebo dokumenty z DSL.|[Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)|
|Umožňuje přizpůsobit způsob ukládání modelů do souboru.|Viz [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Ukládání modelů do databází nebo jiných médií.|Přepsat *YourLanguage*DocData<br /><br /> Viz [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrujte několik DSL, aby fungovaly jako součást jedné aplikace.|Viz [Integrace modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Umožněte, aby se vaše DSL rozšířila třetími stranami, a řídit rozšíření.|[Rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Sdílení tříd mezi DSL pomocí knihovny DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definování zásady zamykání pro vytváření segmentů jen pro čtení](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
|||

## <a name="see-also"></a>Viz také
 [Definování kódu specifického](../modeling/how-to-define-a-domain-specific-language.md) [pro doménu psaní kódu pro přizpůsobení jazykové](../modeling/writing-code-to-customise-a-domain-specific-language.md) [sady SDK pro specifické domény pro sadu Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
