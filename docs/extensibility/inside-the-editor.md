---
title: Práce v editoru
description: Seznamte se s podsystémy a funkcemi editoru. Můžete roztáhnout funkce editoru sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bd45bb0a47de7283d75c083edc46b6fc38fe7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079199"
---
# <a name="inside-the-editor"></a>Uvnitř editoru

Editor se skládá z několika různých subsystémů, které jsou navrženy tak, aby model textu editoru byly oddělené od zobrazení textu a uživatelského rozhraní.

Tyto části popisují různé aspekty editoru:

- [Přehled subsystémů](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Textový model](../extensibility/inside-the-editor.md#the-text-model)

- [Textové zobrazení](../extensibility/inside-the-editor.md#the-text-view)

Tyto části popisují funkce editoru:

- [Značky a klasifikátory](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Grafických doplňků](../extensibility/inside-the-editor.md#adornments)

- [Projekce](../extensibility/inside-the-editor.md#projection)

- [Sbalování](../extensibility/inside-the-editor.md#outlining)

- [Vazby myši](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operace editoru](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Přehled subsystémů

### <a name="text-model-subsystem"></a>Podsystém textového modelu

Subsystém textový model zodpovídá za to, že představuje text a povoluje jeho manipulaci. Podsystém textový model obsahuje <xref:Microsoft.VisualStudio.Text.ITextBuffer> rozhraní, které popisuje posloupnost znaků, které se mají zobrazit v editoru. Tento text se dá upravovat, sledovat a jinak manipulovat mnoha způsoby. Textový model také poskytuje typy pro následující aspekty:

- Služba, která přidruží text k souborům a spravuje jejich čtení a zápis v systému souborů.

- Rozdílová služba, která najde minimální rozdíly mezi dvěma sekvencemi objektů.

- Systém pro popis textu ve vyrovnávací paměti v souvislosti s podmnožinami textu v jiných vyrovnávacích pamětech.

Subsystém textový model není v konceptech uživatelského rozhraní (UI) volné. Například není zodpovědná za formátování textu nebo rozložení textu a nemá žádné znalosti vizuálních doplňků, které mohou být spojeny s textem.

Veřejné typy subsystému textového modelu jsou obsaženy v *Microsoft.VisualStudio.Text.Data.dll* a *Microsoft.VisualStudio.CoreUtility.dll*, které závisejí pouze na .NET Framework základní třídy knihovny a Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Podsystém zobrazení textu

Subsystém zobrazení textu je zodpovědný za formátování a zobrazení textu. Typy v tomto subsystému jsou rozděleny do dvou vrstev v závislosti na tom, zda typy spoléhají na Windows Presentation Foundation (WPF). Nejdůležitější typy jsou <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , které ovládají sadu textových řádků, které se mají zobrazit, a také blikající kurzor, výběr a zařízení pro další text pomocí prvků uživatelského rozhraní WPF. Tento podsystém také poskytuje okraje kolem oblasti zobrazení textu. Tyto okraje lze rozšířit a mohou obsahovat různé druhy obsahu a vizuálních efektů. Příklady okrajů jsou zobrazení a posuvníky čísla řádku.

Veřejné typy subsystému zobrazení textu jsou obsaženy v *Microsoft.VisualStudio.Text.UI.dll* a *Microsoft.VisualStudio.Text.UI.Wpf.dll*. První sestavení obsahuje elementy nezávislé na platformě a druhý obsahuje prvky specifické pro WPF.

### <a name="classification-subsystem"></a>Subsystém klasifikace

Subsystém klasifikace zodpovídá za určení vlastností písma pro text. Třídění rozdělí text na jiné třídy, například "klíčové slovo" nebo "comment". Mapa formátu klasifikace má tyto třídy v těchto třídách na skutečné vlastnosti písma, například "Blue Consolas 10 PT". Tyto informace používá zobrazení textu při formátování a vykreslování textu. Označování, které je podrobněji popsáno dále v tomto tématu, umožňuje, aby data byla přidružena k rozsahům textu.

Veřejné typy subsystému klasifikace jsou obsaženy v Microsoft.VisualStudio.Text.Logic.dll a pracují s vizuálními aspekty klasifikace, které jsou obsaženy v Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Provozní subsystém

Provozní subsystém definuje chování editoru. Poskytuje implementaci pro příkazy editoru sady Visual Studio a systém vrácení zpět.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bližší pohled na textový model a textové zobrazení

### <a name="the-text-model"></a>Textový model

Podsystém textový model se skládá z různých seskupení textových typů. Mezi ně patří textová vyrovnávací paměť, snímky textu a text.

#### <a name="text-buffers-and-text-snapshots"></a>Textové vyrovnávací paměti a snímky textu

<xref:Microsoft.VisualStudio.Text.ITextBuffer>Rozhraní představuje sekvenci znaků Unicode, které jsou zakódovány pomocí kódování UTF-16, což je kódování používané `String` typem v .NET Framework. Textová vyrovnávací paměť může být trvalá jako dokument systému souborů, ale není to nutné.

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Slouží k vytvoření prázdné textové vyrovnávací paměti nebo textové vyrovnávací paměti, která je inicializována z řetězce nebo z <xref:System.IO.TextReader> . Velikost textové vyrovnávací paměti může být uložena v systému souborů jako <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Jakékoli vlákno může upravovat textovou vyrovnávací paměť, dokud vlákno převezme vlastnictví textové vyrovnávací paměti voláním <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Potom může provádět úpravy pouze v tomto vlákně.

Textová vyrovnávací paměť může během své životnosti procházet mnoha verzemi. Nová verze je vygenerována pokaždé, když je upravena vyrovnávací paměť, a neměnná <xref:Microsoft.VisualStudio.Text.ITextSnapshot> představuje obsah této verze vyrovnávací paměti. Vzhledem k tomu, že se snímky textu nemění, můžete získat přístup k snímku textu v jakémkoli vlákně bez omezení, a to i v případě, že je velikost vyrovnávací paměti, kterou představuje, nadále měnit.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Snímky textu a řádky snímků textu

Můžete zobrazit obsah snímku textu jako posloupnost znaků nebo posloupnosti řádků. Znaky a řádky jsou indexovány počínaje nulou. Prázdný snímek textu obsahuje nula znaků a jeden prázdný řádek. Řádek je oddělený jakoukoli platnou posloupností znaků zalomení řádku Unicode nebo na začátku nebo konci vyrovnávací paměti. Znaky zalomení řádku jsou explicitně reprezentované ve snímku textu a zalomení řádků v textovém snímku nemusí být stejné.

> [!NOTE]
> Další informace o znacích zalomení řádku v editoru sady Visual Studio naleznete v tématu [kódování a zalomení řádků](../ide/encodings-and-line-breaks.md).

Řádek textu je reprezentován <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objektem, který lze získat z textového snímku pro konkrétní číslo řádku nebo pro konkrétní pozici znaku.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Body snapshotpoint, SnapshotSpans a NormalizedSnapshotSpanCollections

<xref:Microsoft.VisualStudio.Text.SnapshotPoint>Představuje pozici znaku ve snímku. Pozice je zaručena, že leží mezi nulou a délkou snímku. <xref:Microsoft.VisualStudio.Text.SnapshotSpan>Představuje rozsah textu ve snímku. Koncová pozice je zaručena, že leží mezi nulou a délkou snímku. Sestává ze <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> sady <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objektů ze stejného snímku.

#### <a name="spans-and-normalizedspancollections"></a>Rozsahy a NormalizedSpanCollections

<xref:Microsoft.VisualStudio.Text.Span>Představuje interval, který lze použít na rozsah textu v textovém snímku. Pozice snímků jsou založené na nule, takže rozsahy můžou začínat na libovolné pozici, včetně nuly. `End`Vlastnost rozsahu je rovna součtu jeho vlastnosti `Start` a jeho `Length` Vlastnosti. `Span`Nezahrnuje znak, který je indexován `End` vlastností. Například rozpětí, které má Start = 5 a length = 3, má end = 8 a obsahuje znaky na pozici 5, 6 a 7. Zápis pro tento rozsah je [5.. 8).

Dva jsou rozloženy mezi sebou, pokud mají všechny pozice společné, včetně koncové pozice. Proto průnik [3, 5) a [2, 7) je [3, 5) a průsečík [3, 5) a [5, 7) je [5, 5). (Všimněte si, že [5, 5) je prázdný rozsah.)

Dva rozsahy se překrývají, pokud mají společné pozice, s výjimkou koncové pozice. Prázdné rozpětí se nikdy nepřekrývá s žádným jiným rozsahem a překrytí dvou rozsahů není nikdy prázdné.

<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>Je seznam rozsahů v pořadí počátečních vlastností rozsahů. V seznamu se sloučí překrývající nebo sousedící rozsahy. Například pro sadu rozsahů [5.. 9), [0.. 1), [3.. 6) a [9.. 10) je normalizovaný Seznam rozsahů [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Oznámení o změnách ITextEdit, TextVersion a text

Obsah vyrovnávací paměti textu lze změnit pomocí <xref:Microsoft.VisualStudio.Text.ITextEdit> objektu. Vytvoření takového objektu (pomocí jedné z `CreateEdit()` metod <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) spustí textovou transakci, která se skládá z textových úprav. Každá úprava je náhradou rozsahu textu ve vyrovnávací paměti pomocí řetězce. Souřadnice a obsah každé úpravy jsou vyjádřeny relativně ke snímku vyrovnávací paměti při spuštění transakce. <xref:Microsoft.VisualStudio.Text.ITextEdit>Objekt upravuje souřadnice úprav, které jsou ovlivněny jinými úpravami ve stejné transakci.

Můžete například zvážit textovou vyrovnávací paměť, která obsahuje tento řetězec:

```
abcdefghij
```

Použijte transakci, která obsahuje dvě úpravy, jedno úpravy, které nahradí rozpětí v [2.. 4) pomocí znaku `X` a druhého úprav, který nahradí rozpětí v [6.. 9) pomocí znaku `Y` . Výsledkem je tato vyrovnávací paměť:

```
abXefYj
```

Souřadnice pro druhou úpravu byly vypočítány s ohledem na obsah vyrovnávací paměti na začátku transakce před použitím první úpravy.

Změny vyrovnávací paměti se projeví po <xref:Microsoft.VisualStudio.Text.ITextEdit> potvrzení objektu voláním jeho `Apply()` metody. Pokud existovala aspoň jedna neprázdná úprava, vytvoří se nový, vytvoří se <xref:Microsoft.VisualStudio.Text.ITextVersion> nový <xref:Microsoft.VisualStudio.Text.ITextSnapshot> a `Changed` vyvolá se jedna událost. Každá textová verze má jiný textový snímek. Textový snímek představuje kompletní stav textové vyrovnávací paměti po úpravě transakce, ale textová verze popisuje pouze změny z jednoho snímku na další. Obecně platí, že textové snímky mají být použity jednou a následně zahozeny, zatímco textové verze musí být pro určitou dobu aktivní.

Textová verze obsahuje <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . V této kolekci jsou popsány změny, které při aplikování na snímek vydávají následující snímek. Každý <xref:Microsoft.VisualStudio.Text.ITextChange> v kolekci obsahuje pozici znaku změny, nahrazeného řetězce a nahrazujícího řetězce. Nahrazený řetězec je prázdný pro základní vložení a náhradní řetězec je prázdný pro základní odstranění. Normalizovaná kolekce je vždy `null` pro nejnovější verzi textové vyrovnávací paměti.

<xref:Microsoft.VisualStudio.Text.ITextEdit>Pro vyrovnávací paměť pro text může být vytvořena instance pouze jednoho objektu a všechny úpravy textu musí být provedeny ve vlákně, které vlastní textovou vyrovnávací paměť (pokud bylo požadováno vlastnictví). Úpravy textu lze odvolat voláním její `Cancel` metody nebo její `Dispose` metody.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> také poskytuje `Insert()` `Delete()` metody, a `Replace()` , které se podobají těm, které jsou nalezeny na <xref:Microsoft.VisualStudio.Text.ITextEdit> rozhraní. Volání mají stejný účinek jako vytvoření <xref:Microsoft.VisualStudio.Text.ITextEdit> objektu, provedení podobného volání a následné použití Edit.

#### <a name="tracking-points-and-tracking-spans"></a>Sledovací body a rozsahy sledování

<xref:Microsoft.VisualStudio.Text.ITrackingPoint>Představuje pozici znaku v textové vyrovnávací paměti. Pokud je vyrovnávací paměť upravována způsobem, který způsobí, že se pozice znaku posune, posune se s ním bod sledování. Například pokud bod sledování odkazuje na pozici 10 ve vyrovnávací paměti a na začátek vyrovnávací paměti je vloženo pět znaků, bod sledování pak odkazuje na pozici 15. Pokud dojde k vložení přesně na pozici označené sledovacím bodem, jeho chování je určeno podle jeho <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , což může být buď `Positive` nebo `Negative` . Je-li režim sledování kladný, odkazuje bod sledování na stejný znak, který je nyní na konci vložení. Pokud je režim sledování záporný, bod sledování odkazuje na první vložený znak na původní pozici. Pokud je odstraněn znak na pozici, která je reprezentovaná sledovacím bodem, přesune se bod sledování na první znak, který následuje po odstraněném rozsahu. Například pokud bod sledování odkazuje na znak na pozici 5 a znaky na pozicích 3 až 6 jsou odstraněny, bod sledování odkazuje na znak na pozici 3.

<xref:Microsoft.VisualStudio.Text.ITrackingSpan>Představuje rozsah znaků namísto pouze jedné pozice. Jeho chování je určeno podle jeho <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Pokud je režim sledování rozsahu [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), rozpětí sledování se rozrůstá tak, aby zahrnovalo text vložený na jeho okrajích. Pokud je režim sledování rozsahu [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), rozpětí sledování nezahrnuje text vložený na jeho okrajích. Pokud je však režim sledování rozsahu [SpanTrackingMode. pozitivní okraj rozsahu](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), vložení vloží aktuální pozici směrem k začátku, a pokud je režim sledování rozsahu [SpanTrackingMode. negativní okraj rozsahu](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), vložení Posune aktuální pozici k elementu end.

Pozici sledovacího bodu nebo rozpětí sledovacího rozpětí můžete získat pro libovolný snímek textové vyrovnávací paměti, do které patří. Body sledování a rozsahy sledování mohou být bezpečně odkazovány z libovolného vlákna.

#### <a name="content-types"></a>Typy obsahu

Typy obsahu představují mechanismus pro definování různých druhů obsahu. Typ obsahu může být typ souboru, například "text", "Code" nebo "Binary" nebo typ technologie, například "XML", "VB" nebo "c#". Například slovo "using" je klíčové slovo v jazyce C# i Visual Basic, ale ne v jiných programovacích jazycích. Proto by definice tohoto klíčového slova byla omezena na typy obsahu c# a VB.

Typy obsahu slouží jako filtr pro doplňky a další prvky editoru. Mnoho funkcí editoru a rozšiřovacích bodů je definováno na typ obsahu. Například barevné zvýraznění textu je jiné pro soubory prostého textu, soubory XML a Visual Basic soubory zdrojového kódu. Při vytváření textových vyrovnávacích pamětí je typ obsahu obecně přiřazen a typ obsahu vyrovnávací paměti textu lze změnit.

Typy obsahu mohou dědit více typů obsahu. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Umožňuje zadat více základních typů jako nadřazených prvků daného typu obsahu.

Vývojáři mohou definovat své vlastní typy obsahu a zaregistrovat je pomocí <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Mnoho funkcí editoru lze definovat s ohledem na konkrétní typ obsahu pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Například lze definovat okraje editoru, doplňky a obslužné rutiny myši, aby byly použity pouze pro editory, které zobrazují konkrétní typy obsahu.

### <a name="the-text-view"></a>Textové zobrazení

Část vzoru kontroleru zobrazení modelu (MVC) definuje textové zobrazení, formátování zobrazení, grafické prvky, jako je posuvník, a blikající kurzor. Všechny prvky prezentace v editoru sady Visual Studio jsou založeny na WPF.

#### <a name="text-views"></a>Textová zobrazení

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>Rozhraní je reprezentace textového zobrazení nezávislé na platformě. Slouží primárně k zobrazení textových dokumentů v okně, ale lze ji také použít pro jiné účely, například v popisu tlačítka.

Textové zobrazení odkazuje na různé druhy textových vyrovnávacích pamětí. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>Vlastnost odkazuje na <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objekt, který odkazuje na tyto tři různé textové vyrovnávací paměti: vyrovnávací paměť, která je horní vyrovnávací paměť na úrovni dat, vyrovnávací paměť pro úpravy, v němž dojde k úpravám, a vizuální vyrovnávací paměť, což je vyrovnávací paměť, která je zobrazena v zobrazení text.

Text je formátovaný na základě klasifikátorů, které jsou připojeny k podkladové vyrovnávací paměti textu, a je napsaný pomocí poskytovatelů doplňků, kteří jsou připojeni k samotnému zobrazení textu.

#### <a name="the-text-view-coordinate-system"></a>Systém souřadnicového zobrazení textu

Systém souřadnicového zobrazení textu určuje pozice v textovém zobrazení. V tomto souřadnicovém systému odpovídá hodnota x 0,0 levému okraji zobrazeného textu a hodnota y 0,0 odpovídá hornímu okraji zobrazeného textu. Souřadnice x se zvětšuje zleva doprava a souřadnice y se zvýší od shora dolů.

Zobrazení (část textu zobrazeného v textovém okně) se nedá posouvat stejným způsobem vodorovně, protože se posouvá svisle. Zobrazení se posouvá vodorovně změnou jeho levé souřadnice, aby se přesouval s ohledem na plochu vykreslování. Zobrazení lze však procházet vertikálně pouze změnou vykresleného textu, což způsobí <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> vyvolání události.

Vzdálenosti v souřadnicovém systému odpovídají logickým pixelům. Pokud je plocha vykreslování textu zobrazena bez transformace škálování, pak jedna jednotka v systému souřadnic vykreslování textu odpovídá jednomu pixelu na displeji.

#### <a name="margins"></a>Okraje

<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>Rozhraní představuje okraj a umožňuje ovládat viditelnost okraje a jeho velikosti. K dispozici jsou čtyři předdefinované okraje, které jsou pojmenovány "Top", "Left", "Right" a "Bottom" a jsou připojeny k hornímu, dolnímu, levému nebo pravému okraji zobrazení. Tyto okraje jsou kontejnery, ve kterých lze umístit jiné okraje. Rozhraní definuje metody, které vracejí velikost okraje a viditelnost okraje. Okraje jsou vizuální prvky, které poskytují další informace o zobrazení textu, ke kterému jsou připojeny. Například okraj pro číslo řádku zobrazuje čísla řádků pro zobrazení textu. Glyfový okraj zobrazuje prvky uživatelského rozhraní.

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>Rozhraní zpracovává vytvoření a umístění okrajů. Okraje lze seřadit s ohledem na jiné okraje. Okraje s vyšší prioritou jsou umístěny blíž k textovému zobrazení. Například pokud existují dva levé okraje, okraje A a okraje B a marže B má nižší prioritu než okraj A, zobrazí se marže B vlevo od okraje A.

#### <a name="the-text-view-host"></a>Hostitel zobrazení textu

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Rozhraní obsahuje textové zobrazení a všechny sousedící ozdoby, které jsou přiloženy k zobrazení, například posuvníky. Hostitel zobrazení textu obsahuje také okraje, které jsou připojeny k okraji zobrazení.

#### <a name="formatted-text"></a>Formátovaný text

Text zobrazený v textovém zobrazení se skládá z <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objektů. Každý řádek pro zobrazení textu odpovídá jednomu řádku textu v zobrazení text. Dlouhé čáry v podkladové textové vyrovnávací paměti mohou být částečně skryty (Pokud není povoleno zalamování řádků) nebo rozdělené do více řádků textových zobrazení. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>Rozhraní obsahuje metody a vlastnosti pro mapování mezi souřadnicemi a znaky a pro doplňky, které mohou být spojeny s řádkem.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objekty jsou vytvořeny pomocí <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> rozhraní. Pokud máte právě obavy o text, který je aktuálně zobrazen v zobrazení, můžete zdroj formátování ignorovat. Pokud máte zájem o formát textu, který není zobrazen v zobrazení (například pro podporu vyjmutí a vložení formátovaného textu), můžete použít <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> k formátování textu v textové vyrovnávací paměti.

V zobrazení text se naformátuje jeden <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> po druhém.

## <a name="editor-features"></a>Funkce editoru

Funkce editoru jsou navržené tak, aby definice funkce byla oddělená od jeho implementace. Editor zahrnuje tyto funkce:

- Značky a klasifikátory

- Grafických doplňků

- Projekce

- Sbalování

- Vazby myši a kláves

- Operace a primitivní prvky

- IntelliSense

### <a name="tags-and-classifiers"></a>Značky a klasifikátory

Značky jsou značky, které jsou přidruženy k rozsahu textu. Mohou být prezentovány různými způsoby, například pomocí barvy textu, podtržení, grafiky nebo automaticky otevíraných oken. Klasifikátory jsou jeden druh značky.

Jiné druhy značek jsou <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> pro zvýraznění textu, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pro sbalení a <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> chyby při kompilaci.

#### <a name="classification-types"></a>Typy klasifikace

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Rozhraní představuje třídu rovnosti, která je abstraktní kategorií textu. Typy klasifikace můžou vícenásobně dědit z jiných typů klasifikace. Klasifikace programovacích jazyků může například zahrnovat klíčová slova "klíčové slovo", "comment" a "identifier", která dědí z "Code". Typy klasifikace přirozeného jazyka mohou zahrnovat "substantivum", "sloveso" a "adjektivum", které všechny dědí z "přirozeného jazyka".

#### <a name="classifications"></a>Klasifikace

Klasifikace je instance konkrétního typu klasifikace, obvykle přes rozsah textu. <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>Slouží k reprezentaci klasifikace. Rozsah klasifikace lze představit jako popisek, který pokrývá konkrétní rozsah textu a oznamuje systému, že tento rozsah textu je určitého typu klasifikace.

#### <a name="classifiers"></a>Klasifikátorů

<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Je mechanismus, který přerušuje text do sady klasifikací. Klasifikátory musí být definovány pro konkrétní typy obsahu a vytvořeny pro konkrétní textové vyrovnávací paměti. Klienti musí implementovat, <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> aby se účastnili klasifikace textu.

#### <a name="classifier-aggregators"></a>Agregátory klasifikátoru

Agregátor klasifikátoru je mechanismus, který kombinuje všechna třídění pro jednu vyrovnávací paměť textu do jediné sady klasifikací. Například klasifikátor v jazyce C# i klasifikátor v anglickém jazyce by mohl vytvořit klasifikace v souboru C# pomocí komentáře. Vezměte v úvahu tento komentář:

```
// This method produces a classifier
```

Klasifikátor v jazyce C# může označit celý rozsah jako komentář a třídění v anglickém jazyce může klasifikovat "produkuje" jako "sloveso" a "metoda" jako "substantivum". Agregátor vytváří sadu překrývajících se klasifikací a typ sady je založen na všech příspěvcích.

Agregátor klasifikátoru je také klasifikátor, protože přerušuje text do sady klasifikací. Agregátor třídění také zajišťuje, že nejsou k dispozici žádné překrývající se klasifikace a že klasifikace jsou seřazené. Jednotlivá třídění jsou zdarma vracet jakékoli sady klasifikací, v libovolném pořadí a překrývající se jakýmkoli způsobem.

#### <a name="classification-formatting-and-text-coloring"></a>Formátování klasifikace a zvýraznění textu

Formátování textu je příklad funkce, která je založena na klasifikaci textu. Je používána vrstvou zobrazení text k určení zobrazení textu v aplikaci. Oblast formátování textu závisí na technologii WPF, ale logická definice klasifikací není.

Klasifikační formát je sada vlastností formátování pro konkrétní typ klasifikace. Tyto formáty dědí z formátu nadřazeného typu klasifikace.

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Je mapa z typu klasifikace na sadu vlastností formátování textu. Implementace mapování formátu v editoru zpracovává všechny exporty formátů klasifikace.

### <a name="adornments"></a>Grafických doplňků

Doplňky jsou grafické efekty, které přímo nesouvisejí s písmem a barvou znaků v zobrazení text. Například červená vlnovka podtržení, která se používá k označení nekompilování kódu v mnoha programovacích jazycích, je vložené doplňky a popisy tlačítek jsou místní doplňky. Doplňky jsou odvozeny od <xref:System.Windows.UIElement> a implementovány <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Dva specializované typy značky doplňky jsou <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> pro doplňky, které zabírají stejné místo jako text v zobrazení, a <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pro podtržení vlnovkou.

Vložená vylepšení jsou grafika, která tvoří součást formátovaného textu. Jsou uspořádány v různých vrstvách pořadí Z. Existují tři předdefinované vrstvy následujícím způsobem: text, blikající kurzor a výběr. Vývojáři však mohou definovat více vrstev a vkládat je do pořadí s ohledem na sebe. Tři druhy integrovaných doplňků jsou textová vylepšení (která se pohybují při přesunu textu a odstraňují se, když se text odstraní), vzhledy relativních zobrazení (která se musí dělat s netextovými částmi zobrazení) a doplňky řízené vlastníkem (vývojář musí spravovat jejich umístění).

Rozbalovací doplňky jsou grafické prvky, které se zobrazují v malém okně nad zobrazením textu, například popisy tlačítek.

### <a name="projection"></a><a name="projection"></a> Třetího

Projekcí je technika pro sestavování jiného typu textové vyrovnávací paměti, která ve skutečnosti neukládá text, ale místo toho kombinuje text z jiných textových vyrovnávacích pamětí. Například vyrovnávací paměť projekce může být použita k zřetězení textu ze dvou dalších vyrovnávacích pamětí a k prezentaci výsledku, jako by byla v pouze jedné vyrovnávací paměti, nebo pro skrytí částí textu v jedné vyrovnávací paměti. Vyrovnávací paměť projekce může fungovat jako zdrojová vyrovnávací paměť do jiné vyrovnávací paměti projekce. Sadu vyrovnávacích pamětí, které souvisejí s projekcí, lze vytvořit tak, aby se text změnil v mnoha různých způsobech. (Taková sada je také známá jako *graf vyrovnávací paměti*.) Funkce sbalení textu sady Visual Studio je implementována pomocí vyrovnávací paměti projekce pro skrytí sbaleného textu a aplikace Visual Studio editor pro stránky ASP.NET používá projekci k podpoře vložených jazyků, jako jsou Visual Basic a C#.

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Je vytvořen pomocí <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Vyrovnávací paměť projekce je reprezentována uspořádanou sekvencí <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objektů, které se označují jako *zdrojové rozsahy*. Obsah těchto rozsahů se zobrazí jako posloupnost znaků. Textové vyrovnávací paměti, ze kterých se vykreslují zdrojové rozsahy, se nazývají *zdrojové vyrovnávací paměti*. Klienti vyrovnávací paměti projekce nemusí vědět, že se liší od běžné vyrovnávací paměti textu.

Vyrovnávací paměť projekce naslouchají událostem změny textu ve zdrojových vyrovnávacích pamětech. Když se změní text ve zdrojovém rozsahu, vyrovnávací paměť projekce mapuje změny souřadnic textu na vlastní souřadnice a vyvolá příslušné události změny textu. Zvažte například zdrojové vyrovnávací paměti a a B, které mají tento obsah:

```
A: ABCDE
B: vwxyz
```

Pokud je vyrovnávací paměť projekce P tvořena dvěma rozsahy textu, jednu, která má veškerou vyrovnávací paměť a a druhou, která má veškerou vyrovnávací paměť B, pak P má následující obsah:

```
P: ABCDEvwxyz
```

Pokud je dílčí řetězec `xy` odstraněn z vyrovnávací paměti B, pak vyrovnávací paměť P vyvolá událost, která indikuje, že se odstranily znaky na pozici 7 a 8.

Vyrovnávací paměť projekce se dá upravovat také přímo. Rozšiřuje úpravy na příslušné zdrojové vyrovnávací paměti. Například pokud je řetězec vložen do vyrovnávací paměti P na pozici 6 (původní pozice znaku "v"), vložení je rozšířeno na vyrovnávací paměť B na pozici 1.

Existují omezení pro zdrojové rozsahy, které přispívají k vyrovnávací paměti projekce. Zdrojové rozsahy se nesmí překrývat; umístění ve vyrovnávací paměti projekce nelze namapovat na více než jedno umístění ve zdrojové vyrovnávací paměti a umístění ve zdrojové vyrovnávací paměti nelze namapovat na více než jedno umístění ve vyrovnávací paměti projekce. Ve zdrojové relaci vyrovnávací paměti nejsou povoleny žádné cykly.

Události jsou vyvolány, když se změní sada zdrojových vyrovnávacích pamětí pro vyrovnávací paměť projekce a když se změní sada zdrojů.
Vyrovnávací paměť Elizi je zvláštní druh vyrovnávací paměti projekce. Používá se hlavně pro sbalení a pro operace, které rozšiřují a sbalí bloky textu. Vyrovnávací paměť Elizi je založena pouze na jedné zdrojové vyrovnávací paměti a rozsahy ve vyrovnávací paměti Elizi musí být seřazeny stejně, jako jsou seřazené ve zdrojové vyrovnávací paměti.

#### <a name="the-buffer-graph"></a>Graf vyrovnávací paměti

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Rozhraní umožňuje mapování v grafu vyrovnávací paměti projekce. Všechny vyrovnávací paměti textu a vyrovnávací paměti projekce jsou shromažďovány v řízeném acyklického grafu podobně jako abstraktní strom syntaxe, který je vytvořen kompilátorem jazyka. Graf je definován pomocí horní vyrovnávací paměti, což může být libovolná textová vyrovnávací paměť. Graf vyrovnávací paměti lze namapovat z bodu v horní vyrovnávací paměti do bodu ve zdrojové vyrovnávací paměti nebo z rozsahu v horní vyrovnávací paměti do sady rozsahů ve zdrojové vyrovnávací paměti. Podobně může mapovat bod nebo rozpětí ze zdrojové vyrovnávací paměti do bodu v horní vyrovnávací paměti. Grafy vyrovnávací paměti se vytvářejí pomocí <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Vyrovnávací paměti pro události a projekce

Když se upraví vyrovnávací paměť projekce, změny se odesílají z vyrovnávací paměti projekce do vyrovnávacích pamětí, které jsou na ní závislé. Po úpravě všech vyrovnávacích pamětí jsou vyvolány události změny vyrovnávací paměti, počínaje nejnižší vyrovnávací pamětí.

### <a name="outlining"></a>Sbalování

Sbalení je schopnost rozbalit nebo sbalit různé bloky textu v textovém zobrazení. Sbalení je definováno jako druh <xref:Microsoft.VisualStudio.Text.Tagging.ITag> a stejným způsobem jako doplňky jsou definovány. <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>Je značka definující textovou oblast, kterou lze rozbalit nebo sbalit. Chcete-li použít sbalení, je nutné importovat a <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> získat <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Správce osnovy vypíše, sbalí a rozbalí různé bloky, které jsou reprezentovány jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objekty, a vyvolá odpovídající události.

### <a name="mouse-bindings"></a>Vazby myši

Vazby myši propojí pohyby myši s různými příkazy. Vazby myši jsou definovány pomocí prvku <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> a vazby klíčů jsou definovány pomocí <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Automaticky vytvoří instanci všech vazeb a připojí je k událostem myši v zobrazení.

<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>Rozhraní obsahuje obslužné rutiny událostí předběžného zpracování a následného procesu pro různé události myši. Chcete-li zpracovat jednu z událostí, můžete přepsat některé z metod v <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Operace editoru

Operace editoru lze použít k automatizaci interakce s editorem, pro skriptování nebo jiné účely. Můžete importovat <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> do operací přístupu pro daný objekt <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Pak můžete pomocí těchto objektů upravit výběr, posunout zobrazení nebo přesunout blikající kurzor do různých částí zobrazení.

### <a name="intellisense"></a>IntelliSense

Technologie IntelliSense podporuje dokončování příkazů, podpisové nápovědě (označované také jako informace o parametrech), rychlé informace a žárovky.

Dokončování příkazů poskytuje místní seznamy potenciálních dokončení pro názvy metod, XML elementy a další prvky kódování nebo značek. Obecně platí, že uživatelské gesto vyvolá relaci dokončení. V relaci se zobrazí seznam potenciálních dokončení a uživatel může vybrat jeden nebo zavřít seznam. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>Zodpovídá za vytvoření a aktivaci <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Vypočítá <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> položky dokončení pro relaci.

## <a name="see-also"></a>Viz také

- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Importy editoru](../extensibility/editor-imports.md)
