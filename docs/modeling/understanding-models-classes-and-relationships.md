---
title: Porozumění modelům, třídám a vztahům
description: Přečtěte si, jak je definovaný jazyk domény (DSL) definovaný souborem definice DSL a že většina kódu programu v řešení DSL se z tohoto souboru vygeneruje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b086f21b466863c3498ce15c15f7077b358c6d39
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388617"
---
# <a name="understanding-models-classes-and-relationships"></a>Porozumění modelům, třídám a vztahům
Jazyk specifický pro doménu (DSL) je definován souborem definice DSL společně s jakýmkoli vlastním programovým kódem, který můžete napsat. Většina kódu programu v řešení DSL je vygenerována z tohoto souboru.

 Toto téma vysvětluje hlavní funkce definice DSL.

## <a name="the-dsl-definition"></a>Definice DSL
 Po otevření `Dsl\DslDefinition.dsl` se okno aplikace Visual Studio podobá následujícímu obrázku.

 ![Návrhář DSL](../modeling/media/dsl_designer.png)

 Nejdůležitější informace v definici DSL se zobrazí v diagramu definice DSL. Další informace, které jsou také součástí DslDefinition. DSL, se zobrazí v Průzkumníku DSL, která se obvykle zobrazuje na straně diagramu. Pracujete s diagramem pro nejčastější úlohy a s Průzkumníkem DSL pro pokročilejší přizpůsobení.

 Diagram definice DSL zobrazuje doménové třídy, které definují prvky modelu, a vztahy, které definují propojení mezi prvky modelu. Zobrazuje také obrazce a konektory, které jsou použity k zobrazení prvků modelu uživateli.

 ![Návrhář DSL s plaveckou dráhou](../modeling/media/dsl_desinger.png)

 Když vyberete položku v definici DSL buď v diagramu, nebo v Průzkumníku DSL, informace o ní se zobrazí v okno Vlastnosti. V okně Podrobnosti DSL se můžou zobrazit další informace.

### <a name="models-are-instances-of-dsls"></a>Modely jsou instance DSL
 *Model* je instance vaší DSL vytvořeného uživatelem. Model obsahuje prvky modelu, které jsou instancemi tříd domény, které definujete, a propojení mezi prvky, které jsou instancemi doménových vztahů, které definujete. Model může mít také obrazce a spojnice, které zobrazují prvky modelu a odkazy v diagramu. Definice DSL obsahuje třídy tvarů, třídy konektorů a třídu pro diagram.

 Definice DSL se také označuje jako *doménový model*. Definice nebo doménový model DSL je reprezentace jazyka specifického pro doménu, zatímco model je instance modulu runtime pro jazykově specifické domény.

## <a name="domain-classes-define-model-elements"></a>Třídy domény definují prvky modelu
 Doménové třídy slouží k vytvoření různých prvků v doméně a vztahy domény jsou propojením mezi prvky. Jedná se o reprezentace prvků a odkazů, které budou vytvářet instance uživatelů v jazyce specifickém pro návrh při vytváření jejich modelů.

 Tento obrázek znázorňuje model, který byl vytvořen uživatelem knihovny hudby DSL. Hudební alba jsou reprezentovaná poli obsahujícími seznamy písní. Interprety jsou reprezentovány pomocí kulatého rohového pole a jsou propojeny s alba, ke kterým přispěli.

 ![Model instance generované DSL](../modeling/media/music_instance.png)

 Definice DSL odděluje dvě aspekty. Vzhled prvků modelu v diagramu modelu je definován pomocí tříd tvarů a tříd konektorů. Informace přenesené v modelu jsou definované pomocí doménových tříd a doménových vztahů.

 Následující ilustrace znázorňuje třídy domény a vztahy v definici DSL knihovny hudby.

 ![Vztahy vložení a odkazování](../modeling/media/music_classes.png)

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

 Stejně jako můžete definovat různé třídy prvků, můžete definovat různé třídy odkazů. Třída odkazu se nazývá *doménový vztah*. Doménový vztah určuje, ke kterým třídám prvků se může připojit. Každý konec relace se nazývá *role* a doménová relace definuje názvy pro tyto dvě role a také pro samotný vztah.

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

 ![Vygenerovaný Průzkumník DSL](../modeling/media/music_explorer.png)

 V Průzkumníkovi se zobrazí všechny prvky v modelu, i ty, pro které nejsou definovány žádné tvary. Zobrazuje elementy a vkládání vztahů, ale ne referenčních vztahů.

 Chcete-li zobrazit hodnoty vlastností domény elementu, uživatel vybere prvek, buď v diagramu modelu, nebo v Průzkumníku modelů a otevře okno Vlastnosti. Zobrazí se všechny vlastnosti domény, včetně těch, které nejsou v diagramu zobrazené. V tomto příkladu má každá skladba název i žánr, ale na diagramu se zobrazuje jenom hodnota Názvu.

