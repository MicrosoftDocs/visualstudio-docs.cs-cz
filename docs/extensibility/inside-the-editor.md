---
title: V editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18587516298fa58e8a5e783ffb1f7c37d5a6b497
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859678"
---
# <a name="inside-the-editor"></a>V editoru
Editoru se skládá z několika různé subsystémy, které mají zachovat editoru samostatného modelu text ze zobrazení textu a uživatelské rozhraní.  
  
 Tyto části popisují různé aspekty editoru:  
  
- [Přehled subsystémů](../extensibility/inside-the-editor.md#overview-of-the-subsystems)  
  
- [Textový model](../extensibility/inside-the-editor.md#the-text-model)  
  
- [Zobrazení textu](../extensibility/inside-the-editor.md#the-text-view)  
  
  Tyto části popisují funkce editoru:  
  
- [Značky a třídění](../extensibility/inside-the-editor.md#tags-and-classifiers)  
  
- [Vylepšení](../extensibility/inside-the-editor.md#adornments)  
  
- [Projekce](../extensibility/inside-the-editor.md#projection)  
  
- [Sbalení](../extensibility/inside-the-editor.md#outlining)  
  
- [Vazby myši](../extensibility/inside-the-editor.md#mousebindings)  
  
- [Editor operace](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a>Přehled subsystémů  
  
### <a name="text-model-subsystem"></a>Subsystém modelu text  
 Subsystém modelu text zodpovídá za představující text a povolení její zpracování. Obsahuje podsystém modelu text <xref:Microsoft.VisualStudio.Text.ITextBuffer> rozhraní, které popisuje posloupnost znaků, které se mají zobrazit, můžete v editoru. Tento text můžete upravit, sledovány a jinak pracovat mnoha způsoby. Textový model také poskytuje typy pro následující aspekty:  
  
- Služba, která přidruží textové soubory a spravuje čtení a zápis v systému souborů.  
  
- Rozdílové služba, která najde minimální rozdíly mezi dvěma sekvencemi objektů.  
  
- Systém pro popis textu ve vyrovnávací paměti z hlediska podmnožiny textu v jiné vyrovnávací paměti.  
  
  Subsystém modelu text je zdarma koncepty uživatelské rozhraní (UI). Například není zodpovědná za rozložení textu nebo formátování textu a nemá žádné znalosti jazyka visual vylepšení, které může být spojen s textem.  
  
  Veřejné typy podsystém text modelu jsou obsaženy v *Microsoft.VisualStudio.Text.Data.dll* a *Microsoft.VisualStudio.CoreUtility.dll*, který záviset pouze na základní rozhraní .NET Framework Knihovna tříd a Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Subsystém zobrazení textu  
 Subsystém zobrazení textu je zodpovědná za formátování a zobrazení textu. Typy v tomto subsystému dělí do dvou vrstev, v závislosti na tom, zda typy Spolehněte se na Windows Presentation Foundation (WPF). Nejdůležitější typy <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, které řídí sadu řádků textu, které mají být zobrazeny a také blikajícího kurzoru, výběru a zařízení pro adorning text za použití prvků uživatelského rozhraní WPF. Tato subsystému také poskytuje okraje kolem textu umožňuje zobrazit oblast. Těchto okrajů je možné rozšířit a může obsahovat různé druhy obsahu a vizuální efekty. Okraje příklady číslo pruhy zobrazí a přejděte na řádku.  
  
 Veřejné typy subsystému zobrazení textu jsou obsaženy v *Microsoft.VisualStudio.Text.UI.dll* a *Microsoft.VisualStudio.Text.UI.Wpf.dll*. První sestavení obsahuje prvky nezávislá na platformě a druhý obsahuje prvky specifické pro WPF.  
  
### <a name="classification-subsystem"></a>Subsystém klasifikace  
 Subsystém klasifikace zodpovídá za určení vlastností písma pro text. Klasifikátor rozdělí text na různých tříd, například "– klíčové slovo" nebo "komentář". Formát mapování klasifikace se týká těchto tříd vlastností skutečné písma, například "Blue Consolas velikost písma 10 bodů". Tyto informace slouží zobrazení textu, formátuje a generuje text. Označování, které je popsáno podrobněji dále v tomto tématu, umožníte dat spojené s rozsahy textu.  
  
 Veřejné typy subsystému klasifikace jsou obsaženy v Microsoft.VisualStudio.Text.Logic.dll a komunikují s visual aspektů klasifikace, které jsou součástí Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Operace subsystému  
 Subsystém operace definuje chování editoru. Poskytuje implementaci pro příkazy editoru sady Visual Studio a systému vrácení zpět.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bližší pohled na textový model a zobrazení textu  
  
### <a name="the-text-model"></a>Textový model  
 Subsystém modelu textu se skládá z různých seskupení typů text. Patří mezi ně textovou vyrovnávací paměť, textových snímků a rozsahy text.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Vyrovnávací paměti textu a textových snímků.  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> Rozhraní představuje posloupnost znaků Unicode, které jsou zakódovány pomocí UTF-16, což je kódování používané `String` typu v rozhraní .NET Framework. Vyrovnávací paměť textu můžete nastavit jako trvalý, jako dokument systému souborů, ale tento krok není povinný.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> Slouží k vytvoření prázdné textové vyrovnávací paměti nebo vyrovnávací paměť textu, který je inicializován z řetězce nebo z <xref:System.IO.TextReader>. Vyrovnávací paměť textu můžete nastavit jako trvalý, do systému souborů jako <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Vyrovnávací paměť textu lze upravovat z žádného vlákna, dokud vlákno trvá vlastnictví textovou vyrovnávací paměť pomocí volání <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Potom můžete jenom toto vlákno provádění úprav.  
  
 Vyrovnávací paměť textu můžete projít mnoho verzí během celé jeho životnosti. Nová verze je generována pokaždé, když se do vyrovnávací paměti je upravovat a neměnné <xref:Microsoft.VisualStudio.Text.ITextSnapshot> představuje obsah vyrovnávací paměti, že tato verze. Protože jsou neměnné textových snímků, dostanete snímku text v libovolném vlákně, bez omezení, i v případě, že vyrovnávací paměť textu, který představuje stále se mění.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Textových snímků a snímek řádky textu  
 Obsah snímku text můžete zobrazit jako posloupnost znaků, nebo jako posloupnost řádky. Znaky a řádky jsou že obě indexované od nuly. Na snímku prázdný text obsahuje nulové znaky a jeden prázdný řádek. Řádek je oddělen libovolný platný sekvence znaků Unicode oddělených koncem řádku, nebo na začátek nebo konec vyrovnávací paměti. Konec řádku jsou explicitně znaky v textu snímku a ne všechny konce řádků ve snímku text mají být stejné.  
  
> [!NOTE]
>  Další informace o oddělených koncem řádku znaků v editoru sady Visual Studio najdete v tématu [kódování a zalomení řádků](../ide/encodings-and-line-breaks.md).  
  
 Řádek textu je reprezentována <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objektu, který můžete získat ze snímku text pro číslo určitého řádku nebo pro konkrétní znakem.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Body Snapshotpoint SnapshotSpans a NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> představuje pozici znaku ve snímku. Pozice je zaručeno, že leží mezi nulou a délka snímku. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> reprezentuje rozpětí textu ve snímku. Je zaručeno, že jeho koncová pozice ležet mezi nulou a délka snímku. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> Se skládá ze sady <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objekty ze stejné snímku.  
  
#### <a name="spans-and-normalizedspancollections"></a>Rozsahy a NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> představuje intervalu, který lze použít k rozpětí textu ve snímku textu. Pozice snímku jsou založený na nule, rozsahy můžete začít v jakékoliv pozici včetně nula. `End` Vlastnost rozpětí je roven součtu jeho `Start` vlastnost a její `Length` vlastnost. A `Span` neobsahuje znak, který je indexované podle `End` vlastnost. Například značka span, který má počáteční = 5 a délka = 3 má konec = 8, a obsahuje znaky v místech, 5, 6 a 7. Pro toto rozpětí se 5..8).  
  
 Dva rozsahy intersect, pokud mají všechny pozice v běžném, včetně koncová pozice. Proto je určena průsečíkem [3, 5) a [2, 7) je [3, 5) a je určena průsečíkem [3, 5) a [5, 7) je [5, 5). (Všimněte si, že [5, 5) je prázdný rozpětí.)  
  
 Dva rozsahy překrývat, pokud mají pozic v běžném, s výjimkou koncová pozice. Prázdný rozsah nikdy překrývá další rozpětí a překrytí dva rozsahy nikdy je prázdný.  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> je seznam rozsahy v pořadí podle vlastnosti Start rozsahy. V seznamu jsou sloučeny sousedící nebo překrývající se rozsahy. Mějme například sadu rozsahy [5..9), [0..1), [3..6), a [9..10), normalizovaná seznam rozsahy [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>Upozornění na změnu ITextEdit, TextVersion a text  
 Obsah vyrovnávací paměti textu lze změnit pomocí <xref:Microsoft.VisualStudio.Text.ITextEdit> objektu. Vytvoření takového objektu (pomocí jedné z `CreateEdit()` metody <xref:Microsoft.VisualStudio.Text.ITextBuffer>) spustí transakci text, který se skládá z úprav textu. Všechny úpravy nahrazuje některé rozsah textu ve vyrovnávací paměti řetězcem. Souřadnice a obsah každé úpravy jsou vyjádřeny vzhledem ke snímku vyrovnávací paměti při spuštění transakce. <xref:Microsoft.VisualStudio.Text.ITextEdit> Objekt upraví souřadnice úpravy, které jsou ovlivněny další úpravy v rámci jedné transakce.  
  
 Představte si třeba textovou vyrovnávací paměť, která obsahuje tento řetězec:  
  
```  
abcdefghij  
```  
  
 Použít transakci, která obsahuje dvě úpravy, jeden úpravy, který nahrazuje rozpětí na [2..4) pomocí znaku `X` a druhý úpravy, který nahrazuje rozpětí na [6..9) pomocí znaku `Y`. Výsledkem je této vyrovnávací paměti:  
  
```  
abXefYj  
```  
  
 Souřadnice pro druhý úpravy byly vypočítané s ohledem na obsah vyrovnávací paměti na začátku transakce, byla použita první upravit.  
  
 Změny do vyrovnávací paměti se projeví při <xref:Microsoft.VisualStudio.Text.ITextEdit> objektu je potvrzené voláním jeho `Apply()` metoda. Pokud se alespoň jeden neprázdný Upravit nový <xref:Microsoft.VisualStudio.Text.ITextVersion> se vytvoří nový <xref:Microsoft.VisualStudio.Text.ITextSnapshot> je vytvořen a jeden `Changed` událost se vyvolá. Každá verze text obsahuje jiný text snímku. Snímek text představuje stav dokončení textové vyrovnávací paměti po transakci upravit, ale textovou verzi popisuje pouze změny z jednoho snímku na další. Obecně platí textových snímků jsou jednou používat a zahodit, zatímco verze text musí zůstat naživu nechystáte nějakou dobu.  
  
 Obsahuje textovou verzí <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Tato kolekce jsou zde popsány změny, při použití snímku, vytvoří další snímek. Každý <xref:Microsoft.VisualStudio.Text.ITextChange> v kolekci obsahuje znak na pozici změnu, do nahrazeného řetězce a řetězci pro nahrazení. Do nahrazeného řetězce je prázdný pro základní vložení a řetězci pro nahrazení je prázdná pro základní odstranění. Normalizovaná kolekce je vždy `null` pro nejnovější verzi vyrovnávací paměti textu.  
  
 Pouze jeden <xref:Microsoft.VisualStudio.Text.ITextEdit> můžete vytvořit instanci objektu pro textovou vyrovnávací paměť v okamžiku, a všechny úpravy textu se musí provádět ve vlákně, které vlastní textové vyrovnávací paměti (Pokud byl vyžádaný vlastnictví). Úprava textu můžete opuštěných voláním jeho `Cancel` metoda nebo jeho `Dispose` metoda.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> také poskytuje `Insert()`, `Delete()`, a `Replace()` metody, které se podobají těm v nalezen <xref:Microsoft.VisualStudio.Text.ITextEdit> rozhraní. Toto volání má stejný účinek jako vytváření <xref:Microsoft.VisualStudio.Text.ITextEdit> objektu, podobně jako volání a následným použitím úpravy.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Body sledování a sledování rozpětí  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> Představuje pozici znaku ve vyrovnávací paměti textu. Pokud vyrovnávací paměť je upravit tak, aby pozice znaku a posunutí způsobí, že, bod sledování přesune s ním. Například pokud bod sledování odkazuje na 10 pozice ve vyrovnávací paměti a pět znaků, které jsou vložené na začátek vyrovnávací paměti, bod sledování pak odkazuje na pozici 15. Pokud vložení se odehrává na přesné umístění, které jsou označeny bod sledování, je dáno jeho chování jeho <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, což může být buď `Positive` nebo `Negative`. Pokud je režim sledování kladná, že sledování bod odpovídá stejnému znaku, který je teď na konci vložení; Pokud je záporné režimu sledování, bod sledování odkazuje na první vložený znak na původní pozici. Pokud je odstraněn znak na pozici, která je reprezentována bod sledování, bod sledování přesouvá na první znak, který následuje odstraněného rozsahu. Například pokud bod sledování odkazuje na znak na pozici 5 a odstraní se znaky na pozic 3 až 6, bod sledování odkazuje na znak na pozici 3.  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Představuje celou řadu namísto pouze jednu pozici. Její chování je dáno jeho <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Pokud je režim span sledování <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, sledování rozpětí roste začlenit text vložené na jeho okrajů; Pokud je režim span sledování <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, sledování rozpětí sestavené text vložené na jeho okrajů. Ale pokud je režim span sledování <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, vložení nabízených oznámení na aktuální pozici směrem k začátku a v případě režimu span sledování <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, vložení nabízených oznámení aktuální pozice na konci.  
  
 Získáte umístění bodu sledování nebo v rozsahu rozpětí sledování pro libovolný snímek textové vyrovnávací paměti, ke kterému patří. Body sledování a sledování rozsahy může být bezpečně odkazovat z libovolného vlákna.  
  
#### <a name="content-types"></a>Typy obsahu  
 Typy obsahu slouží jako mechanismus pro definování různé druhy obsahu. Typ obsahu může být typ souboru, například "text", "kód" nebo "binární" nebo typ technologie, jako je například "xml", "vb" nebo "c". Slova "pomocí" je například – klíčové slovo v jazyce C# a Visual Basic, ale ne v jiných programovacích jazycích. Definice toto klíčové slovo by proto omezena na typy obsahu "c" a "vb".  
  
 Typy obsahu jsou použity jako filtr pro vylepšení a další prvky v editoru. Mnoho funkcí editoru a Rozšiřovací body jsou definovány pro každý typ obsahu; barevné zvýrazňování textu se například liší pro soubory ve formátu prostého textu, soubory XML a soubory zdrojového kódu jazyka Visual Basic. Vyrovnávací paměti textu se obecně přiřazují typ obsahu, když jsou vytvořeny a můžete změnit typ obsahu textovou vyrovnávací paměť.  
  
 Typy obsahu může více dědit z jiné typy obsahu. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Umožňuje zadat více základních typů jako nadřazené položky daného typu obsahu.  
  
 Vývojáři můžou definovat jejich vlastní typy obsahu a zaregistrovat pomocí <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Mnoho funkcí editoru lze definovat s ohledem na konkrétní typ obsahu pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Například okraje editoru, vylepšení a obslužné rutiny myši můžete definovat tak, aby se vztahují pouze na editorů, které zobrazí konkrétní typy obsahu.  
  
###  <a name="the-text-view"></a>Zobrazení textu  
 Zobrazení součástí vzor model view controller (MVC) definuje textové zobrazení, formát zobrazení, grafické prvky, jako je například posuvník a blikajícím kurzorem. Všechny prvky prezentace editoru sady Visual Studio jsou založeny na WPF.  
  
#### <a name="text-views"></a>Zobrazení textu  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Rozhraní je nezávislá na platformě reprezentace zobrazení textu. Používá se především pro zobrazení v okně textové dokumenty, ale jej lze také pro jiné účely, třeba v popisku.  
  
 Zobrazení textu odkazuje na různé druhy vyrovnávací paměti textu. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Vlastnost odkazuje na <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> , která odkazuje na tyto tři různé textové vyrovnávací paměti: do vyrovnávací paměti dat, což je horní vyrovnávací paměti dat na úrovni, úpravy v vyrovnávací paměť, kde dojde k a visual vyrovnávací paměti, což je vyrovnávací paměť, která je Zobrazit v zobrazení textu.  
  
 Text formátována podle třídění, které jsou připojeny k základní textové vyrovnávací paměti a je opatřený pomocí poskytovatelů dalších úprav, které jsou připojeny k zobrazení textu, samotného.  
  
#### <a name="the-text-view-coordinate-system"></a>Souřadnicový systém zobrazení textu  
 Určuje souřadnicový systém zobrazení textu pozice v zobrazení textu. V tomto systému souřadnice x hodnota 0,0 odpovídá na levý okraj textu se zobrazí a hodnota y 0,0 odpovídá na horní okraj textu se zobrazí. Souřadnice x zvyšuje zleva doprava, a souřadnice y shora dolů.  
  
 Zobrazení (součást viditelný text v textovém okně) nemůže být stejným způsobem vodorovně posuvný jako je svisle posuvný. Oblast zobrazení je vodorovně posuvný tak, že změníte její levou souřadnici tak, aby se přesune s ohledem na návrhovém povrchu. Ale oblast zobrazení posunout svisle jenom změnou vykresleného textu, což způsobí, že <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> vyvolána událost.  
  
 Vzdálenost v souřadnicovém systému odpovídají logické pixelů. Pokud vykreslovací plochu text se zobrazí bez měřítka transformace, jednu jednotku v souřadnicovém systému vykreslování textu odpovídá na jeden pixel v zobrazení.  
  
#### <a name="margins"></a>Okraje  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Rozhraní představuje okraj a umožňuje řízení viditelnosti na okraj a jeho velikost. Existují čtyři předdefinované okraje, které jsou s názvem "Top", "Vlevo", "Vpravo" a "Dolů" a jsou připojeny k horní, dolní, levý nebo pravý okraj zobrazení. Těchto okrajů jsou kontejnery, ve kterých je možné použít jiné okraje. Rozhraní definuje metody, které vrací velikost na okraji a viditelnosti okraj. Okraje jsou vizuální prvky, které poskytují další informace o zobrazení textu, ke kterému jsou připojené. Například na okraji číslo řádku zobrazí čísla řádků pro zobrazení textu. Okraj piktogram zobrazuje prvky uživatelského rozhraní.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Rozhraní se stará o vytvoření a umístění rozpětí. Okraje lze provést řazení s ohledem na ostatní okraje. Okraj s vyšší prioritou jsou umístěno blíž k zobrazení textu. Například pokud existují dvě levý okraj, A okraj a okraj B a má s nižší prioritou než okraj A okraj B, okraj B, které se zobrazí nalevo od okraj A.  
  
#### <a name="the-text-view-host"></a>Hostitel zobrazení textu  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Rozhraní obsahuje zobrazení textu a všechny sousedící dekorace doprovázejících zobrazení, například posuvníky. Zobrazení hostitele text obsahuje také okraje, které jsou připojeny k ohraničení zobrazení.  
  
#### <a name="formatted-text"></a>Formátovaný text  
 Text, který se zobrazí v náhledu textu se skládá z <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objekty. Každý jednotlivý řádek zobrazení textu odpovídá jeden řádek textu v zobrazení textu. Dlouhé řádky v podkladových textovou vyrovnávací paměť může být částečně zakryto (Pokud není povoleno zalamování) nebo rozdělen do více řádků textu a zobrazení. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Rozhraní obsahuje metody a vlastnosti pro mapování mezi souřadnice a znaků a vylepšení, které může být spojen s řádku.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objekty vytvořené pomocí <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> rozhraní. Pokud máte obavy pouze text, který je zobrazen v zobrazení, můžete ignorovat zdroj formátování. Pokud vás zajímá ve formátu textu, který není v zobrazení (například pro podporu vyjmutí formátovaný text a vložte), můžete použít <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> formátování textu ve vyrovnávací paměti textu.  
  
 Zobrazení textu formáty jeden <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> najednou.  
  
## <a name="editor-features"></a>Funkce editoru  
 Funkce editoru jsou navrženy tak, aby definice funkce je oddělený od jeho implementace. Editor zahrnuje tyto funkce:  
  
-   Značky a třídění  
  
-   Vylepšení  
  
-   Projekce  
  
-   Sbalování  
  
-   Myš a klíč vazby  
  
-   Operace a primitiv  
  
-   IntelliSense  
  
### <a name="tags-and-classifiers"></a>Značky a třídění  
 Klíčová slova jsou značky, které jsou spojeny s rozsah textu. Jejich lze zobrazit různými způsoby, například pomocí barevné zvýrazňování textu, podtržení, grafické nebo automaticky otevíraná okna. Třídění je jeden typ značky.  
  
 Jiné druhy značky jsou <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> pro zvýraznění textu <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> pro sbalení, a <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> chyby kompilace.  
  
#### <a name="classification-types"></a>Typy klasifikace  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Rozhraní představuje třídu ekvivalence, což je abstraktní kategorie textu. Typy klasifikace může více dědit z jiných typů klasifikace. Například programovací jazyk klasifikace může obsahovat "– klíčové slovo", "komentář" a "identifikátor", které dědí nastavení z "kód". "Podstatné jméno", "akce" a "přídavného", jména, které dědí "přirozeného jazyka" může obsahovat typy klasifikace přirozeného jazyka.  
  
#### <a name="classifications"></a>Klasifikacích  
 Klasifikace instanci určité klasifikace typu, je obvykle konfigurovatelnou textu. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> se používá k reprezentování klasifikaci. Značka span klasifikace můžete představit jako popisek, který obsahuje konkrétní rozsah textu a říká systému, který tento text rozsahu je typu konkrétní klasifikaci.  
  
#### <a name="classifiers"></a>Třídění  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Virtuálních sítí je mechanismus, která rozdělí text na sadu klasifikace. Třídění musí být definována pro určité typy obsahu a vytvořit instance pro konkrétní textové vyrovnávací paměti. Klienti musí implementovat <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> k účasti v textu klasifikace.  
  
#### <a name="classifier-aggregators"></a>Třídění agregátorů  
 Třídění agregátoru virtuálních sítí je mechanismus, který kombinuje všechny třídění pro jednu textovou vyrovnávací paměť do jediné sady klasifikace. Například třídění C# a angličtinu třídění například vytvořit klasifikace na komentář v souboru C#. Vezměte v úvahu tento komentář:  
  
```  
// This method produces a classifier  
```  
  
 Třídění C# může označovat celý rozsah jako komentář a třídění angličtině může klasifikovat "vytvoří" jako "akce" a "method" jako "podstatné jméno". Agregátor vytvoří sadu překrývat klasifikace a typ objektu set je založen na všechny vaše příspěvky.  
  
 Agregátor třídění je také třídění, protože rozdělí text na sadu klasifikace. Agregátor třídění také zajišťuje, že neexistují žádné překrývající se klasifikace a že jsou seřazeny klasifikace. Jednotlivé třídění jsou zdarma vrátit libovolnou sadu klasifikace, v libovolném pořadí a překrývající se žádným způsobem.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Formátování klasifikace a barevné zvýraznění textu  
 Formátování textu je příkladem funkce, která je založená na klasifikaci text. Používá se ve vrstvě zobrazení textu k určení zobrazení textu v aplikaci. Formátování textu je závislá na WPF, ale není logické definice klasifikací.  
  
 Formát klasifikace je sada vlastností pro konkrétní klasifikaci typ formátování. Tyto formáty dědit z formátu nadřazený typ klasifikace.  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Je mapování typ klasifikace na sadu vlastností pro formátování textu. Implementace formát mapy v editoru zpracovává všechny exporty z formátů klasifikace.  
  
###   <a name="adornments"></a>Vylepšení  
 Vylepšení jsou grafické efekty, které přímo nesouvisejí s písma a barvy znaků v textové zobrazení. Například podtržení červená vlnovka, který se používá k označení – kompilace kódu v řadě programovacích jazyků je vložený dalších úprav a popisy tlačítek jsou místní vylepšení. Vylepšení jsou odvozeny z <xref:System.Windows.UIElement> a implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Jsou dva speciální typy dalších úprav značky <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, pro vylepšení, které zabírají stejné místo jako text v zobrazení, a <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, pro podtržení vlnovku.  
  
 Vložený vylepšení jsou obrázky, které tvoří část zobrazení formátovaného textu. Tyto jsou uspořádány do různých vrstev pořadí vykreslování. Existují tři předdefinované vrstvy, následujícím způsobem: text, blikajícího kurzoru a výběru. Vývojáři však můžete definovat další vrstvy a seřadit je podle vztahu mezi sebou. Jsou tři druhy vložený vylepšení grafické doplňky textu relativní (které přesunutí přesun text a se odstraní při odstranění textu), relativní k zobrazení grafických doplňků, (které jste prováděli pomocí jiné textové části zobrazení) a řídí vlastník vylepšení (na Vývojář musí spravovat jejich umístění).  
  
 Místní vylepšení jsou obrázky, které se zobrazí v malém okně nad zobrazení textu, například popisky.  
  
###  <a name="projection"></a> Projekce  
 Projekce je postup pro vytváření jiný typ textové vyrovnávací paměti, která ve skutečnosti neukládá textu, ale místo toho kombinuje text z jiné textové vyrovnávací paměti. Například projekce vyrovnávací paměť lze zřetězit text ze dvou dalších vyrovnávací paměti a zobrazí výsledky, pokud je v jediné vyrovnávací paměti nebo skrýt části textu v jedné vyrovnávací paměti. Projekce vyrovnávací paměť může fungovat jako zdrojová vyrovnávací paměť do vyrovnávací paměti jiného projekce. Chcete-li uspořádat text mnoha různými způsoby lze sestavit sadu vyrovnávacích pamětí, které se týkají projekcí. (Takové sadě se taky říká *vyrovnávací paměti grafu*.) Funkce sbalování text sady Visual Studio je implementovaný s využitím vyrovnávací paměti projekce ke skrytí sbalených textu a editoru sady Visual Studio pro stránky ASP.NET používá projekce pro podporu vložené jazyků, jako je například Visual Basic a C#.  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Je vytvořena pomocí <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Projekce vyrovnávací paměť je reprezentována seřazená posloupnost <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objekty, které jsou označovány jako *zdrojové rozsahy*. Obsah tyto rozsahy jsou uvedené jako posloupnost znaků. Textové vyrovnávací paměti, ze kterých se vykreslují zdrojové rozsahy jsou pojmenovány *zdrojové vyrovnávací paměti*. Klienti projekce vyrovnávací paměti není potřeba mějte na paměti, že se liší od vyrovnávací paměť běžného textu.  
  
 Vyrovnávací paměť projekce naslouchá událostem změny textu ve zdrojové vyrovnávací paměti. Když text ve zdroji span změny, vyrovnávací paměti projekce souřadnice změněného textu se mapuje na svůj vlastní souřadnice a vyvolává události odpovídající změny textu. Představte si třeba zdrojové vyrovnávací paměti A a B, které mají tento obsah:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Pokud vyrovnávací paměť projekce P je vytvořen ze dvou rozpětí textu, ten, který má všechny vyrovnávací paměti a dalších obsahující všechny vyrovnávací paměti B, P má následující obsah:  
  
```  
P: ABCDEvwxyz  
```  
  
 Pokud se podřetězec `xy` je odstraněn z vyrovnávací paměti B, pak vyrovnávací paměti P vyvolá událost, která označuje, že se odstranily znaky na pozice 7 a 8.  
  
 Vyrovnávací paměť projekce můžete také upravovat přímo. Ji postoupí úprav příslušné zdrojové vyrovnávací paměti. Například pokud řetězec je vložen do vyrovnávací paměti P na pozici 6 (původní pozici znaku "v"), se šíří vložení do vyrovnávací paměti B na pozici 1.  
  
 Existují omezení týkající se zdrojové rozsahy, které přispívají k projekci vyrovnávací paměti. Zdrojové rozsahy se nemohou překrývat; umístění ve vyrovnávací paměti projekce nelze mapovat na více než jedno umístění v jakékoli zdrojové vyrovnávací paměti a umístění, do zdrojové vyrovnávací paměti nelze mapovat na více než jedné oblasti ve vyrovnávací paměti projekce. Žádné circularities nejsou povoleny ve vztahu zdrojové vyrovnávací paměti.  
  
 Události jsou vyvolány při sadu zdrojové vyrovnávací paměti pro změny vyrovnávací paměti projekce a sadu source zahrnuje změny.  
  
 Vyrovnávací paměť elize je zvláštní druh projekce vyrovnávací paměti. Používá se především pro sbalení a pro operace, které rozbalit nebo sbalit bloky textu. Vyrovnávací paměť elize se odvíjí jenom jeden zdrojová vyrovnávací paměť a rozsahy ve vyrovnávací paměti elize musejí být seřazeny stejné jako jsou řazeny ve zdrojové vyrovnávací paměti.  
  
#### <a name="the-buffer-graph"></a>Graf vyrovnávací paměti  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Rozhraní umožňuje mapování mezi graf projekce vyrovnávacích pamětí. Všechny vyrovnávací paměti textu ve vyrovnávací paměti projekce se shromažďují orientovaného acyklického grafu, podobně jako strom abstraktní syntaxe, který je vytvořen pomocí kompilátoru jazyka. Graf je definována horní vyrovnávací paměti, což může být jakékoli textovou vyrovnávací paměť. Vyrovnávací paměť grafu můžete namapovat z bodu v horní vyrovnávací paměti do bodu ve zdrojové vyrovnávací paměti nebo z rozsahu v horní vyrovnávací paměti na sadu rozsahy ve zdrojové vyrovnávací paměti. Podobně může mapovat do bodu nebo spojíte zdrojová vyrovnávací paměť do bodu v horní vyrovnávací paměti. Grafy vyrovnávací paměti jsou vytvářeny instalační sadou <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
#### <a name="events-and-projection-buffers"></a>Události a projekce vyrovnávací paměti  
 Při změně vyrovnávací paměti projekce změny odesílají z projekce vyrovnávací paměť do vyrovnávací paměti, které jsou na ní závislé. Po změně všechny vyrovnávací paměti jsou vyvolány události změny vyrovnávací paměti, počínaje nejhlubší vyrovnávací paměti.  
  
###  <a name="outlining"></a> Sbalování  
 Sbalení je schopnost rozbalit nebo sbalit různé bloky textu v textovém zobrazení. Sbalení je definována jako typ z <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, v stejným způsobem, jak jsou definovány vylepšení. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> jsou klíčová slova, která definuje, které můžete rozbalit nebo sbalit oblast textu. Pokud chcete použít, osnovy, je nutné naimportovat <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> zobrazíte <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Sbalování správce vytvoří výčet sbalí a rozbalí různé bloky, které jsou reprezentovány ve formě <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objektů a vyvolává události odpovídajícím způsobem.  
  
###  <a name="mousebindings"></a> Vazby myši  
 Vazby myši propojit různé příkazy pohyby myší. Myši vazby jsou definované pomocí <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, a klávesové zkratky jsou definované pomocí <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Automaticky inicializuje všechny vazby a připojí je k události myši v zobrazení.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Rozhraní obsahuje předběžného zpracování a následného zpracování obslužné rutiny události různých myši. Úchyt pro jednu z událostí, můžete přepsat některé metody v <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Editor operace  
 Editor operací můžete použít k automatizaci interakci s editoru pro skriptování nebo z jiných důvodů. Můžete importovat <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> přístup k operacím na daný <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Pak můžete tyto objekty k úpravě výběru, posuňte zobrazení nebo přesune blikající kurzor do různých částí zobrazení.  
  
###  <a name="intellisense"></a> Technologie IntelliSense  
 Technologie IntelliSense podporuje doplňování výrazů, signaturám (označované také jako informace o parametrech), rychlé informace a návrhy.  
  
 Dokončování příkazů obsahuje místní seznam potenciální dokončování pro názvy metod, prvky XML a další prvky kódu nebo značky. Obecně platí gesto uživatele vyvolá relace dokončení. Relace zobrazí seznam možných dokončení, a uživatel může vybrat jednu nebo zavřít seznamu. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> Zodpovídá za vytvoření a aktivace <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Vypočítá <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> položek dokončení pro relaci.  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)   
 [Importy do editoru](../extensibility/editor-imports.md)
