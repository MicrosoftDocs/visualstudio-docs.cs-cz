---
title: Obrázky a ikony
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 843829c56fcbd2f5c558d7c4a8b14a660a431eac
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558218"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrázky a ikony pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_ImageUseInVisualStudio"></a>Použití obrázku v aplikaci Visual Studio
 Před vytvořením kresby zvažte použití 1000 imagí v [knihovně imagí sady Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy imagí

- **Ikony**. Malé obrázky, které se zobrazují v příkazech, hierarchie, šablon a tak dále. Výchozí velikost ikona používaná v sadě Visual Studio je PNG 16 x 16. Ikony vytvářených služba bitových kopií automaticky generovat formátu XAML pro podporu HDPI.

     **Poznámka:** I když se obrázky používají v systému nabídek, neměli byste pro každý příkaz vytvořit ikonu. Podívejte se na [nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) , abyste viděli, jestli by se měl váš příkaz dostat na ikonu.

- **Snímků.** Obrázky používané v části dialogového okna, jako je například dialogové okno Nový projekt ve verzi preview.

- **Obrázky dialogových oken** Bitové kopie, které se zobrazí v dialogových oknech nebo průvodce, buď jako zprávy ukazatele nebo popisný grafiky. Použijte jen zřídka a pouze v případě potřeby k objasnění konceptu obtížné nebo k získání pozornosti uživatele (upozornění, upozornění).

- **Animované obrázky.** Použít indikátory průběhu, stavovém řádku a dialogů operace.

- **Kurzory.** Umožňuje určit, zda je povolena operace pomocí myši, kde objekt může být zrušená a tak dále.

## <a name="BKMK_IconDesign"></a>Návrh ikony

### <a name="overview"></a>Přehled
 Visual Studio používá moderní styl ikony, které čisté geometrie a rozdělení 50/50 zůstatek pozitivní nebo negativní (světlý/tmavý) a použijte metaphors s přímým přístupem, srozumitelné. Zásadní ikona center body návrhu kolem přehlednost zjednodušení a kontext.

- **Přehlednost:** Zaměřte se na základní metafora, který dává ikonu jeho významu a jednotlivce.

- **Zjednodušení:** zmenšete ikonu na svůj základní význam – Získejte motiv napříč pomocí pouze nezbytných prvků a žádné Frills.

- **Kontext:** Vezměte v úvahu všechny aspekty role ikony během vývoje konceptů, což je rozhodující při rozhodování, které prvky představují základní metafora ikony.

  S ikonami existuje několik bodů, aby:

- Nepoužívejte ikon, které místo prvky uživatelského rozhraní s výjimkou v případě potřeby. Zvolte abstraktní nebo symbolické přístup, pokud prvek uživatelského rozhraní není běžné, zřejmá, ani jedinečný.

- Nelíbí společné prvky nadměrnému využití dokumentů, složky, šipky a ikonu lupy. Pomocí těchto prvků pouze v případě, že je velmi důležité na ikonu význam. Například na lupu směřující doprava by měla zobrazovat pouze vyhledávání, procházet a vyhledat.

- I když některé prvky starší ikona udržovat použití perspektivy, nevytvářejte nové ikony prostorových Pokud element nemá přehlednost bez něj.

- Není cram příliš mnoho informací do ikonu. Jednoduchý obrázek, který lze snadno rozpoznat nebo se naučili jako symbol rozpoznatelných je mnohem užitečnější než bitovou kopii příliš složitý. Ikona nelze poskytují kompletní představu.

### <a name="icon-creation"></a>Ikona vytvoření

#### <a name="concept-development"></a>Koncepce rozvoje
 Visual Studio obsahuje ve svém uživatelském rozhraní nejrůznější typy ikon. Pečlivě zvažte ikonou typu během vývoje. Nepoužívejte jasné nebo neobvyklé objektů uživatelského rozhraní pro vaše ikona prvky. Vyjádřit souhlas s symbolický odkaz v těchto případech, například s ikonou inteligentních značek. Mějte na paměti, že význam abstraktní značky na levé straně je jasnější než verze vágní, na základě uživatelského rozhraní na pravé straně:

|||
|-|-|
|**Správné použití symbolického snímků**|**Nesprávné použití symbolického snímků**|
|![Správná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404 – 01_SmartTagCorrect")|![Nesprávná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404 – 02_SmartTagIncorrect")|

 Existují případy, ve kterých prvky uživatelského rozhraní pro standardní, snadno zjistíte fungují dobře u ikony. Přidáte že okno je jedním z takových příkladů:

|||
|-|-|
|**Správné prvky uživatelského rozhraní v ikoně**|**Nesprávný prvek uživatelského rozhraní v ikoně**|
|![Správná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404 – 03_AddWindowCorrect")|![Nesprávná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404 – 04_AddWindowIncorrect")|

 Nepoužívejte dokument jako základní prvek Pokud to je velmi důležité na ikonu význam. Bez dokumentů dojde ke ztrátě, element v dokumentu přidat (význam níže), že při aktualizaci není potřeba sdělit význam element dokumentu.

|||
|-|-|
|**Správné použití ikony dokumentu**|**Nesprávné použití ikony dokumentu**|
|![Ikona správné ikony dokumentu](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404 – 05_DocumentIconCorrect")|![Nesprávná Ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404 – 06_DocumentIconIncorrect")|

 Pojem "show" by měla být reprezentovaná ikonu, která nejlépe znázorňuje, co je zobrazeno, například stejně jako u příkladu zobrazit všechny soubory. Metafora přehledu slouží k označení pojmu "Zobrazit" v případě potřeby, jako v příkladu zobrazení prostředků.

|||
|-|-|
|**Uvádí**|**Zobrazení**|
|![Zobrazit ikonu](../../extensibility/ux-guidelines/media/0404-07-show.png "0404 – 07_Show")|![Ikona zobrazení](../../extensibility/ux-guidelines/media/0404-08-view.png "0404 – 08_View")|

 Pravého okraje zvětšení ikonu lupy, by měla pouze představují hledání, hledání a procházení. Variant směřující na levé straně s znaménko plus nebo minus by měla představují pouze přiblížit / oddálení.

|||
|-|-|
|**Nápovědě**|**Přibliž**|
|![Ikona hledání](../../extensibility/ux-guidelines/media/0404-09-search.png "0404 – 09_Search")|![Ikona přiblížení](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404 – 10_Zoom")|

 Ve stromové zobrazení, nepoužívejte na ikonu složky a modifikátor. Pokud je k dispozici, použijte pouze modifikátor.

|||
|-|-|
|**Správné ikony stromového zobrazení**|**Nesprávné ikony zobrazení stromu**|
|![Ikona &#40;správné stromové zobrazení&#41; 1](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404 – 11_TreeViewCorrect1") ![správná ikona &#40;stromového&#41; zobrazení 2](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404 – 12_TreeViewCorrect2")|![Nesprávná ikona &#40;zobrazení&#41; stromu 1](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404 – 13_TreeViewIncorrect1") ![ &#40;nesprávná&#41; ikona zobrazení stromu 2](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404 – 14_TreeViewIncorrect2")|

### <a name="style-details"></a>Podrobnosti o stylu

#### <a name="layout"></a>Rozložení
 Prvky zásobníku, jak je znázorněno pro standardní ikony 16 x 16:

 ![Zásobník rozložení pro ikony 16x16](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404 – 15_LayoutStack")

 **Zásobník rozložení pro ikony 16x16**

 Stav oznámení prvky jsou lepší použít jako samostatný ikony. Existují kontextech, ve kterých oznámení by měl být skládaný na základní element, jako se ikona dokončeného úkolu:

 ![Samostatná oznámení v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404 – 16_StandaloneNotificationIcons")

 **Samostatné ikony oznámení**

 ![Ikona dokončení úlohy](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404 – 17_TaskComplete")

 **Ikona dokončení úlohy**

 Ikony projektu jsou obvykle .ico soubory, které obsahují více velikostí. Většina ikony 16 x 16 obsahují stejné elementy. Verze 32 x 32 mají další podrobnosti, včetně typu projektu v případě potřeby.

 ![Ikony projektu v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404 – 18_IconProjectThreeSizes")

 **Ikony projektu knihovny ovládacích prvků systému Windows VB, 16x16 a 32x32**

 System Center ikony v rámci jeho pixelů. Pokud to není možné, zarovnejte ikony do horní části a/nebo napravo od rámce.

 ![Ikona na střed snímku v pixelech](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404 – 19_IconCentered")

 **Ikona na střed snímku v pixelech**

 ![Ikona zarovnaná do pravé horní části pixelového rámečku](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404 – 20_IconTopRight")

 **Ikona zarovnaná vpravo nahoře v rámci rámečku**

 ![Ikona zarovnané na střed a zarovnání do horní části rámce pixelu](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404 – 21_IconTopAlign")

 **Ikona na střed a zarovnání do horní části rámce**

 K dosažení ideální zarovnání a zůstatek, vyhněte se neblokuje element base na ikonu s glyfy akce. Místo glyfů v horní levé části base element. Při přidávání dalších elementu, vezměte v úvahu zarovnání a zbytek na ikonu.

|||
|-|-|
|**Správné zarovnání a vyrovnání**|**Nesprávné zarovnání a zůstatek**|
|![Správný zůstatek a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404 – 22_AlignBalanceCorrect")|![Nesprávný vyvážení a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404 – 23_AlignBalanceIncorrect")|

 Zkontrolujte velikost parity u ikon, které sdílejí elementy a se používají v sadách. Všimněte si, že v nesprávné párování kruh a šipku nadměrnou velikost a se neshodují.

|||
|-|-|
|**Parita správné velikosti**|**Nesprávná parita velikosti**|
|![Správná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404 – 24_SizeParityCorrect")|![Nesprávná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404 – 25_SizeParityIncorrect")|

 Pomocí řádků a vizuální váhy. Vyhodnoťte, jak na ikonu, kterou vytváříte porovná s ikonami ostatních pomocí porovnání vedle sebe. Nikdy nepoužívejte celý 16 x 16 rámce, použijte 15 × 15 nebo menší. Poměr negativní pozitivní (tmavá light) by měl být rozdělení 50/50.

|||
|-|-|
|**Správný poměr záporných k kladnému**|**Nesprávný negativ na kladný poměr**|
|![Správná vizuální váha pro ikony &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404 – 26_VisualWeightCorrect1")<br /><br /> ![Správná vizuální váha pro ikony &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404 – 27_VisualWeightCorrect2")<br /><br /> ![Správná vizuální váha pro ikony &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404 – 28_VisualWeightCorrect3")|![Nesprávná vizuální váha pro ikony](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404 – 29_VisualWeightIncorrect")|

 Použijte jednoduchý, srovnatelné tvary a úhly doplňkové k vytváření elementů aniž byste museli obětovat element integrity. Použijte 45 stupňů nebo 90° úhly, kde je to možné.

 ![Správné úhly ikon](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404 – 30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektiva
 Zachovejte na ikonu jasný a srozumitelný. Pomocí perspektivy a světelného zdroje jenom v případě potřeby. I když mělo by se vyhnout pomocí perspektivy u elementů ikonu, některé prvky nerozpoznatelný bez něj. V takových případech komunikuje stylizované perspektivy přehlednost daného elementu.

 ![Perspektiva 3&#45;bodů](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404 – 31_3PointPerspective")

 **Perspektiva 3 bodů**

 ![Perspektiva 1&#45;bodu](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404 – 32_1PointPerspective")

 **Perspektiva 1 bodů**

 Většinu prvků by měl být připojena nebo vpravo v lomených.

 ![Ikony šikmé vpravo](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404 – 33_AngledRight")

 Použijte zdroje světla pouze v případě, že přidáte nezbytné přehlednost na objekt.

|||
|-|-|
|**Správný zdroj světla**|**Nesprávný zdroj světla**|
|![Správné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404 – 34_LightSourcesCorrect")|![Nesprávné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404 – 35_LightSourcesIncorrect")|

 Použijte jsou podrobněji popsány dále pouze ke zvýšení čitelnost a lepší komunikaci metafora. Zůstatek pozitivní záporná (dark-light) by měl být rozdělení 50/50.

|||
|-|-|
|**Správné použití obrysů**|**Nesprávné použití obrysů**|
|![Správné osnovy](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404 – 36_OutlinesCorrect")|![Nesprávné osnovy](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404 – 37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 Ikony **prostředí a panelů příkazů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Ikony prostředí a panelu příkazů](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404 – 38_ShellIcons")

 **Příklady ikon prostředí a panelů příkazů**

 Ikony **panelu příkazů v okně nástrojů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Ikony panelu příkazů v okně nástrojů](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404 – 39_ToolWindowCommandBarIcons")

 **Příklady ikon panelu příkazů v okně nástrojů**

 Ikony **nejednoznačnosti stromového zobrazení** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Ikony nejednoznačnosti stromového zobrazení](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404 – 40_TreeViewIcons")

 **Příklady ikon nejednoznačnosti stromového zobrazení**

 Ikony **taxonomie hodnot založené na stavu** existují v následujících stavech: aktivní, aktivní zakázané a neaktivní zakázané.

 ![Ikony&#45;hodnot taxonomie založené na stavu](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404 – 41_StateBasedTaxonomy")

 **Příklady ikon taxonomie hodnot založených na stavu**

 Ikony **IntelliSense** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor a jeden stav.

 ![Ikony IntelliSense](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404 – 42_IntelliSenseIcons")

 **Příklady ikon technologie IntelliSense**

 **Malé (16x16) ikony projektu** by neměly mít více než dva prvky: jeden základní a jeden modifikátor.

 ![16x16 &#40;ikona projektu 1&#41; ](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404 – 43_16x16Project1") ![16x16 ikona projektu &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404 – 44_16x16Project2") ![16x16 &#40;ikona projektu 3&#41; ](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404 – 45_16x16Project3")

 **Příklady malých (16) ikon projektu**

 **Velké (32x32) ikony projektu** se skládají z více než čtyř z následujících prvků: jedna základna, jedna až dvě Modifikátory a jedna překryva jazyka.

 ![ikony projektu 32x32](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404 – 46_32x32Project")

 **Příklady velkých (32x32) projektových ikon**

### <a name="production-details"></a>Podrobnosti o výrobní
 Všechny nové prvky uživatelského rozhraní by měl být vytvořen pomocí Windows Presentation Foundation (WPF) a všechny nové ikony pro WPF musí být ve formátu PNG 32-bit. PNG – 24 bitů je starší verze formátu, který nepodporuje transparentnosti a nedoporučuje se u ikony.

 Uložte řešení při 96 DPI.

#### <a name="file-types"></a>Typy souborů

- **32 bitová verze PNG:** upřednostňovaný formát pro ikony. Formát souboru komprese beze ztrát dat, který může ukládat bitové kopie jedné rastrových (v pixelech). 32-bit soubory PNG podporují průhlednost alfa kanálu, gama korekce a prokládání.

- **32-bitová BMP:** pro jiné ovládací prvky než WPF. Označovaný taky jako XP nebo vysokou color, 32-bit BMP je RGB/A image ve formátu, true color image s transparentnost alfa kanálu. Kanál alfa je vrstva průhlednosti určené v aplikaci Adobe Photoshop, která se pak uloží v rámci rastrového obrázku jako další (čtvrté) barevného kanálu. Černé pozadí se přidá během kresby produkční na všechny soubory BMP 32-bit zajistit rychlé vizuální upozornění o barevnou hloubku. Tato černé pozadí představuje oblasti, ke které zamaskuje v uživatelském rozhraní.

- **32-bit ICO:** pro ikony projektu a přidat položku. 32bitové true barvy s alfa kanálu transparentnosti jsou všechny soubory ICO (RGB/A). Protože více velikostí a barev hlubin můžete ukládat soubory ICO, Vista ikony jsou často ve formátu ICO obsahující 16 x 16, 32 x 32, 48 x 48 a velikost 256 x 256. Aby bylo možné zobrazit správně v Průzkumníku Windows, ICO, soubory musí být uložit dolů do hlubin 24 bitů a 8 bitů barev pro velikost každého obrázku.

- **XAML:** pro návrhové plochy a doplňky Windows. Ikony XAML jsou vektorové obrázky, které podporují škálování, otáčení, archivace a transparentnost. Nejsou běžné v sadě Visual Studio ještě dnes, ale jsou stále oblíbenější z důvodu jejich flexibilitu.

- **SVG**

- **24BITOVÉ BMP:** pro panel příkazů sady Visual Studio. Formát obrázku RGB true-color, BMP 24-bit je ikona konvence, která vytvoří vrstvu transparentnosti pomocí Purpurová (R = 255, G = 0, B = 255) jako barevný kód pro vrstvu navýšením kapacity knock průhlednosti. Ve 24-bit BMP jsou zobrazeny všechny plochy purpurová barvou pozadí.

- **24bitového formátu GIF:** pro panel příkazů sady Visual Studio. True – barva RGB bitové kopie formátu, který podporuje průhlednost. Soubory GIF se často používají v kresbě průvodce a animací ve formátu GIF.

### <a name="icon-construction"></a>Ikona konstrukce
 Nejmenší velikost ikony v sadě Visual Studio je 16 x 16. Největší v běžných použití je 32 x 32. Mějte na paměti nechcete zaplní celý 16 x 16, 24 × 24 nebo 32 x 32 rámce při navrhování ikonu. Ikona čitelné, jednotné konstrukce je nezbytné pro rozpoznávání uživatele. Při vytváření ikony proto zavázala dodržovat následující body.

- Ikony by měl být jasné, srozumitelné a konzistentní vzhledem k aplikacím.

- Je lepší použít elementy oznámení stavu jako jeden ikony a ne do zásobníku nad základní prvek ikonu. V některých kontextech může vyžadovat uživatelské rozhraní elementu stav, který chcete spárovat s elementem base.

- Ikony projektu jsou obvykle .ico soubory, které obsahují několik velikostí. Pouze rozměr 16 × 16, 24 × 24 a 32 × 32 ikony se aktualizují. Většina 16 x 16 a 24 × 24 ikony se obsahují stejné elementy. Ikony 32 x 32 obsahují další podrobnosti, včetně typ projektu jazyka v případě potřeby.

- U ikon, 32 x 32 základní elementy mají obvykle tloušťku čáry 2 pixelů. Tloušťka čáry 1 nebo 2 pixelů může použitých pro elementy podrobností. Chcete-li zjistit, která je vhodnější použijte nejlepší rozhodnutí.

- Máte nejméně s 1 pixelu mezery mezi elementy pro rozměr 16 × 16 a ikony 24 × 24. Ikony 32 x 32 použijte 2 pixel mezery mezi elementy a mezi modifikátor a base element.

  ![Mezery mezi prvky pro ikony 16x16, 24x24 a 32x32](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404 – 47_ElementSpacing")

  **Mezery mezi prvky pro velikost ikon 16x16, 24x24 a 32x32**

#### <a name="color-and-accessibility"></a>Barvy a usnadnění přístupu
 Zásady dodržování předpisů Visual Studio vyžadují, aby všechny ikony v rámci produktu předat požadavky na usnadnění přístupu barvy a kontrast. Toho můžete dosáhnout inverzi ikonu a při návrhu, byste měli vědět, že se bude obrácený prostřednictvím kódu programu v rámci produktu.

 Další informace o použití barev v ikonách sady Visual Studio naleznete v tématu [použití barev v obrázcích](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Použití barev v obrázcích

### <a name="overview"></a>Přehled
 Ikony v sadě Visual Studio jsou primárně Monochromatický. Barva je vyhrazená k předání konkrétních informací a nikdy pro dekoraci. Barva se používá:

- označuje akci

- Upozornit uživatele na oznámení o stavu

- Chcete-li určit jazyk přidružení

- k rozlišení položek v rámci technologie IntelliSense

### <a name="accessibility"></a>Přístupnost
 Zásady dodržování předpisů Visual Studio vyžadují, že všechny ikony zapsány do produktu průchod požadavků usnadnění přístupu pro barvy a kontrast. Barev v paletě vizuálního jazyka byly testovány a tyto požadavky splňují.

#### <a name="color-inversion-for-dark-themes"></a>Inverze barev pro tmavé motivy
 Aby bylo možné ikony se zobrazí s správné kontrastní poměr v tmavém motivu sady Visual Studio, se použije inverzi prostřednictvím kódu programu. Barvy v této příručce se rozhodli v části tak, aby se správně Invertovat. Omezit použití barev palety nebo dojde k nepředvídatelným výsledkům se použije inverzi.

 ![Příklady ikon, jejichž barvy byly obráceny](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **Příklady ikon, u kterých byly barvy převráceny**

### <a name="base-palette"></a>Základní paleta
 Všechny standardní ikony obsahuje tři základní barev. Ikony obsahovat žádné přechody nebo stíny s jednu nebo dvě výjimky pro 3D nástroj ikony.

|Využití|Název|Hodnota (světlý motiv)|Vzorníku|Příklad|
|-----------|----------|---------------------------|------------|-------------|
|Pozadí nebo tmavý|VS BG|424242 / 66,66,66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Základní paleta – příklad](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|Popředí/světla|VS FG|F0EFF1 / 240,239,241|![F0EFF1 vzorníku](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Obrys|VS navýšení kapacity|F6F6F6 / 246,246,246|![F6F6F6 vzorníku](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Kromě základní barvy jednotlivé ikony může obsahovat jednu další barvu z palety rozšířené.

### <a name="extended-palette"></a>Rozšířené palety

#### <a name="action-modifiers"></a>Modifikátory akce
 Následující čtyři barvy zahrnovaly typy akce vyžadované Modifikátory akce:

|Využití|Název|Hodnota (všechny motivy)|Vzorníku|
|-----------|----------|--------------------------|------------|
|Kladné|Zelená akce VS|388A34 / 56,138,52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Záporný|Červená akce VS|A1260D / 161,38,13|![A1260D vzorníku](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Neutrální|Modrá akce VS|00539C / 0,83,156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Vytvořit nový|Akcí Orange VS|C27D1A / 194,156,26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Příklady
 Zelená se používá pro modifikátory kladné akce, jako je například "Add", "Spuštění," "Play" a "Ověřit".

|||||
|-|-|-|-|
|Spuštění ![ikony spuštění](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun")|Spustit **dotaz** s ![ikonou dotazu](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery")|![Přehrání všech kroků ikona](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **Přehrát všechny kroky**|Přidat **ovládací prvek** ![ikona ovládacího prvku](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") přidat|

 Červená se používá pro modifikátory negativní akce, jako "Odstranit," "Stop", "Storno" a "Zavřít".

|||||
|-|-|-|-|
|![Ikona odstranění](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") vztahu **odstranění relace**|![Ikona odstranění](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") sloupce – **Odstranit sloupec**|![Zastavit](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") **dotaz na** ukončení ikony dotazu|Připojení ![offline ikony připojení](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") offline|

 Modrá je použita na neutrální akce modifikátory nejčastěji reprezentovány šipkami, jako například "Otevřít," "Next", "Předchozí", "Import" a "Export".

|||||
|-|-|-|-|
|![Přejít na ikonu pole](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") **Přejít k poli**|Dávková vrácení se změnami ![&#45;v](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") dávce dávkového vrácení **se** změnami|**Editor** adres ![ikona editoru adres](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor")|**Editor přidružení** ![ikona editoru přidružení](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor")|

 Tmavě gold se používá především pro modifikátor "New".

|||||
|-|-|-|-|
|![Ikona nového projektu](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **Nový projekt**|![Vytvořit novou ikonu grafu](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") **vytvořit nový graf**|![Nová ikona testu jednotek](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") – **Nový test jednotek**|![Nová](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") položka seznamu – ikona nové položky **seznamu**|

#### <a name="special-cases"></a>Zvláštní případy
 Ve zvláštních případech modifikátor barevné akce lze nezávisle na sobě jako samostatné ikonu. Barva použitá pro ikonu odráží akce, které je přidružený ikonu. Toto použití je omezené na malou podmnožinu ikony, včetně:

||||||
|-|-|-|-|-|
|Spuštění ![ikony spuštění](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun")|Zastavení ![ikony zastavení](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop")|![Odstranit ikonu](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **Delete**|Uložit ![ikonu](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **Uložit**|![Přejít zpátky ikonu zpět](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Kód hierarchie palety

#### <a name="folder"></a>Složka

|Využití|Název|Hodnota (všechny motivy)|Vzorníku|Příklad|
|-----------|----------|--------------------------|------------|-------------|
|Složky|Složka|DCB67A / 220,182,122|![DCB67A vzorníku](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Ikona barvy složky](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Jazyky sady Visual Studio
 Každá z běžných jazycích či platformách, které jsou k dispozici v sadě Visual Studio obsahuje odpovídající barva. Tyto barvy použijí na ikonu základní nebo modifikátorů jazyka, které se zobrazují v pravém horním rohu složené ikony.

|Využití|Název|Hodnota (všechny motivy)|Vzorníku|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|Modrá HTML WPF ASP|0095D 7 / 0,149,215|![0095D7 vzorníku](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP nachová|9B4F96 / 155,79,150|![9B4F96 vzorníku](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS zelenou (Green VS akce)|388A34 / 56,138,52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|Červená šablon stylů CSS|BD1E2D / 189,30,45|![BD1E2D vzorníku](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|Služba FS nachová|672878 / 103,40,120|![Vzorník 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|Oranžová JS|F16421 / 241,100,33|![F16421 vzorníku](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|Modrá VB (modrá VS akce)|00539C / 0,83,156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|Oranžová TS|E04C06 / 224,76,6|![E04C06 vzorníku](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|Zelená PY|879636 / 135,150,54|![Vzorník 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Příklady ikony modifikátory přístupu jazyka

|||||||
|-|-|-|-|-|-|
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![Ikona&#35; jazyka C](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp")**C#**|![Ikona&#43; &#43; jazyka C](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus")**C++**|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp")**F#**|JavaScript – ![ikona](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScriptu**|![Ikona Pythonu](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|HTML ![ikona](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|CSS – ![ikona](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![Ikona TypeScript](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 Ikony technologie IntelliSense pomocí exkluzivní barevné palety. Tyto barvy se používají k poskytování pomoci uživatelům rychle odlišit různé položky v seznamu automaticky otevírané okno technologie IntelliSense.

|Využití|Název|Hodnota (všechny motivy)|Vzorníku|
|-----------|----------|--------------------------|------------|
|Třída událostí|Akcí Orange VS|C27D1A / 194,125,26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Metody rozšíření, delegát metody, modul,|Akce nachová VS|652D 90 / 101,45,144|![652D90 vzorníku](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Pole, položku výčtu, – makro, struktura, typ Union hodnotu, operátor, rozhraní|Modrá akce VS|00539C / 0,83,156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Objekt|Zelená akce VS|388A34 / 56,138,52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Konstanta, výjimky, položku výčtu, Map, položka mapování, Namespace, šablony, definice typu|Na pozadí (VS BG)|424242 / 66,66,66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Příklady ikony technologie IntelliSense

||||||
|-|-|-|-|-|
|**Třída** ![ikon technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass")|Soukromá **událost** ![ikony technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|**Delegát** ![ikony delegáta technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Metoda IntelliSense – ikona přítele](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") – **přítel**|**Pole** ![ikony pole](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field")|
|Chráněná **Položka výčtu** chráněného výčtu ![technologie IntelliSense – ikona položky](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|**Objekt** ![ikony objektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject")|**Šablona** ![ikony šablony technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate")|Zástupce výjimky ![technologie IntelliSense ikona zkratky](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")||

### <a name="notifications"></a>Oznámení
 Oznámení v sadě Visual Studio se používají k označení stavu. Paleta oznámení pomocí následující čtyři barvy, jakož i možností výplně černé nebo bílé popředí, definuje oznámení s následující úrovní stavu.

|Využití|Název|Hodnota (všechny motivy)|Vzorníku|
|-----------|----------|--------------------------|------------|
|Stav: neutrální|Modrá oznámení (VS modrá)|1BA1E2 / 27,161,226|![1BA1E2 vzorníku](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Stav: pozitivní|Oznámení zelenou (VS Green)|339933 / 51,153,51|![Vzorník 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Stav: záporná|Oznámení Red (červená VS)|E51400 / 229,20,0|![E51400 vzorníku](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Stav: upozornění|Žlutá oznámení (VS oranžová)|FFCC00 / 255,204,0|![FFCC00 vzorníku](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Výplň popředí|Oznámení černé (Black)|000000 / 0,0,0|![000000 &#35;vzorníku](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Výplň popředí|Oznámení prázdné (prázdné)|FFFFFF / 255,255,255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Příklady oznamovací ikony

|||||
|-|-|-|-|
|**Výstraha** ![ikony výstrahy](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert")|**Upozornění** na ![ikonu upozornění](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning")|![Úplná ikona](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **dokončena**|Zastavení ![ikony zastavení](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop")|

### <a name="visual-studio-online"></a>Visual Studio Online
 Obecně platí Visual Studio Online se skládá z funkcí hostované v prohlížeči. Barva se liší v různých prostředích, ale styl zůstává stejná.

|Skupina|Využití|Název|Hodnota (všechny motivy)|Vzorníku|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Pozadí|TFSO BG|656565/ 101, 101, 101|![Vzorník 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Obrys|TFSO NAVÝŠENÍ KAPACITY|FFFFFF / 255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Pozadí|White|FFFFFF / 255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Monako|Pozadí|White|FFFFFF / 255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Pozadí|White|FFFFFF / 255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normální|F12 Grey_Primary|555555 / 85, 85, 85|![Vzorník 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Při najetí myší|F12 Blue_Hover|2279BF / 34,121,191|![2279BF vzorníku](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Zakázáno|F12 LtGrey_Disabled|ABABAC / 171,171,172|![ABABAC vzorníku](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Najeďte myší na pozadí|Bg při najetí myší|D9EBF7 / 217,235,247|![D9EBF7 vzorníku](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Při stisknutí na pozadí|Při stisknutí bg|B2D7F0 / 178,215,240|![B2D7F0 vzorníku](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Obrys|VS NAVÝŠENÍ KAPACITY|F6F6F6 / 246,246,246|![F6F6F6 vzorníku](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Informace|Informace|00BCF2 / 0,188,242|![00BCF2 vzorníku](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Upozornění|Upozornění|F28300 / 242,131,0|![F28300 vzorníku](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Chyba / záporná|Error_Negative|E81123 / 232,17,35|![E81123 vzorníku](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Spustit / pozitivní|Start_Positive|009E49 / 0,158,73|![009E49 vzorníku](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Typ ukončení|Typ ukončení|9B4F96 / 155,79,150|![9B4F96 vzorníku](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Značka události|Značka události|A51F00 / 165,31,0|![A51F00 vzorníku](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Značka uživatele|Značka uživatele|F16220 / 241,98,32|![F16220 vzorníku](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Příklady sady Visual Studio Online ikon

|TFS Online||||
|----------------|-|-|-|
|**Online tým** ![ikony týmu TFS online](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam")|**Informace** o ![ikoně TFS](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation")|**Historie** ![ikon TFS](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory")|**Větev** ![ikony větve TFS](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch")|

|Napa||||
|----------|-|-|-|
|**Obsah** ![ikony obsahu Napa](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent")|![Napa – ikona poštovního](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") Office **mailu**|![Napa SharePoint – ikona](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePointu**|**Podokno úloh** ![ikona podokna úloh Napa](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane")|

|Monako||||
|------------|-|-|-|
|Soubory ![ikon Monako](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") souborů|![Monako – ikona Git](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") – **Git**|**Hledání** ![ikony hledání Monako](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch")|**Text** ![ikony Monako textu](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText")|

|F12||||
|---------|-|-|-|
|Klávesa ![F12 Přezdívka Icon Code](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode")|**Upozornění** na ![výstražnou ikonu F12](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning")|**Emulace** ![ikony emulace F12](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate")|
