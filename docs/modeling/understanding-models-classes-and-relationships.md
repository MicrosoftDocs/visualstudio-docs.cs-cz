---
title: Porozumění modelům, třídám a vztahům
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 74172b6e7f03d7e3baef329f053fc4a83ee6ae28
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967386"
---
# <a name="understanding-models-classes-and-relationships"></a>Porozumění modelům, třídám a vztahům
Jazyka specifického pro doménu (DSL) je definován v jeho souboru definice DSL, společně s jakýkoli vlastní program kód, který může zapisovat. Většina programového kódu v řešení DSL je generována z tohoto souboru.

 Toto téma popisuje funkce centrální v definici DSL.

## <a name="the-dsl-definition"></a>Definice DSL
 Když otevřete `Dsl\DslDefinition.dsl`, Visual Studio okno vypadá podobně jako na následujícím obrázku.

 ![Návrhář DSL](../modeling/media/dsl_designer.png)

 V definici DSL diagramu se zobrazí nejdůležitější informace v definici DSL. Další informace, které je také součástí DslDefinition.dsl, se zobrazí v Průzkumníku DSL, který je obvykle v části diagramu. Pracujete s diagram pro nejčastěji používané úkoly a Průzkumník DSL pokročilejší úpravy.

 Diagramem definice DSL ukazuje doménové třídy, které definují prvků modelu a vztahy, které definují propojení mezi elementy modelu. Také ukazuje obrazců a konektorů, které se používají k zobrazení prvků modelu pro uživatele.

 ![Návrhář DSL s plavecké dráhy](../modeling/media/dsl_desinger.png)

 Když vyberete položku v definici DSL v diagramu nebo v Průzkumníku DSL, zobrazí se informace o ho v okně Vlastnosti. Další informace může být zobrazen v okně podrobností DSL.

### <a name="models-are-instances-of-dsls"></a>Modely jsou instance DSL
 A *modelu* je instance tohoto kódu DSL vytvořené uživatelem. Model obsahuje prvky modelu, které jsou instancemi třídy domény, které definujete a propojení mezi elementy, které jsou instancemi vztahy domén, které definujete. Model může mít také obrazců a konektorů, které budou zobrazovat prvků modelu a odkazy v diagramu. Definice DSL zahrnuje třídy tvar, konektor třídy a třídu diagramu.

 Je také označován jako definici DSL *doménový model*. Definice DSL nebo domény model je návrhu reprezentace jazyka specifického pro doménu, zatímco model je za běhu instance jazyka specifického pro doménu.

## <a name="domain-classes-define-model-elements"></a>Doménové třídy definují elementů modelu
 Doménové třídy umožňují vytvářet různé prvky v této doméně a doménové vztahy jsou propojení mezi elementy. Jedná se o reprezentaci návrhu prvků a odkazy, které bude vytvořena instance pro uživatele jazyka specifického pro návrh při vytváření své modely.

 Tento obrázek ukazuje modelu, který byl vytvořen uživatelem Hudba library DSL. Hudba alb jsou reprezentované pomocí polí, které obsahují seznamy skladeb. Vašim animátorům jsou reprezentovány zaoblenými polí a jsou připojené do alb, ke kterým přispěli.

 ![Instance modelu generované DSL](../modeling/media/music_instance.png)

 Definice DSL odděluje dva aspekty. Vzhled elementů modelu v diagramu modelu je definována pomocí obrazce a spojnice třídy. Informace v modelu je definováno pomocí třídy domény a vztahy domén.

 Následující obrázek znázorňuje doménovými třídami a vztahy v definici DSL knihovna.

 ![Vztahy vložení a referenční informace](../modeling/media/music_classes.png)

 Na obrázku znázorňuje čtyři doménovými třídami: Hudba, fotoalba, interpreta a skladby. Doménové třídy definují vlastnosti domény, například název, nadpis a tak dále. Instance modelu jsou hodnoty některých z těchto vlastností zobrazí v diagramu.

 Třídy, aby se vztahy domén: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs a ArtistAppearedOnAlbums. Vztahy mít například 1..1, násobnosti 0.. *. Například každý skladby musí mít relaci ke přesně jeden alba prostřednictvím AlbumHasSongs vztahu. Každý alba může mít libovolný počet skladeb.

### <a name="rearranging-the-dsl-definition-diagram"></a>Změna uspořádání diagramem definice DSL
 Všimněte si, že doménová třída může zobrazit několikrát v definici DSL diagramu, alba stejně jako na tomto obrázku. Je vždy jeden hlavní zobrazení a můžou být některé *odkaz* zobrazení.

 Chcete-li uspořádat diagramem definice DSL, můžete:

