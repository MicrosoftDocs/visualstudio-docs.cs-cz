---
title: 'Diagramy případů použití UML: pokyny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74302831"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramy případů použití UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete nakreslit *Diagram případu použití* pro sumarizaci, kdo používá vaši aplikaci nebo systém a co s ním můžou dělat. Chcete-li vytvořit diagram případu použití UML, v nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**.

 Ukázku videa najdete v tématu [uspořádání funkcí do případů použití](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 S využitím diagramu případu použití můžete diskutovat a sdělit tyto informace:

- Scénáře, ve kterých váš systém nebo aplikace komunikuje s lidmi, organizacemi nebo externími systémy.

- Cíle, které tyto aktéry pomáhají dosáhnout.

- Rozsah vašeho systému.

  Diagram případu použití nezobrazuje podrobnosti o případech použití: shrnuje pouze některé relace mezi případy použití, aktéry a systémy. Konkrétně Diagram nezobrazuje pořadí, ve kterém se provádí kroky pro dosažení cílů každého případu použití. Tyto podrobnosti můžete popsat v dalších diagramech a dokumentech, které můžete propojit s každým případem použití. Další informace najdete v části [popisující případy použití podrobněji](#Details) v tomto tématu.

  Popisy, které zadáte pro případy použití, budou používat několik podmínek souvisejících s doménou, ve které systém pracuje, jako je například prodej, nabídka, zákazník atd. Je důležité definovat tyto výrazy a jejich vztahy jasně a můžete to provést pomocí diagramu tříd UML. Další informace najdete v tématu [diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).

  Případy použití se týkají pouze funkčních požadavků pro systém. Jiné požadavky, jako jsou obchodní pravidla, požadavky na služby a omezení implementace, musí být zastoupeny samostatně. Architektura a interní podrobnosti musí být také popsány samostatně. Další informace o tom, jak definovat požadavky uživatelů, najdete v tématu [model uživatelských požadavků](../modeling/model-user-requirements.md).

  Příklady používané v tomto tématu se týkají webu, na kterém můžou zákazníci objednat jídla z místního restaurací.

  ![Prvky v diagramu případu použití](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- *Objekt actor* (1) je třída osoby, organizace, zařízení nebo externí softwarové komponenty, která komunikuje s vaším systémem. Příklady Actors jsou **Customer**, **restaurace**, **snímač teploty**a oprávněný **autorizační karta.**

- *Případ použití* (2) představuje akce, které provádí jeden nebo více aktérů při dosahování určitého cíle. Příklady případů použití jsou **Order jídlo**, **nabídka aktualizace**, **platba procesu**.

   V diagramu případu použití jsou případy použití přidruženy (3) k objektům Actor, které je provádějí.

- Váš *systém (4)* je bez ohledu na to, co vyvíjíte. Může se jednat o malou součást softwaru, jejíž aktéry jsou pouze další softwarové komponenty; nebo to může být kompletní aplikace; nebo se může jednat o velkou distribuovanou sadu aplikací nasazených přes mnoho počítačů a zařízení. Příklady subsystémů jsou **weby objednávání dle moučky**, **firmy pro doručování moučky**, **Webová verze 2**.

   Diagram případu použití může zobrazit, které případy použití jsou podporovány vaším systémem nebo jeho subsystémy.

## <a name="basic-steps-for-drawing-use-case-diagrams"></a><a name="BasicSteps"></a> Základní kroky pro vykreslování diagramů případů použití

> [!NOTE]
> Podrobné pokyny pro vytvoření některého z diagramů modelování jsou popsány v tématu [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>Vytvoření nového diagramu případu použití

1. V nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**.

2. V části **šablony**klikněte na **Diagram případu UMLUse**.

3. Pojmenujte diagram.

4. V nabídce **Přidat k projektu modelování**vyberte existující projekt modelování v řešení nebo **vytvořte nový projekt modelování**a pak klikněte na tlačítko **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>Vykreslení diagramu případu použití

1. Přetáhněte hranice **podsystému** z panelu nástrojů do diagramu, aby představovaly celý systém nebo jeho hlavní součásti.

    - Diagram případu použití můžete vykreslit bez hranic systému, pokud nechcete popsat, které případy použití jsou podporovány vaším systémem nebo jeho komponentami.

    - Pokud je to nutné, přetáhněte roh systému na větší.

    - Přejmenujte ji odpovídajícím způsobem.

2. Přetáhněte **objekty actor** ze sady nástrojů do diagramu (jejich umístění mimo jakoukoli hranici systému).

    - Objekty actor reprezentují třídy uživatelů, organizací a externích systémů, které pracují s vaším systémem.

    - Přejmenujte je. Příklad: **Zákazník, restaurace, platební karta.**

3. Přetáhněte z panelu nástrojů **případy použití** na příslušné systémy.

    - Případy použití reprezentují aktivity, které aktéri vykonává, s tím, jak se systém nachází.

    - Přejmenujte je pomocí nadpisů, které by znali účastníci. Nepoužívejte názvy, které se vztahují k vašemu kódu. Například: **objednat jídlo, platíte za moučku, doručovat jídlo**.

    - Začněte s hlavními transakcemi, jako je například **objednávka**, a nechejte až později menší interakce, jako je například **položka nabídky výběru**.

    - Jednotlivé případy použití umístěte do systému nebo hlavního subsystému, který je podporuje (bez ohledu na fasádu nebo komponentu, která se účastní pouze připojení k uživateli).

    - Můžete nakreslit případ použití mimo hranici systému, abyste ukázali, že systém není podporovaný vaším systémem, třeba v konkrétní verzi nebo vydání.

4. Klikněte na tlačítko **přidružení** na panelu nástrojů, pak na případ použití a pak na objekt actor, který se účastní případu použití. Tímto způsobem propojte každý objekt actor s jeho případy použití.

5. Struktury případů použití se vztahy **zahrnutí**, **prodloužení** a **generalizace** . Chcete-li vytvořit každý z těchto odkazů, klikněte na nástroj, pak na zdrojový případ použití a pak na cíl. Viz následující část s názvem [strukturování případů použití](#Structuring).

6. Popište případy použití podrobněji. Podívejte se na následující část [s podrobnými informacemi o případech použití](#Details).

7. Nakreslete samostatné diagramy, abyste se mohli zaměřit na různé subsystémy nebo různé skupiny souvisejících případů použití. Všechny diagramy v jednom projektu modelování jsou zobrazení stejného modelu.

## <a name="drawing-actors-and-use-cases"></a><a name="Actors"></a> Kreslení objektů actor a případů použití
 Hlavním účelem diagramu případu použití je Ukázat, kdo komunikuje s vaším systémem, a hlavní cíle, které s ním dosáhnou.

- Vytvořte **objekty actor** , které reprezentují třídy lidí, organizací, dalších systémů, softwaru nebo zařízení, které pracují s vaším systémem nebo podsystémem.

  - Další informace o vykreslování objektů actor a dalších prvků najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

  - Pro každou jednotlivou sadu cílů Identifikujte aktéry podle jejich typu nebo role, i když fyzické osoby nebo subjekty se můžou shodovat. Například restaurace a zákazník jsou samostatné aktéry, i když zaměstnanec restaurace může být někdy zákazníkem.

- Vytvořte **případy použití** pro každý cíl, který každý objekt actor usiluje o dosažení systému.

  - Název a popište případy použití ve slovech, které by objekt actor rozuměl, místo prováděcích podmínek.

- Pomocí **přidružení** můžete propojit objekty actor s případy použití.

### <a name="inheritance-between-actors"></a>Dědičnost mezi aktéry
 ![Diagram případu použití znázorňující dědění](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Propojení **generalizace** mezi objekty actor lze nakreslit. Specializovaný objekt actor, například zákazník v příkladu, dědí případy použití obecného objektu actor, jako je například zákazník. Tato šipka by měla ukazovat na obecnější objekt actor, jako je třeba zákazník. Když vytvoříte odkaz, najeďte nejprve na specializovaného objektu actor.

 Specializovaný objekt actor může mít své vlastní další případy použití, které nejsou k dispozici ostatním objektům actor.

> [!CAUTION]
> Neměli byste vytvářet smyčky vztahů generalizace, které vedou k generalizaci objektu actor. Smyčky mohou generovat chyby.

### <a name="alternative-actor-icons"></a>Alternativní ikony objektu actor
 Vlastní ikony můžete použít k reprezentaci objektu actor namísto standardního prvku. Můžete ho například změnit tak, aby vypadal jako zařízení, restaurace, banka atd.

##### <a name="to-change-the-appearance-of-an-actor"></a>Změna vzhledu objektu actor

1. Klikněte pravým tlačítkem myši na objekt actor a potom klikněte na příkaz **vlastnosti**.

     Zobrazí se okno **vlastnosti** .

2. Nastavte vlastnost **cesta k obrázku** na umístění souboru obrázku.

    - Můžete použít libovolný z několika formátů obrázků, včetně formátu. gif,. jpg a. bmp.

    - Použijte soubor, který je součástí správy řešení nebo zdroje projektu tak, aby byl stále k dispozici, když je řešení přesunuto nebo zkopírováno.

3. Chcete-li tento vzhled replikovat v jiných diagramech případů použití, zkopírujte objekt actor a vložte jej do jiného diagramu.

    - Změna obrázku se vztahuje pouze na zobrazení v konkrétním diagramu. Nevztahuje se na základní prvek modelu. Pokud přetáhnete objekt actor z Průzkumníka modelů UML na jiný diagram, bude zobrazen jako standardní obrázek.

### <a name="multiplicities-between-actors-and-use-cases"></a>Násobnosti mezi objekty actor a případy použití
 Přidružení mezi objektem actor a případem použití může zobrazit *násobnost* na každém konci.

 ![Případ použití jednoho k jednomu objektu actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> Násobnosti přidružení v diagramu případu použití jsou skryté, pokud jsou obě **1**.

 Ve výchozím nastavení je každá násobnost **1**. V přísném výkladu modelu je násobnost 1 znamená, že je třeba pouze jeden zákazník, který je součástí řazení jednotlivých jídla a že každý zákazník má v jednom okamžiku pouze jednu moučku.

 Tyto násobnosti můžete změnit.

 Příklad:

 ![Případ použití znázorňující násobnost mnoha k mnoha](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Chcete-li určit, že několik objektů actor stejné třídy může být součástí jednoho výskytu případu použití, nastavte násobnost na konci přidružení na hodnotu **1.. \* **.

   Na ilustraci může být jedna nebo více restaurací součástí plnění stejné objednávky na jídlo.

- Chcete-li Ukázat, že se každý objekt actor může zúčastnit ve stejnou dobu v několika výskytech případu použití, nastavte násobnost na konci případu použití přidružení k **\*** .

   Na ilustraci může každá restaurace spolupracovat na plnění více objednávek najednou.

##### <a name="to-set-multiplicities-on-an-association"></a>Nastavení násobnosti u přidružení

1. Klikněte pravým tlačítkem na přidružení a pak klikněte na **vlastnosti**.

2. Rozbalte možnost **první role** nebo **druhá role**.

    *Role* znamená prvek na jednom konci přidružení.

3. Nastavte vlastnost násobnosti výběrem ze seznamu:

   - **1** pro stav, že se v každém odkazu účastní přesně jedna instance této role.

   - **1.. \* ** pro stav, že se v každém odkazu účastní jedna nebo víc instancí této role.

   - **0.. 1** pro stav, že účast je volitelná.

   - **\*** k tomu, aby se na odkaz účastnila nula nebo více instancí této role.

> [!NOTE]
> Mnoho týmů neobsahuje informace o násobnostech v diagramech případů použití, přičemž násobnost je nastavená na výchozí hodnotu 1. Místo toho poskytují informace v samostatných popisech případů použití. V tomto případě budou všechny násobnosti v diagramech případů použití skryté.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Použití objektu actor nebo případu použití ve více diagramech
 Můžete zobrazit stejné objekty actor a případy použití na několika diagramech. Příklad:

- V různých diagramech můžete popsány různé případy použití, ve kterých se účastní jeden objekt actor.

- Můžete použít jeden diagram k zobrazení objektů actor a subsystémů, ke kterým je přidružen případ použití, a použít jiný diagram k zobrazení způsobu, jakým je proces použití strukturován do zahrnutého a rozšířeného použití.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Zobrazení stejného objektu actor nebo případu použití v různých diagramech

1. Vytvořte objekt actor nebo případ použití na jednom diagramu.

2. Vytvořte jiný diagram případu použití.

3. Přetáhněte objekt actor nebo případ použití z **Průzkumníka modelů** do nového diagramu.

    > [!NOTE]
    > Pokud umístíte do nového diagramu objekt actor a případ použití, který už je přidružený, přidružení mezi nimi se automaticky zobrazí v novém diagramu.

## <a name="describing-use-cases-in-detail"></a><a name="Details"></a> Podrobně popisující případy použití
 Případ použití představuje:

- Cíl objektu actor v používání systému, například **koupit moučku**; ani

- Jeden nebo více *scénářů*, tj. posloupnosti kroků provedených v rámci cíle, například: {**Order moučk, Pay, Delivery**}. Kromě scénářů úspěšnosti může nastat několik scénářů výjimky nebo selhání, jako je například **odmítnutá platební karta**.

  Případ použití lze popsat v různých úrovních podrobností. V prvotní fázi návrhu stačí pouze název v diagramu případu použití.  Později můžete zapsat podrobnější popis scénářů.

  V Visual Studio Ultimate můžete popsat případ použití několika způsoby, které lze použít samostatně nebo společně:

- Propojení případu použití s jiným diagramem nebo diagramy v projektu.

  - Diagram činnosti vám pomůže vysvětlovat složitější procesy, kde jsou smyčky, větve a paralelní vlákna. Může také zobrazit tok dat mezi částmi procesu. Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

  - Sekvenční diagram vám pomůže vysvětlit složitou řadu interakcí mezi různými aktéry. Můžete ji také použít k zobrazení toho, co se v systému děje v reakci na každý případ použití. Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

- Propojit případ použití se stránkou, oddílem nebo odstavcem OneNotu, které podrobně popisuje případ použití.

- Připojte případ použití k dokumentu aplikace Word, ve kterém použijete text, snímky obrazovky a tak dále, k popisu scénářů případu použití. Další informace najdete v tématu [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Propojení případu použití s diagramem nebo souborem ve stejném řešení

1. Nakreslete diagram, jako je sekvenční diagram nebo diagram aktivity, a ilustrujte scénář případu použití.

2. Vraťte se do diagramu případu použití.

3. Přetáhněte diagram nebo soubor z Průzkumník řešení do prázdné části diagramu případu použití.

4. Připojte se z artefaktu k případu použití pomocí **závislosti**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Připojení k souboru řešení, například k dokumentu aplikace Word nebo prezentaci aplikace PowerPoint

1. Napíšete dokument, který používá text, snímky obrazovky a tak dále, a popište scénář případu použití.

2. Přidejte dokument do řešení.

    1. Přesuňte dokument aplikace Word do stejné složky systému Windows jako řešení.

    2. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, přejděte na **Přidat**a pak klikněte na **existující položka**.

    3. Přejděte do dokumentu aplikace Word a klikněte na tlačítko **Přidat**.

         Wordový dokument se zobrazí ve složce řešení v Průzkumník řešení.

3. Přetáhněte dokument aplikace Word z Průzkumník řešení do prázdné části diagramu případu použití.

     Zobrazí se nový artefakt.

4. Připojte se z artefaktu k případu použití pomocí **závislosti**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Připojení ke sdílenému dokumentu, prvku OneNotu nebo webové stránce

1. Získejte adresu URL sdíleného elementu. Může to být například cesta k síťovému souboru začínající \\ \\ na ' ', nebo webová stránka nebo adresa URL SharePointu začínající ' http://', nebo odkaz na oddíl, stránku nebo odstavec aplikace OneNote začínající na ' OneNote: '.

2. V sadě nástrojů klikněte na **artefakt** a pak klikněte v diagramu případu použití.

3. Vyberte nový artefakt a zadejte nebo vložte adresu URL do vlastnosti **hypertextový odkaz** .

> [!NOTE]
> Dvojitým kliknutím na artefakt můžete otevřít diagram nebo dokument, na který se odkazuje.

### <a name="linking-use-cases-to-work-items"></a>Propojení případů použití s pracovními položkami
 Pokud váš projekt používá [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] a máte [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , můžete propojit jednotlivé případy použití s pracovní položkou v [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Další informace o tom, jak tyto odkazy vytvořit, naleznete v tématu [propojování prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).

 To umožňuje:

- Popište případ použití v propojené pracovní položce. Zejména pokud váš projekt používá šablonu formálního procesu sady Visual Studio, můžete propojit s pracovní položkou případu použití. Tento typ pracovní položky poskytuje pole pro popis cílů a scénářů případu použití.

- Propojení testovacích případů s případem použití, aby bylo možné získat sestavy o tom, jak daleko vývoj kódu implementuje případ použití.

- Propojte úkoly s případem použití, abyste mohli sledovat průběh vývoje práce.

## <a name="structuring-use-cases"></a><a name="Structuring"></a> Strukturování případů použití
 Měli byste se pokusit popsat chování systému, a to pouze v několika hlavních případech použití. Každý velký případ použití definuje hlavní cíl, který objekt actor dosahuje, jako je například nákup produktu nebo, z pohledu dodavatele a poskytování produktů k prodeji.

 Pokud jste tyto cíle provedli jasný, můžete přejít k podrobnostem o tom, jak se má každý cíl dosáhnout, a o variacích základních cílů.

 Nepoužívejte příliš mnoho podrobností pro případy použití. Případy použití se týkají zkušeností uživatelů vašeho systému, nikoli interních pracovních procesů. Kromě toho obecně zjistíte, že budete mít k disdobě větší produktivitu při vytváření počátečních pracovních verzí kódu místo útraty, které jsou strukturou případů použití.

 V diagramu případu použití můžete shrnout vztahy mezi hlavními a podrobnějšími případy použití. Následující části popisují toto:

- [Zobrazení podrobností případu použití s zahrnutím](#Include)

- [Sdílení cílů pomocí generalizace](#Inheritance)

- [Oddělení variantních případů s rozšířeným](#Extend)

### <a name="showing-the-details-of-a-use-case-with-include"></a><a name="Include"></a> Zobrazení podrobností případu použití s zahrnutím
 Pomocí **zahrnutí** vztahu můžete zobrazit, že jeden případ použití popisuje některé podrobnosti o jiném. Na ilustraci **seřazení moučky** zahrnuje **platby**, **Výběr nabídky**a **Výběr položky nabídky**. Každý z obsažených, podrobnějších případů použití je krok, který může objekt actor nebo actor provést, aby dosáhl celkového cíle včetně případu použití. Šipka by měla ukazovat podrobnější, zahrnutý případ použití.

> [!CAUTION]
> Neměli byste vytvářet smyčky relací zahrnutí, které mají za následek případ použití, včetně sebe samé. Smyčky mohou generovat chyby.

 Můžete sdílet zahrnuté případy použití. V příkladu si **objednávka** a **přihlášení k odběru recenzí** použití zahrnují **platbu**.

 ![Případy použití odložené pomocí include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Cílem a scénářů zahrnutého případu použití by měl být smysl nezávisle, aby mohl být zahrnut v případech použití, které jsou navrženy později.

 Oddělení případů použití do zahrnutí a zahrnutých částí je užitečné k dosažení následujících cílů:

- Strukturu případů použití můžete strukturovat do různých vrstev podrobností.

- Vyhněte se opakujícím se sdíleným scénářům v různých případech použití.

#### <a name="defining-the-order-of-the-detailed-steps"></a><a name="Steps"></a> Definování pořadí podrobných kroků
 Diagram případu použití říká žádné informace o pořadí, ve kterém je nutné provést podrobnější kroky, ani o tom, zda je každý z nich vždy nezbytný.

 Aby bylo jasné, že je pořadí kroků jasné, můžete použít **artefakt** k připojení samostatného dokumentu k včetně případu použití. V následujícím příkladu se diagram aktivity připojil k objednávce použití v rámci moučky. Alternativně můžete použít textový dokument, který obsahuje seznam kroků nebo posloupnosti snímků obrazovky. Další informace naleznete v části [popisující případy použití podrobněji](#Details).

 Tyto zásady vytváření názvů si všimněte při použití diagramu činnosti:

- Název celé aktivity je stejný jako včetně případu použití.

- Akce v diagramu činnosti mají stejné názvy jako zahrnuté případy použití.

  Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

  ![Použít kroky pro případy, které jsou zobrazené v diagramu propojené aktivity](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="sharing-goals-with-generalization"></a><a name="Inheritance"></a> Sdílení cílů pomocí generalizace
 Pomocí vztahu Generalizace můžete ukázat, že *specializovaný* případ použití je konkrétní způsob, jak dosáhnout cílů vyjádřených jiným *obecným* případem použití. Otevřená šipka by měla ukazovat na obecnější případ použití.

 ![Případy použití znázorňující relaci generalizace](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Například **platí** , že generalizace platíte **za platební kartu** a **platíte podle hotovosti**.

> [!CAUTION]
> Neměli byste vytvářet smyčky vztahů generalizace, které vedou k generalizaci objektu actor. Smyčky mohou generovat chyby.

 Specializované případy použití vám mohou posloužit k zobrazení různých způsobů, které systém může dosáhnout stejného cíle.

 Specializované případy použití jsou považovány za dědění cílů a aktérů obecného případu použití. Obecný případ použití nemusí mít scénáře vlastní; jeho specializace popisují různé způsoby dosažení cílů.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Refaktorování běžných cílů ze dvou nebo více případů použití

1. Vytvořte a pojmenujte nový obecný případ použití.

2. Vytvořte relaci **generalizace** s velkou šipkou ukazující na nový obecný případ použití.

    1. V sadě nástrojů klikněte na **generalizace** .

    2. Klikněte na specializovaný případ použití (**platí v příkladu platební karta** ).

    3. Klikněte na obecný případ použití (**platí** v příkladu).

3. Pokud jste popsali cíle pro specializované případy použití, přesuňte společné části do popisu obecného případu použití.

4. Aktéry, které jsou sdíleny mezi specializovanými případy použití, lze přesunout do obecného případu použití.

### <a name="separating-variant-cases-with-extend"></a><a name="Extend"></a> Oddělování variantních případů pomocí Extended
 Pomocí odkazu roztažení můžete zobrazit, že jeden případ použití může za určitých okolností přidat funkci do jiného případu použití. Šipka by měla ukazovat na hlavní, rozšířený případ použití.

 ![Jeden případ použití, který rozšiřuje další](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Neměli byste vytvářet smyčky pro rozšířené relace, což má za následek generalizaci objektu actor. Smyčky mohou generovat chyby.

 Například případ použití **přihlašování** typického webu může zahrnovat **Registrovat nového uživatele** , ale pouze v případě, že uživatel ještě nemá účet.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Oddělení případu použití do hlavní části a rozšíření částí

1. Vytvořte a pojmenujte nový případ použití rozšíření.

2. Vytvoří **rozšířenou** relaci se šipkou ukazující na rozšířeném případu použití.

   1. V soupravě nástrojů klikněte na tlačítko **Rozšířené** .

   2. Klikněte na možnost rozšíření případu použití (**zaregistrovat nového uživatele** v příkladu).

   3. Klikněte na rozšířený případ použití (**přihlášení** v příkladu).

       > [!NOTE]
       > Vyhněte se vytváření smyčky rozšířených vztahů v diagramu. Není správné, pokud by případ použití bylo rozšířením samotného.

3. Pokud jste již vytvořili scénáře pro rozšířený případ použití, přesuňte příslušné kroky do scénáře rozšíření.

4. Popis rozšíření (**registrování nového uživatele** v příkladu) by měl obsahovat podrobnosti o tom, kde se v hlavním scénáři použití vyskytuje, a za jakých okolností. Můžete si ho představit jako úpravy popisu hlavního případu.

   Případ použití rozšíření představuje kroky scénáře, které by jinak byly součástí scénářů hlavního případu použití. Scénář a cíl rozšíření budou vždy čteny v kontextu hlavního případu použití, proto nemusí být užitečné nezávisle.

   Oddělení rozšíření mohou být užitečná pro popis těchto situací:

- Existují další aktéry, kteří se účastní pouze v případě použití rozšíření. Například správce musí schválit registraci zákazníka na webu.

- Samostatný podsystém se bude týkat případu použití rozšíření.

- Toto rozšíření bude k dispozici pouze v konkrétních verzích systému. Jednotlivé verze můžete zobrazit jako samostatný podsystém v diagramu případu použití.

## <a name="using-subsystem-boundaries"></a><a name="Subsystems"></a> Použití hranic subsystému
 Použijte hranici subsystému k zobrazení, které případy použití jsou v rámci rozsahu vašeho systému.

#### <a name="to-draw-a-subsystem-boundary"></a>Vykreslení hranice subsystému

1. V sadě nástrojů klikněte na **podsystém**a pak klikněte na diagram.

    V diagramu se zobrazí podsystém.

2. Přetažením rohů podsystému upravte jeho velikost.

3. Pokud chcete upravit obsah, přetáhněte existující případy použití do nebo ven z subsystému.

   \- ani

   Chcete-li vytvořit nový případ použití přímo v podsystému, klikněte na panelu nástrojů na možnost **použít případ** a pak klikněte na možnost uvnitř subsystému.

> [!NOTE]
> Vlastnost **předměty** případu použití indikuje, jaký subsystém je obsažen v.

### <a name="use-cases-outside-the-system-scope"></a>Případy použití mimo rozsah systému
 Často je vhodné zahrnout do diagramu případy použití, které jsou součástí firmy, ale nezabývá se systémem, který vyvíjíte. To pomáhá vývojářům pochopit kontext jejich práce. Například nabízená moučka by se mohla zobrazit jako případ použití, který se týká aktérů a zákazníků, ale mimo zodpovědnost webu pro objednávání moučky.

### <a name="multiple-subsystems"></a>Více subsystémů
 Můžete vytvořit několik hranic subsystému, abyste viděli, jak různé případy použití jsou řešeny různými součástmi systému. Například na samostatném webu fóra se může vyřídit **hodnocení restaurace** . Mějte na paměti, že diagram případu použití by měl pracovat s tím, co je pro uživatele viditelné. Chcete-li popsat interní dělení práce v systému, zvažte použití diagramu komponent.

### <a name="system-versions"></a>Verze systému
 K ilustraci různých verzí systému můžete použít jiné hranice subsystému. Například případ použití platby může být součástí webu verze 2, ale ne ve verzi 1. to znamená, že systém pomůže zákazníkům vytvořit své objednávky. Musí ale platit přímo v restauraci.

 Vztahy **závislosti** použijte k propojení subsystémů představujících různé verze nebo varianty.

 ![Subsystémy zobrazují různé verze systému.](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Viz také
 [Modely uživatelských požadavků modelu](../modeling/model-user-requirements.md) [UML sekvenční diagramy: pokyny](../modeling/uml-sequence-diagrams-guidelines.md) [Upravit modely UML a diagramy](../modeling/edit-uml-models-and-diagrams.md) [případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) diagramy [tříd](../modeling/uml-class-diagrams-reference.md) UML: referenční diagramy [komponent](../modeling/uml-component-diagrams-reference.md) UML: referenční informace k diagramům aktivit UML: [pokyny](../modeling/uml-activity-diagrams-guidelines.md) [video: uspořádání funkcí v případech použití](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