## <a name="reference-relationships"></a>Referenční relace
 Referenční relace představuje jakýkoli druh relace, který se nevkládá.

 Relace odkazů se obvykle zobrazují v diagramu jako konektory mezi tvary.

 V reprezentaci XML modelu je odkazové propojení mezi dvěma prvky reprezentováno pomocí *monikerů.* To znamená, že monikery jsou názvy, které jednoznačně identifikují každý prvek v modelu. Uzel XML pro každý prvek modelu obsahuje uzel, který určuje název relace a moniker druhého prvku.

## <a name="roles"></a>Role
 Každý vztah domény má dvě role, zdrojovou a cílovou roli.

 Na následujícím obrázku je zdrojovou rolí řádek mezi doménovou třídou Vydavatel a doménou **PublisherCatalog.**  Čára mezi doménovou vztahem a doménovou třídou **Vlastnost** je cílovou rolí.

 ![Role a vlastnosti.](../modeling/media/propertycode.png)

 Názvy přidružené k relaci jsou zvláště důležité, když píšete programový kód, který prochová model. Když například sestavíte řešení DSL, vygenerovaná třída Publisher má vlastnost Catalog, která je kolekcí katalogu Nachytá. Třída Má vlastnost Publisher, která je jedinou instancí třídy Publisher.

 Když vytvoříte relaci v definici DSL, mají názvy vlastností a vztahů výchozí hodnoty. Můžete je ale změnit.

## <a name="multiplicities"></a>Násobení
 Násobnosti určují, kolik prvků může mít stejnou roli v relaci domény. Nastavení násobnosti 0:N (0.. ) u role katalogu v tomto příkladu určuje, že každá instance třídy domény Vydavatel může mít libovolný počet odkazů na vztahy \* **PublisherCatalog,** kolik  chcete. 

 Násobnost role můžete nakonfigurovat buď zadáním do diagramu, nebo úpravou `Multiplicity` vlastnosti v **okně** Vlastnosti. Následující tabulka popisuje nastavení této vlastnosti.

|Typ násobnosti|Description|
|-|-|
|0..* (nula k mnoha)|Každá instance třídy domény může mít více instancí vztahu nebo žádné instance vztahu.|
|0..1 (nula k jedné)|Každá instance třídy domény nemůže mít více než jednu instanci relace nebo žádné instance relace.|
|1..1 (jeden)|Každá instance třídy domény může mít jednu instanci vztahu. Z jakékoli instance třídy role nelze vytvořit více než jednu instanci tohoto vztahu. Pokud je povolené ověřování, zobrazí se chyba ověření, když kterákoli instance třídy role nemá žádnou instanci relace.|
|1..* (1:M)|Každá instance třídy v roli, která má tuto násobnost, může mít více instancí relace a každá instance musí mít alespoň jednu instanci relace. Pokud je povolené ověřování, zobrazí se chyba ověření, když kterákoli instance třídy role nemá žádnou instanci relace.|

## <a name="domain-relationships-as-classes"></a>Vztahy mezi doménami jako třídy
 Odkaz je reprezentován v Store jako instance LinkElement, což je odvozená třída ModeluElement. Tyto vlastnosti můžete definovat v diagramu doménového modelu u vztahů mezi doménami.

 Relaci můžete také nastavit jako zdroj nebo cíl jiných relací. V diagramu modelu domény klikněte pravým tlačítkem na vztah domény a pak klikněte na **Zobrazit jako třídu**. Zobrazí se další pole třídy. Pak k ní můžete připojit relace.

 Vztah můžete definovat částečně dědičností, stejně jako u tříd domén. Vyberte odvozenou relaci a **nastavte základní relaci** v okno Vlastnosti.

 Odvozená relace se specializuje na svou základní relaci. Třídy domény, které odkazuje, by měly být odvozeny z třídy nebo stejné jako třídy propojené základní vztah. Když je v modelu vytvořeno propojení odvozené relace, jedná se o instanci odvozených i základních relací. V kódu programu můžete přejít na opačný konec odkazu pomocí vlastností generovaných buď základní třídou, nebo odvozenou třídou.

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))