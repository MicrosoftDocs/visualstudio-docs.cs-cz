---
title: Začínáme s jazyky specifickými pro doménu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 29699609ee095c7e95434492afc531869453da4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877763"
---
# <a name="getting-started-with-domain-specific-languages"></a>Začínáme s jazyky specifickými pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma vysvětluje základní koncepty při definování a používání jazyka specifického pro doménu (DSL) vytvořené pomocí sady SDK modelování pro sadu Visual Studio.  
  
 Pokud jste ještě DSL, doporučujeme pracovat prostřednictvím **testovacího prostředí nástroje DSL**, které můžete vyhledat v této lokalitě: [Visualizaton and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co můžete dělat s jazyka specifického pro doménu?  
 Jazyka specifického pro doménu je zápis, obvykle grafické, který se používá pro určitý účel. Naopak jazyků, jako je UML jsou pro obecné účely. V DSL můžete definovat typy prvku modelu a jejich vztahy a jak se zobrazí na obrazovce.  
  
 Když jste vytvořili DSL, můžete ji budete distribuovat jako součást balíčku rozšíření integrace Visual Studio (VSIX). Uživatelé pracovat s DSL v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![Řada stromového diagramu, nástrojů a Průzkumník](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 Zápis je jenom část DSL. Spolu s zápis balíčku VSIX obsahuje nástroje, které můžou uživatelé používat, aby to pomohl ostatním upravit a generovat materiál ze své modely.  
  
 Jednou z instančního objektu aplikace DSL je ke generování programového kódu, konfigurační soubory a další artefakty. Zejména velkých projektů a produktové řady, kde se vytvoří několik variant produktu, generování mnoho aspektů proměnné z DSL může poskytnout velký nárůst v spolehlivost a velmi rychle reagovat na změny požadavků.  
  
 Zbytek tohoto přehledu je návod, který představuje základní operace vytváření a používání jazyka specifického pro doménu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Sada Modeling SDK pro Visual Studio|[Stáhněte si MSDK](http://www.microsoft.com/download/details.aspx?id=40754)|  
  
## <a name="creating-a-dsl-solution"></a>Vytvoření řešení DSL  
 Chcete-li vytvořit nový jazyk specifický pro doménu, vytvořte nový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení pomocí šablony projektu jazyka specifického pro doménu.  
  
#### <a name="to-create-a-dsl-solution"></a>K vytvoření řešení DSL  
  
1. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2. V části **typy projektů**, rozbalte **ostatní typy projektů** uzel a klikněte na tlačítko **rozšiřitelnost**.  
  
3. Klikněte na tlačítko **návrháře jazyka specifického pro doménu**.  
  
    ![Vytvoření dialogového okna DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4. V **název** zadejte **FamilyTree**. Klikněte na tlačítko **OK**.  
  
    **Průvodce jazyka specifického pro doménu** se otevře a zobrazí seznam šablon řešení DSL.  
  
    Klikněte na každou šablonu zobrazíte popis,  
  
    Šablony jsou užitečné počáteční body. Každý z nich poskytuje kompletní funkční DSL, který můžete upravit tak, aby odpovídala vašim potřebám. Obvykle byste zvolili šablony nejbližší co byste chtěli vytvořit.  
  
5. V tomto návodu, zvolte **minimální jazykový** šablony.  
  
6. Zadejte příponu názvu souboru vašeho DSL v na odpovídající stránku průvodce. Toto je rozšíření, které budou používat soubory, které obsahují instance tohoto kódu DSL.  
  
   -   Vyberte rozšíření, která nejsou spojena s libovolnou aplikací v počítači nebo v libovolném počítači, ve kterém chcete nainstalovat DSL. Například **docx** a **htm** bude nepřijatelná souboru přípony názvu.  
  
   -   Průvodce zobrazí upozornění, pokud se používá rozšíření, které jste zadali jako DSL. Zvažte možnost použít jinou příponu. Můžou také resetovat Visual Studio SDK experimentální instanci vymazání starých experimentální návrháře. Klikněte na tlačítko **Start**, klikněte na tlačítko **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a potom **resetování Microsoftu Instance sady Visual Studio 2010 experimentální**.  
  
7. Kontrolovat další stránky a pak klikněte na tlačítko **Dokončit**.  
  
    Řešení se vygeneruje, který obsahuje dva projekty. Jsou pojmenovány Dsl a DslPackage. Otevře soubor diagramu, který je pojmenovaný DslDefinition.dsl.  
  
   > [!NOTE]
   >  Většinu kódu, který se zobrazí ve složkách v dva projekty se generuje z DslDefinition.dsl. Z tohoto důvodu se provádí většinu úpravy do vašeho DSL v tomto souboru.  
  
   Uživatelské rozhraní teď vypadá podobně jako na následujícím obrázku.  
  
   ![Návrhář DSL](../modeling/media/dsl-designer.png "dsl_designer")  
  
   Definuje toto řešení jazyka specifického pro doménu. Další informace najdete v tématu [přehled uživatelského rozhraní nástrojů jazyka specifického pro doménu](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Důležité části řešení DSL  
 Všimněte si, že následující aspekty nové řešení.  
  
-   **Dsl\DslDefinition.DSL** jedná se o soubor, jestli se při vytváření řešení DSL. Téměř všechny kódu v řešení se vygeneruje z tohoto souboru, a jsou jste tady udělali většinu změny provedené v definici DSL. Další informace najdete v tématu práci s [práce s diagramem definice DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **Projektu DSL** tento projekt obsahuje kód, který definuje jazyka specifického pro doménu.  
  
-   **Projekt DslPackage** tohoto projektu obsahuje kód, který umožňuje, aby instance DSL otevřít a upravit v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
##  <a name="Debugging"></a> Spuštění DSL  
 Řešení DSL můžete spustit ihned po jeho vytvoření. Později můžete upravit definice DSL postupně, spouštění řešení znovu po každé změně.  
  
#### <a name="to-experiment-with-the-dsl"></a>Můžete experimentovat s DSL  
  
1. Klikněte na tlačítko **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení. To obnoví většinu zdrojový kód z DslDefinition.dsl.  
  
   > [!NOTE]
   >  Pokaždé, když změníte DslDefinition.dsl, musíte kliknout na **Transformovat všechny šablony** předtím, než znovu sestavte řešení. Tento krok můžete automatizovat. Další informace najdete v tématu [jak automatizovat Transformovat všechny šablony](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2. Stiskněte klávesu F5 nebo na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
    DSL sestavení a je nainstalován v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    Experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí. Experimentální instanci trvá jeho nastavení z samostatné podstromu registru, ve kterém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření jsou registrované pro účely ladění. Normální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemají přístup k rozšíření zaregistrován.  
  
3. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete soubor modelu s názvem **testovací** z **Průzkumníka řešení**.  
  
    \- nebo –  
  
    Klikněte pravým tlačítkem na projekt ladění, přejděte na **přidat**a potom klikněte na tlačítko **položky**. V **přidat položku** dialogovém okně vyberte soubor, zadejte tohoto kódu DSL.  
  
    Otevře se soubor modelu jako prázdný diagram.  
  
    Panel nástrojů se otevře a zobrazí odpovídající typ diagramu nástroje.  
  
4. Pomocí nástrojů pro vytváření obrazců a konektorů v diagramu.  
  
   1.  K vytvoření tvarů, přetáhněte z nástroje příklad tvar do diagramu.  
  
   2.  Chcete-li připojit dva tvary, klikněte na nástroj konektor příklad, klepněte na první tvar a klikněte obrazec.  
  
5. Klikněte na popisky obrazce tím je Změníme.  
  
   Vaše experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bude vypadat podobně jako v následujícím příkladu:  
  
   ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Obsah modelu  
 Obsah souboru, který je instancí DSL je volána *modelu*. Model obsahuje *elementům modelu* a *odkazy* mezi prvky. Definice DSL Určuje, jaké typy prvků modelu a odkazy mohou existovat v modelu. Například v DSL vytvořené z šablony minimální jazykový, je jeden typ prvku modelu a jeden typ odkazu.  
  
 Definice DSL můžete určit, jak se model zobrazen v diagramu. Můžete vybrat z různých stylů obrazců a konektorů. Můžete určit, že nějaké obrazce uvnitř ostatním tvarům.  
  
 Můžete zobrazit modelu jako strom v **Explorer** zobrazení při úpravách modelu. Při přidávání obrazců do diagramu, se zobrazí také v Průzkumníku prvky modelu. V Průzkumníku lze i v případě, že neexistuje žádný diagram.  
  
 Pokud nevidíte v instanci ladění aplikace v Průzkumníku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]na **zobrazení** přejděte **ostatní Windows**a potom klikněte na tlačítko  *\<svůj jazyk >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>Rozhraní API tohoto kódu DSL  
 Vaše DSL generuje rozhraní API, které umožňuje číst a aktualizovat modely, které jsou instancemi DSL. Jednu aplikaci rozhraní API je generování textových souborů z modelu. Další informace najdete v tématu [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 V řešení ladění otevřete soubory šablon s příponou ".tt". Tyto ukázky ukazují, jak můžete generovat text z modelů a využijete k otestování rozhraní API vašeho DSL. Jednou z ukázek je napsána v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], ostatní v [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
 V každé šabloně soubor je soubor, který jej generuje. Rozbalte soubor šablony v Průzkumníku řešení a otevřete vygenerovaný soubor.  
  
 Soubor šablony, který obsahuje krátký segmentu kódu, který obsahuje všechny prvky v modelu.  
  
 Vygenerovaný soubor obsahuje výsledek.  
  
 Při změně souboru modelu, zobrazí se odpovídající změny v generované soubory po opětovném vygenerování soubory.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Znovu vygenerovat textové soubory po změně souboru modelu  
  
1. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], uložit soubor modelu.  
  
2. Ujistěte se, že parametr názvu souboru do každého souboru .tt odkazuje na soubor modelu, který používáte pro experimentů. Uložte soubor .tt.  
  
3. Klikněte na tlačítko **Transformovat všechny šablony** na panelu nástrojů **Průzkumníka řešení**.  
  
    \- nebo –  
  
    Klikněte pravým tlačítkem na šablony, které chcete obnovit a pak klikněte na tlačítko **spustit vlastní nástroj**.  
  
   Do projektu můžete přidat libovolný počet soubory textových šablon. Každá šablona generuje jeden soubor s výsledky.  
  
> [!NOTE]
>  Při změně definice DSL ukázkový kód šablony textu nebude fungovat, pokud ji aktualizovat.  
  
 Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md) a [psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Přizpůsobení DSL  
 Pokud chcete upravit definici DSL, ukončete experimentální instanci a aktualizovat definici v hlavním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instance.  
  
> [!NOTE]
>  Poté, co jste změnili definici DSL, může dojít ke ztrátě informací v modelech testu, které jste vytvořili pomocí starší verze.  Ladění řešení například obsahuje soubor s názvem vzorek, který obsahuje některé obrazců a konektorů. Po spuštění pro vývoj vaší definice DSL nebudou viditelné a budou ztraceny při uložení souboru.  
  
 Můžete provádět širokou škálu rozšíření vašeho DSL. Následující příklady vám poskytne dojem možností.  
  
 Po každé změně, Uložit definici DSL, klikněte na tlačítko **Transformovat všechny šablony** v **Průzkumníka řešení**a potom stiskněte klávesu **F5** můžete experimentovat s změněné DSL.  
  
### <a name="rename-the-types-and-tools"></a>Přejmenovat typy a nástroje  
 Přejmenujte existující doménovými třídami a vztahy. Například od definice Dsl z minimální jazykový šablony, můžete provést následující operace přejmenování, provést DSL představují stromů řady.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Chcete-li přejmenovat doménovými třídami, relace a nástroje  
  
1.  V diagramu DslDefinition přejmenovat **ExampleModel** k **FamilyTreeModel**, **ExampleElement** k **osoba**,  **Cíle** k **rodiče**, a **zdroje** k **podřízené**. Můžete kliknout na každý popisek jej můžete změnit.  
  
     ![Diagramem definice DSL &#45; řady stromu modelu](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2.  Přejmenujte element a konektor nástroje.  
  
    1.  Kliknutím na kartu v Průzkumníku řešení otevřete okno Průzkumník DSL. Pokud nevidíte, na **zobrazení** přejděte **ostatní Windows** a potom klikněte na tlačítko **Průzkumník DSL**. Průzkumník modelu DSL je viditelná pouze v případě diagramem definice DSL aktivní okno.  
  
    2.  Otevřete okno Vlastnosti a umístěte ho tak, aby se zobrazí Průzkumník DSL a vlastnosti ve stejnou dobu.  
  
    3.  V okně Průzkumník DSL, rozbalte **Editor**, **karty panelu nástrojů**,  *\<vašeho DSL >* a potom **nástroje**.  
  
    4.  Klikněte na tlačítko **ExampleElement**. Toto je položku sady nástrojů, který se používá k vytváření prvků.  
  
    5.  V okně Vlastnosti změňte **název** vlastnost **osoba**.  
  
         Všimněte si, že **titulek** vlastnost také změní.  
  
    6.  Stejným způsobem, změňte název **ExampleConnector** nástroje **ParentLink**. Příkaz ALTER **titulek** vlastnost tak, že není kopie vlastnost Name. Zadejte například **nadřazeného odkazu**.  
  
3.  Opětovné sestavení DSL.  
  
    1.  Uložte soubor definici DSL.  
  
    2.  Klikněte na tlačítko **Transformovat všechny šablony** na panelu nástrojů Průzkumník řešení  
  
    3.  Stiskněte klávesu F5. Počkejte, dokud experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se zobrazí.  
  
4.  V řešení ladění v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete soubor modelu testu. Prvky problém napravit přetáhnout z panelu nástrojů. Všimněte si, že došlo ke změně nástroj popisků a názvy typů v Průzkumník DSL.  
  
5.  Uložte soubor modelu.  
  
6.  Otevřete soubor .tt a nahradit výskyty prvku staré názvy typ a vlastnost nové názvy.  
  
7.  Ujistěte se, že název souboru, který je zadaný v souboru .tt určuje Testovat model.  
  
8.  Uložte soubor .tt. Otevřete vygenerovaný soubor zobrazit výsledek spuštění kódu v souboru .tt. Ověřte, zda je správný.  
  
### <a name="add-domain-properties-to-classes"></a>Přidání domény vlastností do třídy  
 Přidání vlastností do doménovou třídou, třeba k reprezentaci let narození a smrti osoby.  
  
 Chcete-li nové vlastnosti viditelné v diagramu, je nutné přidat *dekoratéry* na tvar, který se zobrazí na prvek modelu. Vlastnosti je třeba také namapovat na dekorátory.  
  
##### <a name="to-add-properties-and-display-them"></a>Přidání vlastností a jejich zobrazení  
  
1. Přidejte vlastnosti.  
  
   1.  V definici DSL diagramu, klikněte pravým tlačítkem na **osoba** doménové třídy, přejděte na příkaz **přidat**a potom klikněte na tlačítko **doménovou vlastnost**.  
  
   2.  Zadejte seznam nové názvy vlastností, jako například **narození** a **smrti**. Stisknutím klávesy **Enter** po každé z nich.  
  
2. Přidáte dekoratéry, které se zobrazí vlastnosti ve tvaru.  
  
   1.  Postupujte podle Šedá čára, která rozšiřuje z doménové třídy osoba na druhé straně diagramu. Toto je mapa elementu diagramu. Doménová třída odkazuje na třídu tvaru.  
  
   2.  Klikněte pravým tlačítkem na tuto třídu tvar, přejděte na **přidat**a potom klikněte na tlačítko **Text Dekoratér**.  
  
   3.  Přidejte dva dekoratéry s názvy, například **BirthDecorator** a **DeathDecorator**.  
  
   4.  Vyberte každý nový dekoratér a v okně Vlastnosti nastavte **pozice** pole. Určuje, kde se zobrazí hodnota vlastnosti domény na obrazec. Například nastavte **InnerBottomLeft** a **InnerBottomRight**.  
  
        ![Definici obrazce oddílu](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3. Mapovat dekoratéry vlastnosti.  
  
   1.  Otevřete okno Podrobnosti DSL. Obvykle je na kartě vedle v okně výstup. Pokud nevidíte, na **zobrazení** nabídky, přejděte k **ostatní Windows**a potom klikněte na tlačítko **podrobnosti DSL**.  
  
   2.  Na diagramem definice DSL, klikněte na řádek, který se připojí **osoba** doménovou třídu třídy obrazce.  
  
   3.  V **podrobnosti DSL**na **mapování Dekoratéru** kartu, klikněte na zaškrtávací políčko na nenamapované dekoratér. V **vlastnost Display, vlastnost**, vyberte doménová vlastnost, ke kterému chcete mapovat. Například namapovat **BirthDecorator** k **narození**.  
  
4. Uložit DSL, klikněte na možnost Transformovat všechny šablony a stiskněte klávesu F5.  
  
5. V diagramu modelu ukázka ověřte, že můžete nyní kliknout pozic, kterou jste zvolili a zadejte hodnoty do nich. Kromě toho, když vyberete **osoba** tvaru, v okně vlastností zobrazuje nové vlastnosti narození a smrti.  
  
6. V souboru .tt můžete přidat kód, který získá vlastnosti každé osoby.  
  
   ![Řada stromového diagramu, nástrojů a Průzkumník](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definovat nové třídy  
 Doménovými třídami a vztahy můžete přidat do modelu. Můžete například vytvořit novou třídu k vyjádření měst a nový vztah k reprezentaci, uživatel žít ve městě.  
  
 Aby se různé typy liší na diagramu modelu, můžete namapovat doménovými třídami různé druhy obrazec nebo obrazce s jinou geometrie a barvy.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Přidat a zobrazit novou třídu domény  
  
1.  Přidat doménovou třídu a udělat podřízeným kořen modelu.  
  
    1.  V definici DSL diagramu, klikněte na tlačítko **vztah obsažení** nástroj, klikněte na tlačítko kořenová třída **FamilyTreeModel**a potom klikněte na prázdnou část diagramu.  
  
         Novou třídu doménové se zobrazí, který je připojen k FamilyTreeModel s vztah obsažení.  
  
         Nastavte její název, například **městě**.  
  
        > [!NOTE]
        >  Každá třída domény s výjimkou kořen modelu musí být pro cílový alespoň jeden vztah obsažení, nebo musí dědit z třídy, která je cílem obsažení. Z tohoto důvodu je často vhodné vytvořit doménovou třídu s použitím nástroje vztah obsažení.  
  
    2.  Přidat doménová vlastnost, která na novou třídu, například **název**.  
  
2.  Přidáte vztah odkazu mezi osoby a města.  
  
    1.  Klikněte na tlačítko **referenční vztah** nástroj, klikněte na osobu a potom klikněte na města.  
  
         ![Fragment definice DSL: kořen stromu řady](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Referenční stavy představují křížové odkazy z jedné části stromu modelu do jiného.  
  
3.  Přidáte prvek k reprezentaci měst v diagramech modelů.  
  
    1.  Přetáhněte **obrazec geometrie** z panelu nástrojů do diagramu a přejmenujte jej, například **TownShape**.  
  
    2.  V okně Vlastnosti nastavte pole vzhled nové obrazce, jako je barva výplně a Geometry.  
  
    3.  Přidejte Dekoratér pro zobrazovaný název města a přejmenujte jej NameDecorator. Nastavte jeho vlastnost umístění.  
  
4.  Doménová třída městě namapujte TownShape.  
  
    1.  Klikněte na tlačítko **mapa elementu diagramu** nástroje a potom klikněte na městě doménové třídy a třídy TownShape obrazce.  
  
    2.  V **mapování Dekoratéru** karty **podrobnosti DSL** vybrané okno s konektorem mapy, zkontrolujte NameDecorator a nastavit **vlastnost Display, vlastnost** název.  
  
5.  Vytvořte konektor k zobrazení vztah mezi osoby a měst.  
  
    1.  Konektor z panelu nástrojů přetáhněte do diagramu. Přejmenujte ho a nastavte jeho vlastnosti vzhledu.  
  
    2.  Použití **mapa elementu diagramu** nástroj propojit nový konektor pro vztah mezi osoby a města.  
  
         ![Definice řady stromu pomocí přidání obrazce mapy](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6.  Vytvořte nástroj pro element umožňující města new.  
  
    1.  V **Průzkumník DSL**, rozbalte **Editor** pak **karty panelu nástrojů**.  
  
    2.  Klikněte pravým tlačítkem na  *\<vašeho DSL >* a potom klikněte na tlačítko **přidejte nový prvek nástroj**.  
  
    3.  Nastavte **název** vlastnosti nového nástroje a sady jeho **třídy** vlastnost město.  
  
    4.  Nastavte **panelu nástrojů ikonu** vlastnost. Klikněte na tlačítko **[...]**  a **název souboru** vyberte soubor ikony.  
  
7.  Vytvořte konektor nástroje pro vytvoření propojení mezi měst a osoby.  
  
    1.  Klikněte pravým tlačítkem na  *\<vašeho DSL >* a potom klikněte na tlačítko **přidat nový konektor nástroje**.  
  
    2.  Nastavte vlastnost Name atributu nový nástroj.  
  
    3.  V **Tvůrce propojení** vlastnosti, vyberte tvůrce, který obsahuje název města osoba vztah.  
  
    4.  Nastavte **panelu nástrojů ikonu**.  
  
8.  Uložte definici DSL, klikněte na **Transformovat všechny šablony**a potom stiskněte klávesu **F5**.  
  
9. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete soubor modelu testu. Použijte nové nástroje k vytvoření měst a propojení mezi měst a osoby. Všimněte si, že můžete vytvořit pouze odkazy mezi správné typy prvků.  
  
10. Vytvořte kód, který obsahuje města, ve kterém každý uživatel, který se nachází. Textové šablony se jeden z míst, kde můžete spouštět takového kódu. Například může upravit existující Sample.tt soubor řešení ladění tak, aby obsahoval následující kód:  
  
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
  
     Při ukládání souboru *.tt vytvoří pomocný soubor, který obsahuje seznam osoby a jejich objekty. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Ověření a příkazy  
 Dál tento DSL může vyvíjet přidáním omezení ověření. Tato omezení jsou metody, které můžete definovat, které Ujistěte se, že model je ve správném stavu. Například můžete definovat omezení a ujistěte se, která je novější než u jejích nadřazených tříd datum narození dítěte. Funkce ověření zobrazí upozornění, pokud uživatel DSL pokusí uložit model, který přeruší žádné omezení. Další informace najdete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).  
  
 Můžete také definujte příkazy nabídek, které může uživatel vyvolat. Příkazy můžete měnit model. Můžete také pracovat s jinými modely v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a s externím prostředkům. Další informace najdete v tématu [postupy: úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Nasazení DSL  
 Chcete-li umožnit dalším uživatelům používat jazyka specifického pro doménu, distribuovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soubor Extension (VSIX). To je vytvořen při sestavení řešení DSL.  
  
 Vyhledejte soubor VSIX do složky bin vašeho řešení. Zkopírujte ho do počítače, na kterém chcete nainstalovat. V tomto počítači dvakrát klikněte na soubor VSIX. DSL je možné ve všech instancích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tomto počítači.  
  
 Stejný postup slouží k instalaci DSL ve vašem počítači, takže není potřeba použít experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="Reset"></a> Odebrání starého experimentální DSL  
 Pokud jste vytvořili experimentální DSL, která už nechcete, můžete ho odebrat z počítače resetováním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentální instanci aplikace.  
  
 Tato akce odebere z počítače všechny experimentální DSL a další experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření. Toto jsou rozšíření, které byly provedeny v režimu ladění.  
  
 Tento postup neodebere DSL nebo jiné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, které byly plně nainstalovat spuštěním souboru VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Resetovat Visual Studio experimentální instance  
  
1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a potom **resetování Microsoftu Instance sady Visual Studio 2010 experimentální**.  
  
2.  Znovu sestavit všechny experimentální DSL nebo další experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, které chcete použít.  
  
## <a name="see-also"></a>Viz také  
 [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)   
 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)   
 [Visualizaton a modelování SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



