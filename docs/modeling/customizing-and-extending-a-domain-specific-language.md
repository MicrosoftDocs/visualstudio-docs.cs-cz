---
title: Přizpůsobení a rozšíření jazyka specifického pro doménu
description: Zjistěte, jak Visual Studio Sdk pro modelování a vizualizace (VMSDK) poskytuje několik úrovní, na kterých můžete definovat nástroje pro modelování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389381"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Přizpůsobení a rozšíření jazyka specifického pro doménu

Visual Studio Modeling and Visualization SDK (VMSDK) poskytuje několik úrovní, na kterých můžete definovat nástroje pro modelování:

1. Definujte jazyk specifický pro doménu (DSL) pomocí diagramu definice DSL. Můžete rychle vytvořit DSL s diagrammatickou notací, čitelným formulářem XML a základními nástroji potřebnými ke generování kódu a dalších artefaktů. Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md)

2. Vylaďte DSL pomocí pokročilejších funkcí definice DSL. Můžete například vytvořit další odkazy, které se zobrazí, když uživatel vytvoří prvek. Těchto technik se většinou dosahuje v definici DSL a některé vyžadují několik řádků programového kódu.

3. Rozšiřte své nástroje modelování pomocí kódu programu. VMSDK je navržený speciálně pro snadnou integraci rozšíření s kódem vygenerovaný z definice DSL. Další informace najdete v tématu [Psaní kódu pro přizpůsobení Domain-Specific jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Po aktualizaci souboru definic DSL nezapomeňte před znovu  sestavením řešení kliknout na transformovat všechny šablony na panelu **Průzkumník řešení** panelu nástrojů.

## <a name="article-reference"></a>Referenční informace k článku

|K dosažení tohoto efektu|Přečtěte si toto téma.|
|-|-|
|Umožní uživateli nastavit vlastnosti barvy a stylu obrazce.|Klikněte pravým tlačítkem na obrazec nebo třídu konektoru, přejděte na **Přidat vystavené** a klikněte na položku.|
|Různé třídy prvků modelu vypadají v diagramu podobně a sdílejí vlastnosti, jako je počáteční výška a šířka, barva, popisy tlačítek.|Používat dědičnost mezi tvary nebo třídami konektoru. Mapování mezi odvozenými tvary a odvozenými třídami domény dědí podrobnosti mapování o rodičůch.<br /><br /> Nebo namapovat různé třídy domény na stejnou třídu obrazce.|
|Třída prvku modelu je zobrazena pomocí různých kontextů tvarů.|Namapuje více tříd obrazce na stejnou třídu domény. Při sestavování řešení postupujte podle zprávy o chybách a zadejte požadovaný kód, abyste se rozhodli, jaký tvar použít.|
|Barva obrazce nebo jiné funkce, jako je písmo, označují aktuální stav.|Viz [Aktualizace obrazců a konektorů tak, aby odrážely model.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Vytvořte pravidlo, které aktualizuje zveřejněné vlastnosti. Viz [Pravidla šíření změn v rámci modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Nebo můžete použít OnAssociatedPropertyChanged() k aktualizaci nechráněných funkcí, jako jsou šipky odkazů nebo písmo.|
|Ikona u obrazce se změní tak, aby indikuje stav.|V okně Podrobnosti DSL nastavte viditelnost mapování dekorátoru. Na stejné pozici vyhledejte několik dekorátorů obrázků. Viz [Aktualizace obrazců a konektorů tak, aby odrážely model.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Nebo přepište `ImageField.GetDisplayImage()` . Podívejte se na příklad v <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Nastavení obrázku pozadí na libovolném tvaru|Přepište InitializeInstanceResources() pro přidání ukotvené vlastnosti ImageField.|
|Vnořování tvarů do jakékoli hloubky|Nastavte rekurzivní strom vkládání. Definujte pravidla BoundsRule, která budou obsahovat tvary.|
|Připojte konektory v pevných bodech na hranici elementu.|Definujte vložené prvky terminálu reprezentované malými porty v diagramu. K opravě portů použijte BoundsRules. Podívejte se na ukázku diagramu okruhu v [tématu Vizualizace a sada Modeling SDK.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|
|Textové pole zobrazí hodnotu odvozenou od jiných hodnot.|Namapovat dekorátor textu na vlastnost domény Calculated (Počítané) nebo Custom Storage (Vlastní úložiště). Další informace najdete v tématu [Počítané a vlastní vlastnosti úložiště.](../modeling/calculated-and-custom-storage-properties.md)|
|Šíření změn mezi prvky modelu nebo mezi tvary|Viz [Ověření v jazyce Domain-Specific.](../modeling/validation-in-a-domain-specific-language.md)|
|Šířete změny prostředků, jako jsou Visual Studio rozšíření mimo úložiště.|Viz [Obslužné rutiny událostí šíření změn mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Okno vlastností zobrazuje vlastnosti souvisejícího prvku.|Nastavte předávání vlastností. Viz [Přizpůsobení okna Vlastnosti.](../modeling/customizing-the-properties-window.md)|
|Kategorie vlastností|Okno vlastností je rozdělené do oddílů nazývaných kategorie. Nastavte **kategorii** vlastností vaší domény. Vlastnosti se stejným názvem kategorie se zobrazí ve stejné části. Můžete také nastavit **kategorii** role relace.|
|Řízení přístupu uživatelů k vlastnostem domény|Pokud **chcete zabránit tomu,** aby se vlastnost domény v prohlížeči okno Vlastnosti za běhu, nastavte možnost Is Browsable false. Pořád ho můžete namapovat na dekorátory textu.<br /><br /> **Je uživatelské rozhraní jen** pro čtení brání uživatelům ve změně vlastnosti domény.<br /><br /> Přístup programu k vlastnosti domény není ovlivněn.|
|Změňte název, ikonu a viditelnost uzlů v průzkumníku modelů DSL.|Viz [Přizpůsobení Průzkumníka modelů.](../modeling/customizing-the-model-explorer.md)|
|Povolení kopírování, vyjmutí a vložení|V **Průzkumníku DSL nastavte** vlastnost **Povolit** kopírování a vložení uzlu Editor.|
|Odkazové odkazy a jejich cíle zkopírujte při každém zkopírování elementu. Můžete například zkopírovat Komentáře připojené k položce.|Nastavte **vlastnost Propagates Copy** zdrojové role (reprezentované čárou na jedné straně vztahu domény v diagramu definice DSL).<br /><br /> Napíšete kód pro přepsání ProcessOnCopy, abyste dosáhli složitějších efektů.<br /><br /> Viz [Přizpůsobení chování kopírování.](../modeling/customizing-copy-behavior.md)|
|Odstranit související prvky, znovu je odstranit nebo znovu propojet, když je prvek odstraněn.|Nastavte **hodnotu Šíří odstranění** role vztahu. Pro složitější účinky přepište a `ShouldVisitRelationship` metody ve třídě definované v souboru `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs**.|
|Zachování rozložení a vzhledu obrazce při kopírování a přetažení|Přidejte obrazce a konektory do zkopírované položky `ElementGroupPrototype` . Nejpohodlnější metodou přepsání je `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Viz [Přizpůsobení chování kopírování.](../modeling/customizing-copy-behavior.md)|
|Vložte obrazce do zvoleného umístění, například aktuální pozici kurzoru.|Přepsání, `ClipboardCommandSet.ProcessOnCopy()` pokud chcete použít verzi pro konkrétní umístění viz Přizpůsobení chování `ElementOperations.Merge().` [kopírování.](../modeling/customizing-copy-behavior.md)|
|Vytvoření dalších odkazů při vložení|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|Povolení přetahování z tohoto diagramu, dalších dsL a prvků Windows|Viz [Postupy: Přidání obslužné rutiny přetahováním](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Umožňuje přetáhnout tvar nebo nástroj do podřízeného tvaru, jako je port, jako by byl přetažen do nadřazeného tvaru.|Definujte direktivu Element Merge pro třídu cílového objektu, která přeposílá vyřazený objekt nadřazenému objektu. Viz [Přizpůsobení vytvoření a přesunu elementu.](../modeling/customizing-element-creation-and-movement.md)|
|Umožňuje přetáhnout tvar nebo nástroj na tvar a vytvořit další odkazy nebo objekty. Pokud například chcete povolit, aby se komentář přetánul na položku, se kterou se má propojit.|Definujte direktivu elementu merge pro cílovou třídu domény a definujte odkazy, které se mají vygenerovat. Ve složitých případech můžete přidat vlastní kód. Viz [Přizpůsobení vytvoření a přesunu elementu.](../modeling/customizing-element-creation-and-movement.md)|
|Pomocí jednoho nástroje vytvořte skupinu prvků. Například komponenta s pevnou sadu portů.|Přepište metodu inicializace sady nástrojů v souboru ToolboxHelper.cs. Vytvořte prototyp skupiny elementů (EGP), který obsahuje elementy a jejich propojení vztahů. Viz [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Buď zahrňte obrazce objektů zabezpečení a port do EGP, nebo definujte BoundsRules pro umístění obrazců portů při vytváření instance EGP.|
|Pro vytvoření instance několika typů relací použijte jeden nástroj pro připojení.|Přidejte do Tvůrce připojení direktivy Link Connect (LCD), které nástroj vyvolá. LCDs určuje typ relace z typů těchto dvou prvků. Aby to bylo závislé na stavech prvků, můžete přidat vlastní kód. Viz [přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md).|
|Nástroje pro rychlé čtení – uživatel může dvakrát kliknout na libovolný nástroj, aby bylo možné vytvořit mnoho tvarů nebo konektorů po sobě.|V Průzkumníku DSL vyberte `Editor` uzel. V okno Vlastnosti sada **používá položky sady nástrojů s rychlým** nastavením.|
|Definování příkazů nabídky|Viz [Postupy: Změna standardního příkazu nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Omezení modelu pomocí ověřovacích pravidel|Viz [ověřování v jazyce Domain-Specific](../modeling/validation-in-a-domain-specific-language.md) .|
|Vygenerujte kód, konfigurační soubory nebo dokumenty z DSL.|[Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)|
|Umožňuje přizpůsobit způsob ukládání modelů do souboru.|Viz [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Ukládání modelů do databází nebo jiných médií.|Přepsat *YourLanguage* DocData<br /><br /> Viz [přizpůsobení File Storage a serializace XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrujte několik DSL, aby fungovaly jako součást jedné aplikace.|Viz [Integrace modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Umožněte, aby se vaše DSL rozšířila třetími stranami, a řídit rozšíření.|[Rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Sdílení tříd mezi DSL pomocí knihovny DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definování zásady zamykání pro vytváření segmentů jen pro čtení](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Viz také

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Psaní kódu pro přizpůsobení Domain-Specificho jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
