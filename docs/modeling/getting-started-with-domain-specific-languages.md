---
title: Začínáme s jazyky specifickými pro doménu
description: Seznamte se se základními pojmy při definování a používání jazyka specifického pro doménu (DSL) vytvořeného pomocí sady Modeling SDK pro sadu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fe531b127d657228ed68fa79358ef5df69ff17c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941486"
---
# <a name="get-started-with-domain-specific-languages"></a>Začínáme s jazyky specifickými pro doménu

Toto téma vysvětluje základní pojmy při definování a používání jazyka DSL (Domain Specific Language) vytvořeného pomocí sady Modeling SDK pro Visual Studio.

> [!NOTE]
> Sada text Template Transform SDK a sada Visual Studio Modeling SDK jsou nainstalovány automaticky při instalaci specifických funkcí sady Visual Studio. Další podrobnosti najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Pokud s DSL začínáte, doporučujeme vám pracovat přes **testovací prostředí nástrojů DSL**, které najdete na tomto webu: [vizualizace a sada SDK pro modelování](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co se dá dělat s Domain-Specificm jazykem?

Jazyk specifický pro doménu je notaci, obvykle grafický, který je navržený tak, aby se použil pro konkrétní účel. Naopak jazyky, jako je například UML, jsou obecné účely. V DSL můžete definovat typy prvku modelu a jejich vztahy a jak jsou uvedeny na obrazovce.

Pokud jste navrhli DSL, můžete ji distribuovat jako součást balíčku rozšíření integrace sady Visual Studio (VSIX). Uživatelé pracují s DSL v aplikaci Visual Studio:

![Diagram stromu rodiny, panel nástrojů a Průzkumník](../modeling/media/familyt_instance.png)

Zápis je pouze součástí DSL. Spolu s zápisem obsahuje váš balíček VSIX nástroje, které mohou uživatelé použít, aby mohli upravovat a generovat materiál z jejich modelů.

Jednou z hlavních aplikací DSL je generování kódu programu, konfiguračních souborů a dalších artefaktů. Zejména ve velkých projektech a produktových řádcích, kde se vytvoří několik variant produktu, může generování mnoha aspektů proměnných z DSL zajistit velký nárůst spolehlivosti a velmi rychlou reakci na změny požadavků.

Zbytek tohoto přehledu je návod, který zavádí základní operace vytváření a používání jazyka specifického pro doménu v aplikaci Visual Studio.

## <a name="prerequisites"></a>Požadavky

K definování DSL musíte mít nainstalované následující součásti:

| Komponenta | Odkaz |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Sada Modeling SDK pro Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Vytvoření řešení DSL

Chcete-li vytvořit nový jazyk specifický pro doménu, vytvořte nové řešení sady Visual Studio pomocí šablony projektu Domain-Specific jazyka.

1. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

2. V části **typy projektů** rozbalte uzel **ostatní typy projektů** a klikněte na **rozšiřitelnost**.

3. Klikněte na **Návrhář jazyka specifického pro doménu**.

     ![Dialog vytvořit DSL](../modeling/media/create_dsldialog.png)

4. Do pole **název** zadejte **FamilyTree**. Klikněte na **OK**.

     Spustí se **Průvodce jazykem specifickým pro doménu** a zobrazí se seznam řešení DSL šablon.

     Kliknutím na každou šablonu zobrazíte její popis.

     Šablony jsou užitečné pro počáteční body. Každé z nich poskytuje kompletní pracovní DSL, který můžete upravit podle svých potřeb. Obvykle byste zvolili nejbližší šablonu, kterou chcete vytvořit.

5. Pro tento návod vyberte šablonu **minimálního jazyka** .

6. Na příslušné stránce průvodce zadejte příponu názvu souboru DSL. Toto je rozšíření, které budou používat soubory, které obsahují instance vaší DSL.

    - Vyberte rozšíření, které není přidruženo k žádné aplikaci ve vašem počítači, nebo na počítači, na který chcete nainstalovat DSL. Například soubory **DOCX** a **htm** by mohly být nepřijatelné přípony názvů souborů.

    - Průvodce vás upozorní, pokud rozšíření, které jste zadali, je používáno jako DSL. Zvažte použití jiné přípony názvu souboru. Můžete také resetovat experimentální instanci sady Visual Studio SDK a vymazat starší experimentální návrháře. Klikněte na tlačítko **Start**, klikněte na položku **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje** a poté **resetujte experimentální instanci Microsoft Visual Studio 2010**.

7. Zkontrolujte ostatní stránky a pak klikněte na **Dokončit**.

     Vygeneruje se řešení, které obsahuje dva projekty. Mají název DSL a DslPackage. Otevře se soubor diagramu s názvem DslDefinition. DSL.

    > [!NOTE]
    > Většina kódu, který vidíte ve složkách ve dvou projektech, je vygenerována z DslDefinition. DSL. Z tohoto důvodu se v tomto souboru provedou většina úprav DSL.

Uživatelské rozhraní teď vypadá podobně jako na následujícím obrázku.

![Návrhář DSL](../modeling/media/dsl_designer.png)

Toto řešení definuje jazyk specifický pro doménu. Další informace najdete v tématu [Přehled uživatelského rozhraní nástroje Domain-Specific Language Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Důležité části řešení DSL

Všimněte si následujících aspektů nového řešení:

- **Dsl\DslDefinition.DSL** Jedná se o soubor, který vidíte při vytváření řešení DSL. V tomto souboru je vygenerován téměř veškerý kód v řešení a většina změn, které jste provedli v definici DSL, jsou zde. Další informace najdete v tématu práce s [diagramem definice DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Projekt DSL** Tento projekt obsahuje kód, který definuje jazyk specifický pro doménu.

- **Projekt DslPackage** Tento projekt obsahuje kód, který umožňuje otevřít a upravit instance DSL v aplikaci Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Spuštění DSL

Řešení DSL můžete spustit hned po jeho vytvoření. Později můžete definici DSL upravit postupně a znovu spustit řešení po každé změně.

### <a name="to-experiment-with-the-dsl"></a>Experimentování s DSL

1. Na panelu nástrojů **Průzkumník řešení** klikněte na **transformovat všechny šablony** . Tím se znovu vygeneruje většina zdrojového kódu z DslDefinition. DSL.

    > [!NOTE]
    > Pokaždé, když změníte *DslDefinition. DSL*, musíte před opětovným sestavením řešení kliknout na **transformovat všechny šablony** . Tento krok můžete automatizovat. Další informace najdete v tématu [Jak automatizovat transformaci všech šablon](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Stiskněte klávesu **F5** nebo v nabídce **ladění** klikněte na **Spustit ladění**.

     DSL se vytvoří a nainstaluje v experimentální instanci sady Visual Studio.

     Spustí se experimentální instance sady Visual Studio. Experimentální instance přebírá své nastavení z samostatného podstromu registru, kde jsou rozšíření sady Visual Studio registrována pro účely ladění. Běžné instance sady Visual Studio nemají přístup k rozšířením, která jsou zaregistrovaná tady.

3. V experimentální instanci aplikace Visual Studio otevřete soubor modelu s názvem **test** z **Průzkumník řešení**.

     \- ani

     Klikněte pravým tlačítkem na projekt ladění, přejděte na **Přidat** a pak klikněte na **položka**. V dialogovém okně **Přidat položku** vyberte typ souboru vaší DSL.

     Soubor modelu se otevře jako prázdný diagram.

     Panel nástrojů se otevře a zobrazí nástroje vhodné pro typ diagramu.

4. Pomocí nástrojů můžete vytvářet obrazce a spojnice v diagramu.

    1. Chcete-li vytvořit obrazce, přetáhněte je z příkladu nástroj Obrazec do diagramu.

    2. Chcete-li propojit dva tvary, klikněte na nástroj vzorový konektor, klikněte na první tvar a potom klikněte na druhý tvar.

5. Klikněte na popisky tvarů a změňte je.

Experimentální Visual Studio bude vypadat jako v následujícím příkladu:

![Strom ukázkového jazyka specifického pro doménu v aplikaci Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Obsah modelu

Obsah souboru, který je instancí DSL, se nazývá *model*. Model obsahuje prvky *modelu* <em></em> a *propojení* mezi prvky. Definice DSL určuje, které typy prvků modelu a odkazy mohou existovat v modelu. Například v DSL vytvořené ze šablony minimálního jazyka je jeden typ elementu modelu a jeden typ odkazu.

Definice DSL může určovat způsob, jakým se model zobrazuje v diagramu. Můžete vybírat z nejrůznějších stylů obrazců a konektorů. Můžete určit, že se některé obrazce zobrazí uvnitř jiných tvarů.

Model můžete zobrazit jako strom v zobrazení **Průzkumníka** při úpravách modelu. Při přidávání tvarů do diagramu se prvky modelu zobrazí také v Průzkumníkovi. Průzkumník lze použít i v případě, že není k dispozici žádný diagram.

Pokud Průzkumník nevidíte v instanci ladění aplikace Visual Studio, v nabídce **zobrazení** přejděte na položku **ostatní okna** a klikněte na příkaz *\<Your Language>* **Průzkumník**.

### <a name="the-api-of-your-dsl"></a>Rozhraní API vaší DSL

Vaše DSL vygeneruje rozhraní API, které umožňuje čtení a aktualizaci modelů, které jsou instancemi DSL. Jednou z aplikací rozhraní API je generování textových souborů z modelu. Další informace najdete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

V řešení ladění otevřete soubory šablon s příponou ". tt". Tyto ukázky ukazují, jak můžete vygenerovat text z modelů a umožní vám otestovat rozhraní API vaší DSL. Jedna z ukázek je napsána v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , druhá v [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

V každém souboru šablony je soubor, který generuje. Rozbalte soubor šablony v Průzkumník řešení a otevřete vygenerovaný soubor.

Soubor šablony obsahuje krátký segment kódu, který obsahuje seznam všech prvků v modelu.

Vygenerovaný soubor obsahuje výsledek.

Při změně souboru modelu se zobrazí odpovídající změny v generovaných souborech po opětovném vygenerování souborů.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Chcete-li znovu vygenerovat textové soubory po změně souboru modelu

1. V experimentální instanci aplikace Visual Studio uložte soubor modelu.

2. Ujistěte se, že parametr názvu souboru v každém souboru. TT odkazuje na soubor modelu, který používáte pro experimenty. Uložte soubor. tt.

3. Klikněte na možnost **transformovat všechny šablony** na panelu nástrojů **Průzkumník řešení**.

     \- ani

     Klikněte pravým tlačítkem na šablony, které chcete znovu vygenerovat, a pak klikněte na **Spustit vlastní nástroj**.

Do projektu můžete přidat libovolný počet souborů textových šablon. Každá šablona generuje jeden soubor výsledků.

> [!NOTE]
> Když změníte definici DSL, kód ukázkového textu šablony nebude fungovat, pokud ho neaktualizujete.

Další informace naleznete v tématu [generování kódu z Domain-Specific jazyka](../modeling/generating-code-from-a-domain-specific-language.md) a [psaní kódu pro přizpůsobení Domain-Specificho jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Přizpůsobení DSL

Pokud chcete upravit definici DSL, zavřete experimentální instanci a aktualizujte definici v hlavní instanci sady Visual Studio.

> [!NOTE]
> Po úpravě definice DSL může dojít ke ztrátě informací v modelech testu, které jste vytvořili pomocí dřívějších verzí.  Například řešení ladění obsahuje soubor s názvem Sample, který obsahuje některé tvary a konektory. Po zahájení vývoje definice DSL se nebudou zobrazovat a při uložení souboru se ztratí.

Pro vaši DSL můžete využít širokou škálu rozšíření. Následující příklady vám poskytnou dojem o možnostech.

Po každé změně uložte definici DSL, klikněte na **transformovat všechny šablony** v **Průzkumník řešení** a potom stisknutím klávesy **F5** Experimentujte s měněnou DSL.

### <a name="rename-the-types-and-tools"></a>Přejmenování typů a nástrojů

Přejmenujte existující doménové třídy a vztahy. Například od definice DSL vytvořené ze šablony minimálního jazyka můžete provést následující operace přejmenování, aby DSL představovalo rodinné stromy.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Přejmenování doménových tříd, relací a nástrojů

1. V diagramu DslDefinition přejmenujte **ExampleModel** na **FamilyTreeModel**, **ExampleElement** na **Person**, **cílení** na **rodiče** a **zdroje** na **podřízené**. Pro změnu můžete kliknout na jednotlivé štítky.

     ![Diagram definice DSL &#45; model struktury řady](../modeling/media/familyt_person.png)

2. Přejmenujte prvky a nástroje spojnice.

    1. Kliknutím na kartu v části Průzkumník řešení otevřete okno Průzkumník DSL. Pokud ji nevidíte, přejděte v nabídce **zobrazení** do části **jiná okna** a pak klikněte na **Průzkumník DSL**. Průzkumník DSL je viditelný pouze v případě, že je diagram definice DSL aktivním oknem.

    2. Otevřete okno Vlastnosti a umístěte ho, aby se zobrazily současně Průzkumník DSL a vlastnosti.

    3. V Průzkumníku DSL rozbalte **Editor**, **karty nástrojů** *\<your DSL>* a **nástroje**.

    4. Klikněte na **ExampleElement**. Toto je položka sady nástrojů, která se používá k vytvoření prvků.

    5. V okno Vlastnosti změňte vlastnost **název** na hodnotu **Person**.

         Všimněte si, že se také změní vlastnost **Titulek** .

    6. Stejným způsobem změňte název nástroje **ExampleConnector** na **ParentLink**. Změňte vlastnost **Caption** tak, že se nejedná o kopii vlastnosti Name. Zadejte například **odkaz nadřízený**.

3. Znovu sestavte DSL.

    1. Uložte soubor definice DSL.

    2. Na panelu nástrojů Průzkumník řešení klikněte na **transformovat všechny šablony** .

    3. Stiskněte klávesu F5. Počkejte, dokud se nezobrazí experimentální instance aplikace Visual Studio.

4. V řešení ladění v experimentální instanci aplikace Visual Studio otevřete soubor testovacího modelu. Přetáhněte prvky na ni ze sady nástrojů. Všimněte si, že se změnily popisy tlačítek a názvy typů v Průzkumníkovi DSL.

5. Uložte soubor modelu.

6. Otevřete soubor. TT a nahraďte výskyty starého typu a názvů vlastností novými názvy.

7. Ujistěte se, že název souboru, který je zadaný v souboru. TT, určuje testovací model.

8. Uložte soubor. tt. Otevřete vygenerovaný soubor a podívejte se na výsledek spuštění kódu v souboru. tt. Ověřte, zda je správný.

### <a name="add-domain-properties-to-classes"></a>Přidání vlastností domény do tříd
 Přidejte vlastnosti do doménové třídy, například představující roky narození a úmrtí osoby.

 Chcete-li zpřístupnit nové vlastnosti v diagramu, je nutné přidat *dekoratéry* k obrazci, který zobrazuje prvek modelu. Vlastnosti je také nutné namapovat na dekoratéry.

##### <a name="to-add-properties-and-display-them"></a>Přidání vlastností a jejich zobrazení

1. Přidejte vlastnosti.

   1. V diagramu definice DSL klikněte pravým tlačítkem na třídu doména **osoby** , přejděte na **Přidat** a pak klikněte na **vlastnost domény**.

   2. Zadejte seznam nových názvů vlastností, jako je například **narození** a **úmrtí**. Po každém z nich stiskněte klávesu **ENTER** .

2. Přidejte dekoratéry, který zobrazí vlastnosti v obrazci.

   1. Sledujte šedý řádek, který se rozšíří od třídy doména osoby na druhou stranu diagramu. Toto je mapa prvku diagramu. Propojí doménovou třídu s třídou Shape.

   2. Klikněte pravým tlačítkem na tuto třídu tvarů, přejděte na **Přidat** a pak klikněte na **text dekoratér**.

   3. Přidejte dvě dekoratéry s názvy, jako je například **BirthDecorator** a **DeathDecorator**.

   4. Vyberte všechny nové dekoratér a v okno Vlastnosti nastavte pole **pozice** . Tím se určuje, kde se na obraze zobrazí hodnota vlastnosti doména. Nastavte například **InnerBottomLeft** a **InnerBottomRight**.

        ![Definice obrazce oddílu](../modeling/media/familyt_compartment.png)

3. Namapujte dekoratéry na vlastnosti.

   1. Otevřete okno Podrobnosti DSL. Obvykle je na kartě vedle okna výstup. Pokud ho nevidíte, přejděte v nabídce **zobrazení** na položku **ostatní okna** a klikněte na **Podrobnosti DSL**.

   2. V diagramu definice DSL klikněte na řádek, který spojuje třídu domény **osoby** s třídou Shape.

   3. V části **Podrobnosti DSL** na kartě **mapy dekoratér** zaškrtněte políčko u nemapovaných dekoratér. V části **Zobrazovaná vlastnost** vyberte vlastnost domény, ke které se má mapovat. Namapujte například **BirthDecorator** na **narozeniny**.

4. Uložte DSL, klikněte na transformovat všechny šablony a stiskněte F5.

5. V diagramu ukázkového modelu ověřte, že nyní můžete kliknout na vybrané pozice a zadat do nich hodnoty. Kromě toho, když vyberete tvar **osoby** , okno Vlastnosti zobrazí nové vlastnosti narození a smrt.

6. V souboru. tt můžete přidat kód, který získá vlastnosti každé osoby.

   ![Diagram stromu rodiny, panel nástrojů a Průzkumník](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definovat nové třídy
 Do modelu můžete přidat doménové třídy a vztahy. Můžete například vytvořit novou třídu reprezentující města a novou relaci, která bude představovat, že osoba žila ve městě.

 Chcete-li, aby byly různé typy jedinečné v diagramu modelu, můžete mapovat třídy domény na různé druhy tvarů nebo na tvary s jinou geometrií a barvami.

##### <a name="to-add-and-display-a-new-domain-class"></a>Přidání a zobrazení nové doménové třídy

1. Přidejte doménovou třídu a nastavte ji jako podřízenou položku modelu kořene.

    1. V diagramu definice DSL klikněte na nástroj pro **vložení vztahu** , klikněte na kořenovou třídu **FamilyTreeModel** a pak klikněte do prázdné části diagramu.

         Zobrazí se Nová doménová třída, která je připojena k FamilyTreeModel pomocí vztahu vložení.

         Nastavte jeho název, například **město**.

        > [!NOTE]
        > Každá doménová třída s výjimkou kořene modelu musí být cílem nejméně jedné relace vložení, nebo musí dědit ze třídy, která je cílem vložení. Z tohoto důvodu je často vhodné vytvořit doménovou třídu pomocí nástroje pro vkládání vztahů.

    2. Přidejte do nové třídy doménovou vlastnost, například **název**.

2. Přidejte vztah odkazu mezi osobu a město.

    1. Klikněte na nástroj **referenčního vztahu** , klikněte na osoba a pak klikněte na město.

         ![Fragment definice DSL: kořenový adresář stromu rodiny](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Referenční vztahy znázorňují křížové odkazy z jedné části stromu modelu do jiného.

3. Přidejte tvar, který bude představovat městy v diagramech modelů.

    1. Přetáhněte **tvar geometrie** ze sady nástrojů do diagramu a přejmenujte jej, například **TownShape**.

    2. V okno Vlastnosti nastavte pole vzhled nového tvaru, jako je například barva výplně a geometrie.

    3. Přidáním dekoratér zobrazíte název města a přejmenujete ho NameDecorator. Nastavte jeho vlastnost Position.

4. Namapujte třídu města domény na TownShape.

    1. Klikněte na nástroj **Mapa elementu diagramu** , potom klikněte na třídu města domény a potom na třídu TownShape Shape.

    2. Na kartě **mapy dekoratér** okna s **podrobnostmi DSL** s vybraným konektorem mapy ověřte NameDecorator a nastavte **vlastnost Display** na název.

5. Vytvořte konektor pro zobrazení vztahu mezi osobami a městy.

    1. Přetáhněte spojnici z panelu nástrojů do diagramu. Přejmenujte ho a nastavte jeho vlastnosti vzhledu.

    2. Použijte nástroj **Mapa elementu diagramu** k propojení nového konektoru s vztahem mezi osobou a městem.

         ![Definice stromu řady s přidanou mapou obrazce](../modeling/media/familyt_shapemap.png)

6. Vytvořte nástroj elementu pro vytvoření nového města.

    1. V **Průzkumníku DSL** rozbalte **Editor** a pak vyberte **karty nástrojů**.

    2. Klikněte pravým tlačítkem *\<your DSL>* a potom klikněte na tlačítko **Přidat nový prvek nástroje**.

    3. Nastavte vlastnost **název** nového nástroje a vlastnost **Class** nastavte na město.

    4. Nastavte vlastnost **Icon panelu nástrojů** . Klikněte na položku **[...]** a v poli **název souboru** vyberte soubor ikony.

7. Vytvořte nástroj konektoru pro vytvoření propojení mezi městy a lidmi.

    1. Klikněte pravým tlačítkem *\<your DSL>* a pak klikněte na **Přidat nový nástroj konektoru**.

    2. Nastavte vlastnost název nového nástroje.

    3. Ve vlastnosti **tvůrci propojení** vyberte Tvůrce, který obsahuje název vztahu Person-Town.

    4. Nastavte **ikonu panelu nástrojů**.

8. Uložte definici DSL, klikněte na **transformovat všechny šablony** a potom stiskněte klávesu **F5**.

9. V experimentální instanci aplikace Visual Studio otevřete soubor testovacího modelu. Pomocí nových nástrojů můžete vytvářet městy a propojení mezi městy a osobami. Všimněte si, že můžete vytvořit pouze propojení mezi správnými typy elementu.

10. Vytvořte kód, ve kterém se zobrazí město, ve kterém každý člověk bydlí. Textové šablony jsou jedno z míst, kde můžete spustit takový kód. Můžete například upravit existující soubor Sample.tt v řešení ladění tak, aby obsahoval následující kód:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     Když soubor *. TT uložíte, vytvoří se soubor dceřiné společnosti, který obsahuje seznam lidí a jejich pobytů. Další informace naleznete v tématu [generování kódu z Domain-Specificho jazyka](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Ověřování a příkazy
 Tuto DSL můžete vyvinout dále přidáním omezení ověřování. Tato omezení jsou metody, které lze definovat, aby se zajistilo, že model je ve správném stavu. Můžete například definovat omezení, abyste se ujistili, že datum narození dítěte je pozdější než jeho nadřazené položky. Funkce ověřování zobrazí upozornění, pokud se uživatel DSL pokusí uložit model, který zruší některá omezení. Další informace najdete v tématu [ověřování v Domain-Specificm jazyce](../modeling/validation-in-a-domain-specific-language.md).

 Můžete také definovat příkazy nabídky, které může uživatel vyvolat. Příkazy mohou model upravit. Mohou také komunikovat s jinými modely v aplikaci Visual Studio a s externími prostředky. Další informace naleznete v tématu [How to: Modify a Standard a Command nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Nasazení DSL
 Chcete-li ostatním uživatelům dovolit, aby používali jazyk specifický pro doménu, distribuujete soubor rozšíření aplikace Visual Studio (VSIX). Vytvoří se při vytváření řešení DSL.

 Vyhledejte soubor. vsix ve složce Bin vašeho řešení. Zkopírujte ho do počítače, na který ho chcete nainstalovat. V tomto počítači poklikejte na soubor VSIX. DSL lze použít ve všech instancích aplikace Visual Studio na daném počítači.

 Stejný postup můžete použít k instalaci DSL na vlastní počítač, abyste nemuseli používat experimentální instanci sady Visual Studio.

 Další informace najdete v tématu [nasazení Domain-Specific jazykových řešení](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Odebrání starých experimentálních DSL
 Pokud jste vytvořili experimentální DSL, které už nechcete, můžete je z počítače odebrat resetováním experimentální instance sady Visual Studio.

 Tím se z počítače odebere všechna experimentální DSL a další experimentální rozšíření sady Visual Studio. Jedná se o rozšíření, která byla spuštěna v režimu ladění.

 Tento postup neodebere DSL nebo jiná rozšíření sady Visual Studio, která byla plně nainstalována spuštěním souboru VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Resetování experimentální instance sady Visual Studio

1. Klikněte na tlačítko **Start**, klikněte na položku **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje** a poté **resetujte experimentální instanci Microsoft Visual Studio 2010**.

2. Znovu sestavte všechna experimentální DSL nebo jiná experimentální rozšíření sady Visual Studio, která chcete dál používat.

## <a name="see-also"></a>Viz také

- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
