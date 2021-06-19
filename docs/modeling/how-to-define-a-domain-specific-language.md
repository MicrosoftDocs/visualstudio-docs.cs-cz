---
title: Jak se definuje jazyk specifický pro doménu
description: Přečtěte si, jak vytvořit řešení sady Visual Studio ze šablony pro definování jazyka specifického pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51717e4bdbf12478e22bb825a9c84cfc82815f98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387356"
---
# <a name="how-to-define-a-domain-specific-language"></a>Jak se definuje jazyk specifický pro doménu
Pokud chcete definovat jazyk specifický pro doménu (DSL), vytvoříte řešení sady Visual Studio ze šablony. Klíčovou součástí řešení je diagram definice DSL, který je uložený v DslDefinition. DSL. Definice DSL definuje třídy a tvary DSL. Po úpravě a přidání na tyto prvky můžete přidat programový kód pro přizpůsobení DSL.

Pokud s DSL začínáte, doporučujeme vám pracovat přes **testovací prostředí nástrojů DSL**, které najdete na tomto webu: [vizualizace a sada SDK pro modelování](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Výběr řešení šablony

K definování DSL musíte mít nainstalované následující součásti:

- Visual Studio
- Úlohy vývoje rozšíření pro Visual Studio (zahrnuje sadu Visual Studio SDK)
- Modelování sady SDK (instalace jako jednotlivé komponenty v sadě Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Chcete-li vytvořit nový jazyk specifický pro doménu, vytvořte nové řešení sady Visual Studio pomocí šablony projektu Domain-Specific jazyka.

### <a name="to-create-a-dsl-solution"></a>Vytvoření řešení DSL

1. Vytvořte nový projekt **jazyka specifického pro doménu** .

   ::: moniker range="vs-2017"

    ![Dialog vytvořit DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    Otevře se **Průvodce jazykem specifickým pro doménu** a zobrazí se seznam řešení DSL šablon.

2. Kliknutím na každou šablonu zobrazíte její popis. Vyberte řešení, které nejlépe odpovídá těm, které chcete vytvořit.

    Každá šablona DSL definuje základní funkční DSL. Tuto DSL budete upravovat tak, aby vyhovovala vašim požadavkům.

    Další informace získáte po kliknutí na jednotlivé vzorky.

   - Vyberte **tok úlohy** a vytvořte DSL, který má plavecké dráhy. Plavecké dráhy jsou svislé nebo vodorovné oddíly diagramu.

   - Vyberte **modely komponent** pro vytvoření DSL s porty. Porty jsou malé tvary na hranici většího tvaru.

   - Vyberte **diagramy tříd** pro definování DSL, který má obrazce oddílu. Obrazce oddílů obsahují seznam položek.

   - V jiných případech vyberte **Minimální jazyk** , nebo pokud si nejste jistí.

   - Pokud chcete vytvořit DSL, která se zobrazí na model Windows Forms nebo na povrchu WPF, vyberte **minimální Návrhář DataGridView** nebo **Návrhář WPF** . Budete muset napsat kód, který definuje Editor. Další informace najdete v následujících tématech:

        [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Na příslušné stránce průvodce zadejte příponu názvu souboru DSL. Toto je rozšíření, které budou používat soubory, které obsahují instance vaší DSL.

   - Vyberte příponu názvu souboru, která není přidružená k žádné aplikaci ve vašem počítači, nebo na počítači, na který chcete nainstalovat DSL. Například soubory **DOCX** a **htm** by mohly být nepřijatelné přípony názvů souborů.

   - Průvodce vás upozorní, pokud rozšíření, které jste zadali, je používáno jako DSL. Zvažte použití jiné přípony názvu souboru. Můžete také resetovat experimentální instanci sady Visual Studio SDK a vymazat starší experimentální návrháře. Klikněte na tlačítko **Start**, klikněte na položku **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje** a poté **resetujte experimentální instanci Microsoft Visual Studio 2010**.

4. Můžete buď upravit nastavení na ostatních stránkách, nebo ponechat výchozí hodnoty.

5. Klikněte na **Finish** (Dokončit).

    Průvodce vytvoří řešení, které obsahuje dva nebo tři projekty a generuje kód z definice DSL.

   Uživatelské rozhraní teď vypadá podobně jako na následujícím obrázku.

   ![Návrhář DSL](../modeling/media/dsl_designer.png)

   Toto řešení definuje jazyk specifický pro doménu. Další informace najdete v tématu [Přehled uživatelského rozhraní nástroje Domain-Specific Language Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testování řešení
 Řešení šablon poskytuje pracovní DSL, který můžete upravit nebo použít.

 Chcete-li řešení otestovat, stiskněte klávesu F5 nebo CTRL + F5. Nová instance aplikace Visual Studio se otevře v experimentálním režimu.

 V nové instanci aplikace Visual Studio otevřete v Průzkumník řešení ukázkový soubor. Otevře se jako diagram se sadou nástrojů.

 Pokud spustíte řešení, které jste vytvořili ze šablony **minimálního jazyka** , experimentální aplikace Visual Studio bude vypadat jako v následujícím příkladu:

 ![Strom ukázkového jazyka specifického pro doménu v aplikaci Visual Studio](../modeling/media/dsl_min.png)

 Experimentujte s nástroji. Vytvořte prvky a připojte je.

 Zavřete experimentální instanci sady Visual Studio.

> [!NOTE]
> Po úpravě DSL již nebudete moci zobrazit obrazce v ukázkovém testovacím souboru. Budete však moci vytvořit nové prvky.

### <a name="modifying-the-template-dsl"></a>Úprava šablony DSL
 Přejmenujte a udržujte některé nebo všechny třídy domény a třídy tvarů v definici DSL šablony. Nové názvy tříd by měly být platnými názvy CLR bez mezer nebo interpunkčních znamének.

 Je zvláště užitečné pro uchování těchto tříd:

- Kořenová třída se zobrazí v levém horním rohu diagramu definice DSL v části **třídy a vztahy**. Přejmenujte ho na jiný název než DSL. Například DSL s názvem **MusicLibrary** může mít kořenovou třídu s názvem **Music**.

- Třída diagramu se zobrazí v pravém dolním rohu diagramu definice DSL ve sloupci **prvky diagramu** . Možná se budete muset posunout doprava, aby se zobrazila. Obvykle se nazývá _YourDsl_**diagram**.

- Pokud jste použili šablonu **toku úkolů** a chcete vytvořit diagramy s plavecké dráhy, ponechejte a přejmenujte třídu domény objektu actor a ActorSwimlane obrazec.

  Odstraňte nebo přejmenujte jiné třídy tak, aby vyhovovaly vašim požadavkům.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> Vzory pro definování DSL
 Doporučujeme, abyste vyvinuli DSL přidáním nebo úpravou jedné nebo dvou funkcí najednou. Přidejte funkci, spusťte DSL a otestujte ji a pak přidejte jednu nebo dvě další funkce. Typickou funkcí DSL může být:

- Doménová třída, vztah vložení, který připojuje prvek k modelu, tvar potřebný k zobrazení prvků této třídy v diagramu a nástroje prvku, který umožňuje uživatelům vytvářet prvky.

- Vlastnosti domény doménové třídy a dekoratéry, které je zobrazují na obrazci.

- Vztah odkazu a konektor, který ho zobrazuje v diagramu a nástroji konektoru, který umožňuje uživatelům vytvářet odkazy.

- Vlastní nastavení, které vyžaduje programový kód, jako je například omezení ověřování nebo příkaz nabídky.

  Následující části popisují, jak vytvořit nejužitečnější druhy funkcí DSL. Existuje mnoho dalších vzorů, se kterými lze vytvořit DSL, ale jedná se o nejčastěji používané.

> [!NOTE]
> Po přidání funkce nezapomeňte kliknout na **transformovat všechny šablony** na panelu nástrojů Průzkumník řešení před sestavením a spuštěním vaší DSL.

 Následující obrázek ukazuje třídy a vztahy část DSL, která se používá jako příklad v tomto tématu.

 ![Vztahy vložení a odkazování](../modeling/media/music_classes.png)

 Dalším obrázkem je vzorový model této DSL:

 ![Model instance generované DSL](../modeling/media/music_instance.png)

> [!NOTE]
> "Model" odkazuje na instanci vaší DSL, kterou uživatelé vytvářejí, a obvykle se zobrazuje jako diagram. Toto téma popisuje diagram definice DSL i diagramy modelů, které se zobrazí při použití DSL.

## <a name="defining-domain-classes"></a><a name="classes"></a> Definování doménových tříd
 Třídy domény reprezentují koncepty vaší DSL. Instance jsou *prvky modelu*. Například v **MusicLibrary** DSL můžete mít třídy domény s názvem **album** a **skladba**.

 Chcete-li vytvořit doménovou třídu, můžete přetáhnout z **pojmenovaného nástroje doménové třídy** do diagramu a pak přejmenovat třídu.

 Další informace najdete v tématu [vlastnosti doménových tříd](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Vytvoření relace vložení pro každou doménovou třídu
 Každá doménová třída s výjimkou kořenové třídy musí být cílem nejméně jedné relace vložení nebo musí dědit ze třídy, která je cílem relace vložení.

 V modelu je každý prvek modelu uzel v jediném stromu vztahů vkládání. Zdroj a cíl vztahu vkládání se často označují jako nadřazené a podřízené.

 Výběr nadřazené třídy domény závisí na tom, jak chcete, aby životnost jejích prvků závisely na jiných prvcích. Pokud se odstraní uzel stromu, obvykle se odstraní i jeho podstrom. Třídy prvku, které mají nezávislou existenci, jsou proto vloženy přímo do kořenové třídy.

 Pokud zobrazíte prvek uvnitř jiného prvku, obvykle chcete označit vztah vlastníka. V takovém případě je nejvhodnější nadřazenou třídou třída kontejneru. Výjimkou je, když položka, kterou vidíte uvnitř kontejneru, je ve skutečnosti pouze odkazem na nezávislý prvek. V takovém případě odstraněním kontejneru odstraníte odkaz, ale ne jeho cíl.

 Ve vzorech definice DSL popsané v tomto tématu budeme předpokládat, že prvky zobrazené uvnitř kontejneru budou odstraněny při odstranění kontejneru. Složitějších schémat je možné dosáhnout definováním pravidel.

|Zobrazení elementu|Nadřazená třída (vkládání)|Příklad v šabloně řešení DSL|
|-|-|-|
|Tvar v diagramu<br /><br /> Dráha.|Kořenová třída DSL.|Minimální jazyk.<br /><br /> Tok úlohy: Třída objektu actor.|
|Tvarovat v plaveckých drah|Doménová třída prvků, které se zobrazují jako dráhy|Tok úlohy: Třída úlohy.|
|Položka v seznamu ve tvaru , kde se položka odstraní, pokud dojde k odstranění kontejneru.<br /><br /> Port na hraně obrazce.|Doménová třída, která je namapovaná na obrazec kontejneru.|Diagram tříd: Třída atributu.<br /><br /> Diagram komponent: Třída portu.|
|Položka v seznamu, není odstraněná, pokud dojde k odstranění kontejneru.|Kořenová třída DSL.<br /><br /> V seznamu se zobrazí referenční odkazy.||
|Nezobrazuje se přímo.|Třída, která je součástí.||

 V příkladu s knihovnou Music Library se v seznamu zobrazí obdélníky s názvy skladb. Proto je nadřazeným objektem Produchová kořenová třída Music a nadřazeným objektem je Song.

 Pokud chcete vytvořit třídu domény a její vložení současně, klikněte na nástroj Vztah vkládání, klikněte na nadřazenou třídu a potom klikněte na prázdnou část diagramu. 

 Obvykle není nutné upravovat název vztahu vkládání a jeho rolí, protože budou automaticky sledovat názvy tříd.

 Další informace naleznete v části [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and Properties of Domain [Roles](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Vkládání není totéž jako dědičnost. Děti ve vztahu vkládání nezdědí funkce od svých rodičů.

### <a name="add-domain-properties-to-each-domain-class"></a>Přidání vlastností domény do každé třídy domény
 Vlastnosti domény ukládají hodnoty. Příklady: Název, Název, Datum publikování.

 Klikněte **na Vlastnosti** domény ve třídě, stiskněte klávesu ENTER a zadejte název vlastnosti. Výchozí typ vlastnosti domény je String. Pokud chcete typ změnit, vyberte vlastnost domény a  v okně **Vlastnosti** nastavte Typ. Pokud v rozevíracím seznamu není typ, který chcete použít, podívejte se na přidání [typů vlastností](#addTypes).

 **Nastavte vlastnost Název elementu.** Vyberte vlastnost domény, kterou můžete použít k identifikaci prvků v Průzkumníku jazyka. Například ve třídě domény Song byste mohli vybrat vlastnost Doména názvu. V okně **Vlastnosti** nastavte **Is Element Name** na `true` .

### <a name="create-derived-domain-classes"></a>Vytvoření odvozených doménových tříd
 Pokud chcete, aby doménová třída měl varianty, které dědí její vlastnosti a relace, vytvořte třídy, které jsou z ní odvozené. Například Můžete mít Odvozené třídy WMA a MP3.

 Vytvořte odvozenou třídu pomocí nástroje **Domain Class.**

 Klikněte na **nástroj Dědičnost,** klikněte na odvozenou třídu a potom klikněte na základní třídu.

 Zvažte nastavení **modifikátoru dědičnosti** základní třídy na **abstraktní**. Pokud si myslíte, že byste mohli potřebovat instance základní třídy, zvažte místo nich vytvoření samostatné odvozené třídy.

 Odvozené třídy dědí vlastnosti a role svých základních tříd.

### <a name="tidy-the-dsl-definition-diagram"></a>Tidy the DSL Definition Diagram
 Když přidáte relace, některé třídy se zobrazí na více než jednom místě. Pokud chcete snížit počet výskytů a rozšířit diagram, klikněte pravým tlačítkem na cílovou třídu relace a pak klikněte na Bring Tree Here (Sem **přenést strom).** Pro opačný efekt klikněte pravým tlačítkem na cílovou třídu relace a klikněte na **Rozdělit strom**. Pokud tyto příkazy nabídky nevidíte, ujistěte se, že je vybraná pouze třída domény.

 K přesunutí tříd domén a tříd tvarů použijte kombinaci kláves CTRL+šipka nahoru a CTRL+dolů.

### <a name="test-the-domain-classes"></a>Testování doménových tříd

##### <a name="to-test-the-new-domain-classes"></a>Testování nových tříd domény

1. **Kliknutím na Transformovat všechny** šablony na panelu nástrojů Průzkumník řešení a vygenerujte kód návrháře DSL. Tento krok můžete automatizovat. Další informace najdete v tématu [Automatizace transformace všech šablon.](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

2. **Sestavte a spusťte DSL.** Stisknutím kláves F5 nebo CTRL+F5 spusťte novou instanci Visual Studio v experimentálním režimu. V experimentální instanci Visual Studio otevřete nebo vytvořte soubor s příponou názvu vašeho DSL.

3. **Otevřete Průzkumníka.** Na straně diagramu je okno průzkumníka jazyků, které má obvykle název *Průzkumník jazyků.* Pokud toto okno nevidíte, může být na kartě pod Průzkumník řešení. Pokud ho nemůžete najít, v nabídce **View (Zobrazení)** přejděte na Other **Windows (Další okna)** a pak klikněte na YourLanguage Explorer *(Průzkumník jazyků).* 

     Průzkumník zobrazí stromové zobrazení modelu.

4. **Vytvořte nové elementy.** Klikněte pravým tlačítkem na kořenový uzel v horní části a potom klikněte na **Přidat nový**_VašeTřída_.

     V Průzkumníku jazyka se zobrazí nová instance vaší třídy.

5. Při vytváření nových instancí ověřte, že každá instance má jiný název. K tomu dojde pouze v případě, že jste **nastavili** příznak Is Element Name u vlastnosti domény.

6. **Prozkoumejte vlastnosti domény. Když máte vybranou instanci vaší třídy,** zkontrolujte okno Vlastnosti. Měl by se zobrazit vlastnosti domény, které jste definovali v této třídě domény.

7. **Uložte soubor, zavřete ho a znovu ho otevřete.** Po rozbalení uzlů by měly být všechny instance, které jste vytvořili, viditelné v průzkumníku.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Definování obrazců v diagramu
 Třídy prvků, které se zobrazují v diagramu, můžete definovat jako obdélníky, tři tečky nebo ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Definování třídy prvků, které se zobrazují jako obrazce v diagramu

1. **Definujte a otestujte třídu domény podle popisu v tématu** Definování [doménových tříd](#classes) **.**  

   - Nadřazená třída by měla být kořenová třída. To znamená, že mezi kořenovou třídou a novou doménovou třídou by měl být vztah vkládání.

   - Pokud váš diagram obsahuje dráhy, může být nadřazenou třídou domény, která je namapovaná na drah. Než budete pokračovat v tomto postupu, podívejte se na [definici DSL s drahami](#swimlanes).

2. **Přidejte třídu obrazce,** která bude představovat prvky v diagramu modelu. Přetáhněte z jednoho z následujících nástrojů do diagramu definice DSL:

   - **Tvar geometrie** poskytuje obdélník nebo tři tečky.

   - **Tvar obrázku** zobrazuje obrázek, který poskytnete.

   - **Tvar přihrádky** je obdélník, který obsahuje jeden nebo více seznamů položek.

     Přejmenujte třídu shape, která se zobrazí na pravé straně diagramu definice DSL v části Tvary a konektory.

3. **Definujte obrázek, pokud jste vytvořili obrazec obrázku**.

   1. Vytvořte soubor obrázku libovolné velikosti. Podporují se formáty BMP, JPEG, GIF a EMF.

   2. V Průzkumník řešení přidejte soubor do řešení v části Dsl\Resources.

   3. Vraťte se do diagramu definice DSL a vyberte novou třídu obrazce obrázku.

   4. V okno Vlastnosti klikněte na vlastnost **Image** .

   5. V dialogovém okně **Vybrat obrázek** klikněte na rozevírací nabídku v části **název souboru** a vyberte bitovou kopii.

4. **Přidejte text dekoratéry k obrazci, aby se zobrazily vlastnosti domény.**

    Chcete-li zobrazit název nebo název prvku modelu, budete pravděpodobně potřebovat alespoň jeden textový dekoratér.

    Klikněte pravým tlačítkem myši na záhlaví třídy Shape, přejděte na **Přidat** a pak klikněte na **text dekoratér**. Nastavte název dekoratér a ve okno Vlastnosti nastavte jeho **pozici**.

5. **Připojte každý obrazec s mapou elementu diagramu k třídě domény, kterou by měl zobrazit**.

    Klikněte na nástroj **Mapa elementu diagramu** , potom klikněte na doménovou třídu a potom klikněte na třídu Shapes.

6. **Namapujte vlastnosti na text dekoratéry.**

   1. Vyberte šedý spojnici mezi doménovou třídou a třídou Shape, která představuje mapu prvku diagramu.

   2. V okně **Podrobnosti DSL** klikněte na kartu **mapy dekoratér** . Pokud nevidíte okno **Podrobnosti DSL** , přejděte v nabídce **zobrazení** na položku **ostatní okna** a klikněte na **Podrobnosti DSL**. Je často nutné vyvolávat horní část tohoto okna, aby se zobrazil veškerý jeho obsah.

   3. Vyberte název dekoratér. V části **vlastnost zobrazení** vyberte název vlastnosti doménové třídy. Tento postup opakujte pro každou dekoratér.

       Pokud chcete zobrazit vlastnost souvisejícího prvku, klikněte na rozevírací seznam stromové struktury v oblasti **cesta k zobrazení vlastnosti**.

   4. Ujistěte se, že se vedle každého názvu dekoratér zobrazí znak zaškrtnutí.

      ![Mapování obrazců a okno Podrobnosti DSL](../modeling/media/dsldetailswindow.png)

7. **Vytvořte položku sady nástrojů pro vytváření elementů doménové třídy.**

   1. V **Průzkumníku DSL** rozbalte uzel **Editor** a všechny jeho podřízené uzly.

   2. Klikněte pravým tlačítkem myši na uzel v části **karty nástrojů** , která má stejný název jako vaše DSL, například MusicLibrary. Klikněte na tlačítko **Přidat nástroj prvku**.

       > [!NOTE]
       > Kliknete-li pravým tlačítkem myši na uzel **nástroje** , nebudete vidět **Nástroj pro přidání prvku**. Místo toho klikněte na uzel nad ním.

   3. V okno Vlastnosti s vybraným novým nástrojem elementu nastavte **třídu** na doménovou třídu, kterou jste nedávno přidali.

   4. Nastavení **nadpisu** a **popisu tlačítka**

   5. Nastavte **ikonu panelu nástrojů** na ikonu, která se zobrazí v sadě nástrojů. Můžete ji nastavit na novou ikonu nebo ikonu již použitou pro jiný nástroj.

        Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumník řešení**. Zkopírujte a vložte jeden z existujících souborů BMP nástrojů elementu. Přejmenujte vloženou kopii a pak ji dvakrát klikněte pro úpravu.

        Vraťte se do diagramu definice DSL, vyberte nástroj a na okno Vlastnosti klikněte na **[...]** v **panelu nástrojů ikona**. V dialogovém okně **Vybrat rastrový obrázek** vyberte v rozevírací nabídce soubor .BMP.

   Další informace najdete v tématu [vlastnosti geometrických tvarů](../modeling/properties-of-geometry-shapes.md) a [vlastností](../modeling/properties-of-image-shapes.md)obrazových tvarů.

#### <a name="to-test-shapes"></a>Testování obrazců

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 spusťte novou instanci sady Visual Studio v experimentálním režimu. V experimentální instanci aplikace Visual Studio otevřete nebo vytvořte soubor, který má příponu názvu souboru DSL.

3. **Ověřte, zda se nástroje prvku zobrazují v sadě nástrojů.**

4. **Vytváření tvarů** přetažením z nástroje do diagramu modelu.

5. **Ověřte, že se dekoratér všechny texty** a že:

   1. Můžete ho upravit, pokud jste u vlastnosti doména nenastavili příznak **je jen pro čtení uživatelského rozhraní** .

   2. Když upravíte vlastnost v okno Vlastnosti nebo v dekoratér, druhé zobrazení se aktualizuje.

   Po prvním otestování tvaru možná budete chtít upravit některé vlastnosti a přidat ještě pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Definování referenčních vztahů
 Můžete definovat referenční vztah mezi jakoukoli doménovou třídou zdroje a libovolnou cílovou doménovou třídou. Referenční relace se obvykle zobrazují v diagramu jako konektory, které jsou čáry mezi obrazci.

 Například pokud jsou hudební alba a interprety zobrazovány jako obrazce v diagramu, můžete definovat relaci s názvem ArtistsAppearedOnAlbums, která propojuje interprety s alba, na kterých pracovali. Podívejte se na příklad na obrázku.

 ![Model instance generované DSL](../modeling/media/music_instance.png)

 Referenční relace mohou také propojovat prvky stejného typu. Například v DSL, který představuje rodinný strom, je vztah mezi rodiči a jejich podřízenými relace odkazem od osoby k osobě.

### <a name="define-a-reference-relationship"></a>Definování referenčního vztahu
 Klikněte na nástroj referenčního vztahu, potom klikněte na doménovou třídu zdroje relace a pak klikněte na cílovou doménovou třídu. Cílová třída může být stejná jako zdrojová třída.

 Každý vztah má dvě role reprezentované řádkem na každé straně pole relace. Můžete vybrat jednotlivé role a nastavit její vlastnosti v okno Vlastnosti.

 **Zvažte přejmenování rolí**. Například v relaci mezi osobou a osobou můžete chtít změnit výchozí názvy na rodiče a děti, vedoucí a podřízené, učitele a studenta atd.

 Pokud je to nutné, **upravte násobnost jednotlivých rolí**. Pokud chcete, aby každý uživatel měl maximálně jednoho správce, nastavte násobnost, která se zobrazí pod popiskem nadřízený v diagramu, na hodnotu 0.. 1.

 **Přidejte do relace vlastnosti domény.** Na obrázku má relace Artist-Album vlastnost role.

 **Nastavte vlastnost Povolit duplicitní hodnoty vztahu,** Pokud více než jedno propojení stejné třídy může existovat mezi stejnou dvojicí prvků modelu. Můžete například dovolit, aby učitel mohl naučit více než jeden předmět stejnému studentovi.

 ![Mapy obrazců pro konektory](../modeling/media/music_connector.png)

 Další informace najdete v tématu [vlastnosti](../modeling/properties-of-domain-relationships.md) doménových vztahů a [vlastností doménových rolí](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definovat spojnici pro zobrazení vztahu
 Spojnice zobrazuje spojnici mezi dvěma tvary v diagramu modelu.

 Přetáhněte nástroj **spojnice** do diagramu definice DSL.

 Pokud chcete zobrazit popisky na konektoru, přidejte text dekoratéry. Nastavte své pozice. Aby uživatel mohl přesunout dekoratér textu, nastavte jeho vlastnost **je** navýšení.

 Použijte nástroj **Mapa elementu diagramu** k propojení spojnice s referenčním vztahem.

 Když je vybraná mapa elementu diagramu, otevřete okno **Podrobnosti DSL** a otevřete kartu **mapy dekoratér** .

 Vyberte všechny **dekoratér** a nastavte **vlastnost zobrazení** na správnou doménovou vlastnost.

 Ujistěte se, že se vedle každé položky v seznamu **dekoratéry** zobrazí zaškrtnutí.

### <a name="define-a-connection-builder-tool"></a>Definice nástroje Tvůrce připojení
 V okně **Průzkumník DSL** rozbalte uzel **Editor** a všechny jeho poduzly.

 Pravým tlačítkem myši klikněte na uzel, který má stejný název jako vaše DSL, a pak klikněte na **Přidat nový nástroj připojení**.

 Když je vybraný nový nástroj, v okno Vlastnosti:

- Nastavte **Titulek** a **Popis**.

- Klikněte na **Tvůrce připojení** a vyberte příslušného tvůrce pro novou relaci.

- Nastavte **ikonu panelu nástrojů** na ikonu, kterou chcete zobrazit v sadě nástrojů. Můžete ji nastavit na novou ikonu nebo ikonu již použitou pro jiný nástroj.

     Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumník řešení**. Zkopírujte a vložte jeden z existujících souborů BMP nástrojů elementu. Přejmenujte vloženou kopii a pak ji dvakrát klikněte pro úpravu.

     Vraťte se do diagramu definice DSL, vyberte nástroj a na okno Vlastnosti klikněte na **[...]** v **panelu nástrojů ikona**. V dialogovém okně **Vybrat rastrový obrázek** vyberte v rozevírací nabídce soubor .BMP.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Testování vztahu odkazu a konektoru

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

2. **Sestavte a spusťte DSL.** Stisknutím kláves F5 nebo CTRL+F5 spusťte novou instanci Visual Studio v experimentálním režimu. V experimentální instanci Visual Studio otevřete nebo vytvořte soubor s příponou názvu vašeho DSL.

3. **Ověřte, že se na panelu nástrojů zobrazuje nástroj pro připojení.**

4. **Vytvářejte** obrazce přetažením z nástroje do diagramu modelu.

5. **Vytvořte propojení** mezi tvary. Klikněte na nástroj konektoru, klikněte na obrazec a pak klikněte na jiný obrazec.

6. **Ověřte, že nemůžete vytvářet připojení mezi nevhodnými třídami.** Pokud například máte vztah mezi Ádou a Artistsem, ověřte, že nemůžete propojit Artists s Artists.

7. **Ověřte správnost násobení. Ověřte například, že nemůžete připojit osobu k více než jednomu manažerovi.**

8. **Ověřte, že se zobrazuje každý dekorátor textu** a že:

   1. Můžete ho upravit, pokud jste  pro vlastnost domény nenastavíte příznak Je uživatelské rozhraní jen pro čtení.

   2. Když upravíte vlastnost buď v objektu okno Vlastnosti, nebo v dekorátoru, druhé zobrazení se aktualizuje.

   Po prvním otestování konektoru můžete chtít upravit některé jeho vlastnosti a přidat některé pokročilejší funkce. Další informace naleznete v části [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Definování tvarů, které obsahují seznamy: Tvary oddílů
 Tvar přihrádky obsahuje jeden nebo více seznamů položek. Například v dslu knihovny Music Library můžete použít tvary oddílů k reprezentaci hudby Naríd. V každém z nich je seznam songsů.

 ![Tvar přihrádky](../modeling/media/compartmentshape.png)

 V nejjednodušší metodě dosažení tohoto efektu v definici DSL definujete jednu třídu domény pro kontejner a jednu třídu domény pro každý seznam. Třída kontejneru je mapována na tvar přihrádky.

 ![Mapový tvar](../modeling/media/music_mapcomp.png)

 Další informace najdete v tématu [Vlastnosti obrazců oddílů.](../modeling/properties-of-compartment-shapes.md)

#### <a name="to-define-a-compartment-shape"></a>Definování obrazce přihrádky

1. **Vytvořte třídu domény kontejneru**. Klikněte na **nástroj Vztahu vkládání,** klikněte na kořenovou třídu modelu a potom klikněte na prázdnou část diagramu definice DSL. Tím se na obrázku příkladu vytvoří doménová třída s názvem Možné.

     Alternativně místo vkládání do kořenové třídy můžete vložit kontejner do třídy domény, která je namapovaná na drah.

     Do třídy přidejte vlastnost domény, například Name, a nastavte její příznak **Is Element Name** v okno Vlastnosti.

2. **Vytvořte doménu třídy položky seznamu**. Click the **Embedding Relationship** tool, click the container class (Album) and then click a blank part of the diagram. Tím se na příkladu vytvoří třída domény s názvem Song.

     Do třídy přidejte vlastnost domény, například Title, a nastavte její **příznak Is Element Name.**

     Přidejte další vlastnosti domény.

     Pro každý seznam, který chcete zobrazit, přidejte další třídu domény položky seznamu.

3. **Pokud chcete kombinovat několik typů položek v seznamu**, vytvořte třídy, které dědí ze třídy seznamu. Nastavte třídu seznamu jako abstraktní nastavením **modifikátoru dědičnosti**.

     Pokud například chcete, aby klasická hudba byla seřazena podle autora místo autora, můžete vytvořit dvě podtřídy Song, ClassicalSong a NonClassicalSong.

4. **Vytvořte tvar přihrádky**. Přetáhněte z **nástroje Tvar přihrádky** do diagramu definice DSL.

     Přidejte dekorátor textu a nastavte jeho název.

     Přidejte přihrádku a nastavte její název.

5. Pokud chcete uživateli nechat oddíly seznamu skrýt, klikněte pravým tlačítkem na třídu tvaru přihrádky, přejděte na Přidat a potom klikněte na **Rozbalit/sbalit dekorátor**. V okno Vlastnosti nastavte pozici dekorátoru.

6. Klikněte na **nástroj Diagram Element Map,** klikněte na třídu domény kontejneru a pak klikněte na obrazec přihrádky.

7. Vyberte propojení mapy elementů diagramu mezi doménovou třídou a obrazcem. V okně **Podrobnosti DSL:**

    1. Klikněte na **kartu Dekorátory.** Klikněte na název dekorátoru a pak v části Zobrazit vlastnost vyberte **příslušnou položku.** Ujistěte se, že se vedle názvu dekorátoru zobrazuje značka zaškrtnutí.

    2. Klikněte na **kartu Mapy oddílů.**

         Klikněte na název přihrádky.

         V **části Displayed elements collection path (Zobrazená cesta** kolekce elementů) přejděte do třídy elementu list (Song). Kliknutím na šipku rozevíracího seznamu použijte nástroj navigátor.

         V **části Zobrazit** vlastnost vyberte vlastnost, která se má zobrazit v seznamu. V tomto příkladu je to Název.

> [!NOTE]
> Pomocí polí Cesta v polích mapy dekorátoru a mapy přihrádky můžete vytvořit složitější relace mezi třídami domény a tvarem přihrádky.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Definování nástroje pro vytvoření obrazce

1. **Vytvořte položku sady nástrojů pro vytváření prvků třídy domény.**

2. V **Průzkumníku DSL** **rozbalte uzel Editor** a všechny jeho dílčí uzly.

3. Klikněte pravým tlačítkem na uzel v **části Karty** panelu nástrojů se stejným názvem jako váš DSL, například MusicLibrary. Klikněte **na Přidat nástroj elementu**.

    > [!NOTE]
    > Pokud kliknete pravým tlačítkem **na uzel Nástroje,** nástroj **Přidat element neuvidíte.** Místo toho klikněte na uzel nad ní.

4. V okno Vlastnosti s vybraným novým nástrojem elementu nastavte **Třída** na třídu domény, kterou jste nedávno přidali.

5. Nastavte **Caption (Popis)** **a Tooltip (Popis).**

6. Nastavte **ikonu** panelu nástrojů na ikonu, která se zobrazí na panelu nástrojů. Můžete ho nastavit na novou ikonu nebo ikonu, která se už používá pro jiný nástroj.

     Pokud chcete vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumník řešení**. Zkopírujte a vložte jeden z existujících nástrojů elementů .BMP soubory. Přejmenujte v ní vkopírované kopie a dvojím kliknutím ji upravte.

     Vraťte se do diagramu definice DSL, vyberte nástroj a na panelu okno Vlastnosti **klikněte na tlačítko ™** v **ikonu panelu nástrojů**. V dialogovém **okně Vybrat** rastrový obrázek vyberte soubor BMP z rozevírací nabídky.

#### <a name="to-test-a-compartment-shape"></a>Testování tvaru přihrádky

1. **Kliknutím na Transformovat všechny** šablony na panelu nástrojů Průzkumník řešení a vygenerujte kód návrháře DSL.

2. **Sestavte a spusťte DSL.** Stisknutím kláves F5 nebo CTRL+F5 spusťte novou instanci Visual Studio v experimentálním režimu. V experimentální instanci Visual Studio otevřete nebo vytvořte soubor s příponou názvu vašeho DSL.

3. **Ověřte, že se nástroj zobrazí na panelu nástrojů.**

4. Přetáhněte nástroj do diagramu modelu. Vytvoří se tvar.

    Ověřte, že se zobrazí název elementu a je automaticky nastaven na výchozí hodnotu.

5. Klikněte pravým tlačítkem na záhlaví nového obrazce a pak klikněte na Přidat *položku seznamu.* V tomto příkladu je příkaz Add Song (Přidat skladbu).

    Ověřte, že se položka zobrazí v seznamu a že má nový název.

6. Klikněte na jednu z položek seznamu a prohlédněte si okno Vlastnosti. Měli byste vidět vlastnosti položek seznamu.

7. Otevřete Průzkumníka jazyků. Ověřte, že vidíte uzly kontejneru s uzly položek seznamu uvnitř.

   ![Vygenerovaný průzkumník DSL](../modeling/media/music_explorer.png)

   Po prvním otestování tvaru přihrádky můžete upravit některé jeho vlastnosti a přidat některé pokročilejší funkce. Další informace naleznete v části [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Zobrazení odkazu v přihrádkě
 Obvykle je prvek, který zobrazíte v oddílu, podřízeným prvkem prvku, který je reprezentován tvarem přihrádky. Někdy ale chcete zobrazit prvek, který je s ním propojený pomocí referenční relace.

 Mohli bychom například přidat druhou přihrádku do Sémshape, která zobrazí seznam Artists (Malířů), které jsou propojeny s Namem.

 V tomto případě by oddíl měl místo odkazovaného elementu zobrazit propojení. Je to proto, že když uživatel vybere položku v oddělení a stiskne klávesu DELETE, chcete odkaz odstranit, nikoli odkazovaný element.

 Název odkazovaného elementu ale můžete mít v přihrádkě.

 Následující postup předpokládá, že jste už vytvořili třídu domény, referenční relaci, tvar přihrádky a mapu elementů diagramu, jak je popsáno výše v této části.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Zobrazení odkazu v přihrádkě

1. **Přidejte přihrádku do tvaru přihrádky**. V diagramu definice DSL klikněte pravým tlačítkem na třídu tvaru přihrádky, přejděte na **Přidat** a pak klikněte na **Oddíl**.

2. Nastavte **možnost Zobrazená cesta** kolekce elementů tak, aby místo cílového elementu přešla na odkaz. Klikněte na rozevírací nabídku a pomocí stromového zobrazení vyberte místo cíle referenční relaci. V příkladu je relace **ArtistAppearedOnAlbums**.

3. Pokud **chcete přejít z** odkazu na cílový element, nastavte Možnost pro zobrazení vlastnosti. V tomto příkladu je to **Interpret**.

4. Vlastnost **Display nastavte** na příslušnou vlastnost cílového elementu, například **Name**.

5. **Transformovat všechny** šablony , sestavit a spustit DSL a otevřít testovací model.

6. V diagramu modelu vytvořte odpovídající třídy obrazce, nastavte jejich názvy a vytvořte mezi nimi propojení. Ve tvaru přihrádky by se měly zobrazit názvy propojených prvků.

7. Vyberte odkaz nebo položku ve tvaru přihrádky. Odkaz i položka by měly zmizet.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Definování portů na hranici jiného obrazce
 Port je tvar, který se nachází na hranici jiného tvaru.

 Porty lze také použít k poskytnutí pevného spojovacího bodu v jiném tvaru, do kterého může uživatel nakreslit konektory. V takovém případě můžete tvar portu nastavit jako transparentní.

 Pokud chcete zobrazit příklad, který používá porty, vyberte šablonu **Diagram komponent** při vytváření nového řešení DSL. Tento příklad ukazuje hlavní body, které můžete při definování portů vzít v úvahu:

- K dispozici je doménová třída, která představuje kontejner portů `Component` .

- K dispozici je třída domény, která představuje porty. V tomto příkladu je to `ComponentPort` .

- Existuje vztah vkládání z třídy domény kontejneru do třídy domény portu. Další informace najdete v tématu [Definování doménových tříd](#classes).

- Pokud chcete, aby se různé typy portů promíchaného ve stejném kontejneru, můžete vytvořit podtřídy třídy domény portu. V tomto příkladu a `InPort` `OutPort` dědí z `ComponentPort` .

- Třídu domény kontejneru je možné mapovat na jakýkoli druh tvaru. V tomto příkladu je to `ComponentShape` . Další informace najdete v tématu [Definování obrazců](#shapes).

- Třídy domény portů jsou mapovány na tvary portů. Odvozené třídy můžete buď mapovat na samostatné třídy tvaru portu, nebo namapovat základní třídu na jednu třídu tvaru portu.

  V jiných ohledech se tvary portů chovají tak, jak je popsáno v [tématu Definování tvarů](#shapes).

  Další informace najdete v tématu [Vlastnosti tvarů portů.](../modeling/properties-of-port-shapes.md)

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Definování DSL s drahami
 Dráhy jsou vodorovným nebo svislým oddílem diagramu. Každá dráha odpovídá prvku modelu. Definice DSL vyžaduje jednu třídu domény pro elementy plaveckých drah.

 Nejlepším způsobem, jak vytvořit DSL s drahami, je vytvořit nové řešení DSL a zvolit šablonu řešení Tok úloh. V definici DSL je třída Actor doménovou třídou mapovanou na dráhu. Přejmenujte tento a ostatní třídy tak, aby vyhovovaly vašemu projektu.

 Pokud chcete přidat třídu, která se zobrazí jako tvar uvnitř dráhy, vytvořte relaci vkládání mezi třídou drah a novou třídou. Uživatelé budou moct přetahovat prvky z jedné dráhy na jinou, ale každý prvek bude vždy uvnitř konkrétní dráhy. V šabloně řešení Tok úloh je FlowElement podřízeným objektem třídy plaveckých drah.

 Pokud chcete přidat třídu, která se zobrazí jako tvar nezávisle na drahách, vytvořte relaci vkládání mezi kořenovou třídou a novou třídou. Uživatelé budou moct umístit tyto tvary kdekoli v diagramu, včetně hranic drah a mimo dráhy. V šabloně řešení Tok úloh je komentář podřízeným elementem kořenové třídy.

 Další informace najdete v tématu [Vlastnosti drah](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Přidání typů vlastností

### <a name="domain-enumerations-and-literals"></a>Výčty a literály domény
 Výčet domény je typ s několika literálových hodnotami.

 Pokud chcete přidat výčet domény, klikněte pravým tlačítkem na kořen modelu v Průzkumníku **DSL** a potom klikněte na **Přidat nový výčet domény**. Element se zobrazí v **Průzkumníku DSL** pod **uzlem Typy** domén. Tento prvek se nezobrazuje v diagramu.

 Pokud chcete do výčtu domény přidat literály výčtu, klikněte v Průzkumníku **DSL** pravým tlačítkem na výčet domény a potom klikněte na Add New Enumeration Literal (Přidat **nový literál výčtu).**

 Ve výchozím nastavení lze vlastnost, která má typ výčtu, nastavit pouze na jednu hodnotu výčtu najednou. Pokud chcete, aby uživatelé a programátoři mohli nastavit libovolnou kombinaci hodnot – "bitové pole" – nastavte vlastnost **IsFlags** výčtu.

### <a name="external-types"></a>Externí typy
 Pokud nastavíte typ vlastnosti domény a v rozevíracím seznamu Typ  nenajdete typ, který chcete najít, můžete přidat externí typ. Do seznamu můžete například přidat typ **System.Drawing.Color.**

 Pokud chcete přidat typ, klikněte pravým tlačítkem na kořen modelu v Průzkumníku DSL a potom klikněte na **Přidat nový externí typ**. V okno Vlastnosti nastavte název na **Color** a obor názvů na **System.Drawing**. Tento typ se teď zobrazí v Průzkumníku DSL v **části Typy domén**. Můžete ji zvolit při každém nastavení typu vlastnosti domény.

## <a name="customizing-the-dsl"></a><a name="custom"></a> Přizpůsobení DSL
 Pomocí technik popsaných v tomto tématu můžete rychle vytvořit DSL s diagramovou notací, čitelným formulářem XML a základními nástroji potřebnými ke generování kódu a dalších artefaktů.

 Existují dvě metody rozšíření definice DSL:

1. Vylaďte DSL pomocí dalších funkcí definice DSL. Můžete například vytvořit jeden nástroj konektoru, který může vytvořit několik typů konektorů, a řídit pravidla, pomocí kterých odstraněním jednoho prvku odstraníte také související prvky. Těchto technik se většinou dosahuje nastavením hodnot v definici DSL a některé vyžadují několik řádků kódu programu.

     Další informace naleznete v části [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Rozšiřte své nástroje modelování pomocí programového kódu, abyste dosáhli pokročilejších efektů. Můžete například vytvořit příkazy nabídky, které mohou změnit model, a vytvořit nástroje, které integrují dva nebo více souborů DSL. VMSDK je navržený speciálně pro snadnou integraci rozšíření s kódem vygenerovaný z definice DSL.  Další informace najdete v tématu [Psaní kódu pro přizpůsobení Domain-Specific jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Změna definice DSL
 Při vytváření jakékoli položky v definici DSL se automaticky nastaví mnoho výchozích hodnot. Po nastavení je můžete změnit. To zjednodušuje vývoj DSL a zároveň umožňuje výkonná přizpůsobení.

 Když například mapujete tvar na prvek, cesta k nadřazenému elementu mapování se automaticky nastaví podle vztahu vkládání třídy domény. Pokud ale později změníte relaci vkládání, cesta k nadřazenému elementu se automaticky nezmění.

 Proto byste měli mít na paměti, že když změníte některé relace v definici DSL, není neobvyklé, že chyby budou hlášeny buď při uložení definice, nebo při transformaci všech šablon. Většinu těchto chyb lze snadno opravit. Poklikejte na sestavu chyb a zobrazte umístění chyby.

 Viz také [Postupy: Změna oboru názvů jazyka Domain-Specific .](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md)

## <a name="troubleshooting"></a><a name="trouble"></a> Řešení potíží
 Následující tabulka uvádí některé z nejběžnějších problémů, ke kterým dochází při návrhu DSL, spolu s návrhy na jejich řešení. Další rady najdete na fóru [Rozšiřitelnost vizualizačních nástrojů.](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx)

| Problém | Návrh |
|-|-|
| Změny provedené v definiční souboru DSL nemají žádný vliv. | Klikněte **na Transformovat všechny** šablony na panelu nástrojů Průzkumník řešení a pak znovu sestavte řešení. |
| Tvary zobrazují místo hodnoty vlastnosti název dekorátoru. | Nastavte mapování dekorátoru. V diagramu definice DSL klikněte na mapu elementů diagramu, což je šedá čára mezi doménovou třídou a třídou obrazce.<br /><br /> Otevřete okno **Podrobnosti DSL.** Pokud ho nevidíte, v nabídce Zobrazení přejděte na **Další okna** a potom klikněte na **Podrobnosti DSL.**<br /><br /> Klikněte na **kartu Mapy dekorátoru.** Vyberte název dekorátoru. Ujistěte se, že je zaškrtnuté políčko vedle něj. V **části Vlastnost** zobrazení vyberte název vlastnosti domény.<br /><br /> Další informace najdete v tématu [Tvary v diagramu.](#shapes) |
| V Průzkumníku DSL nejde přidat do kolekce. Například když kliknete pravým tlačítkem nástrojů, v nabídce není k dispozici příkaz Přidat nástroj.<br /><br /> V Průzkumníkovi pro moji DSL nemůžu přidat element do seznamu. | Klikněte pravým tlačítkem na položku nad uzlem, který zkoušíte. Pokud chcete přidat do seznamu, příkaz Přidat není v uzlu seznam, ale v jeho vlastníkovi. |
| Vytvořil (a) jsem doménovou třídu, ale v Průzkumníkovi jazyka nemůžu vytvořit instance. | Každá doménová třída s výjimkou kořene musí být cílem relace vložení. |
| V Průzkumníkovi pro moji DSL jsou elementy zobrazeny pouze s názvy jejich typů. | V definici DSL vyberte doménovou vlastnost třídy a ve okno Vlastnosti nastavte vlastnost **název elementu** na hodnotu true. |
| Moje DSL se vždy otevírá v editoru XML. | K tomu může dojít z důvodu chyby při čtení souboru. I když tuto chybu opravíte, musíte explicitně resetovat Editor tak, aby byl vaším návrhářem DSL.<br /><br /> Klikněte pravým tlačítkem myši na položku projektu, klikněte na možnost **otevřít v aplikaci** a vyberte možnost * YourLanguage ***Návrhář (výchozí)**. |
| Sada nástrojů moje DSL se po změně názvů sestavení nezobrazí. | Prohlédněte si a aktualizujte **DslPackage\GeneratedCode\Package.TT** , kde najdete další informace, viz [Postupy: změna oboru názvů Domain-Specificho jazyka](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| Sada nástrojů mého DSL se nezobrazí, ale nezměnili jste název sestavení.<br /><br /> Nebo se zobrazí okno se zprávou, která hlásí selhání načtení rozšíření. | Obnovte experimentální instanci a znovu sestavte řešení.<br /><br /> 1. v nabídce Start systému Windows v části **všechny programy** rozbalte [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] a pak **nástroje** a potom klikněte na **resetovat Microsoft Visual Studio experimentální instanci**.<br />2. v nabídce **sestavení** klikněte na **znovu sestavit řešení**. |

## <a name="see-also"></a>Viz také

- [Začínáme s jazyky specifickými pro doménu](../modeling/getting-started-with-domain-specific-languages.md)
- [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)
