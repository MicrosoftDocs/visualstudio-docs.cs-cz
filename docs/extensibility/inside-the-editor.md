---
title: Práce v editoru
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710318"
---
# <a name="inside-the-editor"></a>Uvnitř editoru

Editor se skládá z několika různých subsystémů, které jsou navrženy tak, aby textový model editoru odděleně od zobrazení textu a uživatelského rozhraní.

Tyto části popisují různé aspekty editoru:

- [Přehled subsystémů](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Textový model](../extensibility/inside-the-editor.md#the-text-model)

- [Zobrazení textu](../extensibility/inside-the-editor.md#the-text-view)

Tyto části popisují funkce editoru:

- [Značky a klasifikátory](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ozdoby](../extensibility/inside-the-editor.md#adornments)

- [Projekce](../extensibility/inside-the-editor.md#projection)

- [Sbalování](../extensibility/inside-the-editor.md#outlining)

- [Vázání myší](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operace editoru](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Přehled subsystémů

### <a name="text-model-subsystem"></a>Podsystém textového modelu

Podsystém textového modelu je zodpovědný za reprezentaci textu a povolení jeho manipulace. Podsystém textového <xref:Microsoft.VisualStudio.Text.ITextBuffer> modelu obsahuje rozhraní, které popisuje posloupnost znaků, které má být zobrazeny editorem. Tento text lze změnit, sledovat a jinak manipulovat mnoha způsoby. Textový model také obsahuje typy pro následující aspekty:

- Služba, která přidružuje text k souborům a spravuje jejich čtení a zápis v systému souborů.

- Služba differencing, která vyhledá minimální rozdíly mezi dvěma sekvencemi objektů.

- Systém pro popis textu ve vyrovnávací paměti z hlediska podmnožiny textu v jiných vyrovnávacích pamětí.

Podsystém textového modelu neposkytuje koncepty uživatelského rozhraní (UI). Například není zodpovědný za formátování textu nebo rozložení textu a nemá žádné znalosti vizuální vylepšení, které mohou být spojeny s textem.

Veřejné typy podsystému textového modelu jsou obsaženy v *souborech Microsoft.VisualStudio.Text.Data.dll* a *Microsoft.VisualStudio.CoreUtility.dll*, které závisí pouze na knihovně základní třídy rozhraní .NET Framework a rozhraní MEF (Managed Extensibility Framework).

### <a name="text-view-subsystem"></a>Podsystém zobrazení textu

Podsystém zobrazení textu je zodpovědný za formátování a zobrazení textu. Typy v tomto subsystému jsou rozděleny do dvou vrstev, v závislosti na tom, zda typy spoléhají na Windows Presentation Foundation (WPF). Nejdůležitější typy jsou <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>a , které řídí sadu textových řádků, které mají být zobrazeny, a také stříšky, výběr a zařízení pro zdobení textu pomocí wpf prvky uživatelského rozhraní. Tento podsystém také poskytuje okraje kolem oblasti zobrazení textu. Tyto okraje mohou být rozšířeny a mohou obsahovat různé druhy obsahu a vizuální efekty. Příklady okrajů jsou zobrazení čísel řádků a posuvníky.

Veřejné typy podsystému zobrazení textu jsou obsaženy v souborech *Microsoft.VisualStudio.Text.UI.dll* a *Microsoft.VisualStudio.Text.UI.Wpf.dll*. První sestavení obsahuje prvky nezávislé na platformě a druhý obsahuje prvky specifické pro WPF.

### <a name="classification-subsystem"></a>Klasifikační subsystém

Subsystém klasifikace je zodpovědný za určení vlastností písma pro text. Třídění rozdělí text do různých tříd, například "klíčové slovo" nebo "komentář". Mapa formátu klasifikace spojuje tyto třídy se skutečnými vlastnostmi písma, například "Blue Consolas 10 pt". Tyto informace jsou používány v zobrazení textu při formátování a vykreslení textu. Označování, které je podrobněji popsáno dále v tomto tématu, umožňuje, aby data byla přidružena k rozsahům textu.

Veřejné typy subsystému klasifikace jsou obsaženy v souboru Microsoft.VisualStudio.Text.Logic.dll a interagují s vizuálními aspekty klasifikace, které jsou obsaženy v souboru Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Operační subsystém

Operační subsystém definuje chování editoru. Poskytuje implementaci pro příkazy editoru sady Visual Studio a systém vrátit.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bližší pohled na textový model a zobrazení textu

### <a name="the-text-model"></a>Textový model

Podsystém textového modelu se skládá z různých seskupení typů textu. Patří mezi ně vyrovnávací paměť textu, textové snímky a rozsahy textu.

#### <a name="text-buffers-and-text-snapshots"></a>Textové vyrovnávací paměti a textové snímky

Rozhraní <xref:Microsoft.VisualStudio.Text.ITextBuffer> představuje posloupnost znaků Unicode, které jsou kódovány pomocí UTF-16, `String` což je kódování používané typem v rozhraní .NET Framework. Textová vyrovnávací paměť může být zachována jako dokument systému souborů, ale to není nutné.

Slouží <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> k vytvoření prázdné textové vyrovnávací paměti nebo textové vyrovnávací paměti, <xref:System.IO.TextReader>která je inicializována z řetězce nebo z . Textovou vyrovnávací paměť lze zachovat v <xref:Microsoft.VisualStudio.Text.ITextDocument>systému souborů jako .

Jakékoli vlákno můžete upravit vyrovnávací paměť textu, dokud vlákno <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>převezme vlastnictví vyrovnávací paměti textu voláním . Poté může úpravy provádět pouze toto vlákno.

Text vyrovnávací paměti může projít mnoho verzí během jeho životnosti. Nová verze je generována při každé úpravě vyrovnávací paměti <xref:Microsoft.VisualStudio.Text.ITextSnapshot> a neměnná představuje obsah této verze vyrovnávací paměti. Vzhledem k tomu, že textové snímky jsou neměnné, můžete přistupovat k snímku textu v libovolném vlákně bez omezení, i když vyrovnávací paměť textu, kterou představuje, se nadále mění.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Textové snímky a řádky snímků textu

Obsah snímku textu můžete zobrazit jako posloupnost znaků nebo jako posloupnost řádků. Znaky a řádky jsou indexovány od nuly. Prázdný textový snímek obsahuje nula znaků a jeden prázdný řádek. Řádek je oddělen libovolnou platnou sekvencí řádků unicode nebo začátkem nebo koncem vyrovnávací paměti. Znaky konce řádku jsou explicitně reprezentovány ve snímku textu a konce řádků ve snímku textu nemusí být všechny stejné.

> [!NOTE]
> Další informace o postavách konce řádků v editoru Sady Visual Studio naleznete v [tématu Kódování a zalomení řádků](../ide/encodings-and-line-breaks.md).

Řádek textu je reprezentován <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objektem, který lze získat ze snímku textu pro určité číslo řádku nebo pro konkrétní pozici znaku.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans a NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> představuje pozici znaku ve snímku. Pozice je zaručeno, že leží mezi nulou a délkou snímku. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> představuje rozsah textu ve snímku. Jeho koncová poloha je zaručena ležet mezi nulou a délkou snímku. Skládá <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> se ze sady <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objektů ze stejného snímku.

#### <a name="spans-and-normalizedspancollections"></a>Rozsahy a normalizedSpanCollections

A <xref:Microsoft.VisualStudio.Text.Span> představuje interval, který lze použít na rozsah textu ve snímku textu. Pozice snímků jsou od nuly, takže rozpětí mohou začínat na libovolné pozici včetně nuly. Vlastnost `End` rozpětí se rovná součtu jeho `Start` majetku `Length` a jeho majetku. A `Span` neobsahuje znak, který je `End` indexován vlastností. Například rozpětí, které má Start = 5 a Length = 3 má End = 8 a obsahuje znaky na pozicích 5, 6 a 7. Zápis pro toto rozpětí je [5..8).

Dva rozsahy se protínají, pokud mají nějaké společné pozice, včetně koncové polohy. Proto je průsečík [3, 5) a [2, 7) [3, 5) a průsečík [3, 5) a [5, 7) je [5, 5). (Všimněte si, že [5, 5) je prázdný rozsah.)

Dva rozsahy se překrývají, pokud mají společné pozice, s výjimkou koncové polohy. Prázdné rozpětí se nikdy nepřekrývá s žádným jiným rozsahem a překrytí dvou rozsahů není nikdy prázdné.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> je seznam rozsahů v pořadí vlastností Start rozsahů. V seznamu se sloučí překrývající se nebo sousedící rozsahy. Například s ohledem na sadu rozpětí [5..9), [0..1), [3..6) a [9..10) je normalizovaný seznam rozpětí [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Oznámení o změně textu iTextEdit, TextVersion a text

Obsah textové vyrovnávací paměti lze změnit <xref:Microsoft.VisualStudio.Text.ITextEdit> pomocí objektu. Vytvoření takového objektu (pomocí `CreateEdit()` jedné <xref:Microsoft.VisualStudio.Text.ITextBuffer>z metod ) spustí textovou transakci, která se skládá z úprav textu. Každá úprava je nahrazením určitého rozsahu textu ve vyrovnávací paměti řetězcem. Souřadnice a obsah každé úpravy jsou vyjádřeny vzhledem k snímku vyrovnávací paměti při spuštění transakce. Objekt <xref:Microsoft.VisualStudio.Text.ITextEdit> upraví souřadnice úprav, které jsou ovlivněny jinými úpravami ve stejné transakci.

Zvažte například textovou vyrovnávací paměť, která obsahuje tento řetězec:

```
abcdefghij
```

Použijte transakci, která obsahuje dvě úpravy, jednu úpravu, která nahradí rozsah `X` na [2..4) pomocí znaku a druhou úpravu, `Y`která nahradí rozsah na [6..9) pomocí znaku . Výsledkem je tato vyrovnávací paměť:

```
abXefYj
```

Souřadnice pro druhou úpravu byly vypočítány s ohledem na obsah vyrovnávací paměti na začátku transakce před použitím první úpravy.

Změny vyrovnávací paměti se projeví, <xref:Microsoft.VisualStudio.Text.ITextEdit> když je `Apply()` objekt potvrzen voláním jeho metody. Pokud došlo alespoň k jedné neprázdné <xref:Microsoft.VisualStudio.Text.ITextVersion> úpravě, vytvoří <xref:Microsoft.VisualStudio.Text.ITextSnapshot> se nová, `Changed` vytvoří se nová a je vyvolána jedna událost. Každá verze textu má jiný snímek textu. Snímek textu představuje úplný stav vyrovnávací paměti textu po transakci úprav, ale textová verze popisuje pouze změny z jednoho snímku na další. Obecně platí, že textové snímky jsou určeny k použití jednou a potom zahozeny, zatímco textové verze musí zůstat naživu po určitou dobu.

Textová verze <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>obsahuje . Tato kolekce popisuje změny, které při použití na snímek, vytvořit následující snímek. Každý <xref:Microsoft.VisualStudio.Text.ITextChange> v kolekci obsahuje pozici znaku změny, nahrazený řetězec a náhradní řetězec. Nahrazený řetězec je prázdný pro základní vložení a náhradní řetězec je prázdný pro základní odstranění. Normalizovaná kolekce `null` je vždy pro nejnovější verzi textové vyrovnávací paměti.

Pouze <xref:Microsoft.VisualStudio.Text.ITextEdit> jeden objekt může být vytvořena instance pro text vyrovnávací paměti v každém okamžiku a všechny úpravy textu musí být provedeny ve vlákně, které vlastní vyrovnávací paměť textu (pokud vlastnictví bylo nárokováno). Úpravu textu lze opustit voláním `Cancel` jeho `Dispose` metody nebo její metody.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>také `Insert()`poskytuje `Delete()`, `Replace()` a metody, které <xref:Microsoft.VisualStudio.Text.ITextEdit> se podobají těm, které se nacházejí v rozhraní. Jejich volání má stejný účinek jako vytvoření objektu, <xref:Microsoft.VisualStudio.Text.ITextEdit> provedení podobného volání a následné použití úpravy.

#### <a name="tracking-points-and-tracking-spans"></a>Sledovací body a rozsahy sledování

A <xref:Microsoft.VisualStudio.Text.ITrackingPoint> představuje pozici znaku ve vyrovnávací paměti textu. Pokud je vyrovnávací paměť upravena způsobem, který způsobí posun pozice znaku, posune se s ním bod sledování. Například pokud bod sledování odkazuje na pozici 10 ve vyrovnávací paměti a pět znaků jsou vloženy na začátku vyrovnávací paměti, bod sledování pak odkazuje na pozici 15. Pokud se vložení provede přesně v pozici označené bodem sledování, jeho <xref:Microsoft.VisualStudio.Text.PointTrackingMode>chování je určeno `Positive` `Negative`jeho , což může být buď nebo . Pokud je režim sledování kladný, bod sledování odkazuje na stejný znak, který je nyní na konci vložení. Pokud je režim sledování záporný, bod sledování odkazuje na první vložený znak v původní poloze. Pokud je znak na pozici, která je reprezentována bodem sledování, odstraněn, bod sledování se posune na první znak, který následuje za odstraněnou oblastí. Pokud například bod sledování odkazuje na znak na pozici 5 a znaky na pozicích 3 až 6 jsou odstraněny, bod sledování odkazuje na znak na pozici 3.

Představuje <xref:Microsoft.VisualStudio.Text.ITrackingSpan> rozsah znaků namísto pouze jednu pozici. Jeho chování je <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>určeno jeho . Pokud je režim sledování rozpětí [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), rozsah sledování se zvětší tak, aby zahrnoval text vložený na jeho okrajích. Pokud je režim sledování rozpětí [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), rozsah sledování nezahrnuje text vložený na jeho okrajích. Pokud je však režim sledování rozsahu [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), vložení posune aktuální pozici směrem k začátku a pokud je režim sledování rozsahu [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), vložení posune aktuální pozici ke konci.

Můžete získat pozici bodu sledování nebo rozpětí sledování pro libovolný snímek vyrovnávací paměti textu, do kterého patří. Sledovací body a rozsahy sledování mohou být bezpečně odkazovány z libovolného vlákna.

#### <a name="content-types"></a>Typy obsahu

Typy obsahu jsou mechanismem pro definování různých druhů obsahu. Typ obsahu může být typ souboru, například "text", "kód" nebo "binární", nebo typ technologie, jako je "xml", "vb" nebo "c#". Například slovo "using" je klíčové slovo v jazyce C# a visual basicu, ale ne v jiných programovacích jazycích. Definice tohoto klíčového slova by proto byla omezena na typy obsahu "c#" a "vb".

Typy obsahu se používají jako filtr pro vylepšení a další prvky editoru. Mnoho funkcí editoru a rozšiřujících bodů je definováno podle typu obsahu. Například vybarvení textu se liší pro soubory ve formátu prostého textu, soubory XML a soubory zdrojového kódu jazyka Visual Basic. Textové vyrovnávací paměti jsou při vytváření obvykle přiřazeny typu obsahu a typ obsahu textové vyrovnávací paměti lze změnit.

Typy obsahu mohou vícedědit z jiných typů obsahu. Umožňuje <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> zadat více základních typů jako rodiče daného typu obsahu.

Vývojáři mohou definovat své vlastní typy <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>obsahu a zaregistrovat je pomocí rozhraní . Mnoho funkcí editoru <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>lze definovat s ohledem na konkrétní typ obsahu pomocí rozhraní . Například okraje editoru, vylepšení a obslužné rutiny myši lze definovat tak, aby se vztahovaly pouze na editory, které zobrazují určité typy obsahu.

### <a name="the-text-view"></a>Zobrazení textu

Část zobrazení vzoru řadiče zobrazení modelu (MVC) definuje zobrazení textu, formátování pohledu, grafické prvky, jako je posuvník, a stříšku. Všechny prezentační prvky editoru Visual Studio jsou založeny na WPF.

#### <a name="text-views"></a>Zobrazení textu

Rozhraní <xref:Microsoft.VisualStudio.Text.Editor.ITextView> je platforma nezávislé reprezentace zobrazení textu. Používá se především k zobrazení textových dokumentů v okně, ale může být také použit pro jiné účely, například v popisku.

Zobrazení textu odkazuje na různé druhy textových vyrovnávacích pamětí. Vlastnost <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> odkazuje na <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objekt, který odkazuje na tyto tři různé textové vyrovnávací paměti: vyrovnávací paměť dat, což je horní vyrovnávací paměť na úrovni dat, vyrovnávací paměť pro úpravy, ve které dochází k úpravám, a vizuální vyrovnávací paměť, což je vyrovnávací paměť zobrazená v textovém zobrazení.

Text je formátován na základě třídění, které jsou připojeny k vyrovnávací paměti základní text a je zdobí pomocí vylepšení zprostředkovatelů, které jsou připojeny k samotné zobrazení textu.

#### <a name="the-text-view-coordinate-system"></a>Souřadnicový systém textového zobrazení

Souřadnicový systém textového zobrazení určuje pozice v textovém zobrazení. V tomto souřadnicovém systému odpovídá hodnota x 0.0 levému okraji zobrazeného textu a hodnota y 0,0 odpovídá hornímu okraji zobrazeného textu. Souřadnice x se zvětšuje zleva doprava a souřadnice y se zvětšuje shora dolů.

Výřez (část textu viditelná v textovém okně) nelze posouvat stejným způsobem vodorovně jako svisle. Výřez se posouvá vodorovně změnou jeho levé souřadnice tak, aby se pohyboval vzhledem k kreslicí ploše. Výřez však lze posouvat svisle pouze změnou vykresleného textu, což způsobí vyvolání <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> události.

Vzdálenosti v souřadnicovém systému odpovídají logickým obrazovým bodům. Pokud je povrch vykreslování textu zobrazen bez transformace měřítka, pak jedna jednotka v souřadnicovém systému vykreslování textu odpovídá jednomu obrazovému bodu na displeji.

#### <a name="margins"></a>Okraje

Rozhraní <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> představuje okraj a umožňuje kontrolu viditelnosti okraje a jeho velikost. Existují čtyři předdefinované okraje s názvem "Nahoře", "Vlevo", "Vpravo" a "Dole" a jsou připojeny k hornímu, dolnímu, levému nebo pravému okraji pohledu. Tyto okraje jsou kontejnery, ve kterých lze umístit další okraje. Rozhraní definuje metody, které vracejí velikost okraje a viditelnost okraje. Okraje jsou vizuální prvky, které poskytují další informace o zobrazení textu, ke kterému jsou připojeny. Například okraj čísla řádků zobrazuje čísla řádků pro textové zobrazení. Okraj glyfu zobrazuje prvky uživatelského rozhraní.

Rozhraní <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> zpracovává vytváření a umístění okrajů. Marže lze objednat s ohledem na jiné marže. Okraje s vyšší prioritou jsou umístěny blíže k zobrazení textu. Pokud například existují dva levé okraje, marže A a marže B a marže B má nižší prioritu než marže A, okraj B se zobrazí vlevo od okraje A.

#### <a name="the-text-view-host"></a>Hostitel zobrazení textu

Rozhraní <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> obsahuje zobrazení textu a všechny přiléhající dekorace, které doprovázejí zobrazení, například posuvníky. Hostitel zobrazení textu také obsahuje okraje, které jsou připojeny k okraji zobrazení.

#### <a name="formatted-text"></a>Formátovaný text

Text zobrazený v textovém zobrazení se <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> skládá z objektů. Každý řádek zobrazení textu odpovídá jednomu řádku textu v zobrazení textu. Dlouhé řádky v podkladové textové vyrovnávací paměti mohou být částečně zakryté (pokud není povoleno obtékání slova) nebo rozděleny do více řádků zobrazení textu. Rozhraní <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obsahuje metody a vlastnosti pro mapování mezi souřadnicemi a znaky a pro vylepšení, které mohou být přidruženy k řádku.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objekty jsou vytvářeny pomocí <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> rozhraní. Pokud se obáváte pouze textu, který je aktuálně zobrazen v zobrazení, můžete zdroj formátování ignorovat. Pokud vás zajímá formát textu, který není zobrazen v zobrazení (například pro podporu vyjmutí <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> a vložení ve formátu RTF), můžete formátovat text ve vyrovnávací paměti textu.

Zobrazení textu se <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> formátuje po jednom.

## <a name="editor-features"></a>Funkce editoru

Funkce editoru jsou navrženy tak, aby definice funkce byla oddělena od jeho implementace. Editor obsahuje tyto funkce:

- Značky a klasifikátory

- Ozdoby

- Projekce

- Sbalování

- Vázání myší a klíčů

- Operace a primitiva

- IntelliSense

### <a name="tags-and-classifiers"></a>Značky a klasifikátory

Značky jsou značky, které jsou přidruženy k rozsahu textu. Mohou být prezentovány různými způsoby, například pomocí zbarvení textu, podtržení, grafiky nebo automaticky otevíraných míst. Klasifikátory jsou jeden druh značky.

Jiné druhy tagů jsou <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pro zvýraznění textu, pro osnovy a <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> pro chyby kompilace.

#### <a name="classification-types"></a>Typy klasifikace

Rozhraní <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> představuje třídu ekvivalence, což je abstraktní kategorie textu. Typy klasifikace mohou vícedědit z jiných typů klasifikace. Například klasifikace programovacího jazyka mohou zahrnovat "klíčové slovo", "komentář" a "identifikátor", které všechny dědí z "kódu". Typy klasifikace přirozeného jazyka mohou zahrnovat "nosné jméno", "sloveso" a "přídavné jméno", které všechny dědí z "přirozeného jazyka".

#### <a name="classifications"></a>Klasifikace

Klasifikace je instance určitého typu klasifikace, obvykle přes rozsah textu. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> se používá k reprezentaci klasifikace. Rozsah klasifikace si lze myslet jako popisek, který pokrývá určitý rozsah textu a říká systému, že toto rozpětí textu je určitého typu klasifikace.

#### <a name="classifiers"></a>Třídění

A <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> je mechanismus, který rozdělí text do sady klasifikací. Klasifikátory musí být definovány pro konkrétní typy obsahu a vytvořena instance pro konkrétní textové vyrovnávací paměti. Klienti musí <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> implementovat k účasti na klasifikaci textu.

#### <a name="classifier-aggregators"></a>Agregátory klasifikátorů

Agregátor třídění je mechanismus, který kombinuje všechny klasifikátory pro jednu textovou vyrovnávací paměť do pouze jedné sady klasifikací. Například klasifikátor jazyka C# a klasifikátor anglického jazyka může vytvořit klasifikace přes komentář v souboru Jazyka C#. Vezměme si tento komentář:

```
// This method produces a classifier
```

Klasifikátor jazyka C# může označit celý rozsah jako komentář a klasifikátor anglického jazyka může klasifikovat "produkuje" jako "sloveso" a "metoda" jako "nosné slovo". Agregátor vytvoří sadu nepřekrývajících se klasifikací a typ sady je založen na všech příspěvcích.

Agregátor třídění je také třídění, protože rozdělí text do sady klasifikací. Agregátor třídění také zajišťuje, že neexistují žádné překrývající se klasifikace a že klasifikace jsou seřazeny. Jednotlivé třídění mohou vrátit libovolnou sadu klasifikací v libovolném pořadí a jakýmkoli způsobem se překrývají.

#### <a name="classification-formatting-and-text-coloring"></a>Formátování klasifikace a barvení textu

Formátování textu je příkladem funkce, která je postavena na klasifikaci textu. Vrstva zobrazení textu ji používá k určení zobrazení textu v aplikaci. Oblast formátování textu závisí na WPF, ale logická definice klasifikací není.

Formát klasifikace je sada vlastností formátování pro konkrétní typ klasifikace. Tyto formáty dědí z formátu nadřazeného typu klasifikace.

A <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> je mapa od typu klasifikace k sadě vlastností formátování textu. Implementace mapy formátu v editoru zpracovává všechny exporty formátů klasifikace.

### <a name="adornments"></a>Ozdoby

Vylepšení jsou grafické efekty, které přímo nesouvisejí s písmem a barvou znaků v textovém zobrazení. Například červené vlnovky podtržení, které se používá k označení nekompilace kódu v mnoha programovacích jazycích je vložené vylepšení a popisky jsou rozbalovací vylepšení. Vylepšení jsou odvozeny <xref:System.Windows.UIElement> od <xref:Microsoft.VisualStudio.Text.Tagging.ITag>a implementovat . Dva specializované typy značky vylepšení <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>jsou , pro vylepšení, které zabírají stejné místo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>jako text v zobrazení a , pro podtržení vlnovkou.

Vložené vylepšení jsou grafiky, které tvoří součást formátovaného zobrazení textu. Jsou uspořádány v různých vrstvách pořadí vykresl. Existují tři předdefinované vrstvy: text, stříška a výběr. Vývojáři však mohou definovat více vrstev a dát je do pořádku s ohledem na sebe navzájem. Tři druhy vložené vylepšení jsou text relativní vylepšení (které se pohybují při pohybu textu a jsou odstraněny při odstranění textu), zobrazení relativní vylepšení (které mají co do činění s netextové části zobrazení) a vlastníkřízené vylepšení (vývojář musí spravovat jejich umístění).

Rozbalovací vylepšení jsou grafiky, které se zobrazují v malém okně nad textovým zobrazením, například popisky.

### <a name="projection"></a><a name="projection"></a>Projekce

Projekce je technika pro vytváření jiného druhu textové vyrovnávací paměti, která ve skutečnosti neukládá text, ale místo toho kombinuje text z jiných textových vyrovnávacích pamětí. Například projekční vyrovnávací paměť lze zřetězit text ze dvou dalších vyrovnávacích pamětí a prezentovat výsledek, jako by byl pouze v jedné vyrovnávací paměti, nebo skrýt části textu v jedné vyrovnávací paměti. Projekční vyrovnávací paměť může fungovat jako zdrojová vyrovnávací paměť do jiné vyrovnávací paměti projekce. Sadu vyrovnávacích pamětí, které souvisejí projekce lze sestavit změnit uspořádání textu mnoha různými způsoby. (Taková sada je také známá jako *graf vyrovnávací paměti*.) Funkce osnovy textu sady Visual Studio je implementována pomocí vyrovnávací paměti projekce ke skrytí sbaleného textu a editor sady Visual Studio pro ASP.NET stránky používá projekci pro podporu vložených jazyků, jako je například Visual Basic a C#.

Vytvoří <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> se pomocí <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>aplikace . Projekční vyrovnávací paměť je <xref:Microsoft.VisualStudio.Text.ITrackingSpan> reprezentována uspořádanou posloupností objektů, které jsou označovány jako *zdrojové rozsahy*. Obsah těchto rozsahů jsou prezentovány jako posloupnost znaků. Textové vyrovnávací paměti, ze kterých jsou vykresleny zdrojové rozsahy, jsou *pojmenovány zdrojové vyrovnávací paměti*. Klienti vyrovnávací paměti projekce nemusí být vědomi, že se liší od běžné textové vyrovnávací paměti.

Vyrovnávací paměť projekce naslouchá událostem změny textu ve zdrojových vyrovnávacích pamětnicích. Když se změní text ve zdrojovém rozpětí, vyrovnávací paměť projekce mapuje změněné souřadnice textu na vlastní souřadnice a vyvolá příslušné události změny textu. Zvažte například zdrojové vyrovnávací paměti A a B, které mají tyto obsahy:

```
A: ABCDE
B: vwxyz
```

Pokud je projekční vyrovnávací paměť P vytvořena ze dvou rozsahů textu, jeden, který má všechny vyrovnávací paměť A a druhý, který má všechny vyrovnávací paměti B, pak P má následující obsah:

```
P: ABCDEvwxyz
```

Pokud je `xy` podřetězec odstraněn z vyrovnávací paměti B, pak vyrovnávací paměť P vyvolá událost, která označuje, že znaky na pozicích 7 a 8 byly odstraněny.

Projekční vyrovnávací paměť lze také upravovat přímo. Šíří úpravy do příslušných zdrojových vyrovnávacích pamětí. Například pokud je řetězec vložen do vyrovnávací paměti P na pozici 6 (původní pozice znaku "v"), vložení je rozšířeno do vyrovnávací paměti B na pozici 1.

Existují omezení na zdrojrozpětí, které přispívají k projekční vyrovnávací paměti. Rozsahy zdroje se nesmí překrývat; umístění ve vyrovnávací paměti projekce nelze mapovat na více než jedno umístění v libovolné zdrojové vyrovnávací paměti a umístění ve zdrojové vyrovnávací paměti nelze mapovat na více než jedno umístění ve vyrovnávací paměti projekce. Ve vztahu zdrojové vyrovnávací paměti nejsou povoleny žádné kruhovitosti.

Události jsou vyvolány při změně sady zdrojových vyrovnávacích pamětí pro projekční vyrovnávací paměti a při změně sady zdrojových rozsahů.
Vyrovnávací paměť elize je zvláštní druh projekční vyrovnávací paměti. Používá se především pro osnovu a pro operace, které rozbalí a sbalí bloky textu. Vyrovnávací paměť elision je založena pouze na jedné zdrojové vyrovnávací paměti a rozsahy ve vyrovnávací paměti elision musí být objednány stejné jako ve zdrojové vyrovnávací paměti.

#### <a name="the-buffer-graph"></a>Graf vyrovnávací paměti

Rozhraní <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> umožňuje mapování přes graf projekční vyrovnávací paměti. Všechny textové vyrovnávací paměti a projekční vyrovnávací paměti jsou shromažďovány v řízeném acyklickém grafu, podobně jako abstraktní syntaktický strom, který je vytvořen kompilátorem jazyka. Graf je definován horní vyrovnávací pamětí, která může být libovolná textová vyrovnávací paměť. Graf vyrovnávací paměti můžete mapovat z bodu v horní vyrovnávací paměti do bodu ve zdrojové vyrovnávací paměti nebo z rozpětí v horní vyrovnávací paměti na sadu rozsahů ve zdrojové vyrovnávací paměti. Podobně může mapovat bod nebo rozsah ze zdrojové vyrovnávací paměti do bodu v horní vyrovnávací paměti. Grafy vyrovnávací paměti jsou <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>vytvářeny pomocí .

#### <a name="events-and-projection-buffers"></a>Události a projekční vyrovnávací paměti

Při změně projekční vyrovnávací paměti jsou změny odeslány z vyrovnávací paměti projekce do vyrovnávacích pamětí, které jsou na ní závislé. Po změně všech vyrovnávacích pamětí jsou vyvolány události změny vyrovnávací paměti, počínaje nejhlubší vyrovnávací paměti.

### <a name="outlining"></a>Sbalování

Osnova je možnost rozbalit nebo sbalit různé bloky textu v textovém zobrazení. Osnova je definována <xref:Microsoft.VisualStudio.Text.Tagging.ITag>jako druh , stejným způsobem jako vylepšení jsou definovány. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> je značka, která definuje oblast textu, kterou lze rozbalit nebo sbalit. Chcete-li použít osnovu, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> musíte <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>importovat získat . Správce osnovy vyjmenovává, sbalí a rozšiřuje různé bloky, které jsou reprezentovány jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objekty, a podle toho vyvolá události.

### <a name="mouse-bindings"></a>Vázání myší

Myš vazby odkaz pohyby myši na různé příkazy. Myš vazby jsou <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>definovány pomocí , a klíče <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>vazby jsou definovány pomocí . Automaticky <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> vytvoří instance všech vazeb a připojí je k událostem myši v zobrazení.

Rozhraní <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> obsahuje obslužné rutiny událostí před procesem a po procesu pro různé události myši. Chcete-li zpracovat jednu z událostí, můžete <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>přepsat některé metody v .

### <a name="editor-operations"></a>Operace editoru

Operace editoru lze automatizovat interakci s editorem, pro skriptování nebo pro jiné účely. Můžete importovat <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> operace pro přístup <xref:Microsoft.VisualStudio.Text.Editor.ITextView>na dané . Tyto objekty pak můžete použít k úpravě výběru, posunu zobrazení nebo přesunutí stříšky do různých částí zobrazení.

### <a name="intellisense"></a>IntelliSense

Technologie IntelliSense podporuje dokončování příkazů, nápovědu k podpisu (označovanou také jako informace o parametrech), rychlé informace a žárovky.

Dokončení výkazu poskytuje automaticky otevírané seznamy potenciálních dokončení pro názvy metod, elementy XML a další prvky kódování nebo značek. Obecně gesto uživatele vyvolá relaci dokončení. Relace zobrazí seznam možných dokončení a uživatel může vybrat jeden nebo zrušit seznam. Je <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> zodpovědný za vytvoření a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>spuštění . Vypočítá <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> položky dokončení relace.

## <a name="see-also"></a>Viz také

- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Editor importy](../extensibility/editor-imports.md)
