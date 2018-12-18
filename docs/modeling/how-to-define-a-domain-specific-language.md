---
title: Jak se definuje jazyk specifický pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ed1259ef04f59d37752d89f922623b963bcbbc22
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967529"
---
# <a name="how-to-define-a-domain-specific-language"></a>Jak se definuje jazyk specifický pro doménu
Do definice jazyka specifického pro doménu (DSL), vytvoříte ze šablony řešení sady Visual Studio. Klíčovou součástí řešení je diagramem definice DSL, která je uložena v DslDefinition.dsl. Definice DSL definuje třídy a tvary DSL. Po úpravě a přidáte k těmto prvkům můžete přidat kód programu k přizpůsobení DSL podrobněji.

Pokud jste ještě DSL, doporučujeme pracovat prostřednictvím **testovacího prostředí nástroje DSL**, které můžete vyhledat v této lokalitě: [Visualizaton and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Výběr šablony řešení
 Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Pokud chcete vytvořit nový jazyk specifický pro doménu, vytvořte nové řešení sady Visual Studio pomocí šablony projektu jazyka specifického pro doménu.

#### <a name="to-create-a-dsl-solution"></a>K vytvoření řešení DSL

1. Vytvoření řešení se **jazyka specifického pro doménu** šablony, které najdete v části **ostatní typy/rozšíření projektu** v **nový projekt** dialogové okno.

    ![Vytvoření dialogového okna DSL](../modeling/media/create_dsldialog.png)

    Po kliknutí na **OK**, **Průvodce jazyka specifického pro doménu** otevře a zobrazí se seznam šablon řešení DSL.

2. Klikněte na každou šablonu zobrazíte popis. Vyberte řešení, které nejlépe odpovídá co byste chtěli vytvořit.

    Každá šablona DSL definuje základní funkční DSL. Upravíte tento DSL podle vlastních požadavků.

    Klikněte na každý vzorek pro další informace.

   -   Vyberte **tok úkolů** vytvoření DSL, která má plaveckých drah. Plaveckých drah jsou vertikální nebo horizontální oddíly diagramu.

   -   Vyberte **komponenty modely** vytvoření DSL, která má porty. Porty jsou malé obrazce na hraničních zařízeních větších obrazce.

   -   Vyberte **diagramů tříd** k definování DSL, která má obrazce oddílu. Obrazce oddílu obsahují seznamy položek.

   -   Vyberte **minimální jazykový** v ostatních případech, nebo pokud si nejste jisti.

   -   Vyberte **minimální návrháře WinForm** nebo **minimální Návrhář WPF** vytvoření DSL, který se zobrazí na ploše Windows Forms a WPF. Budete muset psát kód, který definuje editoru. Další informace naleznete v následujících tématech:

        [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Zadejte příponu názvu souboru vašeho DSL v na odpovídající stránku průvodce. Toto je rozšíření, které budou používat soubory, které obsahují instance tohoto kódu DSL.

   -   Zvolte příponu názvu souboru, která nejsou spojena s libovolnou aplikací v počítači nebo v libovolném počítači, ve kterém chcete nainstalovat DSL. Například **docx** a **htm** bude nepřijatelná souboru přípony názvu.

   -   Průvodce zobrazí upozornění, pokud se používá rozšíření, které jste zadali jako DSL. Zvažte možnost použít jinou příponu. Můžou také resetovat Visual Studio SDK experimentální instanci vymazání starých experimentální návrháře. Klikněte na tlačítko **Start**, klikněte na tlačítko **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a potom **resetování Microsoftu Instance sady Visual Studio 2010 experimentální**.

4. Můžete upravit nastavení na jiných stránkách, nebo ponechte výchozí hodnoty.

5. Klikněte na tlačítko **Dokončit**.

    Průvodce vytvoří řešení, které obsahuje dvě nebo tři projekty a generuje kód v definici DSL.

   Uživatelské rozhraní teď vypadá podobně jako na následujícím obrázku.

   ![Návrhář DSL](../modeling/media/dsl_designer.png)

   Definuje toto řešení jazyka specifického pro doménu. Další informace najdete v tématu [přehled uživatelského rozhraní nástrojů jazyka specifického pro doménu](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Otestování řešení
 Šablona řešení poskytuje funkční DSL, která můžete změnit nebo použít, protože ho.

 Otestování řešení, stiskněte klávesu F5 nebo CTRL + F5. Novou instanci sady Visual Studio se otevře v experimentálním režimu.

 V nové instanci sady Visual Studio v Průzkumníku řešení otevřete ukázkový soubor. Otevře se jako diagram, se panelu nástrojů.

 Pokud spuštění řešení, které jste vytvořili z **minimální jazykový** šablony, experimentální sady Visual Studio bude vypadat podobně jako v následujícím příkladu:

 ![](../modeling/media/dsl_min.png)

 Experimentujte s nástroji. Vytvářet prvky a jejich připojení.

 Ukončete experimentální instanci sady Visual Studio.

> [!NOTE]
>  Změně DSL už budete moci zobrazit tvary v ukázce soubor testu. Nicméně je možné vytvářet nové elementy.

### <a name="modifying-the-template-dsl"></a>Úprava šablony DSL
 Přejmenovat a zachovat některé nebo všechny doménové třídy a třídy tvar v šabloně definici DSL. Vaše nové názvy třídy musí být platné názvy CLR bez mezery ani interpunkci.

 To je zvlášť vhodné ponechat tyto třídy:

- Kořenová třída se zobrazí v levém horním rohu diagramem definice DSL, v části **třídám a vztahům**. Přejmenujte ho na název liší od DSL. Například s názvem DSL **MusicLibrary** může mít kořenová třída s názvem **Hudba**.

- Diagram tříd se zobrazí v pravém dolním rohu diagramem definice DSL, v **elementů diagramu** sloupce. Budete muset posunout doprava a prohlédněte si ho. Je obvykle pojmenována _YourDsl_**Diagram**.

- Pokud jste použili **tok úkolů** šablony a chcete vytvářet diagramy s plaveckých drah, udržovat a přejmenování objektu Actor doménovou třídu a obrazec ActorSwimlane.

  Odstranit nebo přejmenovat jiné třídy tak, aby vyhovoval vašim požadavkům.

## <a name="patterns"></a> Vzory pro definice DSL
 Doporučujeme při vývoji DSL přidáním nebo upravit jednu nebo dvě funkce v čase. Přidat funkci, spustit DSL a otestovat ji a pak přidejte jednu nebo dvě další funkce. Typické funkce tohoto kódu DSL může být:

- Doménové třídy vkládání vztah, který se připojí prvek modelu, tvar vyžadována k zobrazení prvků této třídy na diagramu. proto nástroj elementu, který umožňuje uživatelům vytvářet prvky.

- Vlastnosti domény doménovou třídu a dekorátory, které se zobrazují ve tvaru.

- Referenční vztah a konektor, který se zobrazí v diagramu a nástroj konektor, který umožňuje uživateli vytvořit propojení.

- Vlastní nastavení, která vyžaduje kódu programu, jako je například omezení ověření nebo příkazu nabídky.

  Následující části popisují, jak vytvořit nejužitečnější typy funkcí DSL. Existuje mnoho dalších vzorech, se kterými lze zkonstruovat DSL, ale ty se používají nejčastěji.

> [!NOTE]
>  Po přidání funkce, nezapomeňte kliknout na **Transformovat všechny šablony** na panelu nástrojů Průzkumník řešení před sestavení a spuštění vašeho DSL.

 Následující obrázek ukazuje třídy a vztahy část DSL, která slouží jako příklad v tomto tématu.

 ![Vztahy vložení a referenční informace](../modeling/media/music_classes.png)

 Na následujícím obrázku je příklad typu tento DSL:

 ![Instance modelu generované DSL](../modeling/media/music_instance.png)

> [!NOTE]
>  "Model" odkazuje na instanci tohoto kódu DSL, která uživatelé vytvářet a obvykle se zobrazí jako diagram. Toto téma popisuje diagramem definice DSL a diagramech modelů, které se zobrazí při použití vašeho DSL.

## <a name="classes"></a> Definování doménové třídy
 Doménové třídy představoval pojmy tohoto kódu DSL. Instance jsou *elementům modelu*. Například v **MusicLibrary** DSL může mít doménové třídy s názvem **alba** a **skladby**.

 Chcete-li vytvořit doménovou třídou, lze přetáhnout z **doménovou třídu s názvem** nástrojů do diagramu a potom tuto třídu přejmenovat.

 Další informace najdete v tématu [vlastnosti tříd domény](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Vytvoří vztah obsažení pro každou třídu domény
 Každá třída domény s výjimkou kořenová třída musí být pro cílový alespoň jeden vztah obsažení, nebo musí dědit z třídy, která je cílem vztah obsažení.

 V modelu každý prvek modelu je uzel ve stromu jednoho vkládání vztahy. Zdroj a cíl vztah obsažení jsou často označovány jako nadřazené a podřízené.

 Výběr nadřazené třídy domény závisí na způsobu jeho prvky životnosti závisí na další prvky. Pokud uzel stromu je odstraněn, jeho podstromu je obvykle také odstraněny. Třídy prvku, které mají nezávislé existence jsou proto vložené přímo pod kořenová třída.

 Obvykle Pokud zobrazíte prvek uvnitř jiného prvku chcete určit vztah vlastníka. V takovém případě nejvhodnější nadřazené třídy je třída kontejneru. Výjimkou je, když je položka, která se zobrazí uvnitř kontejneru ve skutečnosti pouze odkaz na prvek nezávislé. V takovém případě odstraníte kontejner odstraní odkaz, ale ne jeho cíl.

 Ve vzorech definice DSL popsané v tomto tématu budeme předpokládat, že prvky zobrazené uvnitř kontejneru se odstraní při odstranění kontejneru. Složitější schémata jsou možné a dosáhnout tak, že definujete pravidla.

|Jak se zobrazí element|Třída nadřazené (vložení)|Příklad v šabloně řešení DSL|
|-|-|-|
|Obrazec v diagramu.<br /><br /> Plavecké dráhy.|Kořenová třída DSL.|Minimální jazykový.<br /><br /> Tok úkolů: Třída Actor.|
|Obrazce v plavecké dráhy.|Doménová třída prvky, které se zobrazují jako plaveckých drah.|Tok úloh: Třída úlohy.|
|Položky v seznamu ve tvaru, kde se odstraní položka, pokud se odstraní kontejner.<br /><br /> Port na hraničních zařízeních obrazce.|Doménová třída, která je namapovaná na obrazec kontejneru.|Diagram tříd: třídy atributů.<br /><br /> Diagram komponent: Port třídy.|
|Položky v seznamu, nebyl odstraněn, pokud se odstraní kontejner.|Kořenová třída DSL.<br /><br /> V seznamu zobrazí odkazy.||
|Zobrazí přímo.|Třída, která je součástí.||

 V příkladu knihovně hudby alb zobrazují jako obdélníky, ve kterých jsou uvedené názvy skladeb. Proto nadřazená alba je kořenová třída Hudba a nadřazené skladby je alba.

 Chcete-li vytvořit třídu domény a jeho vkládání ve stejnou dobu, klikněte na tlačítko **vztah obsažení** nástroj, pak klikněte na nadřazenou třídu a potom klikněte na prázdnou část diagramu.

 Není obvykle nutné upravit název vztah obsažení a její role, protože budou automaticky sledovat názvy tříd.

 Další informace najdete v tématu [vlastnosti vztahů domény](../modeling/properties-of-domain-relationships.md) a [Vlastnosti rolí domény](../modeling/properties-of-domain-roles.md).

> [!NOTE]
>  Vkládání není stejný jako dědičnosti. Podřízené položky v vztah obsažení nedědí ze svých nadřazených složek funkce.

### <a name="add-domain-properties-to-each-domain-class"></a>Přidání vlastnosti domény do každé doménové třídy
 Vlastnosti domény ukládání hodnot. Mezi příklady patří: název, název, data publikování.

 Klikněte na tlačítko **vlastnosti domény** ve třídě, stiskněte klávesu ENTER a pak zadejte název vlastnosti. Výchozí typ doménová vlastnost, která je řetězec. Pokud chcete změnit typ, vyberte doménová vlastnost a nastavte **typ** v **vlastnosti** okna. Pokud typ, který chcete, aby v rozevíracím seznamu není, přečtěte si téma [přidávání typů vlastností](#addTypes).

 **Nastavte vlastnost názvu elementu.** Doménová vlastnost, která slouží k identifikaci prvků v Průzkumníku jazyk vyberte. Například ve třídě domény skladby, můžete vybrat vlastnost názvu domény. V **vlastnosti** okno, nastavte **je název elementu** k `true`.

### <a name="create-derived-domain-classes"></a>Vytvoření domény odvozené třídy
 Pokud chcete mít varianty, které dědí její vlastnosti a vztahy doménovou třídu, vytvořte třídy, které jsou odvozeny z něj. Například může mít alba odvozené třídy WMA a MP3.

 Vytvoření pomocí odvozené třídy **doménové třídy** nástroj.

 Klikněte na tlačítko **dědičnosti** nástroj, klikněte na odvozenou třídu a klikněte na základní třídu.

 Zvažte nastavení **modifikátor dědičnosti** základní třídy, která se **abstraktní**. Pokud se domníváte, že může být nutné instance základní třídy, zvažte místo toho vytváří samostatný odvozené třídy pro ně.

 Odvozené třídy dědí vlastnosti a rolí jejich základních tříd.

### <a name="tidy-the-dsl-definition-diagram"></a>Přehledné diagramem definice DSL
 Při přidání relace některé z tříd se zobrazí ve více než jednom místě. Ke snížení počtu vystoupení na širší diagramu, klikněte pravým tlačítkem na cílovou třídu relace a klikněte na **přenést stromu zde**. Opačný efekt, klikněte pravým tlačítkem na cílovou třídu relace a klikněte na tlačítko **rozdělit strom**. Pokud se tyto příkazy nezobrazí, ujistěte se, že je vybrána pouze doménové třídy.

 Pomocí kombinace kláves CTRL + ŠIPKA NAHORU a CTRL + ŠIPKA DOLŮ přesunout tvar třídy a doménovými třídami.

### <a name="test-the-domain-classes"></a>Testovací třídy domény

##### <a name="to-test-the-new-domain-classes"></a>K testování nových tříd domény

1.  **Klikněte na možnost Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení pro generování kódu návrháře DSL. Tento krok můžete automatizovat. Další informace najdete v tématu [jak automatizovat Transformovat všechny šablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2.  **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 ke spuštění nové instance sady Visual Studio v experimentálním režimu. V experimentální instanci sady Visual Studio otevřete nebo vytvořte soubor, který má příponu názvu souboru tohoto kódu DSL.

3.  **Otevřete Průzkumníka.** Na straně diagramu je okno Průzkumníka jazyk, který se obvykle nazývá *YourLanguage* Explorer. Pokud se toto okno nezobrazí, může být na kartě pod Průzkumníku řešení. Pokud nemůžete najít to, na **zobrazení** nabídky, přejděte k **ostatní Windows**a potom klikněte na tlačítko *YourLanguage* **Explorer**.

     Aplikace explorer představuje stromové zobrazení modelu.

4.  **Vytvořte nové elementy.** Klikněte pravým tlačítkem na kořenový uzel v horní části a potom klikněte na tlačítko **přidat nový**_YourClass_.

     Ve svém jazyce Průzkumníka se zobrazí novou instanci třídy.

5.  Ověřte, že každá instance má jiný název při vytváření nové instance. K tomu dojde pouze v případě, že jste nastavili **je název elementu** příznak doménové vlastnosti.

6.  **Podívejte se na vlastnosti domény. S instancí třídy vybrali** kontrolovat v okně Vlastnosti. Měl by se zobrazit vlastnosti domény, které jste definovali v této doménové třídě.

7.  **Soubor uložte, zavřete ho a znovu ho otevřete**. Po rozbalení uzlů, by se zobrazovat v Průzkumníkovi, všechny instance, kterou jste vytvořili.

## <a name="shapes"></a> Definování obrazců v diagramu
 Třídy prvků, které se zobrazí v diagramu můžete definovat jako obdélníky, symbol tří teček nebo ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Chcete-li definovat třídu prvků, které se zobrazí jako tvary v diagramu

1. **Definování a otestovat doménovou třídu, jak je popsáno v**[definování doménovými třídami](#classes) **.**

   -   Kořenová třída by měla být nadřazené třídu. To znamená by měl být vztah obsažení mezi kořenové třídy a nové domény.

   -   Pokud diagramu plaveckých drah, může být nadřazené doménové třídy, který je namapovaný na plaveckou dráhu. Než budete pokračovat tímto postupem, naleznete v tématu [definice DSL, která má plaveckých drah](#swimlanes).

2. **Přidejte třídu tvar** představující prvky v diagramu modelu. Přetáhněte jednu z následujících nástrojů do diagramu definici DSL:

   - **Obrazec geometrie** poskytuje obdélník nebo elipsu.

   - **Obrázek tvaru** zobrazí obrázek, který zadáte.

   - **Obrazec oddílu** je obdélník, který obsahuje jeden nebo více seznamů položek.

     Přejmenujte obrazec třídy, která se zobrazí na pravé straně diagramem definice DSL, v rámci obrazců a konektorů.

3. **Definujte image, pokud jste vytvořili obrazce obrázku**.

   1.  Vytvořte soubor bitové kopie všech velikostí. BMP, JPEG, ve formátu GIF a EMF jsou podporovány.

   2.  V Průzkumníku řešení přidejte soubor do řešení ve složce Dsl\Resources.

   3.  Vraťte se do diagramem definice DSL a vyberte novou třídu obrazce obrázku.

   4.  V okně Vlastnosti klikněte na tlačítko **Image** vlastnost.

   5.  V **vybrat obrázek** dialogu klikněte do rozevírací nabídky v části **název_souboru**a vyberte bitovou kopii.

4. **Přidáte dekoratéry textu na tvar, chcete-li zobrazit vlastnosti domény.**

    Zobrazit název nebo název prvku modelu, bude pravděpodobně nutné alespoň jeden dekoratér text.

    Klikněte pravým tlačítkem na záhlaví tvaru třídy, přejděte na **přidat**a potom klikněte na tlačítko **Text Dekoratér**. Nastavte název dekoratéru a okno sady vlastností jeho **pozice**.

5. **Připojení jednotlivých tvarů s mapou elementu diagramu do doménové třídy, která by se měla zobrazit**.

    Klikněte na tlačítko **mapa elementu diagramu** nástroj, pak klikněte na tlačítko doménové třídy a pak klikněte na tvar třídy.

6. **Mapování vlastností pro dekoratéry textu.**

   1. Vyberte Šedá čára mezi třídy domény a obrazec, který představuje mapa elementu diagramu.

   2. V **podrobnosti DSL** okna, klikněte na tlačítko **mapování Dekoratéru** kartu. Pokud se nezobrazí **podrobnosti DSL** okno na **zobrazení** nabídky, přejděte k **ostatní Windows** a potom klikněte na tlačítko **podrobnosti DSL**. To je často potřeba vygenerovat horní části tohoto okna, chcete-li zobrazit veškerý jeho obsah.

   3. Vyberte název dekoratér. V části **zobrazit vlastnost**, vyberte název vlastnosti třídy domény. Tento postup opakujte pro každý dekoratér.

       Pokud chcete zobrazit vlastnosti související prvku, klikněte na tlačítko Navigátor rozevíracího seznamu stromu v části **cesta k vlastnosti zobrazení**.

   4. Ujistěte se, že se zobrazí zaškrtávací políčko vedle každý dekoratér název.

      ![Okno mapování obrazce a podrobnosti DSL](../modeling/media/dsldetailswindow.png)

7. **Nastavit položku sady nástrojů pro vytváření elementů doménové třídy.**

   1.  V **Průzkumník DSL**, rozbalte **Editor** uzel a jeho dílčí uzly.

   2.  Klikněte pravým tlačítkem na uzel v rámci **karty panelu nástrojů** , který má stejný název jako vaše DSL, například MusicLibrary. Klikněte na tlačítko **přidat nástroj pro Element**.

       > [!NOTE]
       >  Pokud kliknete pravým tlačítkem **nástroje** uzlu, neuvidíte **přidat nástroj pro Element**. Místo toho klikněte na uzel nad ním.

   3.  V okně Vlastnosti nový nástroj prvek vybraný, nastavte **třídy** do doménové třídy, které jste nedávno přidali.

   4.  Nastavte **titulek** a **popisek**.

   5.  Nastavte **panelu nástrojů ikonu** na ikonu, která se zobrazí na panelu nástrojů. Můžete ho nastavit na novou ikonu nebo ikonu již používá pro jiný nástroj.

        Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumníka řešení**. Zkopírujte a vložte jednu existující soubory BMP nástroj elementu. Přejmenujte vložené kopie a potom dvakrát klikněte na Upravit.

        Vraťte se do diagramem definice DSL, vyberte nástroj a v okně Vlastnosti klikněte na tlačítko **[...]**  v **panelu nástrojů ikonu**. V **vybrat rastrový obrázek** dialogovém okně vyberte vaše. BMP soubor z rozevírací nabídky.

   Další informace najdete v tématu [vlastnosti geometrických obrazců](../modeling/properties-of-geometry-shapes.md) a [vlastnosti obrazových obrazců](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>K otestování obrazce

1. **Klikněte na možnost Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení pro generování kódu návrháře DSL.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 ke spuštění nové instance sady Visual Studio v experimentálním režimu. V experimentální instanci sady Visual Studio otevřete nebo vytvořte soubor, který má příponu názvu souboru tohoto kódu DSL.

3. **Ověřte, že element nástroje na panelu nástrojů.**

4. **Vytvářet tvary** přetažením z nástrojů do diagramu modelu.

5. **Ověřte, že se zobrazí každý dekoratér text,** a že:

   1.  Můžete upravit, pokud jste nastavili **je jen pro čtení uživatelského rozhraní** příznak doménové vlastnosti.

   2.  Při úpravě vlastností v okně Vlastnosti nebo v dekoratéru ostatní zobrazení se aktualizuje.

   Po otestování nejprve tvaru, můžete chtít upravit některé její vlastnosti a přidat některé pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Definování referenční stavy
 Můžete definovat vztah odkazu mezi všechny zdrojové doménové třídy a všechny cílové doménové třídy. Referenční stavy se obvykle zobrazují v diagramu jako konektory, které jsou řádky mezi tvary.

 Například pokud hudebních alb a umělci se zobrazují jako tvarů v diagramu, můžete definovat relace s názvem ArtistsAppearedOnAlbums, která propojení umělci do alb, na kterých jste pracovali. Podívejte se na příklad na obrázku.

 ![Instance modelu generované DSL](../modeling/media/music_instance.png)

 Vztahy odkazu můžete také propojit prvky stejného typu. Například v DSL představující řady stromu, vztah mezi nadřazené položky a jejich podřízené položky, je vztah odkazu z osoba na osobu.

### <a name="define-a-reference-relationship"></a>Definovat vztah odkazu
 Klikněte na nástroj referenční vztah pak klikněte na tlačítko doménová třída zdroje relace a pak klikněte na cílovou třídu domény. Cílová třída může být stejná jako třída zdroje.

 Každý vztah má dvě role, reprezentovaný řádek na každé straně pole relace. Můžete vybrat jednotlivé role a nastavte jeho vlastnosti v okně Vlastnosti.

 **Vezměte v úvahu přejmenování role**. Například ve vztahu mezi osoby a osoby, můžete změnit výchozí názvy nadřazené a podřízené položky, správce a podřízené uzly, učitelů a studentů a tak dále.

 **Nastavení násobnosti každou roli**, pokud je to nezbytné. Pokud chcete, aby každý uživatel mít maximálně jeden vedoucí, nastavení násobnosti, které se zobrazí pod popiskem správce do diagramu a 0..1.

 **Vlastnosti domény přidáte do relace.** Na obrázku má vztah interpreta alba vlastnost role.

 **Nastavte vlastnost relace, umožňuje duplikuje** Pokud více než jedno propojení stejné třídy může existovat mezi stejného páru prvků modelu. Například můžete umožnit učitel naučit více než jeden v souladu s stejné studentů.

 ![Mapy obrazců pro konektory](../modeling/media/music_connector.png)

 Další informace najdete v tématu [vlastnosti vztahů domény](../modeling/properties-of-domain-relationships.md) a [Vlastnosti rolí domény](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definice konektoru k zobrazení relace
 Konektor zobrazí čáry mezi dvěma tvary v diagramu modelu.

 Přetáhněte **konektor** nástroj na diagramem definice DSL.

 Pokud chcete zobrazit popisky na konektoru, přidejte dekoratéry textu. Nastavte jejich umístění. Aby mohl uživatel přesunout dekoratér text, nastavte jeho **je přesouvat** vlastnost.

 Použití **mapa elementu diagramu** nástroj konektor odkaz na referenční vztah.

 S mapou elementu diagramu vybrán, otevřete **podrobnosti DSL** okna a otevřete **mapování Dekoratéru** kartu.

 Vyberte jednotlivé **Dekoratér** a nastavte **zobrazit vlastnost** vlastnosti správné doméně.

 Ujistěte se, že se zobrazí zaškrtávací políčko vedle každé položky v **Dekoratéry** seznamu.

### <a name="define-a-connection-builder-tool"></a>Definování nástroj Tvůrce připojení
 V **Průzkumník DSL** okna, rozbalte **Editor** uzel a všechny jeho podřízené uzly.

 Klikněte pravým tlačítkem na uzel, který má stejný název jako vaše DSL a potom klikněte na tlačítko **přidat nové připojení nástroje**.

 Když je vybraný nový nástroj, v okně Vlastnosti:

-   Nastavte **titulek** a **popisek**.

-   Klikněte na tlačítko **Tvůrce připojení** a vyberte příslušný tvůrce pro novou relaci.

-   Nastavte **panelu nástrojů ikonu** na ikonu, která se má zobrazit na panelu nástrojů. Můžete ho nastavit na novou ikonu nebo ikonu již používá pro jiný nástroj.

     Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumníka řešení**. Zkopírujte a vložte jednu existující soubory BMP nástroj elementu. Přejmenujte vložené kopie a potom dvakrát klikněte na Upravit.

     Vraťte se do diagramem definice DSL, vyberte nástroj a v okně Vlastnosti klikněte na tlačítko **[...]**  v **panelu nástrojů ikonu**. V **vybrat rastrový obrázek** dialogovém okně vyberte vaše. BMP soubor z rozevírací nabídky.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Chcete-li otestovat referenční vztah a spojnici

1. **Klikněte na možnost Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení pro generování kódu návrháře DSL.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 ke spuštění nové instance sady Visual Studio v experimentálním režimu. V experimentální instanci sady Visual Studio otevřete nebo vytvořte soubor, který má příponu názvu souboru tohoto kódu DSL.

3. **Ověřte, že nástroje pro připojení se zobrazí na panelu nástrojů.**

4. **Vytvářet tvary** přetažením z nástrojů do diagramu modelu.

5. **Vytvoření připojení** mezi tvary. Klikněte na nástroj konektor, klikněte na obrazec a potom klikněte na jiný tvar.

6. **Ověřte, že nelze vytvořit připojení mezi třídami nevhodný.** Pokud váš vztah mezi alba a umělci, ověřte například, nelze propojení umělci umělci.

7. **Ověřte správnost násobnosti. Ověřte například, že uživatel nemůže připojit k více než jeden správce.**

8. **Ověřte, že se zobrazí každý dekoratér text,** a že:

   1.  Můžete upravit, pokud jste nastavili **je jen pro čtení uživatelského rozhraní** příznak doménové vlastnosti.

   2.  Při úpravě vlastností v okně Vlastnosti nebo v dekoratéru ostatní zobrazení se aktualizuje.

   Po otestování nejprve konektor, můžete chtít upravit některé její vlastnosti a přidat některé pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Definování tvary, které obsahují seznamy: obrazců oddílů
 Obrazec oddílu obsahuje jeden nebo více seznamů položek. Například v Library DSL Hudba, můžete použít obrazců prostoru k reprezentaci Hudba alb. V každé Album je seznam skladeb.

 ![Obrazec oddílu](../modeling/media/compartmentshape.png)

 V Nejjednodušším způsobem, dosažení tohoto efektu v definici DSL definujete jednu třídu domény kontejneru a jednu třídu domény pro každý seznam. Třída kontejneru je namapována na obrazec oddílu.

 ![Mapa obrazce](../modeling/media/music_mapcomp.png)

 Další informace najdete v tématu [vlastnosti obrazců prostoru](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Chcete-li definovat obrazce oddílu

1.  **Vytvoření doménové třídy kontejneru**. Klikněte na tlačítko **vztah obsažení** nástroj, klikněte na tlačítko kořenová třída modelu a pak klikněte na prázdnou část diagramem definice DSL. Tím se vytvoří doménová třída s názvem alba příklad obrázku.

     Namísto vložení ve třídě kořenové, případně můžete vložit kontejneru ve třídě domény, který je namapovaný na plaveckou dráhou.

     Přidejte do třídy doménová vlastnost, jako je například název a nastavte jeho **je název elementu** příznak v okně Vlastnosti.

2.  **Vytvoření seznamu položek doménová třída**. Klikněte na tlačítko **vztah obsažení** nástroj, klikněte kontejner – třída (alba) a potom klikněte na prázdnou část diagramu. Tím se vytvoří doménová třída s názvem skladby příklad obrázku.

     Přidejte doménová vlastnost, jako je název třídy a nastavte jeho **je název elementu** příznak.

     Přidejte další vlastnosti domény.

     Přidáte jiné třídy domény pro každý seznam, který chcete zobrazit seznam položek.

3.  **Kombinovat několik typů položek v seznamu**, vytváření tříd, které dědí z třídy seznamu. Vytvořte abstraktní třídu seznam tak, že nastavíte její **modifikátor dědičnosti**.

     Například pokud chcete být řada seřazena podle autora místo interpreta klasického Hudba, můžete vytvořit dvě podtřídy skladby, ClassicalSong a NonClassicalSong.

4.  **Vytvoření tvaru prostoru**. Přetáhněte z **obrazec oddílu** nástroj na diagramem definice DSL.

     Přidejte text dekoratér a nastavte její název.

     Přidejte oddíl a nastavte její název.

5.  Aby mohl uživatel skrytí oddílů seznamu, klikněte pravým tlačítkem na třídu obrazec oddílu, přejděte na **přidat**a potom klikněte na tlačítko **Dekoratér rozbalení/sbalení**. V okně Vlastnosti nastavte pozici dekoratéru.

6.  Klikněte na tlačítko **mapa elementu diagramu** nástroj, klikněte na tlačítko doménové třídy kontejneru a klikněte na obrazec oddílu.

7.  Vyberte odkaz Mapa elementu diagramu mezi doménové třídy a tvar. V **podrobnosti DSL** okno:

    1.  Klikněte na tlačítko **Dekoratéry** kartu. Klikněte na název dekoratéru a pak vyberte příslušnou položku v rámci **vlastnost Display, vlastnost**. Ujistěte se, že se zobrazí zaškrtávací políčko vedle názvu dekoratér.

    2.  Klikněte na tlačítko **mapy oddílů** kartu.

         Klikněte na název oddílu.

         V části **cestu ke kolekci elementů zobrazené**, přejděte k seznamu element třídy (skladby). Klikněte na šipku rozevíracího seznamu a pomocí nástroje Navigátor.

         V části **vlastnost Display, vlastnost**, vyberte vlastnost, která má být zobrazen v seznamu. V příkladu je to název.

> [!NOTE]
>  S použitím cesty pole v mapě Dekoratéru a prostoru pro mapování polí, můžete provést složitější vztahy mezi doménovými třídami a obrazce oddílu.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Chcete-li definovat nástroj pro vytváření tvar

1.  **Nastavit položku sady nástrojů pro vytváření elementů doménové třídy.**

2.  V **Průzkumník DSL**, rozbalte **Editor** uzel a jeho dílčí uzly.

3.  Klikněte pravým tlačítkem na uzel v rámci **karty panelu nástrojů** , který má stejný název jako vaše DSL, například MusicLibrary. Klikněte na tlačítko **přidat nástroj pro Element**.

    > [!NOTE]
    >  Pokud kliknete pravým tlačítkem **nástroje** uzlu, neuvidíte **přidat nástroj pro Element**. Místo toho klikněte na uzel nad ním.

4.  V okně Vlastnosti nový nástroj prvek vybraný, nastavte **třídy** do doménové třídy, které jste nedávno přidali.

5.  Nastavte **titulek** a **popisek**.

6.  Nastavte **panelu nástrojů ikonu** na ikonu, která se zobrazí na panelu nástrojů. Můžete ho nastavit na novou ikonu nebo ikonu již používá pro jiný nástroj.

     Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumníka řešení**. Zkopírujte a vložte jednu z existujících nástrojů elementu. Soubory BMP. Přejmenujte vložené kopie a potom dvakrát klikněte na Upravit.

     Vraťte se do diagramem definice DSL, vyberte nástroj a v okně Vlastnosti klikněte na tlačítko **[...]**  v **panelu nástrojů ikonu**. V **vybrat rastrový obrázek** dialogového okna, vyberte svůj soubor BMP z rozevírací nabídky.

#### <a name="to-test-a-compartment-shape"></a>K otestování obrazce oddílu

1. **Klikněte na možnost Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení pro generování kódu návrháře DSL.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 ke spuštění nové instance sady Visual Studio v experimentálním režimu. V experimentální instanci sady Visual Studio otevřete nebo vytvořte soubor, který má příponu názvu souboru tohoto kódu DSL.

3. **Ověřte, zda nástroj objeví na panelu nástrojů.**

4. Nástroj přetáhněte do diagramu modelu. Vytvoření tvaru.

    Ověřte, že název elementu, který se zobrazí a je automaticky nastaven na výchozí hodnotu.

5. Klikněte pravým tlačítkem na záhlaví nový obrazec a potom klikněte na tlačítko Přidat *Your položky seznamu.* V tomto příkladu je příkaz přidat skladby.

    Ověřte, že se položka zobrazí v seznamu a že má nový název.

6. Klikněte na jednu z položek seznamu a potom si prohlédněte okno Vlastnosti. Měli byste vidět vlastnosti položky seznamu.

7. Otevřete Průzkumníka jazyka. Ověřte, že můžete zobrazit uzly kontejneru s uzly seznam položek uvnitř.

   ![Vygenerovaný Průzkumník DSL](../modeling/media/music_explorer.png)

   Po otestování nejprve obrazce oddílu, můžete chtít upravit některé jeho vlastnosti a přidat některé pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Zobrazení odkazu v oddíl
 Element, který se zobrazí v oddíl je obvykle podřízený prvek, který je reprezentován obrazce oddílu. Ale v některých případech se má zobrazit element, který je propojen s vztah odkazu.

 Například jsme do AlbumShape, který zobrazí seznam umělcům, které jsou propojeny s alba přidat druhý oddíl.

 V takovém případě by měl oddílu zobrazí odkaz, namísto odkazovaný element. Důvodem je, že když uživatel vybere položku v oddílu a stiskne klávesu DELETE, má odkaz má být odstraněna, nikoli odkazovaný element.

 Nicméně může mít název odkazovaného elementu se zobrazí v oddílu.

 Následující postup předpokládá, že jste již vytvořili doménová třída, referenční vztah, obrazce oddílu a mapa elementu diagramu, jak je popsáno výše v této části.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Chcete-li zobrazit odkaz v oddíl

1.  **Přidat oddíl obrazce oddílu**. V definici DSL diagramu, klikněte pravým tlačítkem na třídu obrazec oddílu, přejděte na **přidat**a potom klikněte na tlačítko **oddílu**.

2.  Nastavte **cestu ke kolekci elementů zobrazené** přejít na odkaz, namísto jeho cílového prvku. Klikněte na rozevírací nabídku a vyberte vztah odkazu místo jeho cílové pomocí ve stromovém zobrazení. V tomto příkladu je relace **ArtistAppearedOnAlbums**.

3.  Nastavte **cesta k vlastnosti zobrazení** přejít z odkazu na target element. V tomto příkladu je to **interpreta**.

4.  Nastavte **vlastnost Display, vlastnost** příslušné vlastnosti elementu target, například **název**.

5.  **Transformovat všechny šablony**, sestavit a spustit DSL a otevřete model testů.

6.  V diagramu modelu vytvořit příslušné třídy tvar, nastavit jejich názvy a vytvořit propojení mezi nimi. V obrazec oddílu by se zobrazit názvy propojené prvky.

7.  Vyberte odkaz nebo položka v obrazce oddílu. Odkaz a položka by měla zmizet.

## <a name="ports"></a> Definování porty na hranici jiný tvar
 Port je tvar, který se nachází na hraniční části jiného obrazce.

 Porty lze také nabízí bod pevné připojení na jiný tvar, do kterého uživatel můžete nakreslit konektory. V takovém případě můžete nastavit obrazec portu transparentní.

 Chcete-li zobrazit příklad, který používá porty, vyberte **Diagram komponent** šablony při vytváření nové řešení DSL. Tento příklad znázorňuje hlavní body, které můžete zvážit při definování porty:

- Je doménovou třídu, která představuje kontejneru porty `Component`.

- Existuje doménovou třídu, která představuje porty. V tomto příkladu je to `ComponentPort`.

- Existuje vztah obsažení z doménové třídy kontejneru na port doménové třídy. Další informace najdete v tématu [definování doménovými třídami](#classes).

- Pokud chcete různé druhy port kombinovat ve stejném kontejneru, můžete vytvořit podtřídy třídy domény portu. V tomto příkladu `InPort` a `OutPort` dědí `ComponentPort`.

- Doménová třída kontejneru lze mapovat na jakýkoli druh tvaru. V tomto příkladu je `ComponentShape`. Další informace najdete v tématu [definování obrazců](#shapes).

- Port doménovými třídami se mapují na port obrazce. Můžete namapovat odvozené třídy k oddělení tříd obrazec portu nebo mapovat základní třídu třídy obrazec jeden port.

  V ostatních ohledech obrazců portů chovat, jak je popsáno v [definování obrazců](#shapes).

  Další informace najdete v tématu [vlastnosti obrazců portů](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Definice DSL, která má plaveckých drah
 Plaveckých drah jsou vodorovné nebo svislé rozdělení diagramu. Každý plavecké dráhy odpovídá prvku modelu. Vaše definice DSL vyžaduje jednu doménovou třídu pro prvky plavecké dráhy.

 Nejlepší způsob, jak vytvořit DSL pomocí plaveckých drah je vytvořit nové řešení DSL a výběr šablony řešení tok úkolů. V definici DSL je třída Actor doménová třída namapované plavecké dráhy. Přejmenujte tento a jiné třídy tak, aby odpovídala váš projekt.

 Přidat třídu, která se zobrazí jako tvar uvnitř plaveckou dráhou, vytvořte vkládání vztah mezi třídou plavecké dráhy a novou třídu. Uživatelé budou moct prvky přetáhnout z jedné plavecké dráhy do jiné, ale každý prvek bude vždy uvnitř konkrétní plavecké dráhy. V šabloně řešení tok úkolů je FlowElement podřízené třídy plavecké dráhy.

 Přidat třídu, která se zobrazí jako tvar nezávisle na plaveckých drah, vytvořte vztah obsažení mezi kořenová třída a novou třídu. Uživatelé budou moct tyto tvary umístit kamkoli v diagramu, včetně přes hranice plaveckých drah a mimo plaveckých drah. V šabloně řešení tok úkolů komentář je podřízená kořenové třídy.

 Další informace najdete v tématu [vlastnosti plaveckých drah](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Přidání typů vlastností

### <a name="domain-enumerations-and-literals"></a>Výčty domény a literály
 Výčet domén je typ literálu hodnotami.

 Chcete-li přidat výčet domén, klikněte pravým tlačítkem na kořen modelu v **Průzkumník DSL** a potom klikněte na **přidat nový výčet domén**. Prvek se zobrazí v **Průzkumník DSL** pod **typy domén** uzlu. Tento prvek se nezobrazí v diagramu.

 Chcete-li přidat literály výčtu pro výčet domén, klikněte pravým tlačítkem na výčet domén v **Průzkumník DSL** a potom klikněte na **přidat nový výčet literálu**.

 Ve výchozím nastavení vlastnost, která má typ výčtu lze nastavit pouze jednu hodnotu výčtu v čase. Pokud chcete uživatelům a programátoři můžete nastavit libovolnou kombinaci hodnot – "bitového pole" – nastavte **IsFlags** vlastnost výčtu.

### <a name="external-types"></a>Externí typy
 Když nastavíte typ doménová vlastnost, Pokud nenajdete typ má **typ** rozevíracího seznamu, můžete přidat externí. Například můžete přidat **System.Drawing.Color** typem do seznamu.

 Přidejte typ, klikněte pravým tlačítkem na kořen modelu v Průzkumník DSL a potom klikněte na tlačítko **přidat novou externí typ**. V okně Vlastnosti nastavte název na **barva** a oboru názvů **System.Drawing**. Tento typ se nyní zobrazí v Průzkumníku DSL v části **typy domén**. Můžete ho pokaždé, když nastavíte typ doménové vlastnosti.

## <a name="custom"></a> Přizpůsobení DSL
 Pomocí technik popsaných v tomto tématu, můžete rychle vytvořit DSL s graficky zápis, čitelné formě XML a základní nástroje, které jsou nutné ke generování kódu a další artefakty.

 Rozšíření definice DSL dvěma způsoby:

1.  Vylaďte DSL pomocí další funkce definici DSL. Například můžete provést jeden konektor nástroj, který můžete vytvořit několik typů konektor a můžete určit pravidla, které odstraníte jeden element dojde také k odstranění souvisejících prvků. Tyto postupy jsou většinou dosaženo pomocí nastavení hodnoty v definici DSL a některé vyžadují pár řádků kódu programu.

     Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

2.  Rozšíření nástrojů pro modelování pomocí kódu programu k dosažení pokročilejší účinky. Například můžete vytvořit příkazy nabídek, které můžete změnit model a vytvoříte nástroje, které se integrují nejmíň dva DSL. Vmsdk následující položky je navržená speciálně pro usnadnění integrace vašich rozšíření s kódem, který je generován z definice DSL.  Další informace najdete v tématu [psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Změna definice DSL
 Při vytváření libovolnou položku v definici DSL mnoho výchozí hodnoty jsou nastaveny automaticky. Po nastavení, můžete je změnit. To zjednodušuje vývoj DSL, zároveň umožní výkonné úpravy.

 Například když namapuje obrazec na element, cesta k nadřazenému elementu mapování automaticky nastavena podle vztah obsažení doménové třídy. Nicméně pokud později změníte vztah obsažení, cesta k nadřazenému elementu se nezmění automaticky.

 Proto by měl být vědomi, že při změně některých relací v definici DSL není, že u chyby, které má být hlášen při ukládání definice nebo když Transformovat všechny šablony. Většina těchto chyb jsou snadno to vyřešíme. Klikněte dvakrát na zprávy o chybách k zobrazení umístění chyby.

 Viz také [postupy: Změna Namespace jazyka specifického pro doménu](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Řešení potíží
 Následující tabulka uvádí některé z nejběžnějších problémů, které se vyskytují při návrhu DSL, společně s návrhy pro jejich řešení. Další Rady, jak je k dispozici na [vizualizace nástroje Extensibililty fórum](http://go.microsoft.com/fwlink/?LinkId=186074).


| Problém | Návrh |
|-|-|
| Změny, které můžu provedli v souboru definic DSL nemají žádný vliv. | Klikněte na tlačítko **Transformovat všechny šablony** na panelu nástrojů nad Průzkumníka řešení a pak znovu sestavte řešení. |
| Tvary zobrazit název dekoratéru místo hodnoty vlastnosti. | Nastavte mapování dekoratéru. V definici DSL diagramu klikněte na tlačítko mapa elementu diagramu, který je Šedá čára mezi třídy domény a tvar.<br /><br /> Otevřít **podrobnosti DSL** okna. Pokud nevidíte, v nabídce Zobrazit, přejděte na **ostatní Windows**a potom klikněte na tlačítko **podrobnosti DSL**.<br /><br /> Klikněte na tlačítko **mapování Dekoratéru** kartu. Vyberte název dekoratér. Ujistěte se, že je zaškrtnuté políčko vedle něj. V části **zobrazit vlastnost**, vyberte název doménové vlastnosti.<br /><br /> Další informace najdete v tématu [tvary v diagramu](#shapes). |
| V Průzkumníku DSL nelze přidat do kolekce. Například když mám klikněte pravým tlačítkem na nástroje, neexistuje žádný příkaz "Přidat nástroj" v nabídce.<br /><br /> V Průzkumníku pro tento DSL nelze přidat element do seznamu. | Klikněte pravým tlačítkem na položku nad uzel, který se pokoušíte. Pokud chcete přidat do seznamu, je příkaz Přidat není v seznamu uzlu, ale jeho vlastník. |
| Jsem vytvořil doménovou třídou, ale nejde mi vytvořit instance v Průzkumníku jazyka. | Každá třída domény s výjimkou kořenové musí být cílem vztah obsažení. |
| V Průzkumníku pro tento DSL prvky jsou zobrazeny pouze s jejich názvů typů. | V definici DSL vyberte doménovou vlastnost třídy a ve vlastnostech okno, nastavte **je název elementu** na hodnotu true. |
| Moje DSL vždy otevře v editoru XML. | To může nastat z důvodu chyby při při čtení souboru. Ale i poté, co je opravit tuto chybu, je nutné explicitně obnovit editoru návrháře DSL.<br /><br /> Klikněte pravým tlačítkem na položku projektu, klikněte na tlačítko **otevřít v** a vyberte * YourLanguage ***návrháře (výchozí)**. |
| Panel nástrojů DSL, své nezobrazuje po změně názvy sestavení. | Zkontrolovat a aktualizovat **DslPackage\GeneratedCode\Package.tt** Další informace najdete v tématu [postupy: Změna Namespace jazyka specifického pro doménu](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| Nástrojů DSL, své nezobrazí, ale I nedošlo ke změně názvu sestavení.<br /><br /> Nebo se zobrazí okno se zprávou, vytváření sestav selhání při načítání rozšíření. | Resetovat experimentální instanci a znovu sestavte své řešení.<br /><br /> 1.  V Windows nabídky Start, v části **všechny programy**, rozbalte [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)], pak **nástroje**a potom klikněte na tlačítko **resetování Microsoft Visual Studio experimentální instanci aplikace**.<br />2.  Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**. |

## <a name="see-also"></a>Viz také

- [Začínáme s jazyky specifickými pro doménu](../modeling/getting-started-with-domain-specific-languages.md)
- [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)