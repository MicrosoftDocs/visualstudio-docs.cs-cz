---
title: Definování jazyka specifického pro doménu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4bcd1f1f023c9e439fb870c9e31f07aa5be215d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299559"
---
# <a name="how-to-define-a-domain-specific-language"></a>Jak se definuje jazyk specifický pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete definovat jazyk specifický pro doménu (DSL), vytvoříte řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ze šablony. Klíčovou součástí řešení je diagram definice DSL, který je uložený v DslDefinition. DSL. Definice DSL definuje třídy a tvary DSL. Po úpravě a přidání na tyto prvky můžete přidat programový kód pro přizpůsobení DSL.

 Pokud s DSL začínáte, doporučujeme vám pracovat přes **testovací prostředí nástrojů DSL**, které najdete na tomto webu: [VISUALIZATON and modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a>Výběr řešení šablony
 Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 Chcete-li vytvořit nový jazyk specifický pro doménu, vytvořte nové řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocí šablony projektu jazyka specifického pro doménu.

#### <a name="to-create-a-dsl-solution"></a>Vytvoření řešení DSL

1. Vytvořte řešení pomocí šablony **jazyka specifického pro doménu** , kterou lze nalézt v části **Další typy projektů a rozšiřitelnost** v dialogovém okně **Nový projekt** .

    ![Dialog vytvořit DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    Po kliknutí na tlačítko **OK**se otevře **Průvodce jazykem specifickým pro doménu** a zobrazí seznam řešení DSL šablon.

2. Kliknutím na každou šablonu zobrazíte její popis. Vyberte řešení, které nejlépe odpovídá těm, které chcete vytvořit.

    Každá šablona DSL definuje základní funkční DSL. Tuto DSL budete upravovat tak, aby vyhovovala vašim požadavkům.

    Další informace získáte po kliknutí na jednotlivé vzorky.

   - Vyberte **tok úlohy** a vytvořte DSL, který má plavecké dráhy. Plavecké dráhy jsou svislé nebo vodorovné oddíly diagramu.

   - Vyberte **modely komponent** pro vytvoření DSL s porty. Porty jsou malé tvary na hranici většího tvaru.

   - Vyberte **diagramy tříd** pro definování DSL, který má obrazce oddílu. Obrazce oddílů obsahují seznam položek.

   - V jiných případech vyberte **Minimální jazyk** , nebo pokud si nejste jistí.

       > [!NOTE]
       > Chcete-li vytvořit diagram tříd nebo diagram komponent, zvažte použití modelů UML. Nástroje pro modelování UML poskytují sadu diagramů integrovaných kolem jednoho modelu. Jsou rozšiřitelné a dají se integrovat s vaší DSL pomocí ModelBus. Další informace najdete v tématu [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

   - Pokud chcete vytvořit DSL, která se zobrazí na model Windows Forms nebo na povrchu WPF, vyberte **minimální Návrhář DataGridView** nebo **Návrhář WPF** . Budete muset napsat kód, který definuje Editor. Další informace naleznete v následujících tématech:

        [Vytvoření jazyka specifického pro doménu založeného na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Na příslušné stránce průvodce zadejte příponu názvu souboru DSL. Toto je rozšíření, které budou používat soubory, které obsahují instance vaší DSL.

   - Vyberte příponu názvu souboru, která není přidružená k žádné aplikaci ve vašem počítači, nebo na počítači, na který chcete nainstalovat DSL. Například soubory **DOCX** a **htm** by mohly být nepřijatelné přípony názvů souborů.

   - Průvodce vás upozorní, pokud rozšíření, které jste zadali, je používáno jako DSL. Zvažte použití jiné přípony názvu souboru. Můžete také resetovat experimentální instanci sady Visual Studio SDK a vymazat starší experimentální návrháře. Klikněte na tlačítko **Start**, klikněte na položku **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a poté **resetujte experimentální instanci Microsoft Visual Studio 2010**.

4. Můžete buď upravit nastavení na ostatních stránkách, nebo ponechat výchozí hodnoty.

5. Klikněte na tlačítko **Dokončit**.

    Průvodce vytvoří řešení, které obsahuje dva nebo tři projekty a generuje kód z definice DSL.

   Uživatelské rozhraní teď vypadá podobně jako na následujícím obrázku.

   ![Návrhář DSL](../modeling/media/dsl-designer.png "dsl_designer")

   Toto řešení definuje jazyk specifický pro doménu. Další informace najdete v tématu [Přehled uživatelského rozhraní nástroje DSL](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testování řešení
 Řešení šablon poskytuje pracovní DSL, který můžete upravit nebo použít.

 Chcete-li řešení otestovat, stiskněte klávesu F5 nebo CTRL + F5. V experimentálním režimu se otevře nová instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 V nové instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]v Průzkumník řešení otevřete vzorový soubor. Otevře se jako diagram se sadou nástrojů.

 Pokud spustíte řešení, které jste vytvořili ze šablony **minimálního jazyka** , bude experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vypadat jako v následujícím příkladu:

 ![](../modeling/media/dsl-min.png "DSL_min")

 Experimentujte s nástroji. Vytvořte prvky a připojte je.

 Ukončete experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

> [!NOTE]
> Po úpravě DSL již nebudete moci zobrazit obrazce v ukázkovém testovacím souboru. Budete však moci vytvořit nové prvky.

### <a name="modifying-the-template-dsl"></a>Úprava šablony DSL
 Přejmenujte a udržujte některé nebo všechny třídy domény a třídy tvarů v definici DSL šablony. Nové názvy tříd by měly být platnými názvy CLR bez mezer nebo interpunkčních znamének.

 Je zvláště užitečné pro uchování těchto tříd:

- Kořenová třída se zobrazí v levém horním rohu diagramu definice DSL v části **třídy a vztahy**. Přejmenujte ho na jiný název než DSL. Například DSL s názvem **MusicLibrary** může mít kořenovou třídu s názvem **Music**.

- Třída diagramu se zobrazí v pravém dolním rohu diagramu definice DSL ve sloupci **prvky diagramu** . Možná se budete muset posunout doprava, aby se zobrazila. Obvykle se nazývá _YourDsl_**diagram**.

- Pokud jste použili šablonu **toku úkolů** a chcete vytvořit diagramy s plavecké dráhy, ponechejte a přejmenujte třídu domény objektu actor a ActorSwimlane obrazec.

  Odstraňte nebo přejmenujte jiné třídy tak, aby vyhovovaly vašim požadavkům.

## <a name="patterns"></a>Vzory pro definování DSL
 Doporučujeme, abyste vyvinuli DSL přidáním nebo úpravou jedné nebo dvou funkcí najednou. Přidejte funkci, spusťte DSL a otestujte ji a pak přidejte jednu nebo dvě další funkce. Typickou funkcí DSL může být:

- Doménová třída, vztah vložení, který připojuje prvek k modelu, tvar potřebný k zobrazení prvků této třídy v diagramu a nástroje prvku, který umožňuje uživatelům vytvářet prvky.

- Vlastnosti domény doménové třídy a dekoratéry, které je zobrazují na obrazci.

- Vztah odkazu a konektor, který ho zobrazuje v diagramu a nástroji konektoru, který umožňuje uživatelům vytvářet odkazy.

- Vlastní nastavení, které vyžaduje programový kód, jako je například omezení ověřování nebo příkaz nabídky.

  Následující části popisují, jak vytvořit nejužitečnější druhy funkcí DSL. Existuje mnoho dalších vzorů, se kterými lze vytvořit DSL, ale jedná se o nejčastěji používané.

> [!NOTE]
> Po přidání funkce nezapomeňte kliknout na **transformovat všechny šablony** na panelu nástrojů Průzkumník řešení před sestavením a spuštěním vaší DSL.

 Následující obrázek ukazuje třídy a vztahy část DSL, která se používá jako příklad v tomto tématu.

 ![Vztahy vložení a odkazování](../modeling/media/music-classes.png "Music_Classes")

 Dalším obrázkem je vzorový model této DSL:

 ![Model instance generované DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> "Model" odkazuje na instanci vaší DSL, kterou uživatelé vytvářejí, a obvykle se zobrazuje jako diagram. Toto téma popisuje diagram definice DSL i diagramy modelů, které se zobrazí při použití DSL.

## <a name="classes"></a>Definování doménových tříd
 Třídy domény reprezentují koncepty vaší DSL. Instance jsou *prvky modelu*. Například v **MusicLibrary** DSL můžete mít třídy domény s názvem **album** a **skladba**.

 Chcete-li vytvořit doménovou třídu, můžete přetáhnout z **pojmenovaného nástroje doménové třídy** do diagramu a pak přejmenovat třídu.

 Další informace najdete v tématu [vlastnosti doménových tříd](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Vytvoření relace vložení pro každou doménovou třídu
 Každá doménová třída s výjimkou kořenové třídy musí být cílem nejméně jedné relace vložení nebo musí dědit ze třídy, která je cílem relace vložení.

 V modelu je každý prvek modelu uzlem v jedné stromové struktuře vztahů vložení. Zdroj a cíl relace vložení se často označují jako nadřazené a podřízené.

 Výběr nadřazeného objektu pro doménovou třídu závisí na tom, jak chcete, aby jeho prvky byly v závislosti na ostatních prvcích. Pokud je odstraněn uzel stromu, je obvykle také odstraněn jeho dílčí strom. Třídy elementu, které mají nezávislou existenci, jsou proto vloženy přímo pod kořenovou třídou.

 Obvykle Pokud zobrazíte prvek uvnitř jiného prvku, chcete označit vztah vlastníka. V takovém případě je nejvhodnější nadřazená třída třídou kontejneru. Výjimkou je, že položka, která se zobrazí uvnitř kontejneru, je vlastně pouze odkazem na nezávislý element. V takovém případě odstraněním kontejneru odstraní odkaz, ale ne jeho cíl.

 Ve vzorcích definice DSL popsaných v tomto tématu budeme předpokládat, že se při odstranění kontejneru odstraní prvky zobrazené uvnitř kontejneru. Je možné, že jsou k dispozici složitější schémata a je možné je dosáhnout definováním pravidel.

|Způsob zobrazení prvku|Parent (vkládání) třída|Příklad v šabloně řešení DSL|
|------------------------------|--------------------------------|--------------------------------------|
|Tvar v diagramu<br /><br /> Plavecké dráhy.|Kořenová třída DSL|Minimální jazyk<br /><br /> Tok úlohy: třída objektu actor.|
|Tvar v plaveckou dráze|Doménová třída prvků, která se zobrazuje jako plavecké dráhy|Tok úkolů: třída Task.|
|Položka v seznamu v prvku Shape, kde je položka odstraněna při odstranění kontejneru.<br /><br /> Port na okraji obrazce|Doménová třída, která je namapována na obrazec kontejneru.|Diagram tříd: třída atributů.<br /><br /> Diagram komponent: třída portu.|
|Položka v seznamu, neodstraněno, pokud je kontejner odstraněn.|Kořenová třída DSL<br /><br /> V seznamu se zobrazí referenční odkazy.||
|Nezobrazuje se přímo.|Třída, která tvoří součást.||

 V příkladu knihovny hudba se zobrazí alba jako obdélníky, ve kterých jsou uvedeny názvy písní. Proto je nadřazeným prvkem Alba Hudba kořenové třídy a Nadřazená položka song je album.

 Pokud chcete vytvořit doménovou třídu a její vložení ve stejnou dobu, klikněte na nástroj pro **vložení vztahu** , potom klikněte na nadřazenou třídu a potom klikněte na prázdnou část diagramu.

 Obvykle není nutné upravovat název vztahu vkládání a jeho rolí, protože budou automaticky sledovat názvy tříd.

 Další informace najdete v tématu [vlastnosti](../modeling/properties-of-domain-relationships.md) doménových vztahů a [vlastností doménových rolí](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Vložení není stejné jako dědičnost. Podřízené položky v relaci vložení nedědí funkce z jejich nadřazených vztahů.

### <a name="add-domain-properties-to-each-domain-class"></a>Přidání vlastností domény do každé doménové třídy
 Vlastnosti domény ukládají hodnoty. Příklady: název, název, datum publikování.

 Ve třídě klikněte na **vlastnosti domény** , stiskněte klávesu ENTER a potom zadejte název vlastnosti. Výchozím typem doménové vlastnosti je řetězec. Chcete-li změnit typ, vyberte vlastnost doména a nastavte **typ** v okně **vlastnosti** . Pokud požadovaný typ není v rozevíracím seznamu, přečtěte si téma [Přidání typů vlastností](#addTypes).

 **Nastavte vlastnost názvu elementu.** Vyberte doménovou vlastnost, která se dá použít k identifikaci prvků v Průzkumníku jazyků. Například ve třídě doménová skladba můžete vybrat vlastnost doména názvu. V okně **vlastnosti** je nastavena vlastnost **název prvku na hodnotu** `true`.

### <a name="create-derived-domain-classes"></a>Vytvořit odvozené doménové třídy
 Chcete-li, aby doménová třída měla varianty, které dědí její vlastnosti a vztahy, vytvořte třídy, které jsou z ní odvozeny. Například album může mít odvozené třídy WMA a MP3.

 Vytvořte odvozenou třídu pomocí nástroje **doménové třídy** .

 Klikněte na nástroj **Dědičnost** , klikněte na odvozenou třídu a potom klikněte na základní třídu.

 Zvažte nastavení **modifikátoru dědičnosti** základní třídy na **abstract**. Pokud si myslíte, že budete možná potřebovat instance základní třídy, zvažte místo toho vytvoření samostatné odvozené třídy.

 Odvozené třídy dědí vlastnosti a role jejich základních tříd.

### <a name="tidy-the-dsl-definition-diagram"></a>Uklizený diagramu definice DSL
 Když přidáte relace, některé z vašich tříd se zobrazí ve více než jednom místě. Chcete-li snížit počet vzhledů a rozšířit diagram na širší, klikněte pravým tlačítkem myši na cílovou třídu relace a potom klikněte na tlačítko **přenést strom**. Pro opakový efekt klikněte pravým tlačítkem myši na třídu cíle relace a klikněte na **rozdělit strom**. Pokud tyto příkazy nabídky nevidíte, ujistěte se, že je vybraná jenom doménová třída.

 Třídy domény a třídy tvarů můžete přesunout pomocí kombinace kláves CTRL + šipka nahoru a CTRL + šipka dolů.

### <a name="test-the-domain-classes"></a>Testování tříd domény

##### <a name="to-test-the-new-domain-classes"></a>Otestování nových tříd domény

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení. Tento krok můžete automatizovat. Další informace najdete v tématu [Jak automatizovat transformaci všech šablon](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 spusťte novou instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v experimentálním režimu. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte soubor, který má příponu názvu vaší DSL.

3. **Otevřete Průzkumníka.** Na straně diagramu je okno Průzkumník jazyka, které se obvykle nazývá *YourLanguage* Explorer. Pokud toto okno nevidíte, může být na kartě pod Průzkumník řešení. Pokud ji nemůžete najít, v nabídce **zobrazení** přejděte na položku **ostatní okna**a klikněte na příkaz**Průzkumník**YourLanguage.

     Průzkumník nabízí stromové zobrazení modelu.

4. **Vytvořte nové prvky.** Klikněte pravým tlačítkem na kořenový uzel v horní části a pak klikněte na **Přidat nový**_YourClass_.

     V Průzkumníku jazyka se zobrazí nová instance vaší třídy.

5. Ověřte, že každá instance má jiný název při vytváření nových instancí. K tomu dojde pouze v případě, že jste pro vlastnost domény nastavili příznak **název prvku** .

6. **Projděte si vlastnosti domény. V případě vybrané instance třídy** zkontrolujte okno Vlastnosti. Měl by se zobrazit vlastnosti domény, které jste definovali v této třídě domény.

7. **Uložte soubor, zavřete ho a znovu ho otevřete**. Po rozbalení uzlů by se měly zobrazit všechny instance, které jste vytvořili v Průzkumníkovi.

## <a name="shapes"></a>Definování tvarů v diagramu
 Můžete definovat třídy prvků, které se zobrazí v diagramu jako obdélníky, elipsy nebo ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Definování třídy prvků, které se zobrazí jako tvary v diagramu

1. **Definujte a otestujte doménovou třídu, jak je popsáno v**tématu[definování tříd domény](#classes) **.**

   - Nadřazená třída by měla být kořenová třída. To znamená, že by měl být vztah vložení mezi kořenovou třídou a novou doménovou třídou.

   - Pokud má váš diagram plavecké dráhy, může být nadřazeným doménovou třídou, která je namapována na plaveckou dráhu. Než budete pokračovat v tomto postupu, přečtěte si téma [definování DSL, který obsahuje plavecké dráhy](#swimlanes).

2. **Přidejte třídu Shape** , která bude reprezentovat prvky v diagramu modelu. Přetáhněte jeden z následujících nástrojů do diagramu definice DSL:

   - **Obrazec geometrie** poskytuje obdélník nebo elipsu.

   - **Obrazec obrázku** obsahuje obrázek, který zadáte.

   - **Obrazec oddílu** je obdélník, který obsahuje jeden nebo více seznamů položek.

     Přejmenujte třídu Shape, která se zobrazí na pravé straně diagramu definice DSL v části obrazce a konektory.

3. **Definujte obrázek, pokud jste vytvořili obrazec obrázku**.

   1. Vytvořte soubor obrázku libovolné velikosti. Podporují se formáty BMP, JPEG, GIF a EMF.

   2. V Průzkumník řešení přidejte soubor do řešení v části Dsl\Resources.

   3. Vraťte se do diagramu definice DSL a vyberte novou třídu obrazce obrázku.

   4. V okno Vlastnosti klikněte na vlastnost **Image** .

   5. V dialogovém okně **Vybrat obrázek** klikněte na rozevírací nabídku v části **název souboru**a vyberte bitovou kopii.

4. **Přidejte text dekoratéry k obrazci, aby se zobrazily vlastnosti domény.**

    Chcete-li zobrazit název nebo název prvku modelu, budete pravděpodobně potřebovat alespoň jeden textový dekoratér.

    Klikněte pravým tlačítkem myši na záhlaví třídy Shape, přejděte na **Přidat**a pak klikněte na **text dekoratér**. Nastavte název dekoratér a ve okno Vlastnosti nastavte jeho **pozici**.

5. **Připojte každý obrazec s mapou elementu diagramu k třídě domény, kterou by měl zobrazit**.

    Klikněte na nástroj **Mapa elementu diagramu** , potom klikněte na doménovou třídu a potom klikněte na třídu Shapes.

6. **Namapujte vlastnosti na text dekoratéry.**

   1. Vyberte šedý spojnici mezi doménovou třídou a třídou Shape, která představuje mapu prvku diagramu.

   2. V okně **Podrobnosti DSL** klikněte na kartu **mapy dekoratér** . Pokud nevidíte okno **Podrobnosti DSL** , přejděte v nabídce **zobrazení** na položku **ostatní okna** a klikněte na **Podrobnosti DSL**. Je často nutné vyvolávat horní část tohoto okna, aby se zobrazil veškerý jeho obsah.

   3. Vyberte název dekoratér. V části **vlastnost zobrazení**vyberte název vlastnosti doménové třídy. Tento postup opakujte pro každou dekoratér.

       Pokud chcete zobrazit vlastnost souvisejícího prvku, klikněte na rozevírací seznam stromové struktury v oblasti **cesta k zobrazení vlastnosti**.

   4. Ujistěte se, že se vedle každého názvu dekoratér zobrazí znak zaškrtnutí.

      ![Mapování obrazců a okno Podrobnosti DSL](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Vytvořte položku sady nástrojů pro vytváření elementů doménové třídy.**

   1. V **Průzkumníku DSL**rozbalte uzel **Editor** a všechny jeho podřízené uzly.

   2. Klikněte pravým tlačítkem myši na uzel v části **karty nástrojů** , která má stejný název jako vaše DSL, například MusicLibrary. Klikněte na tlačítko **Přidat nástroj prvku**.

       > [!NOTE]
       > Kliknete-li pravým tlačítkem myši na uzel **nástroje** , nebudete vidět **Nástroj pro přidání prvku**. Místo toho klikněte na uzel nad ním.

   3. V okno Vlastnosti s vybraným novým nástrojem elementu nastavte **třídu** na doménovou třídu, kterou jste nedávno přidali.

   4. Nastavení **nadpisu** a **popisu tlačítka**

   5. Nastavte **ikonu panelu nástrojů** na ikonu, která se zobrazí v sadě nástrojů. Můžete ji nastavit na novou ikonu nebo ikonu již použitou pro jiný nástroj.

        Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumník řešení**. Zkopírujte a vložte jeden z existujících souborů BMP nástrojů elementu. Přejmenujte vloženou kopii a pak ji dvakrát klikněte pro úpravu.

        Vraťte se do diagramu definice DSL, vyberte nástroj a na okno Vlastnosti klikněte na **[...]** v **panelu nástrojů ikona**. V dialogovém okně **Vybrat rastrový obrázek** vyberte. Soubor BMP z rozevírací nabídky.

   Další informace najdete v tématu [vlastnosti geometrických tvarů](../modeling/properties-of-geometry-shapes.md) a [vlastností](../modeling/properties-of-image-shapes.md)obrazových tvarů.

#### <a name="to-test-shapes"></a>Testování obrazců

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 spusťte novou instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v experimentálním režimu. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte soubor, který má příponu názvu vaší DSL.

3. **Ověřte, zda se nástroje prvku zobrazují v sadě nástrojů.**

4. **Vytváření tvarů** přetažením z nástroje do diagramu modelu.

5. **Ověřte, že se dekoratér všechny texty** a že:

   1. Můžete ho upravit, pokud jste u vlastnosti doména nenastavili příznak **je jen pro čtení uživatelského rozhraní** .

   2. Když upravíte vlastnost v okno Vlastnosti nebo v dekoratér, druhé zobrazení se aktualizuje.

   Po prvním otestování tvaru možná budete chtít upravit některé vlastnosti a přidat ještě pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a>Definování referenčních vztahů
 Můžete definovat referenční vztah mezi jakoukoli doménovou třídou zdroje a libovolnou cílovou doménovou třídou. Referenční relace se obvykle zobrazují v diagramu jako konektory, které jsou čáry mezi obrazci.

 Například pokud jsou hudební alba a interprety zobrazovány jako obrazce v diagramu, můžete definovat relaci s názvem ArtistsAppearedOnAlbums, která propojuje interprety s alba, na kterých pracovali. Podívejte se na příklad na obrázku.

 ![Model instance generované DSL](../modeling/media/music-instance.png "Music_Instance")

 Referenční relace mohou také propojovat prvky stejného typu. Například v DSL, který představuje rodinný strom, je vztah mezi rodiči a jejich podřízenými relace odkazem od osoby k osobě.

### <a name="define-a-reference-relationship"></a>Definování referenčního vztahu
 Klikněte na nástroj referenčního vztahu, potom klikněte na doménovou třídu zdroje relace a pak klikněte na cílovou doménovou třídu. Cílová třída může být stejná jako zdrojová třída.

 Každý vztah má dvě role reprezentované řádkem na každé straně pole relace. Můžete vybrat jednotlivé role a nastavit její vlastnosti v okno Vlastnosti.

 **Zvažte přejmenování rolí**. Například v relaci mezi osobou a osobou můžete chtít změnit výchozí názvy na rodiče a děti, vedoucí a podřízené, učitele a studenta atd.

 Pokud je to nutné, **upravte násobnost jednotlivých rolí**. Pokud chcete, aby každý uživatel měl maximálně jednoho správce, nastavte násobnost, která se zobrazí pod popiskem nadřízený v diagramu, na hodnotu 0.. 1.

 **Přidejte do relace vlastnosti domény.** Na obrázku má vztah umělec-album vlastnost role.

 **Nastavte vlastnost Povolit duplicitní hodnoty vztahu,** Pokud více než jedno propojení stejné třídy může existovat mezi stejnou dvojicí prvků modelu. Můžete například dovolit, aby učitel mohl naučit více než jeden předmět stejnému studentovi.

 ![Mapy obrazců pro konektory](../modeling/media/music-connector.png "Music_Connector")

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

     Vraťte se do diagramu definice DSL, vyberte nástroj a na okno Vlastnosti klikněte na **[...]** v **panelu nástrojů ikona**. V dialogovém okně **Vybrat rastrový obrázek** vyberte. Soubor BMP z rozevírací nabídky.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Testování vztahu odkazu a konektoru

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 spusťte novou instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v experimentálním režimu. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte soubor, který má příponu názvu vaší DSL.

3. **Ověřte, zda se v sadě nástrojů zobrazuje nástroj připojení.**

4. **Vytváření tvarů** přetažením z nástroje do diagramu modelu.

5. **Vytvořte připojení** mezi obrazci. Klikněte na nástroj konektor, klikněte na tvar a potom klikněte na jiný tvar.

6. **Ověřte, že nemůžete vytvářet připojení mezi nevhodnými třídami.** Například pokud je váš vztah mezi alba a interprety, ověřte, že nemůžete propojit interprety s interprety.

7. **Ověřte správnost násobností. Ověřte například, že nemůžete připojit osobu k více než jednomu správci.**

8. **Ověřte, že se dekoratér všechny texty** a že:

   1. Můžete ho upravit, pokud jste u vlastnosti doména nenastavili příznak **je jen pro čtení uživatelského rozhraní** .

   2. Když upravíte vlastnost v okno Vlastnosti nebo v dekoratér, druhé zobrazení se aktualizuje.

   Po prvním otestování konektoru budete možná chtít upravit některé vlastnosti a přidat ještě pokročilejší funkce. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a>Definování tvarů, které obsahují seznamy: obrazce oddílu
 Obrazec oddílu obsahuje jeden nebo více seznamů položek. Například v hudební knihovně DSL můžete k reprezentaci hudebních alb použít obrazce oddílů. V každém albu se nachází seznam písní.

 ![Obrazec oddílu](../modeling/media/compartmentshape.png "CompartmentShape")

 Nejjednodušším způsobem dosažení tohoto efektu v definici DSL definujete pro kontejner jednu doménovou třídu a jednu doménovou třídu pro každý seznam. Třída kontejneru je namapována na tvar oddílu.

 ![Mapa obrazce](../modeling/media/music-mapcomp.png "Music_MapComp")

 Další informace najdete v tématu [vlastnosti obrazců oddílů](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Definování obrazce oddílu

1. **Vytvořte třídu domény kontejneru**. Klikněte na nástroj pro **vložení vztahu** , klikněte na kořenovou třídu modelu a pak klikněte na prázdnou část diagramu definice DSL. Tím se vytvoří doménová třída s názvem album v příkladu obrázku.

     Nebo místo vložení do kořenové třídy můžete kontejner vložit do doménové třídy, která je namapována na plaveckou dráhu.

     Přidejte do třídy doménovou vlastnost, jako je název, a nastavte její příznak **název elementu** na okno Vlastnosti.

2. **Vytvořte třídu domény položky seznamu**. Klikněte na nástroj pro **vložení vztahu** , klikněte na třídu kontejneru (album) a pak klikněte na prázdnou část diagramu. Tím se vytvoří doménová třída s názvem song v příkladu obrázku.

     Přidejte do třídy doménovou vlastnost, jako je název, a nastavte její příznak **název elementu** .

     Přidejte další vlastnosti domény.

     Přidejte další doménovou třídu položky seznamu pro každý seznam, který chcete zobrazit.

3. **Chcete-li v seznamu kombinovat několik typů položek**, vytvořte třídy, které dědí z třídy list. Nastavením jeho **modifikátoru dědičnosti**nastavte abstraktní třídu seznamu.

     Například pokud chcete, aby klasická hudba byla seřazena podle skladatele namísto interpreta, mohli byste vytvořit dvě podtřídy song, ClassicalSong a NonClassicalSong.

4. **Vytvořte obrazec oddílu**. Přetáhněte z nástroje **tvar oddílu** do diagramu definice DSL.

     Přidejte text dekoratér a nastavte jeho název.

     Přidejte oddíl a nastavte jeho název.

5. Aby uživatel mohl skrýt oddíly seznamu, klikněte pravým tlačítkem myši na třídu Shape Shape, přejděte na **Přidat**a pak klikněte na **Rozbalit nebo sbalit dekoratér**. V okno Vlastnosti nastavte pozici dekoratér.

6. Klikněte na nástroj **Mapa prvku diagramu** , klikněte na třídu doména kontejneru a potom klikněte na tvar oddílu.

7. Vyberte odkaz Mapa elementu diagramu mezi doménovou třídou a obrazcem. V okně **Podrobnosti DSL** :

    1. Klikněte na kartu **dekoratéry** . klikněte na název dekoratér a pak vyberte příslušnou položku pod **vlastností zobrazení**. Ujistěte se, že se vedle názvu dekoratér zobrazuje znak zaškrtnutí.

    2. Klikněte na kartu **mapy oddílů** .

         Klikněte na název oddílu.

         V části **zobrazená cesta kolekce elementů**přejděte na třídu prvku seznamu (skladba). Klikněte na šipku rozevíracího seznamu a použijte nástroj navigátor.

         V části **vlastnost zobrazení**vyberte vlastnost, která se má zobrazit v seznamu. V tomto příkladu je to title.

> [!NOTE]
> Pomocí polí cesta v polích mapa dekoratér a rozvržení oddílu můžete vytvořit složitější vztahy mezi doménovými třídami a obrazcem oddílu.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Definování nástroje pro vytvoření obrazce

1. **Vytvořte položku sady nástrojů pro vytváření elementů doménové třídy.**

2. V **Průzkumníku DSL**rozbalte uzel **Editor** a všechny jeho podřízené uzly.

3. Klikněte pravým tlačítkem myši na uzel v části **karty nástrojů** , která má stejný název jako vaše DSL, například MusicLibrary. Klikněte na tlačítko **Přidat nástroj prvku**.

    > [!NOTE]
    > Kliknete-li pravým tlačítkem myši na uzel **nástroje** , nebudete vidět **Nástroj pro přidání prvku**. Místo toho klikněte na uzel nad ním.

4. V okno Vlastnosti s vybraným novým nástrojem elementu nastavte **třídu** na doménovou třídu, kterou jste nedávno přidali.

5. Nastavení **nadpisu** a **popisu tlačítka**

6. Nastavte **ikonu panelu nástrojů** na ikonu, která se zobrazí v sadě nástrojů. Můžete ji nastavit na novou ikonu nebo ikonu již použitou pro jiný nástroj.

     Chcete-li vytvořit novou ikonu, otevřete Dsl\Resources v **Průzkumník řešení**. Zkopírujte a vložte jeden z existujících nástrojů elementu. Soubory BMP. Přejmenujte vloženou kopii a pak ji dvakrát klikněte pro úpravu.

     Vraťte se do diagramu definice DSL, vyberte nástroj a na okno Vlastnosti klikněte na **[...]** v **panelu nástrojů ikona**. V dialogovém okně **Vybrat rastrový obrázek** vyberte v rozevírací nabídce soubor BMP.

#### <a name="to-test-a-compartment-shape"></a>Otestování obrazce oddílu

1. Chcete-li vygenerovat kód návrháře DSL, **klikněte na možnost transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

2. **Sestavte a spusťte DSL.** Stisknutím klávesy F5 nebo CTRL + F5 spusťte novou instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v experimentálním režimu. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte soubor, který má příponu názvu vaší DSL.

3. **Ověřte, zda se nástroj zobrazuje v sadě nástrojů.**

4. Přetáhněte nástroj do diagramu modelu. Vytvoří se obrazec.

    Ověřte, že se název prvku zobrazí a automaticky se nastaví na výchozí hodnotu.

5. Klikněte pravým tlačítkem na záhlaví nového obrazce a pak klikněte na Přidat *položku seznamu.* V tomto příkladu je příkaz Přidat skladbu.

    Ověřte, zda se položka zobrazuje v seznamu a zda má nový název.

6. Klikněte na jednu z položek seznamu a potom zkontrolujte okno Vlastnosti. Měly by se zobrazit vlastnosti položek seznamu.

7. Otevřete Průzkumníka jazyků. Ověřte, zda jsou uzly kontejneru zobrazeny v rámci uzlů položky seznamu.

   ![Vygenerovaný Průzkumník DSL](../modeling/media/music-explorer.png "Music_Explorer")

   Po prvním otestování obrazce oddílu můžete chtít upravit některé jeho vlastnosti a přidat několik pokročilejších funkcí. Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Zobrazení odkazu odkazu v oddílu
 Obvykle je prvek, který je zobrazen v oddílu, podřízený prvku, který je reprezentován obrazcem oddílu. Někdy byste ale chtěli zobrazit prvek, který je k němu propojený, s referenční relací.

 Například můžeme přidat druhý oddíl do AlbumShape, který zobrazí seznam interpretů, které jsou propojeny s daným alba.

 V tomto případě by měl oddíl zobrazit odkaz namísto odkazovaného prvku. Důvodem je, že když uživatel vybere položku v oddílu a stiskne DELETE, přejete si odstranit odkaz, nikoli odkazovaný element.

 Nicméně můžete mít název odkazovaného prvku zobrazený v oddílu.

 Následující postup předpokládá, že jste již vytvořili doménovou třídu, referenční vztah, obrazec oddílu a mapu elementu diagramu, jak je popsáno výše v této části.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Zobrazení odkazu odkazu v oddílu

1. **Přidejte oddíl do obrazce oddílu**. V diagramu definice DSL klikněte pravým tlačítkem myši na třídu Shape Shape, přejděte na **Přidat**a pak klikněte na **oddíl**.

2. Nastavte **cestu kolekce zobrazených elementů** pro přechod na odkaz namísto jeho cílového prvku. Klikněte na rozevírací nabídku a pomocí stromového zobrazení vyberte odkazový vztah namísto jeho cíle. V příkladu je relace **ArtistAppearedOnAlbums**.

3. Nastavte **vlastnost Cesta k zobrazení** na přejít z odkazu na cílový element. V tomto příkladu je to **Interpret**.

4. Nastavte **vlastnost zobrazení** na odpovídající vlastnost cílového prvku, například **název**.

5. **Transformujte všechny šablony**, sestavte a spusťte DSL a otevřete testovací model.

6. V diagramu modelu vytvořte příslušné třídy tvaru, nastavte jejich názvy a vytvořte propojení mezi nimi. V obrazci oddílu by se měly zobrazit názvy propojených elementů.

7. Vyberte buď odkaz, nebo položku v obrazovém oddílu. Odkaz i položka by měly zmizet.

## <a name="ports"></a>Definování portů na hranici jiného obrazce
 Port je tvar, který je umístěn na hranici jiného obrazce.

 Porty lze také použít k poskytnutí pevného spojovacího bodu na jiném obraze, na který může uživatel vykreslit konektory. V takovém případě můžete tvar portu označit jako průhledný.

 Pokud chcete zobrazit příklad, který používá porty, vyberte šablonu **diagramu komponent** při vytváření nového řešení DSL. Tento příklad ukazuje hlavní body, které lze vzít v úvahu při definování portů:

- Existuje doménová třída, která představuje kontejner portů, `Component`.

- Existuje doménová třída, která představuje porty. V tomto příkladu je to `ComponentPort`.

- Existuje vztah vložení z třídy doména kontejneru do třídy domény portů. Další informace najdete v tématu [definování tříd domény](#classes).

- Pokud chcete, aby byly různé typy portů smíchány na stejném kontejneru, můžete vytvořit podtřídy třídy doména portů. V příkladu `InPort` a `OutPort` dědí z `ComponentPort`.

- Třída domény kontejneru může být mapována na libovolný typ obrazce. V tomto příkladu je `ComponentShape`. Další informace najdete v tématu [definování tvarů](#shapes).

- Třídy domény portu jsou namapovány na obrazce portů. Můžete buď namapovat odvozené třídy na samostatné třídy obrazců portů, nebo namapovat základní třídu na jednu třídu tvarů portů.

  V jiných ohledech se obrazce portů chovají, jak je popsáno v tématu [definování tvarů](#shapes).

  Další informace najdete v tématu [vlastnosti obrazců portů](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a>Definice DSL, která má plavecké dráhy
 Plavecké dráhy jsou vodorovný nebo svislý oddíl diagramu. Každá plavecká dráha odpovídá prvku modelu. Definice DSL vyžaduje pro elementy plavecké dráhy jednu doménovou třídu.

 Nejlepším způsobem, jak vytvořit DSL pomocí plaveckých drah, je vytvořit nové řešení DSL a zvolit šablonu řešení flow (Task flow). V definici DSL je třída objektu actor doménová třída mapovaná na plaveckou dráhu. Přejmenujte tuto a další třídy tak, aby vyhovovaly vašemu projektu.

 Chcete-li přidat třídu, která bude zobrazena jako tvar v rámci plavecké dráhy, vytvořte vztah vložení mezi třídou plavecká dráha a novou třídou. Uživatelé budou moci přetahovat prvky z jedné plavecké dráhy na jinou, ale každý prvek bude vždy uvnitř konkrétní plavecké dráhy. V šabloně řešení flow je FlowElement podřízenou třídou plavecké dráhy.

 Chcete-li přidat třídu, která bude zobrazena jako obrazec nezávisle na plaveckých drahách, vytvořte relaci vložení mezi kořenovou třídou a novou třídou. Uživatelé budou moci umístit tyto obrazce kdekoli v diagramu, včetně hranic plaveckých drah a mimo ni. V šabloně řešení toku úloh je komentář podřízenou položkou kořenové třídy.

 Další informace najdete v tématu [vlastnosti plaveckých drah](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a>Přidávání typů vlastností

### <a name="domain-enumerations-and-literals"></a>Výčty a literály domény
 Výčet domény je typ s několika hodnotami literálů.

 Pokud chcete přidat výčet domény, klikněte pravým tlačítkem na kořen modelu v **Průzkumníku DSL** a pak klikněte na **Přidat nový výčet domén**. Element se zobrazí v **Průzkumníkovi DSL** pod uzlem **typy domén** . Tento prvek se nezobrazí v diagramu.

 Chcete-li přidat literály výčtu do výčtu domény, klikněte pravým tlačítkem na výčet domény v **Průzkumníkovi DSL** a pak klikněte na **Přidat nový literál výčtu**.

 Ve výchozím nastavení může být vlastnost, která má typ výčtu, nastavena pouze na jednu hodnotu výčtu v jednom okamžiku. Pokud chcete, aby uživatelé a programátoři mohli nastavit libovolnou kombinaci hodnot – "bitové pole" – nastavte vlastnost **příznak** výčtu.

### <a name="external-types"></a>Externí typy
 Pokud v rozevíracím seznamu **typ** nenajdete požadovaný typ, můžete přidat externí typ, pokud jste nastavili vlastnost domény. Do seznamu můžete například přidat typ **System. Drawing. Color** .

 Pokud chcete přidat typ, klikněte pravým tlačítkem na kořen modelu v Průzkumníku DSL a pak klikněte na **Přidat nový externí typ**. V okno Vlastnosti nastavte název na **Color** a obor názvů na **System. Drawing**. Tento typ se nyní zobrazuje v Průzkumníkovi DSL v části **typy domén**. Můžete ji vybrat vždy, když nastavíte typ doménové vlastnosti.

## <a name="custom"></a>Přizpůsobení DSL
 Pomocí technik popsaných v tomto tématu můžete rychle vytvořit DSL pomocí zápisu diagramatické, čitelného formuláře XML a základních nástrojů, které jsou nutné k vygenerování kódu a dalších artefaktů.

 Definice DSL se rozšiřuje na dvě metody:

1. Vyladění DSL pomocí dalších funkcí definice DSL Můžete například vytvořit jeden konektorový nástroj, který může vytvořit několik typů konektoru, a můžete řídit pravidla, pomocí kterých odstranění jednoho prvku odstraní také související prvky. Tyto techniky se většinou dosahují nastavením hodnot v definici DSL a některé vyžadují několik řádků programového kódu.

     Další informace najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Rozšíříte nástroje pro modelování pomocí kódu programu, čímž dosáhnete pokročilejších efektů. Můžete například vytvořit příkazy nabídky, které mohou změnit model a můžete vytvořit nástroje, které integrují dva nebo více DSL. VMSDK je navržený specificky pro usnadnění integrace vašich rozšíření s kódem, který je vygenerován z definice DSL.  Další informace najdete v tématu [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Změna definice DSL
 Při vytváření libovolné položky v definici DSL se automaticky nastaví řada výchozích hodnot. Po nastavení je můžete změnit. Tím se zjednodušuje vývoj DSL, ale pořád se umožňuje výkonné přizpůsobení.

 Například při mapování tvaru na prvek je cesta k nadřazenému elementu mapování automaticky nastavena podle vztahu vložení doménové třídy. Nicméně pokud později změníte vztah vložení, cesta k nadřazenému elementu se automaticky nemění.

 Proto byste si měli být vědomi, že když změníte některé relace v definici DSL, není neobvyklé, že při uložení definice uložíte definici nebo když transformují všechny šablony, nejedná se o chyby. Většinu těchto chyb lze snadno opravit. Dvojím kliknutím na zprávu o chybách zobrazíte umístění chyby.

 Viz také [Postupy: Změna oboru názvů jazyka specifického pro doménu](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a>Při
 V následující tabulce jsou uvedeny některé nejběžnější problémy, které se vyskytly při návrhu DSL, spolu s návrhy na jejich řešení. Další rady jsou k dispozici na [fóru Extensibililty nástrojů pro vizualizaci](https://go.microsoft.com/fwlink/?LinkId=186074).

|Problém|Doporučení|
|-------------|----------------|
|Změny provedené v souboru definice DSL nemají žádný vliv.|Na panelu nástrojů výše Průzkumník řešení klikněte na **transformovat všechny šablony** a znovu sestavte řešení.|
|Tvar zobrazuje název dekoratér místo hodnoty vlastnosti.|Nastavte mapování dekoratér. V diagramu definice DSL klikněte na mapu prvku diagramu, což je šedý spojnice mezi doménovou třídou a třídou Shape.<br /><br /> Otevřete okno **Podrobnosti DSL** . Pokud ho nevidíte, přejděte v nabídce zobrazení na položku **ostatní okna**a klikněte na **Podrobnosti DSL**.<br /><br /> Klikněte na kartu **mapy dekoratér** . Vyberte název dekoratér. Ujistěte se, že je zaškrtnuté políčko vedle něho. V části **vlastnost zobrazení**vyberte název doménové vlastnosti.<br /><br /> Další informace najdete v tématu [tvary v diagramu](#shapes).|
|V Průzkumníku DSL nejde přidat do kolekce. Například když kliknete pravým tlačítkem nástrojů, v nabídce není k dispozici příkaz Přidat nástroj.<br /><br /> V Průzkumníkovi pro moji DSL nemůžu přidat element do seznamu.|Klikněte pravým tlačítkem na položku nad uzlem, který zkoušíte. Pokud chcete přidat do seznamu, příkaz Přidat není v uzlu seznam, ale v jeho vlastníkovi.|
|Vytvořil (a) jsem doménovou třídu, ale v Průzkumníkovi jazyka nemůžu vytvořit instance.|Každá doménová třída s výjimkou kořene musí být cílem relace vložení.|
|V Průzkumníkovi pro moji DSL jsou elementy zobrazeny pouze s názvy jejich typů.|V definici DSL vyberte doménovou vlastnost třídy a ve okno Vlastnosti nastavte vlastnost **název elementu** na hodnotu true.|
|Moje DSL se vždy otevírá v editoru XML.|K tomu může dojít z důvodu chyby při čtení souboru. I když tuto chybu opravíte, musíte explicitně resetovat Editor tak, aby byl vaším návrhářem DSL.<br /><br /> Klikněte pravým tlačítkem na položku projektu, klikněte na tlačítko **otevřít v** a vyberte _YourLanguage_ **návrháře (výchozí)** .|
|Sada nástrojů moje DSL se po změně názvů sestavení nezobrazí.|Prohlédněte si a aktualizujte **DslPackage\GeneratedCode\Package.TT** , kde najdete další informace, viz [Postupy: Změna oboru názvů jazyka specifického pro doménu](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Sada nástrojů mého DSL se nezobrazí, ale nezměnili jste název sestavení.<br /><br /> Nebo se zobrazí okno se zprávou, která hlásí selhání načtení rozšíření.|Obnovte experimentální instanci a znovu sestavte řešení.<br /><br /> 1. v nabídce Start ve Windows klikněte na **všechny programy**, rozbalte [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], pak **nástroje**a potom klikněte na **resetovat Microsoft Visual Studio experimentální instanci**.<br />2. v nabídce **sestavení** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]klikněte na **znovu sestavit řešení**.|

## <a name="see-also"></a>Viz také
 [Začínáme s jazyky specifickými](../modeling/getting-started-with-domain-specific-languages.md) pro doménu [Vytvoření jazyka specifického pro doménu založeného na model Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [Vytvoření jazyka specifického pro doménu založeného na WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)
