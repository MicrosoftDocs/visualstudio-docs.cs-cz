---
title: 'Diagramy tříd UML: Pokyny | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bfd0b13942f5faee82e284c435b7f937d3ae5094
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726504"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramy tříd UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio, můžete použít *diagram tříd UML* pro popis datových typů a jejich vztahů nezávisle na jejich implementaci. Díky diagramu se lze místo jejich implementace zaměřit na logické aspekty tříd.  
  
 Chcete-li vytvořit diagram tříd UML, na **architektura** nabídce zvolte **nového diagramu UML nebo diagramu vrstev**.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Toto téma se zabývá diagramy tříd UML. Existuje jiný typ diagramu tříd, který lze vytvořit a použít jej k vizualizaci kódu programu. Zobrazit [navrhování a zobrazování tříd a typů](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="Using"></a> Použití diagramů tříd UML  
 Diagram tříd UML lze použít pro různé účely:  
  
-   Pro poskytnutí popisu nezávislého na implementaci typů, které jsou v systému použity a předány mezi komponentami.  
  
     Například typ Objednávka jídla lze implementovat v kódu .NET v obchodní vrstvě, v jazyce XML v rozhraních mezi komponentami, v jazyce SQL v databázi nebo v jazyce HTML v uživatelském rozhraní. Přestože se tyto implementace drobně liší, je vztah mezi Objednávkou jídla a ostatními typy, jako je například Nabídka a Platba, vždy stejný. Diagram tříd UML umožňuje diskuzi o těchto vztazích bez ohledu na implementaci.  
  
-   Aby bylo možné vyjasnit glosář termínů použitých pro komunikaci mezi aplikací a jejími uživateli a pro popis požadavků uživatele. Zobrazit [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
     Je třeba například zvážit uživatelské scénáře, případy užití nebo další popisy požadavků aplikace pro restauraci. V takových popisech lze najít termíny jako Nabídka, Objednávka, Jídlo, Cena, Platba a tak dále. Lze nakreslit diagram tříd UML, který definuje vztahy mezi těmito výrazy. To sníží riziko nesrovnalostí v popisech požadavků, v uživatelském prostředí a v pomocných dokumentech.  
  
### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
 Diagram tříd UML je obvykle nakreslen spolu s jinými diagramy modelování za účelem poskytnutí popisů typů, které používají. V každém případě není fyzická reprezentace typů implikována v žádném z diagramů.  
  
 Diagram činnosti  
  
 Typ dat procházejících skrz Uzel objektu.  
  
 Typy spojek vstupů a výstupů a uzlů parametrů aktivit.  
  
 Zobrazit [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
 Sekvenční diagram  
  
 Typy parametrů a vrácených hodnot zpráv.  
  
 Typy životností. Třída životnosti by měla zahrnovat operace pro všechny zprávy, které může přijímat.  
  
 Zobrazit [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagram součásti  
  
 Rozhraní komponent, výpis jejich operací.  
  
 Zobrazit [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).  
  
 Použití diagramu případu  
  
 Typy zmíněné v popisech cílů a v krocích případu užití.  
  
 Zobrazit [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Základní postup pro vytvoření diagramů tříd  
 Referenční informace o prvcích diagramu tříd UML lze najdete v tématu [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md).  
  
> [!NOTE]
>  Podrobné pokyny k vytvoření všech diagramů modelování jsou popsány v [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-uml-class-diagram"></a>Vytvoření diagramu tříd UML  
  
1.  Na **architektura** nabídce zvolte **nové UML nebo diagramu vrstev**.  
  
2.  V části **šablony**, zvolte **Diagram tříd UML**.  
  
3.  Pojmenujte diagram.  
  
4.  V **přidat k projektu modelování**, vyberte existující projekt modelování z řešení, nebo **vytvořit nový projekt modelování**a klikněte na tlačítko **OK**.  
  
     Zobrazí se nový diagram tříd **UMLClass Diagram** sady nástrojů. Sada nástrojů obsahuje požadované prvky a vztahy.  
  
#### <a name="to-draw-a-uml-class-diagram"></a>Nakreslení diagramu tříd UML  
  
1.  Chcete-li vytvořit typ, zvolte **třídy**, **rozhraní** nebo **výčet** nástroje na panelu nástrojů a potom klikněte na prázdnou část diagramu. (Pokud nevidíte panel nástrojů, stiskněte kombinaci kláves CTRL+ALT+X.)  
  
2.  Chcete-li přidat atributy nebo operace typům, nebo literály výčtu, zvolte **atributy**, **operace** nebo **literály** v typu nadpis a stiskněte klávesu ENTER.  
  
     Lze zapsat signaturu, jako `f(x:Boolean):Integer`. Zobrazit [atributy a operace](#AttributesAndOperations).  
  
     Pro rychlé přidání několika položek stiskněte klávesu ENTER dvakrát na konci každé položky. Pro procházení seznamu nahoru a dolů lze použít šipky.  
  
3.  Pro rozbalení a sbalení typu klikněte na ikonu dvojité šipky v levém horním rohu. Můžete rozbalit nebo sbalit **atributy** a **operace** části třídy nebo rozhraní.  
  
4.  Chcete-li nakreslit asociace, dědičnosti nebo závislosti mezi typy, klikněte na vhodný nástroj, následně na typ zdroje a nakonec na typ cíle.  
  
5.  Chcete-li vytvořit typy v balíčku, nejprve vytvořte balíček pomocí **balíčku** nástroje a pak vytvořte nové typy a balíčky v rámci balíčku. Rovněž lze použít kopírovací příkazy pro zkopírování typů a následné vložení do balíčku.  
  
6.  Každý diagram je zobrazení modelu, které je sdíleno mezi ostatními diagramy ve stejném projektu. Chcete-li zobrazení stromového zobrazení celého modelu, zvolte **zobrazení**, **ostatní Windows**, **Průzkumníku modelů UML**.  
  
##  <a name="UsingTypes"></a> Použití tříd, rozhraní a výčty  
 V panelu nástrojů jsou k dispozici tři standardní typy klasifikátorů. Tyto jsou označovány jako *typy* v tomto dokumentu.  
  
 ![Třída, výčet a rozhraní](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- Použití **třídy** (1) pro reprezentaci dat nebo objektových typů pro většinu účelů.  
  
- Použití **rozhraní** (2) v kontextu, ve kterém je třeba rozlišovat mezi čistým rozhraním a konkrétními třídami, které mají interní implementace. Toto rozlišení je užitečné, pokud je účelem diagramu popsat implementaci softwaru. Je méně vhodné, pokud jsou modelována pasivní data nebo pokud jsou definovány koncepty použité k popisu požadavků uživatele.  
  
- Použití **výčet** (3) pro reprezentaci typu, který má omezený počtem literálových hodnot, například `Stop` a `Go`.  
  
  -   Přidejte do výčtu literálové hodnoty. Každé přidělte odlišný název.  
  
  -   V případě potřeby lze rovněž každé literálové hodnotě poskytnout číselnou hodnotu. Otevřete místní nabídku pro literál ve výčtu, zvolte **vlastnosti**a potom zadejte číslo v **hodnotu** pole **vlastnosti** okna.  
  
  Každému typu zadejte jedinečný název.  
  
### <a name="getting-types-from-other-diagrams"></a>Získávání typů z ostatních diagramů  
 Do diagramu tříd UML lze zobrazit typy z jiného diagramu.  
  
 Diagram tříd UML  
  
 Třídu lze vložit do více než jednoho diagramu tříd UML. Když vytvoříte třídu na jednom diagramu přetáhněte z **Průzkumníku modelů UML** do jiného diagramu.  
  
 To je užitečné, pokud vyžadujete, aby se každý diagram zaměřoval na konkrétní skupinu vztahů.  
  
 Lze například na jednom diagramu ukázat asociace mezi entitami Objednávka jídla a Nabídka restaurace a na jiném asociace mezi entitami Objednávka jídla a Platba.  
  
 Diagram součásti  
  
 Pokud byla definována rozhraní na komponentách v diagramu komponent, můžete přetáhnout rozhraní z **Průzkumníku modelů UML** do diagramu tříd. V diagramu třídy můžete definovat metody, které jsou zahrnuty v rozhraní.  
  
 Zobrazit [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).  
  
 Sekvenční diagram UML  
  
 Můžete vytvořit ze životností sekvenčního diagramu třídy a rozhraní a následně třídu přetáhnout z **Průzkumníku modelů UML** do diagramu tříd UML. Každá životnost sekvenčního diagramu představuje instanci objektu, komponenty nebo aktéra.  
  
 Pro vytvoření třídy ze životnosti, otevřete místní nabídku životnosti a klikněte na tlačítko **vytvořit třídu** nebo **vytvořit rozhraní**. Zobrazit [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
##  <a name="AttributesAndOperations"></a> Atributy a operace  
 Atribut (4) je pojmenovaná hodnota, kterou může každá instance typu mít. Přístup k atributu stav instance nezmění.  
  
 Operace (5) je metoda nebo funkce, kterou může instance daného typu provést. Může vrátit hodnotu. Pokud jeho **isQuery** vlastnost má hodnotu true, nelze změnit stav instance.  
  
 Chcete-li do typu přidejte atribut nebo operace, otevřete místní nabídku pro typ, zvolte **přidat**a klikněte na tlačítko **atribut** nebo **operace**.  
  
 Můžete zobrazit její vlastnosti, otevřete místní nabídku pro atribut nebo operaci a klikněte na tlačítko **vlastnosti**. Vlastnosti se zobrazí v **vlastnosti** okna.  
  
 Chcete-li zobrazit vlastnosti parametrů operace zobrazíte, zvolte <strong>[...]</strong> v **parametry** vlastnost. Zobrazí se nové dialogové okno vlastností.  
  
 Podrobné informace o všech vlastnostech, které lze nastavit, lze nalézt v tématech:  
  
-   [Vlastnosti atributů v diagramech tříd UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Vlastnosti operací v diagramech tříd UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>Typy atributů a operací  
 Každý *typ* atributu nebo operace a každý typ parametru může být jedna z následujících akcí:  
  
- **(žádné)**  – Můžete ponechat typ nespecifikovaný v signatuře vynecháním předcházející dvojtečky (`:`).  
  
- Jeden ze standardních primitivních typů: **logická**, **celé číslo**, **řetězec**.  
  
- Typ, který je definován v modelu.  
  
- Parametrizovaná hodnota typu šablony zapsaná jako Template\<parametr >. Zobrazit [typy šablon](#Templates).  
  
  Lze rovněž napsat název typu, který ještě nebyl v modelu definován. Zobrazí se název v části **nespecifikované typy** v Průzkumníku modelů UML.  
  
> [!NOTE]
>  Pokud bude v modelu následně definována třída nebo rozhraní tohoto názvu, budou se starší atributy a operace stále odkazovat na prvek v seznamu Nespecifikované typy. Pokud je chcete změnit, aby se odkazovaly na novou třídu, je nutné u každého atributu a operace obnovit typ vybráním nové třídy z rozevírací nabídky.  
  
#### <a name="multiple-types"></a>Více typů  
 Lze nastavit násobnost atributu, operace nebo typu parametru.  
  
 Povoleny jsou následující hodnoty:  
  
 `[1]`  
  
 Jednu hodnotu daného typu. Toto nastavení je výchozí.  
  
 `[0..1]`  
  
 **Null** nebo hodnotu daného typu.  
  
 `[*]`  
  
 Kolekci libovolného počtu instancí daného typu.  
  
 `[1..*]`  
  
 Kolekci alespoň jedné instance daného typu.  
  
 `[n..m]`  
  
 Kolekci mezi `n` a `m` instance daného typu.  
  
 Pokud je násobnost větší než 1, lze rovněž nastavit následující vlastnosti:  
  
-   **IsOrdered** – Pokud je nastavena hodnota true a kolekce má definované uspořádání.  
  
-   **IsUnique** – Pokud je nastavena hodnota true, nejsou žádné duplicitní hodnoty v kolekci.  
  
### <a name="visibility"></a>Viditelnost  
 *Viditelnost* označuje, zda atribut nebo operace přístupné mimo definici třídy. Povoleny jsou následující hodnoty:  
  
 **Public**  
  
 **+**  
  
 Přístupné z jiných typů.  
  
 **Private**  
  
 **-**  
  
 Přístupné pouze pro interní definice tohoto typu.  
  
 **Balíček**  
  
 **~**  
  
 Přístupné pouze v rámci balíčku, který obsahuje tento typ a ve všech balíčcích, které jej explicitně importují. Zobrazit [definování oborů názvů a balíčků](#Packages).  
  
 **Protected**  
  
 **#**  
  
 Přístupný pouze pro tento typ a typy, které z něj dědí. Zobrazit [dědičnosti](#Inheritance).  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Nastavení signatury atributu nebo operace  
 Signatura atributu nebo operace je sada vlastností obsahující viditelnost, název, parametry (pro operace) a typ.  
  
 Signaturu lze napsat přímo do diagramu. Kliknutím vyberte atribut nebo operaci a poté na ně klikněte znovu.  
  
 Signaturu zadejte ve tvaru:  
  
```  
visibility attribute-name : Type  
```  
  
 \- nebo –  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 Příklad:  
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 Používejte krátký tvar viditelnosti. Výchozí hodnota je `+` (veřejné).  
  
 Každý typ může být typem, který byl definován v modelu, standardním typem, jako je například Integer či String, nebo může jít o název nového typu, který ještě nebyl definován.  
  
> [!NOTE]
>  Pokud do seznamu parametrů napíšete název bez typu, označuje tato položka název parametru namísto typu. V tomto příkladu budou MenuItem a Integer názvy dvou parametrů s nespecifikovanými typy:  
>   
>  `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 Pro nastavení násobnosti typu v signatuře zadejte násobnost do hranatých závorek za názvem typu. Například takto:  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 Pokud jsou atribut nebo operace statické, jejich název se zobrazí v signatuře podtrženě. Pokud je abstraktní, název se zobrazí kurzívou.  
  
 Však lze nastavit pouze **Is Static** a **je abstraktní** vlastnosti **vlastnosti** okna.  
  
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
  
 Obvykle se úplná signatura v diagramu zobrazí pouze při jeho úpravě. Po dokončení úprav jsou další vlastnosti skryty. Pokud chcete zobrazit být úplná signatura zobrazena neustále, otevřete místní nabídku pro typ a klikněte na tlačítko **zobrazit úplnou signaturu**.  
  
##  <a name="Associations"></a> Vykreslování a používání asociací  
 Asociace je používána pro reprezentaci jakéhokoli vztahu mezi dvěma prvky, bez ohledu na to, jakým způsobem je spojení v softwaru implementováno. Přidružení může například představovat ukazatele v jazyce C#, relace v databázi nebo křížový odkaz z jedné části souboru XML do jiné. Reprezentuje asociace mezi objekty reálného světa, jako je například země a slunce. Asociace neříkají, jak jsou spojení reprezentována, pouze to, že existují.  
  
### <a name="properties-of-an-association"></a>Vlastnosti asociace  
 Po vytvoření asociace je třeba nastavit její vlastnosti. Otevřete místní nabídku pro asociaci a klikněte na tlačítko **vlastnosti**.  
  
 Kromě vlastností asociace jako celku každý *role*, tedy každý konec asociace, má některé vlastnosti. Chcete-li je zobrazit, rozbalte **první Role** a **druhá Role** vlastnosti.  
  
 Některé vlastnosti jednotlivých rolí jsou v diagramu přímo viditelné. Jsou to tyto:  
  
- Název role. Zobrazí se na správném konci asociace v diagramu. V diagramu nebo v, můžete ho nastavit **vlastnosti** okna.  
  
- **Násobnost**, která má výchozí hodnotu **1**. Toto se rovněž na diagramu zobrazí blízko odpovídajícího konce asociace.  
  
- **Agregace**. Zobrazí se ve tvaru kosočtverce na jednom konci spojnice. Tím lze naznačit, že instance agregačních rolí vlastní nebo obsahují instance jiných.  
  
- **Jedná o navigaci**. Pokud je hodnota true pouze u jedné role, zobrazí se v jejím směru šipka. Toto lze použít k indikaci směru spojení a databázových relací v softwaru.  
  
  Podrobnosti o těchto a dalších vlastnostech naleznete v tématu [vlastnosti přidružení v UML diagramech tříd](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
### <a name="navigability"></a>Navigace  
 Po zakreslení má asociace na jednom konci šipku, což označuje, že asociace je provázána v tomto směru. To je užitečné, pokud diagram tříd reprezentuje softwarové třídy a asociace reprezentují ukazatele nebo odkazy. Pokud je však diagram tříd použit k reprezentaci entit a vztahů nebo obchodních konceptů, není použití navigace relevantní. V takovém případě je lepší použít zakreslení asociací bez šipek. Můžete to provést nastavením **Is Navigable** vlastnost na obou stranách asociace na hodnotu True. Abychom to usnadnili, si můžete stáhnout vzorový kód [modelování UML domény](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).  
  
### <a name="attributes-and-associations"></a>Atributy a asociace  
 Asociace je grafický způsob zobrazení atributu. Například namísto vytvoření třídy Restaurace s atributem typu Nabídka lze nakreslit asociaci z entity Restaurace do entity Nabídka.  
  
 Každý název atributu se stane názvem role. Objeví se na protilehlé straně asociace vlastnícího typu. Podívejte se, například na `myMenu` na obrázku.  
  
 Obecně je vhodnější použít atributy pouze pro typy, které by se neměly zakreslovat do diagramu, jako jsou například primitivní typy.  
  
 ![Ekvivalentní přidružení a atributy](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
##  <a name="Inheritance"></a> Dědičnost  
 Použití **dědičnosti** nástroj k vytvoření následujících vztahů:  
  
- A *generalizace* vztah mezi specializovaným typem a obecným typem  
  
   \- nebo –  
  
- A *realizace* vztah mezi třídou a, který implementuje rozhraní.  
  
  Ve vztazích dědičnosti nelze vytvořit smyčky.  
  
### <a name="generalization"></a>Generalizace  
 Generalizace znamená to, že specializované nebo odvozené typy dědí atributy, operace a asociace obecného nebo základního typu.  
  
 Obecný typ se zobrazí na konci vztahu se šipkou.  
  
 Zděděné operace a atributy se obvykle ve specializovaných typech nezobrazí. Do seznamu operací specializovaných typů však lze přidat zděděné operace. To je užitečné, pokud je zapotřebí přepsat některé vlastnosti operace ve specializovaném typu nebo pokud je zapotřebí naznačit to, že by to měl dělat implementovaný kód.  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Přepsání definice operace ve specializovaném typu  
  
1. Klikněte na relaci generalizace.  
  
    Zobrazí se zvýrazněně a v její blízkosti se objeví značka Akce.  
  
2. Klikněte na značku akce a potom klikněte na tlačítko **přepsat operace**.  
  
    **Přepsat operace** zobrazí se dialogové okno.  
  
3. Vyberte operace, které chcete zobrazit ve specializovaném typu, a pak klikněte na tlačítko **OK**.  
  
   Operace, které jste vybrali, se nyní zobrazí ve specializovaném typu.  
  
### <a name="realization"></a>Realizace  
 Realizace znamená, že třída implementuje atributy a operace zadané rozhraním. Rozhraní je na konci spojnice se šipkou.  
  
 Při vytvoření spojnice realizace budou operace rozhraní automaticky replikovány do realizační třídy. Pokud budou do rozhraní přidány nové operace, budou replikovány do realizační třídy.  
  
 Po vytvoření vztahu realizace jej lze převést do zápisu typu Lupa. Klikněte pravým tlačítkem na vztah a zvolte **zobrazit jako typ Lupa**.  
  
 To umožní zobrazit rozhraní, která třída implementuje, bez zbytečných diagramů tříd s odkazy realizace. Rozhraní a třídy, které je realizují, lze rovněž zobrazit v samostatných diagramech.  
  
 ![Realizace znázorněná s konektorem a lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
##  <a name="Templates"></a> Typy šablon  
 Lze definovat generický typ nebo typ šablony, který může být parametrizován jinými typy nebo hodnotami.  
  
 Lze například vytvořit generický slovník parametrizovaný typy klíče a hodnoty:  
  
 ![Třída šablony se dvěma parametry](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>Vytvoření typu šablony  
  
1. Vytvořte třídu nebo rozhraní. To bude váš typ šablony. Vhodně jej pojmenujte například `Dictionary`.  
  
2. Otevřete místní nabídku pro nový typ a klikněte na tlačítko **vlastnosti**.  
  
3. V **vlastnosti** okna, klikněte na tlačítko **[...]**  v **parametry šablony** pole.  
  
    **Editor kolekce parametrů šablony** zobrazí se dialogové okno.  
  
4. Zvolte **přidat**.  
  
5. Nastavte vlastnost name na název parametru pro typ šablony, například `Key`.  
  
6. Nastavte **druh parametru**. Výchozí hodnota je **třídy**.  
  
7. Pokud chcete parametr Přijmout pouze odvozené třídy určité základní třídy, nastavte **hodnota s omezením** na základní třídu, která chcete.  
  
8. Přidejte tolik parametrů, kolik potřebujete, klikněte na tlačítko **OK**.  
  
9. Typům šablony přidejte atributy a operace, jako byste to udělali u tříd.  
  
     Můžete použít parametry, jejichž druh je **třídy**, **rozhraní** nebo **výčet** v definici atributů a operací. Například použitím tříd parametrů `Key` a `Value`, lze definovat tuto operaci v `Dictionary`:  
  
     `Get(k : Key) : Value`  
  
     Můžete použít parametr, jehož druh je **celé číslo** jako vazbu v násobnosti. Například může použít parametr maximálního celého čísla pro definici násobnosti atributu jako `[0..max]`.  
  
   Pokud jste vytvořili typy šablon, lze je použít pro definici vazeb šablony:  
  
   ![Třída vázaná v šabloně slovníku](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>Použití typu šablony  
  
1.  Vytvoření nového typu, například `AddressTable`.  
  
2.  Otevřete místní nabídku pro nový typ a klikněte na tlačítko **vlastnosti**.  
  
3.  V **vazba šablony** vlastnosti, vyberte typ šablony, například `Dictionary`, z rozevíracího seznamu.  
  
4.  Rozbalte **vazba šablony** vlastnost.  
  
     Pro každý parametr typu šablony se zobrazí řádek.  
  
5.  Nastavte každý parametr na vhodnou hodnotu. Například nastavit `Key` parametr na třídu nazvaný `Name`.  
  
##  <a name="Packages"></a> Balíčky  
 V diagramu tříd UML lze zobrazit balíčky. Balíček je kontejner pro ostatní prvky modelu. Uvnitř balíčku lze vytvořit jakýkoli prvek. V diagramu budou prvky uvnitř balíčku přesouvány společně s balíčkem.  
  
 Pro skrytí nebo zobrazení obsahu balíčku lze použít ovládací prvek rozbalení/sbalení.  
  
 Zobrazit [definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).  
  
##  <a name="generating"></a> Generování kódu z diagramů tříd UML  
 Pro zahájení implementace tříd lze na základě diagramu tříd UML vygenerovat kód jazyka C# nebo upravit šablony pro generování kódu. Spuštění generování kódu pomocí poskytnutých šablon jazyka C#:  
  
-   Otevřete místní nabídku diagramu nebo prvku, zvolte **generovat kód**a následně nastavte nezbytné vlastnosti.  
  
     Další informace o tom, jak tyto vlastnosti nastavit a přizpůsobit poskytnuté šablony najdete v tématu [generování kódu z diagramů tříd UML](../modeling/generate-code-from-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)



