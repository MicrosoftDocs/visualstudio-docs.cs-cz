---
title: Obrázky a ikony pro Visual Studio | Microsoft Docs
description: Přečtěte si o konceptech návrhu používaných k vytváření imagí a ikon pro Visual Studio.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36b77dc79574b1741c8feaded65104810e58c2fb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898789"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrázky a ikony pro Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Použití obrázku v aplikaci Visual Studio
 Před vytvořením kresby zvažte použití 1000 imagí v [knihovně imagí sady Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy imagí

- **Ikony**. Malé obrázky, které se zobrazují v příkazech, hierarchiích, šablonách atd. Výchozí velikost ikony používané v aplikaci Visual Studio je 16x16 PNG. Ikony vytvářené službou image automaticky generují formát XAML pro podporu HDPI.

    > [!NOTE]
    > I když se obrázky používají v systému nabídek, neměli byste pro každý příkaz vytvořit ikonu. Podívejte se na [nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) , abyste viděli, jestli by se měl váš příkaz dostat na ikonu.

- **Snímků.** Obrázky používané v oblasti náhledu dialogového okna, například v dialogovém okně Nový projekt.

- **Obrázky dialogových oken** Obrázky, které se zobrazují v dialogových oknech nebo průvodcích, jako popisné grafické prvky nebo indikátory zpráv. Používejte zřídka a jenom v případě potřeby k ilustraci obtížného konceptu nebo získejte pozornost uživatele (upozornění, varování).

- **Animované obrázky.** Používá se v indikátorech průběhu, stavových pruzích a dialogových oknech operací.

- **Kurzory.** Slouží k označení, zda je operace povolena pomocí myši, kde může být objekt vyřazen, a tak dále.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Návrh ikony

### <a name="overview"></a>Přehled
 Visual Studio používá ikony moderního stylu, které mají čistou geometrii a 50/50ou rovnováhu kladné/záporné (světlé/tmavé) a využívají přímo, srozumitelnou metaphors. Důležité body návrhu ikon v centru pro přehlednost, zjednodušení a kontext.

- **Přehlednost:** Zaměřte se na základní metafora, který dává ikonu jeho významu a jednotlivce.

- **Zjednodušení:** zmenšete ikonu na svůj základní význam – získat motiv napříč pomocí pouze nezbytných prvků a žádné Frills.

- **Kontext:** Vezměte v úvahu všechny aspekty role ikony během vývoje konceptů, což je rozhodující při rozhodování, které prvky představují základní metafora ikony.

  S ikonami je k dispozici několik bodů návrhu, abyste se vyhnuli:

- Nepoužívejte ikony, které označují prvky uživatelského rozhraní s výjimkou případů, kdy je to vhodné Vyberte více abstraktní nebo symbolický přístup, pokud prvek uživatelského rozhraní není ani společný, zjevný ani jedinečný.

- Nepoužívejte běžné prvky, jako jsou dokumenty, složky, šipky a zvětšovací sklo. Tyto prvky použijte pouze v případě, že jsou nezbytné pro význam ikony. Například Lupa směřující doprava by měla označovat pouze hledání, procházení a hledání.

- I když některé starší prvky ikony zachovávají použití perspektivy, nevytvářejte nové ikony s perspektivou, pokud element nemá přehlednost bez něj.

- Hromadily příliš mnoho informací do ikony. Jednoduchý obrázek, který lze snadno rozpoznat nebo zjistit jako rozpoznatelný symbol, je mnohem užitečnější než příliš složitý obraz. Ikona nemůže sdělit celý příběh.

### <a name="icon-creation"></a>Vytváření ikon

#### <a name="concept-development"></a>Vývoj konceptů
 Visual Studio má v uživatelském rozhraní širokou škálu typů ikon. Během vývoje pečlivě zvažte typ ikony. Pro prvky ikony nepoužívejte nejasné nebo neobvyklé objekty uživatelského rozhraní. V těchto případech můžete vyjádřit výslovný symbol, například s ikonou inteligentní značky. Všimněte si, že význam abstraktní značky na levé straně je jasnější než Vague verze založená na uživatelském rozhraní vpravo:

|**Správné použití symbolického snímků**|**Nesprávné použití symbolického snímků**|
|-|-|
|![Správná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nesprávná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Existují instance, ve kterých standardní, snadno rozpoznatelné prvky uživatelského rozhraní fungují dobře pro ikony. Přidat okno je jedním z těchto příkladů:

|**Správné prvky uživatelského rozhraní v ikoně**|**Nesprávný prvek uživatelského rozhraní v ikoně**|
|-|-|
|![Správná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Nesprávná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nepoužívejte dokument jako základní prvek, pokud není zásadní pro význam ikony. Bez prvku dokumentu v nabídce Přidat dokument (níže) je význam ztracen, zatímco s aktualizací elementu dokumentu není nutné sdělit význam.

|**Správné použití ikony dokumentu**|**Nesprávné použití ikony dokumentu**|
|-|-|
|![Ikona správné ikony dokumentu](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Nesprávná Ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Koncept "show" by měl být reprezentován ikonou, která nejlépe ukazuje, co se zobrazuje, například s příkladem Zobrazit všechny soubory. V případě potřeby lze pomocí metafora objektivu označit koncept "zobrazení", například s příkladem Prostředky.

|**Uvádí**|**Zobrazení**|
|-|-|
|![Zobrazit ikonu](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ikona zobrazení](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Ikona lupy na pravé straně by měla představovat pouze hledání, hledání a procházení. Varianta vlevo s znaménkem plus nebo mínus by měla představovat pouze přiblížení nebo oddálení.

|**Nápovědě**|**Přibliž**|
|-|-|
|![Ikona Hledat](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ikona přiblížení](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Ve stromovém zobrazení nepoužívejte ikonu složky i modifikátor. Pokud je k dispozici, používejte pouze modifikátor.

|**Správné ikony stromového zobrazení**|**Nesprávné ikony zobrazení stromu**|
|-|-|
|![Ikona správného zobrazení stromu &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![správné ikony zobrazení stromu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Nesprávná ikona zobrazení stromu &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![nesprávná ikona zobrazení stromu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Podrobnosti stylu

#### <a name="layout"></a>Layout
 Prvky zásobníku, jak je znázorněno u standardních ikon 16x16:

 ![Zásobník rozložení pro ikony 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Zásobník rozložení pro ikony 16x16

 Prvky upozornění na stav jsou lépe používány jako samostatné ikony. Existují však kontexty, ve kterých má být oznámení navrstveno na základním prvku, například pomocí ikony dokončení úlohy:

 ![Samostatná oznámení v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Samostatné ikony oznámení

 ![Ikona dokončení úlohy](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ikona dokončení úlohy

 Ikony projektu jsou obvykle soubory. ico, které obsahují více velikostí. Většina ikon 16x16 obsahuje stejné prvky. Verze 32x32 obsahují další podrobnosti, včetně typu projektu, pokud je to možné.

 ![Ikony projektu v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ikony projektu knihovny ovládacích prvků systému Windows VB, 16x16 a 32x32

 Nacentruje ikonu v rámci jejího rámce v pixelech. Pokud to není možné, zarovnejte ikonu na horní nebo pravé straně rámečku.

 ![Ikona na střed snímku v pixelech](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ikona na střed snímku v pixelech

 ![Ikona zarovnaná do pravé horní části pixelového rámečku](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ikona zarovnaná vpravo nahoře v rámci rámečku

 ![Ikona zarovnané na střed a zarovnání do horní části rámce pixelu](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ikona na střed a zarovnání do horní části rámce

 Chcete-li dosáhnout ideálního zarovnání a vyrovnání, vyhněte se nebráníte základnímu prvku ikony pomocí glyfů akcí. Umístěte glyf v blízkosti levého horního rohu základního prvku. Při přidávání dalšího prvku zvažte zarovnání a vyvážení ikony.

|**Správné zarovnání a vyrovnání**|**Nesprávné zarovnání a zůstatek**|
|-|-|
|![Správný zůstatek a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Nesprávný vyvážení a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Zajistěte, aby parita velikosti pro ikony, které sdílí prvky, a byly použity v sadách. Všimněte si, že v nesprávném párování jsou kružnice a šipky ve větší velikosti a neodpovídají.

|**Parita správné velikosti**|**Nesprávná parita velikosti**|
|-|-|
|![Správná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nesprávná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Používejte konzistentní tloušťky čar a vizuálů. Vyhodnoťte, jak ikona, kterou vytváříte, porovnává s ostatními ikonami pomocí souběžného porovnání. Nikdy nepoužívejte celý rámec 16x16, použijte 15x15 nebo menší. Poměr negativních na pozitivní (z tmavého na světlo) by měl být 50/50.

|**Správný poměr záporných k kladnému**|**Nesprávný negativ na kladný poměr**|
|-|-|
|![Správná vizuální váha pro ikony &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Správná vizuální váha pro ikony &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Správná vizuální váha pro ikony &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nesprávná vizuální váha pro ikony](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Pomocí jednoduchých, srovnatelných tvarů a doplňkových úhlů Sestavujte prvky bez omezení integrity elementu. Pokud je to možné, použijte 45 ° nebo 90 °.

 ![Správné úhly ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektiva
 Nechejte ikonu jasný a srozumitelná. Použijte perspektivu a zdroj světla pouze v případě potřeby. I když použití perspektivy u elementů Icon by se mělo vyhnout, některé prvky jsou bez něj nerozpoznatelné. V takových případech v stylizované perspektivě komunikuje přehlednost elementu.

 ![Perspektiva 3 bodů](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspektiva 3 bodů

 ![Perspektiva 1 bodů](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspektiva 1 bodů

 Většina elementů by měla být otočená nebo šikmá doprava:

 ![Ikony šikmé vpravo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Zdroje světla používejte pouze v případě, že k objektu přidáte potřebnou přehlednost.

|**Správný zdroj světla**|**Nesprávný zdroj světla**|
|-|-|
|![Správné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nesprávné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Pomocí osnov můžete zlepšit čitelnost nebo lepší komunikaci metafora. Vyvážení negativního (tmavého)ho zůstatku by mělo být 50/50.

|**Správné použití obrysů**|**Nesprávné použití obrysů**|
|-|-|
|![Správné osnovy](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Nesprávné osnovy](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 Ikony **prostředí a panelů příkazů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon prostředí a panelů příkazů](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Příklady ikon prostředí a panelů příkazů

 Ikony **panelu příkazů v okně nástrojů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon panelu příkazů v okně nástrojů](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Příklady ikon panelu příkazů v okně nástrojů

 Ikony **nejednoznačnosti stromového zobrazení** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon nejednoznačnosti stromového zobrazení](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Příklady ikon nejednoznačnosti stromového zobrazení

 Ikony **taxonomie hodnot založené na stavu** existují v následujících stavech: aktivní, aktivní zakázané a neaktivní zakázané.

 ![Příklady ikon taxonomie hodnot založených na stavu](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Příklady ikon taxonomie hodnot založených na stavu

 Ikony **IntelliSense** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor a jeden stav.

 ![Příklady ikon technologie IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Příklady ikon technologie IntelliSense

 **Malé (16x16) ikony projektu** by neměly mít více než dva prvky: jeden základní a jeden modifikátor.

 ![Příklady malých (16x16) ikon projektů](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 ikona projektu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 ikona projektu &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Příklady malých (16) ikon projektu

 **Velké (32x32) ikony projektu** se skládají z více než čtyř z následujících prvků: jedna základna, jedna až dvě Modifikátory a jedna překryva jazyka.

 ![Příklady velkých (32x32) projektových ikon](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Příklady velkých (32x32) projektových ikon

### <a name="production-details"></a>Podrobnosti o produkci
 Všechny nové prvky uživatelského rozhraní by měly být vytvořeny pomocí Windows Presentation Foundation (WPF) a všechny nové ikony pro WPF by měly být ve formátu 32-bit PNG. 24bitové soubory PNG mají starší formát, který nepodporuje transparentnost, a proto se pro ikony nedoporučuje.

 Uložte rozlišení na 96 DPI.

#### <a name="file-types"></a>Typy souborů

- **32 bitová verze PNG:** upřednostňovaný formát pro ikony. Bezeztrátový formát souboru komprese dat, který může obsahovat jeden rastrový obrázek (pixel). 32: bitové soubory PNG podporují transparentnost alfa kanálu, korekci gama a prokládání.

- **32-bitová BMP:** pro jiné ovládací prvky než WPF. Také označované jako XP nebo High Color, 32-bit BMP je formát RGB/A, obrázek True Color s průhledností alfa kanálu. Alfa kanál je vrstva transparentnosti určená v Adobe Photoshopu, která se pak uloží v bitmapě jako další (čtvrtý) barevný kanál. Během produkce grafiky se přidá černé pozadí do všech 32 souborů BMP, aby se zajistila rychlá vizuální hromádka s hloubkou barev. Toto černé pozadí představuje oblast, která má být maskována v uživatelském rozhraní.

- **32-bit ICO:** pro ikony projektu a přidat položku. Všechny soubory ICO mají 32 True Color s průhledností alfa kanálu (RGB/A). Vzhledem k tomu, že soubory ICO můžou ukládat víc velikostí a barev, jsou ikony Vista často ve formátu ICO, který obsahuje 16, 32x32, 48x48 a 256x256 velikosti obrázků. Aby bylo možné správně zobrazit v Průzkumníkovi Windows, musí být soubory ICO uloženy do 24bitové a 8bitové hloubky barev pro každou velikost obrázku.

- **XAML:** pro návrhové plochy a doplňky Windows. Ikony XAML jsou vektorové obrázkové soubory, které podporují škálování, otáčení, profilování a transparentnost. V současné době nejsou v nástroji Visual Studio běžné, ale z důvodu jejich flexibility se stávají oblíbenější.

- **SVG**

- **24BITOVÉ BMP:** pro panel příkazů sady Visual Studio. Formát obrázku RGB ve formátu True Color, 24 bitů BMP je konvence ikony, která vytvoří vrstvu transparentnosti pomocí purpurového (R = 255, G = 0, B = 255) jako barevný klíč pro vrstvu transparentnosti vykrojit. V 24hodinovém formátu BMP se všechny fialové povrchy zobrazují pomocí barvy pozadí.

- **24bitového formátu GIF:** pro panel příkazů sady Visual Studio. Formát obrázku RGB ve formátu True Color, který podporuje průhlednost. Soubory GIF se často používají v animacích grafiky a GIF v průvodci.

### <a name="icon-construction"></a>Konstrukce ikony
 Nejmenší velikost ikony v aplikaci Visual Studio je 16x16. Největší běžným použitím je 32x32. Mějte na paměti, že při navrhování ikony není potřeba vyplnit celý snímek 16x16, 24x24 nebo 32x32. Čitelná a jednotná konstrukce ikony je zásadní pro rozpoznávání uživatelů. Dodržovat následující body při vytváření ikon.

- Ikony by měly být jasné, srozumitelné a konzistentní.

- Je lepší používat prvky oznámení o stavu jako samostatné ikony a nemusíte je skládat nad základní prvek ikony. V některých kontextech může uživatelské rozhraní vyžadovat párování elementu status se základním prvkem.

- Ikony projektu jsou obvykle soubory. ico, které obsahují několik velikostí. Aktualizují se jenom ikony 16x16, 24x24 a 32x32. Většina ikon 16x16 a 24x24 bude obsahovat stejné prvky. Ikony 32x32 obsahují další podrobnosti, včetně typu jazyka projektu, pokud je to možné.

- U ikon 32x32 mají základní prvky obecně tloušťku čáry ve velikosti 2 – pixel. Pro prvky podrobností lze použít tloušťku čáry 1 nebo 2-pixel. K určení, který z nich je vhodnější, použijte své nejlepší rozhodnutí.

- Pro ikony 16x16 a 24x24 musí být mezi elementy rozestupy alespoň 1 pixely. Pro ikony 32x32 použijte rozestup 2 – pixel mezi prvky a mezi modifikátorem a základním prvkem.

  ![Mezery mezi prvky pro velikost ikon 16x16, 24x24 a 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Mezery mezi prvky pro velikost ikon 16x16, 24x24 a 32x32

#### <a name="color-and-accessibility"></a>Barvy a přístupnost
 Pokyny pro dodržování předpisů sady Visual Studio vyžadují, aby všechny ikony v produktu předávaly požadavky na přístupnost pro barvy a kontrast. To se provádí prostřednictvím inverze ikon a při navrhování doporučujeme, abyste si vědomi, že budou v produktu převráceny programově.

 Další informace o použití barev v ikonách sady Visual Studio naleznete v tématu [použití barev v obrázcích](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Použití barev v obrázcích

### <a name="overview"></a>Přehled
 Ikony v aplikaci Visual Studio jsou primárně monochromatický. Barva je vyhrazena pro předávání konkrétních informací a nikdy pro dekoraci. Používá se barva:

- označení akce

- upozornění uživatele na stavové oznámení

- určení přidružení jazyka

- odlišení položek v rámci technologie IntelliSense

### <a name="accessibility"></a>Usnadnění
 Pokyny pro dodržování předpisů sady Visual Studio vyžadují, aby všechny ikony vrácené do produktu vyhověly požadavkům na přístupnost pro barvy a kontrast. Barvy v paletě vizuálního jazyka byly testovány a splňovaly tyto požadavky.

#### <a name="color-inversion-for-dark-themes"></a>Inverze barev pro tmavé motivy
 Aby se ikony zobrazovaly se správným poměrem kontrastu v tmavém motivu sady Visual Studio, používá se k tomu program inverze programově. Barvy v této příručce byly vybrány jako součást, aby byly obráceny správně. Omezte použití barev na tuto paletu nebo se při použití inverze dostanete nepředvídatelné výsledky.

 ![Příklady ikon, u kterých byly barvy převráceny](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Příklady ikon, u kterých byly barvy převráceny

### <a name="base-palette"></a>Základní paleta
 Všechny standardní ikony obsahují tři základní barvy. Ikony neobsahují žádné přechody nebo vržené stíny, s jednou nebo dvěma výjimkami pro ikony 3D nástrojů.

|Využití|Name|Hodnota (světlý motiv)|Barvu|Příklad|
|-----------|----------|---------------------------|------------|-------------|
|Pozadí/tmavá|VS BG|424242/66, 66, 66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Základní paleta – příklad](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Popředí a světlo|VS FG|F0EFF1/240 239 241|![F0EFF1 vzorníku](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Obrys|OPROTI|F6F6F6/246 246 246|![F6F6F6 vzorníku](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Kromě základních barev může každá ikona obsahovat jednu další barvu z rozšířené palety.

### <a name="extended-palette"></a>Rozšířená paleta

#### <a name="action-modifiers"></a>Modifikátory akcí
 Níže uvedené čtyři barvy označují typy akcí vyžadovaných modifikátory akce:

|Využití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Kladné|Zelená akce VS|388A34/56138, 52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Záporný|Akce VS – červená|A1260D/161, 38, 13|![A1260D vzorníku](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS – modrá akce|00539C/0, 83156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Vytvořit/nový|Oranžová akce VS|C27D1A/194156, 26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Příklady
 Zelená se používá pro modifikátory pozitivních akcí, jako je "Přidat", "spustit", "přehrát" a "ověřit".

|Spustit|Spustit dotaz|Přehrát všechny kroky|Přidat ovládací prvek|
|-|-|-|-|
|![Ikona spuštění](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Spustit ikonu dotazu](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Ikona pro přehrání všech kroků](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Přidat ikonu ovládacího prvku](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Pro modifikátory negativních akcí, jako je například "odstranit", "Stop", "Storno" a "Zavřít" se používá červená.

|Odstranění relace|Odstranit sloupec|Zastavení dotazu|Offline připojení|
|-|-|-|-|
|![Ikona Odstranit relaci](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Ikona Odstranit sloupec](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Ikona Zastavit dotaz](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Ikona připojení offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Modré se aplikuje na neutrální modifikátory akcí, které jsou nejčastěji reprezentované jako šipky, jako jsou "Otevřít", "Další", "Předchozí", "Import" a "Export".

|Přejít na pole|Dávkové Check-In|Editor adres|Editor přidružení|
|-|-|-|-|
|![Ikona Přejít na pole](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Ikona Dávkové zaškrtnutí&#45;v ikonu](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Ikona editoru adres](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Ikona editoru přidružení](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Tmavě zlaté se primárně používá pro modifikátor New.

|Nový projekt|Vytvoření nového grafu|Nový test jednotek|Nová položka seznamu|
|-|-|-|-|
|![Ikona Nový projekt](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Ikona Vytvořit nový graf](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Nová ikona testu jednotek](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Nová ikona položky seznamu](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Zvláštní případy
 Ve speciálních případech lze modifikátor barevných akcí použít nezávisle jako samostatná ikona. Barva použitá pro ikonu odráží akce, ke které je ikona přidružená. Toto použití je omezené na malou podmnožinu ikon, včetně:

|Spustit|Zastavit|Odstranit|Uložit|Přejít zpět|
|-|-|-|-|-|
|![Ikona spuštění](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Ikona zastavení – plný červený čtverec.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Ikona Odstranit](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Ikona Uložit](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Ikona Přejít zpět](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Paleta hierarchie kódu

#### <a name="folder"></a>Složka

|Využití|Name|Hodnota (všechny motivy)|Políčko|Příklad|
|-----------|----------|--------------------------|------------|-------------|
|Složky|Složka|DCB67A / 220 182 122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona barvy složky](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio jazyků
 Každý z běžných jazyků nebo platforem dostupných v Visual Studio má přidruženou barvu. Tyto barvy se používají u základní ikony nebo u modifikátorů jazyka, které se zobrazují v pravém horním rohu složených ikon.

|Využití|Name|Hodnota (všechny motivy)|Políčko|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095D7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Fialová CPP|9B4F96 / 155 79 150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56 138 52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Šablony stylů CSS|CSS Red|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FIALOVÁ FS|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Swatch F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (VS Action Blue)|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Příklady ikon s modifikátory jazyka

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![Ikona&#35; v jazyce C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![Ikona&#43;&#43; v jazyce C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![Ikona F&#35;](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![Ikona JavaScriptu](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Ikona Pythonu](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|Šablony stylů CSS|TypeScript|
|-|-|-|-|-|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />Šablony stylů CSS|![Ikona TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 Ikony IntelliSense používají výhradní paletu barev. Tyto barvy slouží k usnadnění rozlišení mezi různými položkami v místním seznamu technologie IntelliSense.

|Využití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Třída, událost|Oranžová akce VS|C27D1A/194125, 26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metoda rozšíření, metoda, modul, delegát|Fialová akce VS|652D90/101, 45144|![652D90 vzorníku](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Pole, výčtové položky, makro, struktura, typ hodnoty sjednocení, operátor, rozhraní|VS – modrá akce|00539C/0, 83156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Objekt|Zelená akce VS|388A34/56138, 52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Konstanta, výjimka, enum – položka, mapa, položka mapování, obor názvů, šablona, definice typu|Pozadí (VS BG)|424242/66, 66, 66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Příklady ikon technologie IntelliSense

|Třída|Soukromá událost|Delegát|Metoda Friend|Pole|
|-|-|-|-|-|
|![Ikona třídy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Ikona soukromé události technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Ikona delegáta technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Metoda IntelliSense – ikona přítele](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Ikona pole](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Chráněná položka výčtu|Objekt|Template (Šablona)|Zástupce výjimky|
|-|-|-|-|
|![Ikona položky výčtu Protected IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Ikona objektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Ikona šablony technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Ikona zástupce výjimky technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Oznámení
 Oznámení v aplikaci Visual Studio se používají k indikaci stavu. V paletě oznámení se k definování oznámení s následujícími úrovněmi stavu používá následující čtyři barvy a také černé nebo bílé možnosti výplně popředí.

|Využití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Stav: neutrální|Modré oznámení (VS Blue)|1BA1E2/27 161 226|![1BA1E2 vzorníku](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stav: pozitivní|Oznámení zeleně (VS. zeleně)|339933/51153, 51|![Vzorník 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stav: negativní|Oznámení červeně (oproti červené)|E51400/229, 20, 0|![E51400 vzorníku](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stav: upozornění|Žlutý oznámení (VS oranžová)|FFCC00/255204, 0|![FFCC00 vzorníku](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Výplň popředí|Černá oznámení (černá)|000000/0, 0, 0, 0|![Políčko &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Výplň popředí|Bílá oznámení (bílá)|FFFFFF/255 255 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Příklady ikon oznámení

|Výstrahy|Upozornění|Dokončit|Zastavit|
|-|-|-|-|
|![Ikona upozornění](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Ikona upozornění](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Ikona Dokončit](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Ikona zastavení – plný červený kruh s bílým čtvercem uprostřed.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|