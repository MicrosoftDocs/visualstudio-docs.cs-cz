---
title: Porozumění modelům, třídám a vztahům | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5426c6f8e9c4a932430a0c3bd3df6d98400c3562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659548"
---
# <a name="understanding-models-classes-and-relationships"></a>Porozumění modelům, třídám a vztahům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jazyk specifický pro doménu (DSL) je definován souborem definice DSL společně s jakýmkoli vlastním programovým kódem, který můžete napsat. Většina kódu programu v řešení DSL je vygenerována z tohoto souboru.

 Toto téma vysvětluje hlavní funkce definice DSL.

## <a name="the-dsl-definition"></a>Definice DSL
 Po otevření `Dsl\DslDefinition.dsl` se okno bude [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podobat následujícímu obrázku.

 ![Návrhář DSL](../modeling/media/dsl-designer.png "dsl_designer")

 Nejdůležitější informace v definici DSL se zobrazí v diagramu definice DSL. Další informace, které jsou také součástí DslDefinition. DSL, se zobrazí v Průzkumníku DSL, která se obvykle zobrazuje na straně diagramu. Pracujete s diagramem pro nejčastější úlohy a s Průzkumníkem DSL pro pokročilejší přizpůsobení.

 Diagram definice DSL zobrazuje doménové třídy, které definují prvky modelu, a vztahy, které definují propojení mezi prvky modelu. Zobrazuje také obrazce a konektory, které jsou použity k zobrazení prvků modelu uživateli.

 ![Návrhář DSL s plaveckou dráhou](../modeling/media/dsl-desinger.png "dsl_desinger")

 Když vyberete položku v definici DSL buď v diagramu, nebo v Průzkumníku DSL, informace o ní se zobrazí v okno Vlastnosti. V okně Podrobnosti DSL se můžou zobrazit další informace.

### <a name="models-are-instances-of-dsls"></a>Modely jsou instance DSL
 *Model* je instance vaší DSL vytvořeného uživatelem. Model obsahuje prvky modelu, které jsou instancemi tříd domény, které definujete, a propojení mezi prvky, které jsou instancemi doménových vztahů, které definujete. Model může mít také obrazce a spojnice, které zobrazují prvky modelu a odkazy v diagramu. Definice DSL obsahuje třídy tvarů, třídy konektorů a třídu pro diagram.

 Definice DSL se také označuje jako *doménový model*. Definice nebo doménový model DSL je reprezentace jazyka specifického pro doménu, zatímco model je instance modulu runtime pro jazykově specifické domény.

## <a name="domain-classes-define-model-elements"></a>Třídy domény definují prvky modelu
 Doménové třídy slouží k vytvoření různých prvků v doméně a vztahy domény jsou propojením mezi prvky. Jedná se o reprezentace prvků a odkazů, které budou vytvářet instance uživatelů v jazyce specifickém pro návrh při vytváření jejich modelů.

 Tento obrázek znázorňuje model, který byl vytvořen uživatelem knihovny hudby DSL. Hudební alba jsou reprezentovaná poli obsahujícími seznamy písní. Interprety jsou reprezentovány pomocí kulatého rohového pole a jsou propojeny s alba, ke kterým přispěli.

 ![Model instance generované DSL](../modeling/media/music-instance.png "Music_Instance")

 Definice DSL odděluje dvě aspekty. Vzhled prvků modelu v diagramu modelu je definován pomocí tříd tvarů a tříd konektorů. Informace přenesené v modelu jsou definované pomocí doménových tříd a doménových vztahů.

 Následující ilustrace znázorňuje třídy domény a vztahy v definici DSL knihovny hudby.

 ![Vztahy vložení a odkazování](../modeling/media/music-classes.png "Music_Classes")

 Ilustrace znázorňuje čtyři doménové třídy: hudbu, album, interpret a skladba. Třídy domény definují vlastnosti domény, jako je název, název a tak dále. V modelu instance jsou hodnoty některých z těchto vlastností zobrazeny v diagramu.

 Mezi třídami jsou doménové vztahy: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs a ArtistAppearedOnAlbums. Relace mají násobnost, například 1.. 1, 0.. *. Například každá skladba musí být v relaci k přesně jednomu albu prostřednictvím vztahu AlbumHasSongs. Každé album může mít libovolný počet písní.

### <a name="rearranging-the-dsl-definition-diagram"></a>Změna uspořádání diagramu definice DSL
 Všimněte si, že se doménová třída může několikrát zobrazit v diagramu definice DSL, jako album na tomto obrázku. K dispozici je vždy jedno hlavní zobrazení a může existovat několik zobrazení *odkazů* .

 Chcete-li změnit uspořádání diagramu definice DSL, můžete:

- Proměňte hlavní a referenční zobrazení pomocí příkazů **přenést strom zde** a **rozdělit stromové** příkazy. Kliknutím pravým tlačítkem myši na jednu doménovou třídu zobrazíte tyto příkazy.

- Přeuspořádat třídy domény a třídy tvarů stisknutím kombinace kláves Ctrl + šipka nahoru a Ctrl + šipka dolů.

- Sbalte nebo rozbalte třídy pomocí ikony v pravém horním rohu jednotlivých tvarů.

- Rozbalíte části stromu kliknutím na znaménko mínus (-) v dolní části doménové třídy.

## <a name="inheritance"></a>Dědičnost
 Třídy domény lze definovat pomocí dědičnosti. Chcete-li vytvořit odvození dědičnosti, klikněte na nástroj dědičnost, klikněte na odvozenou třídu a potom klikněte na základní třídu. Prvek modelu má všechny vlastnosti, které jsou definovány na své vlastní doménové třídy, spolu se všemi vlastnostmi děděnými ze základní třídy. Zároveň zdědí své role v relacích.

 Dědičnost se dá použít taky mezi relacemi, obrazci a konektory. Dědičnost musí zůstat ve stejné skupině. Obrazec nemůže dědit z doménové třídy.

## <a name="domain-relationships"></a>Doménové vztahy
 Prvky modelu mohou být propojeny pomocí vztahů. Odkazy jsou vždycky binární; propojí přesně dva prvky. Libovolný element ale může mít mnoho odkazů na jiné objekty a může dokonce být více než jedno propojení mezi stejnou dvojicí prvků.

 Stejně jako můžete definovat různé třídy prvků, můžete definovat různé třídy odkazů. Třída odkazu se nazývá *doménový vztah*. Doménový vztah určuje, ke kterým třídám prvků se může připojit. Každý konec relace se nazývá *role*a doménová relace definuje názvy pro tyto dvě role a také pro samotný vztah.

 Existují dva typy doménových vztahů: vkládání vztahů a referenčních vztahů. V diagramu definice DSL mají relace vložení plné čáry pro každou roli a referenční relace mají přerušované čáry.

### <a name="embedding-relationships"></a>Relace vložení
 Každý prvek v modelu, s výjimkou jeho kořenu, je cílem jednoho odkazu vložení. Proto celý model tvoří jednu stromovou strukturu odkazů vložení. Vztah vložení představuje omezení nebo vlastnictví. Dva prvky modelu, které jsou spojeny tímto způsobem, jsou označovány také jako nadřazené a podřízené. Podřízená položka je označována jako vložená v nadřazeném prvku.

 Odkazy na vložení nejsou obvykle zobrazeny explicitně jako spojnice v diagramu. Místo toho jsou obvykle reprezentované zahrnutím. Kořen modelu je reprezentován diagramem a prvky, které jsou v něm vloženy, jsou zobrazeny jako obrazce v diagramu.

 V příkladu má hudba pro kořenovou třídu MusicHasAlbums vztah vložení do alba, který má vložení AlbumHasSongs do Song. Skladby se zobrazují jako položky v seznamu uvnitř každého alba. Hudba také obsahuje vložení MusicHasArtists do třídy umělec, jejíž instance se také zobrazí jako tvary v diagramu.

 Ve výchozím nastavení jsou vložené prvky automaticky odstraněny při odstranění jejich nadřazených prvků.

 Když je model uložen do souboru ve formátu XML, vložené prvky jsou vnořené uvnitř svých nadřazených prvků, pokud jste neupravili serializaci.

> [!NOTE]
> Vložení není stejné jako dědičnost. Podřízené položky v relaci vložení nedědí vlastnosti nadřazené položky. Vložení je typ propojení mezi prvky modelu. Dědičnost je vztah mezi třídami a nevytváří propojení mezi prvky modelu.

### <a name="embedding-rules"></a>Pravidla vložení
 Každý prvek v modelu instance musí být cílem přesně jednoho odkazu vložení, s výjimkou kořene modelu.

 Proto každá neabstraktní doménová třída, kromě kořenové třídy, musí být cílem alespoň jedné relace vložení, nebo musí dědit vložení ze základní třídy. Třída může být cílem dvou nebo více vložení, ale její prvky modelu instance mohou mít pouze jednu nadřazenou položku v jednom okamžiku. Násobnost z cíle na zdroj musí být 0.. 1 nebo 1.. 1.

### <a name="the-explorer-displays-the-embedding-tree"></a>V Průzkumníkovi se zobrazí strom pro vložení
 Definice DSL také vytvoří Průzkumníka, který se uživatelům zobrazí společně s diagramem modelu.

 ![Vygenerovaný Průzkumník DSL](../modeling/media/music-explorer.png "Music_Explorer")

 V Průzkumníkovi se zobrazí všechny prvky v modelu, i ty, pro které nejsou definovány žádné tvary. Zobrazuje elementy a vkládání vztahů, ale ne referenčních vztahů.

 Chcete-li zobrazit hodnoty vlastností domény elementu, uživatel vybere prvek, buď v diagramu modelu, nebo v Průzkumníku modelů a otevře okno Vlastnosti. Zobrazí se všechny vlastnosti domény, včetně těch, které nejsou v diagramu zobrazené. V příkladu má každá skladba název i Žánr, ale v diagramu je zobrazená jenom hodnota názvu.

## <a name="reference-relationships"></a>Referenční relace
 Vztah odkazu představuje jakýkoli druh relace, která není vložena.

 Referenční relace se obvykle zobrazují v diagramu jako spojnice mezi obrazci.

 V jazyce XML reprezentace modelu je odkaz na odkaz mezi dvěma prvky reprezentován pomocí *monikerů.* To znamená, že monikery jsou názvy, které jednoznačně identifikují každý prvek v modelu. Uzel XML pro každý prvek modelu obsahuje uzel, který určuje název vztahu a moniker druhého prvku.

## <a name="roles"></a>Role
 Každý doménový vztah má dvě role, zdrojovou roli a cílovou roli.

 Na následujícím obrázku je čára mezi třídou domény **vydavatele** a doménovou rolí **PublisherCatalog** zdrojová role. Řádkem mezi doménovým vztahem a doménovou třídou **alba** je cílová role.

 ![Role a vlastnosti.](../modeling/media/propertycode.png "PropertyCode")

 Názvy přidružené k relaci jsou obzvláště důležité při psaní kódu programu, který projde modelem. Například při sestavování řešení DSL má Vydavatel generovaných tříd katalog vlastností, který je kolekcí alb. Album třídy má vydavatele vlastností, který je jedinou instancí třídy Vydavatel.

 Když vytvoříte relaci v definici DSL, názvy vlastností a vztahů jsou zadané výchozí hodnoty. Můžete je ale změnit.

## <a name="multiplicities"></a>Mnohočetnostmi
 Násobnosti určují, kolik prvků může mít stejnou roli v relaci domény. V příkladu má nastavení násobnosti nula (0.. \* ) v roli **Catalog** , že jakákoli instance třídy domény **vydavatele** může mít tolik odkazů na **PublisherCatalog** vztahů, jak je chcete dát.

 Nastavte násobnost role buď zadáním v diagramu, nebo úpravou `Multiplicity` vlastnosti v okně **vlastnosti** . Následující tabulka popisuje nastavení pro tuto vlastnost.

|Typ násobnosti|Popis|
|-----------------------|-----------------|
|0.. * (nula až mnoho)|Každá instance doménové třídy může mít více instancí relace nebo žádné instance relace.|
|0.. 1 (nula až jedna)|Každá instance doménové třídy nemůže mít více než jednu instanci relace nebo žádné instance relace.|
|1.. 1 (jeden)|Každá instance doménové třídy může mít jednu instanci relace. Z jakékoli instance třídy role nemůžete vytvořit více než jednu instanci této relace. Pokud je povoleno ověřování, zobrazí se chyba ověření v případě, že jakákoli instance třídy role nemá žádnou instanci relace.|
|1.. * (jedna až mnoho)|Každá instance třídy v roli, která má tuto násobnost, může mít více instancí relace a každá instance musí mít alespoň jednu instanci vztahu. Pokud je povoleno ověřování, zobrazí se chyba ověření v případě, že jakákoli instance třídy role nemá žádnou instanci relace.|

## <a name="domain-relationships-as-classes"></a>Doménové vztahy jako třídy
 Odkaz je reprezentován ve Storu jako instance LinkElement, která je odvozenou třídou třídy ModelElement. Tyto vlastnosti můžete definovat v diagramu doménového modelu u doménových vztahů.

 Můžete také vytvořit vztah mezi zdrojem a cílem jiných vztahů. V diagramu doménového modelu klikněte pravým tlačítkem na doménový vztah a pak klikněte na **Zobrazit jako třídu**. Zobrazí se další pole třídy. K němu pak můžete připojit relace.

 Relaci můžete definovat částečně děděním, stejně jako u doménových tříd. Vyberte odvozený vztah a nastavte **základní vztah** v okno Vlastnosti.

 Odvozený vztah se specializuje na základní vztah. Třídy domény, na které odkazuje, by měly být odvozeny od nebo stejné jako třídy propojené základní relací. Je-li v modelu vytvořen odkaz odvozeného vztahu, jedná se o instanci odvozeného i základního vztahu. V programovém kódu můžete přejít na opačný konec odkazu pomocí vlastností generovaných buď základní třídou, nebo odvozenou třídou.

## <a name="see-also"></a>Viz také
 [Doménové vztahy ve vygenerovaném rozhraní API](../misc/domain-relationships-in-the-generated-api.md) [nástroje DSL Glosář](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