-   Zaměnit hlavní a odkazovat pomocí zobrazení **přenést stromu zde** a **rozdělit strom** příkazy. Klikněte pravým tlačítkem na jednu doménovou třídu najdete v těchto příkazů.

-   Změnit pořadí doménové třídy a třídy tvar stisknutím kombinace kláves Ctrl + šipka nahoru a Ctrl + šipka dolů.

-   Sbalit či rozbalit třídy pomocí ikony v pravém horním rohu každé obrazce.

-   Kliknutím na znaménko minus (-) v dolní části doménovou třídu sbalení části stromu.

## <a name="inheritance"></a>Dědičnost
 Doménové třídy lze definovat pomocí dědičnosti. Chcete-li vytvořit odvození dědičnosti, klikněte na nástroj dědičnosti, klikněte na tlačítko odvozené třídy a pak klikněte na základní třídu. Prvek modelu má všechny vlastnosti, které jsou definovány ve třídě vlastní domény, společně se všemi vlastnostmi zděděné ze základní třídy. Také dědí její role ve vztazích.

 Dědičnost lze také mezi relace, obrazců a konektorů. Dědičnost musí zůstat ve stejné skupině. Obrazec nemůže dědit z třídy domény.

## <a name="domain-relationships"></a>Doménové vztahy
 Prvky modelu lze propojit vztahy. Odkazy jsou vždy binární; spojují právě dva elementy. Ale libovolný prvek může mít mnoho odkazů na jiné objekty, a může existovat i více než jedno propojení mezi stejného páru prvků.

 Stejně jako můžete definovat různé třídy prvky, můžete definovat různé třídy odkazy. Třída odkaz se nazývá *doménového vztahu*. Doménovým vztahem Určuje, jaké třídy element její instance může připojit. Každý konec prvku relace je volána *role*, a doménového vztahu definuje názvy pro dvě role, stejně jako pro samotnou relaci.

 Existují dva typy vztahů domény: vložení vztah a vztah odkazu. V definici DSL diagramu vkládání vztahy mají čar na každou roli a referenční stavy mají přerušované čáry.

### <a name="embedding-relationships"></a>Vkládání relace
 Každý prvek v modelu, s výjimkou jeho kořenové složky je cílem jednoho vkládání propojení. Proto celý model tvoří jeden strom vkládání odkazů. Vztah obsažení představuje členství ve skupině nebo vlastnictví. Dva prvky modelu, které se týkají tímto způsobem se také označují jako nadřazené a podřízené. Podřízené říká, že je vložený v nadřazeném prvku.

 Vkládání odkazy se nezobrazují obvykle explicitně jako konektory v diagramu. Místo toho že jsou obvykle reprezentováno členství ve skupině. Diagram je reprezentován kořen modelu a prvky vložené v ní jsou zobrazeny jako tvary v diagramu.

 V příkladu má kořenová třída Hudba vztah obsažení MusicHasAlbums do alb, jehož vkládání AlbumHasSongs k skladby. Skladby se zobrazují jako položky v seznamu v každé Album. Hudba má také vkládání MusicHasArtists interpreta třídu, jejíž instance se zobrazí také jako tvary v diagramu.

 Ve výchozím nastavení jsou vložené prvky automaticky odstraněna při odstranění svých nadřazených složek.

 Při uložení modelu do souboru v podobě XML vložené prvky vnořit do svých nadřazených složek, pokud jste upravili serializace.

> [!NOTE]
>  Vkládání není stejný jako dědičnosti. Podřízené položky v vztah obsažení nedědí vlastnosti nadřazeného objektu. Vložení je typ propojení mezi elementy modelu. Dědičnost je vztah mezi třídami a neslouží k vytvoření propojení mezi elementy modelu.

### <a name="embedding-rules"></a>Vkládání pravidla
 Každý prvek v modelu instance musí být cílem přesně jedno propojení vkládání, s výjimkou kořenu modelu.

 Proto se každá domény Neabstraktní třída s výjimkou kořenové třídy musí být cílem alespoň jeden vztah obsažení nebo musí dědit ze základní třídy vložení. Třída může být cílem nejmíň dva vkládání, ale jeho prvky modelu instance může mít pouze jeden nadřazený prvek v čase. Násobnost z cíle na zdroj musí být 0.. 1 nebo 1..1.

### <a name="the-explorer-displays-the-embedding-tree"></a>Vložení stromu se zobrazí v Průzkumníku
 Vaše definice DSL také vytvoří Průzkumníka, které uživatelé uvidí spolu s jejich diagramu modelu.

 ![Vygenerovaný Průzkumník DSL](../modeling/media/music_explorer.png)

 V Průzkumníku ukazuje všechny prvky v modelu, včetně těch, u kterých nebyly definovány žádné obrazce. Ukazuje elementů a vztahů obsažení, ale neodkazuje vztahy.

 Zobrazit hodnoty vlastnosti domény elementu, uživatel vybere elementu, buď v diagramu modelu, nebo v Průzkumníku modelů a otevře v okně Vlastnosti. Zobrazí všechny domény vlastnosti, včetně těch, které se zobrazí v diagramu. V tomto příkladu skladeb má název a rozšířením podle tematických, ale pouze hodnota názvu se zobrazí v diagramu.

## <a name="reference-relationships"></a>Referenční stavy
 Referenční vztah představuje jakýkoli druh vztahu, který není vkládání.

 Referenční stavy se obvykle zobrazují v diagramu jako konektory mezi tvary.

 V reprezentaci XML pro model, je reprezentována pomocí odkazu mezi dvěma prvky *monikery.* To znamená, že jsou tyto monikery názvy, které jedinečně identifikují každý prvek v modelu. Uzel XML pro každý prvek modelu obsahuje uzel, který určuje název relace a zástupného názvu elementu.

## <a name="roles"></a>Role
 Každý doménového vztahu má dvě role, zdrojová role a cílová role.

 Na následujícím obrázku, řádek mezi **vydavatele** doménové třídy a **PublisherCatalog** doménového vztahu je zdrojové role. Řádek mezi doménový vztah a **alba** doménové třídy je cílová role.

 ![Role a vlastnosti.](../modeling/media/propertycode.png)

 Názvy přidružené k relaci jsou zvlášť důležité při psaní kódu programu, který prochází skrz modelu. Například při sestavování řešení DSL generované třídy vydavatel má vlastnost katalog, který je kolekce alb. Třída alba má vlastnost Publisher, který je jedna instance třídy vydavatele.

 Při vytvoření relace v definici DSL názvy vlastností a vztahů jsou uvedeny výchozí hodnoty. Můžete je však změnit.

## <a name="multiplicities"></a>Násobnosti
 Násobnosti zadejte počet prvků, může mít stejný atribut role v doménového vztahu. V příkladu, nula to-many (0..\*) nastavení násobnosti **katalogu** role určuje, že všechny instance **vydavatele** doménová třída může mít tolik  **PublisherCatalog** vztah odkazuje, jak si ho.

 Konfigurace násobnosti atributu role elementu tak, že zadáte v diagramu nebo úpravou `Multiplicity` vlastnost **vlastnosti** okno. Následující tabulka popisuje nastavení pro tuto vlastnost.

|Násobnost typu|Popis|
|-|-|
|0.. * (nula n)|Každá instance třídy domény může mít více instancí relace nebo žádné instance vztahu.|
|0..1 (nula do jednoho)|Každá instance třídy domény může obsahovat více než jednu instanci relace nebo žádné instance vztahu.|
|1..1 (jeden)|Každá instance doménová třída může mít jednu instanci relace. Nelze vytvořit více než jednu instanci této relace z libovolné instance třídy role. Pokud je povoleno ověření, se zobrazí chyba ověření při jakékoli instance třídy role nemá žádná instance vztahu.|
|1.. * (jeden na mnoho)|Každá instance třídy na roli, která má tento násobnost může mít více instancí relace a každá instance musí mít alespoň jednu instanci relace. Pokud je povoleno ověření, se zobrazí chyba ověření při jakékoli instance třídy role nemá žádná instance vztahu.|

## <a name="domain-relationships-as-classes"></a>Doménové vztahy jako třídy
 Odkaz je vyjádřena v Store jako instance LinkElement, což je odvozené třídy ModelElement. Tyto vlastnosti můžete definovat v diagramu modelu domény v doménové vztahy.

 Lze také nastavit vztah zdroj nebo cíl jiné vztahy. V diagramu modelu domény, klikněte pravým tlačítkem na vztah domény a pak klikněte na **zobrazit jako třída**. Do pole další třídy se zobrazí. Vztahy pak můžete připojit k němu.

 Částečně prostřednictvím dědičnosti, můžete definovat vztah, stejně jako s doménovými třídami. Vyberte odvozený vztah a nastavte **základnímu vztahu** v okně Vlastnosti.

 Odvozený vztah se specializuje na jejím základním vztahem. Doména třídy, kterou it, které odkazy by měl být odvozen od nebo stejná jako propojenou relací základní třídy. V modelu je vytvořen odkaz odvozený vztah, je instance odvozené a základních vztahů. V kódu programu můžete přejít na protilehlé straně odkazu pomocí vlastnosti vygeneruje základní nebo odvozené třídy.

## <a name="see-also"></a>Viz také

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
