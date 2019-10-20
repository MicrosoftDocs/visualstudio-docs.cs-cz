---
title: 'Diagramy tříd UML: pokyny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 804678985ae30d833b57fe7589f0903cf1edb291
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652279"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramy tříd UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete použít *Diagram tříd UML* k popisu datových typů a jejich vztahů odděleně od jejich implementace. Díky diagramu se lze místo jejich implementace zaměřit na logické aspekty tříd.

 Chcete-li vytvořit diagram tříd UML, v nabídce **Architektura** vyberte možnost **Nový diagram UML nebo Diagram vrstev**.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Toto téma se zabývá diagramy tříd UML. Existuje jiný typ diagramu tříd, který lze vytvořit a použít jej k vizualizaci kódu programu. Viz [Návrh a zobrazení tříd a typů](http://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a>Použití diagramů tříd UML
 Diagram tříd UML lze použít pro různé účely:

- Pro poskytnutí popisu nezávislého na implementaci typů, které jsou v systému použity a předány mezi komponentami.

     Například typ Objednávka jídla lze implementovat v kódu .NET v obchodní vrstvě, v jazyce XML v rozhraních mezi komponentami, v jazyce SQL v databázi nebo v jazyce HTML v uživatelském rozhraní. Přestože se tyto implementace drobně liší, je vztah mezi Objednávkou jídla a ostatními typy, jako je například Nabídka a Platba, vždy stejný. Diagram tříd UML umožňuje diskuzi o těchto vztazích bez ohledu na implementaci.

- Aby bylo možné vyjasnit glosář termínů použitých pro komunikaci mezi aplikací a jejími uživateli a pro popis požadavků uživatele. Viz [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

     Je třeba například zvážit uživatelské scénáře, případy užití nebo další popisy požadavků aplikace pro restauraci. V takových popisech lze najít termíny jako Nabídka, Objednávka, Jídlo, Cena, Platba a tak dále. Lze nakreslit diagram tříd UML, který definuje vztahy mezi těmito výrazy. To sníží riziko nesrovnalostí v popisech požadavků, v uživatelském prostředí a v pomocných dokumentech.

### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům
 Diagram tříd UML je obvykle nakreslen spolu s jinými diagramy modelování za účelem poskytnutí popisů typů, které používají. V každém případě není fyzická reprezentace typů implikována v žádném z diagramů.

 Diagram činnosti

 Typ dat procházejících skrz Uzel objektu.

 Typy spojek vstupů a výstupů a uzlů parametrů aktivit.

 Podívejte se na téma [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

 Sekvenční diagram

 Typy parametrů a vrácených hodnot zpráv.

 Typy životností. Třída životnosti by měla zahrnovat operace pro všechny zprávy, které může přijímat.

 Podívejte se na téma [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagram součásti

 Rozhraní komponent, výpis jejich operací.

 Viz téma [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).

 Použití diagramu případu

 Typy zmíněné v popisech cílů a v krocích případu užití.

 Viz téma [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Základní kroky pro vykreslování diagramů tříd
 Referenční informace o prvcích v diagramech tříd UML naleznete v tématu [diagramy tříd UML: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Podrobné pokyny pro vytvoření některého z diagramů modelování jsou popsány v tématu [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>Vytvoření diagramu tříd UML

1. V nabídce **Architektura** vyberte **Nový UML nebo Diagram vrstev**.

2. V části **šablony**vyberte možnost **Diagram tříd UML**.

3. Pojmenujte diagram.

4. V možnosti **Přidat do projektu modelování**vyberte existující projekt modelování ve vašem řešení, nebo **vytvořte nový projekt modelování**a pak zvolte možnost **OK**.

     Zobrazí se nový diagram třídy se sadou nástrojů **diagramu UMLClass** . Sada nástrojů obsahuje požadované prvky a vztahy.

#### <a name="to-draw-a-uml-class-diagram"></a>Nakreslení diagramu tříd UML

1. Chcete-li vytvořit typ, zvolte nástroj **Třída**, **rozhraní** nebo **výčet** na panelu nástrojů a pak klikněte na prázdnou část diagramu. (Pokud nevidíte panel nástrojů, stiskněte kombinaci kláves CTRL+ALT+X.)

2. Chcete-li přidat atributy nebo operace do typů nebo literály do výčtu, zvolte nadpis **atributy**, **operace** nebo **literály** v typu a stiskněte klávesu ENTER.

     Můžete napsat podpis, například `f(x:Boolean):Integer`. Viz [atributy a operace](#AttributesAndOperations).

     Pro rychlé přidání několika položek stiskněte klávesu ENTER dvakrát na konci každé položky. Pro procházení seznamu nahoru a dolů lze použít šipky.

3. Pro rozbalení a sbalení typu klikněte na ikonu dvojité šipky v levém horním rohu. Můžete také rozbalit a sbalit oddíl **atributy** a **operace** třídy nebo rozhraní.

4. Chcete-li nakreslit asociace, dědičnosti nebo závislosti mezi typy, klikněte na vhodný nástroj, následně na typ zdroje a nakonec na typ cíle.

5. Chcete-li vytvořit typy v balíčku, vytvořte balíček pomocí nástroje **Package** a pak vytvořte nové typy a balíčky v rámci balíčku. Rovněž lze použít kopírovací příkazy pro zkopírování typů a následné vložení do balíčku.

6. Každý diagram je zobrazení modelu, které je sdíleno mezi ostatními diagramy ve stejném projektu. Chcete-li zobrazit stromové zobrazení kompletního modelu, vyberte možnost **zobrazení**, **ostatní okna**, **Průzkumník modelů UML**.

## <a name="UsingTypes"></a>Použití tříd, rozhraní a výčtů
 V panelu nástrojů jsou k dispozici tři standardní typy klasifikátorů. Ty se v tomto dokumentu označují jako *typy* .

 ![Třída, výčet a rozhraní](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Použijte **třídy** (1) k reprezentování typů dat nebo objektů pro většinu účelů.

- Použijte **rozhraní** (2) v kontextu, kde je nutné rozlišovat mezi čistými rozhraními a konkrétními třídami, které mají interní implementace. Toto rozlišení je užitečné, pokud je účelem diagramu popsat implementaci softwaru. Je méně vhodné, pokud jsou modelována pasivní data nebo pokud jsou definovány koncepty použité k popisu požadavků uživatele.

- Použijte **výčet** (3) k vyjádření typu, který má omezený počet literálových hodnot, například `Stop` a `Go`.

  - Přidejte do výčtu literálové hodnoty. Každé přidělte odlišný název.

  - V případě potřeby lze rovněž každé literálové hodnotě poskytnout číselnou hodnotu. Otevřete místní nabídku pro literál ve výčtu, zvolte možnost **vlastnosti**a zadejte číslo do pole **hodnota** v okně **vlastnosti** .

  Každému typu zadejte jedinečný název.

### <a name="getting-types-from-other-diagrams"></a>Získávání typů z ostatních diagramů
 Do diagramu tříd UML lze zobrazit typy z jiného diagramu.

 Diagram tříd UML

 Třídu lze vložit do více než jednoho diagramu tříd UML. Když jste vytvořili třídu v jednom diagramu, přetáhněte třídu z **Průzkumníka modelů UML** do druhého diagramu.

 To je užitečné, pokud vyžadujete, aby se každý diagram zaměřoval na konkrétní skupinu vztahů.

 Lze například na jednom diagramu ukázat asociace mezi entitami Objednávka jídla a Nabídka restaurace a na jiném asociace mezi entitami Objednávka jídla a Platba.

 Diagram součásti

 Pokud jste definovali rozhraní komponent v diagramu komponent, můžete přetáhnout rozhraní z **Průzkumníku modelů UML** do diagramu tříd. V diagramu třídy můžete definovat metody, které jsou zahrnuty v rozhraní.

 Viz téma [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).

 Sekvenční diagram UML

 Třídy a rozhraní můžete vytvořit ze životností v sekvenčním diagramu a pak ji přetáhnout z **Průzkumníka modelů UML** do diagramu tříd UML. Každá životnost sekvenčního diagramu představuje instanci objektu, komponenty nebo aktéra.

 Chcete-li vytvořit třídu z životnosti, otevřete místní nabídku životnosti a poté zvolte možnost **vytvořit třídu** nebo **vytvořit rozhraní**. Podívejte se na téma [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a>Atributy a operace
 Atribut (4) je pojmenovaná hodnota, kterou může každá instance typu mít. Přístup k atributu stav instance nezmění.

 Operace (5) je metoda nebo funkce, kterou může instance daného typu provést. Může vrátit hodnotu. Pokud má vlastnost pro **dotaz** hodnotu true, nemůže změnit stav instance.

 Chcete-li přidat atribut nebo operaci do typu, otevřete místní nabídku pro daný typ, zvolte možnost **Přidat**a pak zvolte možnost **atribut** nebo **operace**.

 Chcete-li zobrazit jeho vlastnosti, otevřete místní nabídku pro atribut nebo operaci a poté zvolte možnost **vlastnosti**. Vlastnosti se zobrazí v okně **vlastnosti** .

 Chcete-li zobrazit vlastnosti parametrů operace, klikněte na položku <strong>[...]</strong> . ve vlastnosti **Parameters** . Zobrazí se nové dialogové okno vlastností.

 Podrobné informace o všech vlastnostech, které lze nastavit, lze nalézt v tématech:

- [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Typy atributů a operací
 Každý *typ* atributu nebo operace a každý typ parametru může být jedna z následujících:

- **(žádné)** – v podpisu můžete ponechat typ nespecifikovaný, a to vynecháním předchozí dvojtečky (`:`).

- Jeden ze standardních primitivních typů: **Boolean**, **Integer**, **String**.

- Typ, který je definován v modelu.

- Parametrizovaná hodnota typu šablony, napsaná šablona \<Parameter >. Viz [typy šablon](#Templates).

  Lze rovněž napsat název typu, který ještě nebyl v modelu definován. Název bude uveden v části **neurčené typy** v PRŮZKUMNÍKU modelů UML.

> [!NOTE]
> Pokud bude v modelu následně definována třída nebo rozhraní tohoto názvu, budou se starší atributy a operace stále odkazovat na prvek v seznamu Nespecifikované typy. Pokud je chcete změnit, aby se odkazovaly na novou třídu, je nutné u každého atributu a operace obnovit typ vybráním nové třídy z rozevírací nabídky.

#### <a name="multiple-types"></a>Více typů
 Lze nastavit násobnost atributu, operace nebo typu parametru.

 Povoleny jsou následující hodnoty:

 `[1]`

 Jednu hodnotu daného typu. Toto nastavení je výchozí.

 `[0..1]`

 **Null** nebo hodnota daného typu.

 `[*]`

 Kolekci libovolného počtu instancí daného typu.

 `[1..*]`

 Kolekci alespoň jedné instance daného typu.

 `[n..m]`

 Kolekce mezi `n` a `m` instance daného typu.

 Pokud je násobnost větší než 1, lze rovněž nastavit následující vlastnosti:

- Je **-li** nastavena hodnota true, má kolekce definované pořadí.

- **UniqueTable** – Pokud je nastaveno na true, v kolekci nejsou žádné duplicitní hodnoty.

### <a name="visibility"></a>Viditelnost
 *Visibility* označuje, zda lze k atributu nebo operaci přistupovat mimo definici třídy. Povoleny jsou následující hodnoty:

 **Public**

 **+**

 Přístupné z jiných typů.

 **Private**

 **-**

 Přístupné pouze pro interní definice tohoto typu.

 **Balíček**

 **~**

 Přístupné pouze v rámci balíčku, který obsahuje tento typ a ve všech balíčcích, které jej explicitně importují. Viz [definování oborů názvů a balíčků](#Packages).

 **Protected**

 **#**

 Přístupný pouze pro tento typ a typy, které z něj dědí. Viz [Dědičnost](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Nastavení signatury atributu nebo operace
 Signatura atributu nebo operace je sada vlastností obsahující viditelnost, název, parametry (pro operace) a typ.

 Signaturu lze napsat přímo do diagramu. Kliknutím vyberte atribut nebo operaci a poté na ně klikněte znovu.

 Signaturu zadejte ve tvaru:

```
visibility attribute-name : Type
```

 \- nebo-

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Příklad:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Používejte krátký tvar viditelnosti. Výchozí hodnota je `+` (Public).

 Každý typ může být typem, který byl definován v modelu, standardním typem, jako je například Integer či String, nebo může jít o název nového typu, který ještě nebyl definován.

> [!NOTE]
> Pokud do seznamu parametrů napíšete název bez typu, označuje tato položka název parametru namísto typu. V tomto příkladu budou MenuItem a Integer názvy dvou parametrů s nespecifikovanými typy:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Pro nastavení násobnosti typu v signatuře zadejte násobnost do hranatých závorek za názvem typu. Například takto:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Pokud jsou atribut nebo operace statické, jejich název se zobrazí v signatuře podtrženě. Pokud je abstraktní, název se zobrazí kurzívou.

 Nicméně je možné nastavit pouze **statické** a **abstraktní** vlastnosti v okně **vlastnosti** .

#### <a name="full-signature"></a>Úplná signatura
 Při úpravě signatury atributu nebo operace se mohou na konci řádku a za každým parametrem objevit další vlastnosti. Objevují se uzavřené ve složených závorkách {...}. Tyto vlastnosti lze upravovat nebo přidávat. Příklad:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Tyto vlastnosti jsou následující:

 `unique`

 **Je jedinečný**

 V kolekci nejsou duplicitní hodnoty. Platí pro typy s násobností větší než 1.

 `ordered`

 **Je seřazen**

 Kolekce je sekvenční. Pokud má hodnotu false, neexistuje konečný první prvek. Platí pro typy s násobností větší než 1.

 `query`

 **Je dotaz**

 Operace nezmění stav své instance. Platí pouze pro operace.

 `/`

 **Je odvozen**

 Atribut je vypočítán z hodnot jiných atributů nebo asociací.

 Před názvem atributu se zobrazí „/“. Příklad:

```
/TotalPrice: Integer
```

 Obvykle se úplná signatura v diagramu zobrazí pouze při jeho úpravě. Po dokončení úprav jsou další vlastnosti skryty. Pokud chcete úplný podpis zobrazit celý čas, otevřete místní nabídku pro daný typ a pak zvolte možnost **Zobrazit úplný podpis**.

## <a name="Associations"></a>Kreslení a použití přidružení
 Asociace je používána pro reprezentaci jakéhokoli vztahu mezi dvěma prvky, bez ohledu na to, jakým způsobem je spojení v softwaru implementováno. Přidružení může například představovat ukazatele v jazyce C#, relace v databázi nebo křížový odkaz z jedné části souboru XML do jiné. Reprezentuje asociace mezi objekty reálného světa, jako je například země a slunce. Asociace neříkají, jak jsou spojení reprezentována, pouze to, že existují.

### <a name="properties-of-an-association"></a>Vlastnosti asociace
 Po vytvoření asociace je třeba nastavit její vlastnosti. Otevřete místní nabídku pro přidružení a pak zvolte možnost **vlastnosti**.

 Kromě vlastností přidružení jako celku má každá *role*, tedy každý konec přidružení, některé vlastnosti vlastní. Pokud je chcete zobrazit, rozbalte vlastnosti **první role** a **druhá role** .

 Některé vlastnosti jednotlivých rolí jsou v diagramu přímo viditelné. Jsou to tyto:

- Název role. Zobrazí se na správném konci asociace v diagramu. Můžete ji nastavit buď v diagramu, nebo v okně **vlastnosti** .

- **Násobnost**, která má výchozí hodnotu **1**. Toto se rovněž na diagramu zobrazí blízko odpovídajícího konce asociace.

- **Agregace**. Zobrazí se ve tvaru kosočtverce na jednom konci spojnice. Tím lze naznačit, že instance agregačních rolí vlastní nebo obsahují instance jiných.

- **Je naviguje**. Pokud je hodnota true pouze u jedné role, zobrazí se v jejím směru šipka. Toto lze použít k indikaci směru spojení a databázových relací v softwaru.

  Úplné podrobnosti o těchto a dalších vlastnostech naleznete v tématu [Vlastnosti přidružení v diagramech tříd UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Navigace
 Po zakreslení má asociace na jednom konci šipku, což označuje, že asociace je provázána v tomto směru. To je užitečné, pokud diagram tříd reprezentuje softwarové třídy a asociace reprezentují ukazatele nebo odkazy. Pokud je však diagram tříd použit k reprezentaci entit a vztahů nebo obchodních konceptů, není použití navigace relevantní. V takovém případě je lepší použít zakreslení asociací bez šipek. To lze provést nastavením vlastnosti **is naviguje** na obou koncích přidružení na hodnotu true. Chcete-li to usnadnit, můžete si stáhnout ukázkový kód [modelování domény UML](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).

### <a name="attributes-and-associations"></a>Atributy a asociace
 Asociace je grafický způsob zobrazení atributu. Například namísto vytvoření třídy Restaurace s atributem typu Nabídka lze nakreslit asociaci z entity Restaurace do entity Nabídka.

 Každý název atributu se stane názvem role. Objeví se na protilehlé straně asociace vlastnícího typu. Podívejte se například na `myMenu` na obrázku.

 Obecně je vhodnější použít atributy pouze pro typy, které by se neměly zakreslovat do diagramu, jako jsou například primitivní typy.

 ![Ekvivalentní přidružení a atributy](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a>Dědičnost
 Použijte nástroj **Dědičnost** k vytvoření následujících vztahů:

- Vztah *generalizace* mezi specializovaným typem a obecným typem

   \- nebo-

- Vztah *realizace* mezi třídou a rozhraním, které implementuje.

  Ve vztazích dědičnosti nelze vytvořit smyčky.

### <a name="generalization"></a>Generalizace
 Generalizace znamená to, že specializované nebo odvozené typy dědí atributy, operace a asociace obecného nebo základního typu.

 Obecný typ se zobrazí na konci vztahu se šipkou.

 Zděděné operace a atributy se obvykle ve specializovaných typech nezobrazí. Do seznamu operací specializovaných typů však lze přidat zděděné operace. To je užitečné, pokud je zapotřebí přepsat některé vlastnosti operace ve specializovaném typu nebo pokud je zapotřebí naznačit to, že by to měl dělat implementovaný kód.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Přepsání definice operace ve specializovaném typu

1. Klikněte na relaci generalizace.

    Zobrazí se zvýrazněně a v její blízkosti se objeví značka Akce.

2. Klikněte na značku akce a pak klikněte na **potlačit operace**.

    Zobrazí se dialogové okno **přepsat operace** .

3. Vyberte operace, které chcete zobrazit ve specializovaném typu, a pak klikněte na **OK**.

   Operace, které jste vybrali, se nyní zobrazí ve specializovaném typu.

### <a name="realization"></a>Realizace
 Realizace znamená, že třída implementuje atributy a operace zadané rozhraním. Rozhraní je na konci spojnice se šipkou.

 Při vytvoření spojnice realizace budou operace rozhraní automaticky replikovány do realizační třídy. Pokud budou do rozhraní přidány nové operace, budou replikovány do realizační třídy.

 Po vytvoření vztahu realizace jej lze převést do zápisu typu Lupa. Klikněte pravým tlačítkem na vztah a vyberte **Zobrazit jako Lupa**.

 To umožní zobrazit rozhraní, která třída implementuje, bez zbytečných diagramů tříd s odkazy realizace. Rozhraní a třídy, které je realizují, lze rovněž zobrazit v samostatných diagramech.

 ![Realizace zobrazená pomocí konektor a lupy](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a>Typy šablon
 Lze definovat generický typ nebo typ šablony, který může být parametrizován jinými typy nebo hodnotami.

 Lze například vytvořit generický slovník parametrizovaný typy klíče a hodnoty:

 ![Třída šablony se dvěma parametry](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Vytvoření typu šablony

1. Vytvořte třídu nebo rozhraní. To bude váš typ šablony. Pojmenujte ji odpovídajícím způsobem, například `Dictionary`.

2. Otevřete místní nabídku pro nový typ a pak zvolte možnost **vlastnosti**.

3. V okně **vlastnosti** klikněte na položku **[...]** v poli **parametry šablony** .

    Zobrazí se dialogové okno **Editor kolekce parametrů šablony** .

4. Klikněte na tlačítko **Přidat**.

5. Nastavte vlastnost název na název parametru pro typ šablony, například `Key`.

6. Nastavte **druh parametru**. Výchozí hodnota je **Class**.

7. Chcete-li, aby parametr přijímal pouze odvozené třídy určité základní třídy, nastavte **hodnotu omezení** na základní třídu, kterou požadujete.

8. Přidejte tolik parametrů, kolik potřebujete, a pak zvolte **OK**.

9. Typům šablony přidejte atributy a operace, jako byste to udělali u tříd.

     Můžete použít parametry, jejichž druh je **Třída**, **rozhraní** nebo **výčet** v definici atributů a operací. Například pomocí tříd parametrů `Key` a `Value` můžete tuto operaci definovat v `Dictionary`:

     `Get(k : Key) : Value`

     Můžete použít parametr, jehož druh je **celé číslo** jako hranice v násobnosti. Například parametr Max Integer lze použít k definování násobnosti atributu jako `[0..max]`.

   Pokud jste vytvořili typy šablon, lze je použít pro definici vazeb šablony:

   ![Třída vázaná ze šablony slovníku](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Použití typu šablony

1. Vytvořte nový typ, například `AddressTable`.

2. Otevřete místní nabídku pro nový typ a pak zvolte možnost **vlastnosti**.

3. Ve vlastnosti **vazba šablony** vyberte typ šablony, například `Dictionary`, z rozevíracího seznamu.

4. Rozbalte vlastnost **vazba šablony** .

     Pro každý parametr typu šablony se zobrazí řádek.

5. Nastavte každý parametr na vhodnou hodnotu. Například nastavte parametr `Key` na třídu nazvanou `Name`.

## <a name="Packages"></a>Zásilk
 V diagramu tříd UML lze zobrazit balíčky. Balíček je kontejner pro ostatní prvky modelu. Uvnitř balíčku lze vytvořit jakýkoli prvek. V diagramu budou prvky uvnitř balíčku přesouvány společně s balíčkem.

 Pro skrytí nebo zobrazení obsahu balíčku lze použít ovládací prvek rozbalení/sbalení.

 Viz [Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a>Generování kódu z diagramů tříd UML
 Pro zahájení implementace tříd lze na základě diagramu tříd UML vygenerovat kód jazyka C# nebo upravit šablony pro generování kódu. Spuštění generování kódu pomocí poskytnutých šablon jazyka C#:

- Otevřete místní nabídku diagramu nebo prvku, zvolte možnost **generovat kód**a pak nastavte potřebné vlastnosti.

     Další informace o nastavení těchto vlastností a přizpůsobení poskytovaných šablon naleznete v tématu [generování kódu z diagramů tříd UML](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Viz také
 [Umožňuje upravit modely a diagramy UML](../modeling/edit-uml-models-and-diagrams.md) diagramy [tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) [Model požadavky uživatelů](../modeling/model-user-requirements.md) na [diagramy komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) [diagramy UML](../modeling/uml-sequence-diagrams-reference.md) : referenční diagramy [případu použití UML](../modeling/uml-use-case-diagrams-reference.md) [: Referenční dokumentace UML Diagramy komponent: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace
