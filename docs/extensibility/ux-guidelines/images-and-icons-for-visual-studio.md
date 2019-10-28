---
title: Obrázky a ikony pro Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983872"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrázky a ikony pro Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a>Použití obrázku v aplikaci Visual Studio
 Před vytvořením kresby zvažte použití 1000 imagí v [knihovně imagí sady Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy imagí

- **Ikony**. Malé obrázky, které se zobrazují v příkazech, hierarchiích, šablonách atd. Výchozí velikost ikony používané v aplikaci Visual Studio je 16x16 PNG. Ikony vytvářené službou image automaticky generují formát XAML pro podporu HDPI.

    > [!NOTE]
    > I když se obrázky používají v systému nabídek, neměli byste pro každý příkaz vytvořit ikonu. Podívejte se na [nabídky a příkazy pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) , abyste viděli, jestli by se měl váš příkaz dostat na ikonu.

- **Snímků.** Obrázky používané v oblasti náhledu dialogového okna, například v dialogovém okně Nový projekt.

- **Obrázky dialogových oken** Obrázky, které se zobrazují v dialogových oknech nebo průvodcích, jako popisné grafické prvky nebo indikátory zpráv. Používejte zřídka a jenom v případě potřeby k ilustraci obtížného konceptu nebo získejte pozornost uživatele (upozornění, varování).

- **Animované obrázky.** Používá se v indikátorech průběhu, stavových pruzích a dialogových oknech operací.

- **Kurzory.** Slouží k označení, zda je operace povolena pomocí myši, kde může být objekt vyřazen, a tak dále.

## <a name="BKMK_IconDesign"></a>Návrh ikony

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

|||
|-|-|
|**Správné použití symbolického snímků**|**Nesprávné použití symbolického snímků**|
|![Správná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 -01 _SmartTagCorrect")|![Nesprávná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 -02 _SmartTagIncorrect")|

 Existují instance, ve kterých standardní, snadno rozpoznatelné prvky uživatelského rozhraní fungují dobře pro ikony. Přidat okno je jedním z těchto příkladů:

|||
|-|-|
|**Správné prvky uživatelského rozhraní v ikoně**|**Nesprávný prvek uživatelského rozhraní v ikoně**|
|![Správná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 -03 _AddWindowCorrect")|![Nesprávná ikona pro přidání okna](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 -04 _AddWindowIncorrect")|

 Nepoužívejte dokument jako základní prvek, pokud není zásadní pro význam ikony. Bez prvku dokumentu v nabídce Přidat dokument (níže) je význam ztracen, zatímco s aktualizací elementu dokumentu není nutné sdělit význam.

|||
|-|-|
|**Správné použití ikony dokumentu**|**Nesprávné použití ikony dokumentu**|
|![Ikona správné ikony dokumentu](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 -05 _DocumentIconCorrect")|![Nesprávná Ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 -06 _DocumentIconIncorrect")|

 Koncept "show" by měl být reprezentován ikonou, která nejlépe ukazuje, co se zobrazuje, například s příkladem Zobrazit všechny soubory. V případě potřeby lze pomocí metafora objektivu označit koncept "zobrazení", například s příkladem Prostředky.

|||
|-|-|
|**Uvádí**|**Zobrazení**|
|![Zobrazit ikonu](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 -07 _Zobrazit")|![Ikona zobrazení](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 -08 _View")|

 Ikona lupy na pravé straně by měla představovat pouze hledání, hledání a procházení. Varianta vlevo s znaménkem plus nebo mínus by měla představovat pouze přiblížení nebo oddálení.

|||
|-|-|
|**Nápovědě**|**Přibliž**|
|![Ikona hledání](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 -09 _Search")|![Ikona přiblížení](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 -10 _Zoom")|

 Ve stromovém zobrazení nepoužívejte ikonu složky i modifikátor. Pokud je k dispozici, používejte pouze modifikátor.

|||
|-|-|
|**Správné ikony stromového zobrazení**|**Nesprávné ikony zobrazení stromu**|
|![Ikona &#40;správné stromové zobrazení&#41; 1](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 -11 _TreeViewCorrect1") ![správná ikona &#40;stromového&#41; zobrazení 2](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 -12 _TreeViewCorrect2")|![Nesprávná ikona &#40;zobrazení&#41; stromu 1](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 -13 _TreeViewIncorrect1") ![ &#40;nesprávná&#41; ikona zobrazení stromu 2](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 -14 _TreeViewIncorrect2")|

### <a name="style-details"></a>Podrobnosti stylu

#### <a name="layout"></a>Rozložení
 Prvky zásobníku, jak je znázorněno u standardních ikon 16x16:

 ![Zásobník rozložení pro ikony 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 -15 _LayoutStack")<br />Zásobník rozložení pro ikony 16x16

 Prvky upozornění na stav jsou lépe používány jako samostatné ikony. Existují však kontexty, ve kterých má být oznámení navrstveno na základním prvku, například pomocí ikony dokončení úlohy:

 ![Samostatná oznámení v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 -16 _StandaloneNotificationIcons")<br />Samostatné ikony oznámení

 ![Ikona dokončení úlohy](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 -17 _TaskComplete")<br />Ikona dokončení úlohy

 Ikony projektu jsou obvykle soubory. ico, které obsahují více velikostí. Většina ikon 16x16 obsahuje stejné prvky. Verze 32x32 obsahují další podrobnosti, včetně typu projektu, pokud je to možné.

 ![Ikony projektu v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 -18 _IconProjectThreeSizes")<br />Ikony projektu knihovny ovládacích prvků systému Windows VB, 16x16 a 32x32

 Nacentruje ikonu v rámci jejího rámce v pixelech. Pokud to není možné, zarovnejte ikonu na horní nebo pravé straně rámečku.

 ![Ikona na střed snímku v pixelech](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 -19 _IconCentered")<br />Ikona na střed snímku v pixelech

 ![Ikona zarovnaná do pravé horní části pixelového rámečku](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 -20 _IconTopRight")<br />Ikona zarovnaná vpravo nahoře v rámci rámečku

 ![Ikona zarovnané na střed a zarovnání do horní části rámce pixelu](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 -21 _IconTopAlign")<br />Ikona na střed a zarovnání do horní části rámce

 Chcete-li dosáhnout ideálního zarovnání a vyrovnání, vyhněte se nebráníte základnímu prvku ikony pomocí glyfů akcí. Umístěte glyf v blízkosti levého horního rohu základního prvku. Při přidávání dalšího prvku zvažte zarovnání a vyvážení ikony.

|||
|-|-|
|**Správné zarovnání a vyrovnání**|**Nesprávné zarovnání a zůstatek**|
|![Správný zůstatek a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 -22 _AlignBalanceCorrect")|![Nesprávný vyvážení a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 -23 _AlignBalanceIncorrect")|

 Zajistěte, aby parita velikosti pro ikony, které sdílí prvky, a byly použity v sadách. Všimněte si, že v nesprávném párování jsou kružnice a šipky ve větší velikosti a neodpovídají.

|||
|-|-|
|**Parita správné velikosti**|**Nesprávná parita velikosti**|
|![Správná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 -24 _SizeParityCorrect")|![Nesprávná velikost a parita ikony](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 -25 _SizeParityIncorrect")|

 Používejte konzistentní tloušťky čar a vizuálů. Vyhodnoťte, jak ikona, kterou vytváříte, porovnává s ostatními ikonami pomocí souběžného porovnání. Nikdy nepoužívejte celý rámec 16x16, použijte 15x15 nebo menší. Poměr negativních na pozitivní (z tmavého na světlo) by měl být 50/50.

|||
|-|-|
|**Správný poměr záporných k kladnému**|**Nesprávný negativ na kladný poměr**|
|![Správná vizuální váha pro ikony &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 -26 _VisualWeightCorrect1")<br /><br /> ![Správná vizuální váha pro ikony &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 -27 _VisualWeightCorrect2 ")<br /><br /> ![Správná vizuální váha pro ikony &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 -28 _VisualWeightCorrect3 ")|![Nesprávná vizuální váha pro ikony](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 -29 _VisualWeightIncorrect")|

 Pomocí jednoduchých, srovnatelných tvarů a doplňkových úhlů Sestavujte prvky bez omezení integrity elementu. Pokud je to možné, použijte 45 ° nebo 90 °.

 ![Správné úhly ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 -30 _IconAnglesCorrect")

#### <a name="perspective"></a>Perspektiva
 Nechejte ikonu jasný a srozumitelná. Použijte perspektivu a zdroj světla pouze v případě potřeby. I když použití perspektivy u elementů Icon by se mělo vyhnout, některé prvky jsou bez něj nerozpoznatelné. V takových případech v stylizované perspektivě komunikuje přehlednost elementu.

 ![Perspektiva 3 bodů](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 -31 _3PointPerspective")<br />Perspektiva 3 bodů

 ![Perspektiva 1 bodů](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 -32 _1PointPerspective")<br />Perspektiva 1 bodů

 Většina elementů by měla být otočená nebo šikmá doprava:

 ![Ikony šikmé vpravo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 -33 _AngledRight")

 Zdroje světla používejte pouze v případě, že k objektu přidáte potřebnou přehlednost.

|||
|-|-|
|**Správný zdroj světla**|**Nesprávný zdroj světla**|
|![Správné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 -34 _LightSourcesCorrect")|![Nesprávné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 -35 _LightSourcesIncorrect")|

 Pomocí osnov můžete zlepšit čitelnost nebo lepší komunikaci metafora. Vyvážení negativního (tmavého)ho zůstatku by mělo být 50/50.

|||
|-|-|
|**Správné použití obrysů**|**Nesprávné použití obrysů**|
|![Správné osnovy](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 -36 _OutlinesCorrect")|![Nesprávné osnovy](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 -37 _OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 Ikony **prostředí a panelů příkazů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon prostředí a panelů příkazů](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 -38 _ShellIcons")<br />Příklady ikon prostředí a panelů příkazů

 Ikony **panelu příkazů v okně nástrojů** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon panelu příkazů v okně nástrojů](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 -39 _ToolWindowCommandBarIcons")<br />Příklady ikon panelu příkazů v okně nástrojů

 Ikony **nejednoznačnosti stromového zobrazení** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor, jedna akce nebo jeden stav.

 ![Příklady ikon nejednoznačnosti stromového zobrazení](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 -40 _TreeViewIcons")<br />Příklady ikon nejednoznačnosti stromového zobrazení

 Ikony **taxonomie hodnot založené na stavu** existují v následujících stavech: aktivní, aktivní zakázané a neaktivní zakázané.

 ![Příklady ikon taxonomie hodnot založených na stavu](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41 _StateBasedTaxonomy")<br />Příklady ikon taxonomie hodnot založených na stavu

 Ikony **IntelliSense** se skládají z více než tří z následujících prvků: jeden základní, jeden modifikátor a jeden stav.

 ![Příklady ikon technologie IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 -42 _IntelliSenseIcons")<br />Příklady ikon technologie IntelliSense

 **Malé (16x16) ikony projektu** by neměly mít více než dva prvky: jeden základní a jeden modifikátor.

 ![Příklady malých (16x16) ikon projektů](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 -43 _16x16Project1") ![16x16 ikona &#40;projektu 2&#41; ](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 -44 _16x16Project2") ![16x16 ikona &#40;projektu 3&#41; ](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 -45 _16x16Project3")<br />Příklady malých (16) ikon projektu

 **Velké (32x32) ikony projektu** se skládají z více než čtyř z následujících prvků: jedna základna, jedna až dvě Modifikátory a jedna překryva jazyka.

 ![Příklady velkých (32x32) projektových ikon](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 -46 _32x32Project")<br />Příklady velkých (32x32) projektových ikon

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

  ![Mezery mezi prvky pro velikost ikon 16x16, 24x24 a 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 -47 _ElementSpacing")<br />Mezery mezi prvky pro velikost ikon 16x16, 24x24 a 32x32

#### <a name="color-and-accessibility"></a>Barvy a přístupnost
 Pokyny pro dodržování předpisů sady Visual Studio vyžadují, aby všechny ikony v produktu předávaly požadavky na přístupnost pro barvy a kontrast. To se provádí prostřednictvím inverze ikon a při navrhování doporučujeme, abyste si vědomi, že budou v produktu převráceny programově.

 Další informace o použití barev v ikonách sady Visual Studio naleznete v tématu [použití barev v obrázcích](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Použití barev v obrázcích

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

 ![Příklady ikon, u kterých byly barvy převráceny](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 -01 _DarkThemeInversion")<br />Příklady ikon, u kterých byly barvy převráceny

### <a name="base-palette"></a>Základní paleta
 Všechny standardní ikony obsahují tři základní barvy. Ikony neobsahují žádné přechody nebo vržené stíny, s jednou nebo dvěma výjimkami pro ikony 3D nástrojů.

|Použití|Name|Hodnota (světlý motiv)|Barvu|Příklad|
|-----------|----------|---------------------------|------------|-------------|
|Pozadí/tmavá|VS BG|424242/66, 66, 66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Základní paleta – příklad](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 -02 _BasePaletteExample")|
|Popředí a světlo|VS FG|F0EFF1/240 239 241|![F0EFF1 vzorníku](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Obrys|OPROTI|F6F6F6/246 246 246|![F6F6F6 vzorníku](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Kromě základních barev může každá ikona obsahovat jednu další barvu z rozšířené palety.

### <a name="extended-palette"></a>Rozšířená paleta

#### <a name="action-modifiers"></a>Modifikátory akcí
 Níže uvedené čtyři barvy označují typy akcí vyžadovaných modifikátory akce:

|Použití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Kladné|Zelená akce VS|388A34/56138, 52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Záporný|Akce VS – červená|A1260D/161, 38, 13|![A1260D vzorníku](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Jazyk|VS – modrá akce|00539C/0, 83156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Vytvořit/nový|Oranžová akce VS|C27D1A/194156, 26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Příklady
 Zelená se používá pro modifikátory pozitivních akcí, jako je "Přidat", "spustit", "přehrát" a "ověřit".

|||||
|-|-|-|-|
|![Ikona spuštění](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Spustit|![Spustit ikonu dotazu](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 -04 _ExecuteQuery")<br />Spustit dotaz|![Ikona pro přehrání všech kroků](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 -05 _PlayAllSteps")<br />Přehrát všechny kroky|![Přidat ikonu ovládacího prvku](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 -06 _AddControl")<br />Přidat ovládací prvek|

 Pro modifikátory negativních akcí, jako je například "odstranit", "Stop", "Storno" a "Zavřít" se používá červená.

|||||
|-|-|-|-|
|![Ikona odstranění vztahu](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 -07 _DeleteRelationship")<br />Odstranit relaci|![Ikona odstranění sloupce](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 -08 _DeleteColumn")<br />Odstranit sloupec|![Ikona zastavit dotaz](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 -09 _StopQuery")<br />Zastavit dotaz|![Ikona připojení offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 -10 _ConnectionOffline")<br />Připojení offline|

 Modrá se aplikuje na neutrální modifikátory akcí nejčastěji reprezentované jako šipky, jako je "otevřít", "Další", "předchozí", "Import" a "Export".

|||||
|-|-|-|-|
|![Přejít na ikonu pole](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 -11 _GoToField")<br />Přejít k poli|![Ikona dávkového&#45;vrácení se změnami](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 -12 _BatchedCheckIn")<br />Dávkové vrácení se změnami|![Ikona editoru adres](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 -13 _AddressEditor")<br />Editor adres|![Ikona editoru přidružení](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 -14 _AssociationEditor")<br />Editor přidružení|

 Tmavě zlatá se primárně používá pro modifikátor New.

|||||
|-|-|-|-|
|![Ikona nového projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 -15 _NewProject")<br />Nový projekt|![Vytvořit novou ikonu grafu](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 -16 _CreateNewGraph")<br />Vytvořit nový graf|![Ikona nové jednotky testu](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 -17 _NewUnitTest")<br />Nový test jednotek|![Ikona nové položky seznamu](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 -18 _NewListItem")<br />Nová položka seznamu|

#### <a name="special-cases"></a>Zvláštní případy
 Ve zvláštních případech může být modifikátor barevné akce použit nezávisle jako samostatná ikona. Barva použitá pro ikonu odráží akce, ke kterým je ikona přidružena. Toto použití je omezeno na malou podmnožinu ikon, včetně:

||||||
|-|-|-|-|-|
|![Ikona spuštění](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Spustit|![Ikona zastavení](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 -19 _Stop")<br />Zastavit|![Ikona Odstranit](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 -20 _Delete")<br />Odstranit|![Ikona Uložit](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 -21 _Save")<br />Uložit|![Ikona navigace zpátky](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 -22 _NavigateBack")<br />Přejít zpátky|

### <a name="code-hierarchy-palette"></a>Paleta hierarchie kódu

#### <a name="folder"></a>Folder

|Použití|Name|Value (všechny motivy)|Barvu|Příklad|
|-----------|----------|--------------------------|------------|-------------|
|Složka|Folder|DCB67A/220 182 122|![DCB67A vzorníku](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona barvy složky](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 -23 _FolderColor")|

#### <a name="visual-studio-languages"></a>Jazyky sady Visual Studio
 Všechny běžné jazyky nebo platformy, které jsou k dispozici v aplikaci Visual Studio, mají přidruženou barvu. Tyto barvy se používají na základní ikoně nebo na modifikátorech jazyka, které se zobrazují v pravém horním rohu složených ikon.

|Použití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP.NET HTML WPF – modrá|0095D7/0149 215|![0095D7 vzorníku](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Fialová CPP|9B4F96/155, 79150|![9B4F96 vzorníku](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS zelená (akce VS zelená)|388A34/56138, 52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS – červená|BD1E2D/189, 30, 45|![BD1E2D vzorníku](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Nachová FS|672878/103, 40120|![Vzorník 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS – oranžová|F16421/241100, 33|![F16421 vzorníku](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|JAZYK|VB Blue (VS Action Blue)|00539C/0, 83156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Oranžová TS|E04C06/224, 76, 6|![E04C06 vzorníku](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY – zelená|879636/135150, 54|![Vzorník 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Příklady ikon s modifikátory jazyka

|||||||
|-|-|-|-|-|-|
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 -25 _VB")<br />JAZYK|![Ikona&#35; jazyka C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 -26 _CSharp")<br />C#|![Ikona&#43; &#43; jazyka C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 -27 _CPlusPlus")<br />C++|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 -28 _FSharp")<br />F#|![Ikona JavaScriptu](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 -29 _JavaScript")<br />JavaScript|![Ikona Pythonu](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 -30 _Python")<br />Python|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 -31 _HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 -32 _WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 -33 _ASP")<br />FORMÁTU|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 -34 _CSS")<br />CSS|![Ikona TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 -35 _TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Ikony IntelliSense používají výhradní paletu barev. Tyto barvy slouží k usnadnění rozlišení mezi různými položkami v místním seznamu technologie IntelliSense.

|Použití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Třída, událost|Oranžová akce VS|C27D1A/194125, 26|![C27D1A vzorníku](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metoda rozšíření, metoda, modul, delegát|Fialová akce VS|652D90/101, 45144|![652D90 vzorníku](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Pole, výčtové položky, makro, struktura, typ hodnoty sjednocení, operátor, rozhraní|VS – modrá akce|00539C/0, 83156|![00539C vzorníku](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Objekt|Zelená akce VS|388A34/56138, 52|![388A34 vzorníku](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Konstanta, výjimka, enum – položka, mapa, položka mapování, obor názvů, šablona, definice typu|Pozadí (VS BG)|424242/66, 66, 66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Příklady ikon technologie IntelliSense

||||||
|-|-|-|-|-|
|![Ikona třídy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 -36 _IntelliSenseClass")<br />Třída|![Ikona soukromé události technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 -37 _IntelliSensePrivateEvent")<br />Soukromá událost|![Ikona delegáta technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 -38 _IntelliSenseDelegate")<br />Delegát|![Metoda IntelliSense – ikona přítele](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 -39 _IntelliSenseMethodFriend")<br />Metoda Friend|![Ikona pole](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 -40 _Field")<br />Pole|
|![Ikona položky výčtu Protected IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41 _IntelliSenseProtectedEnumItem")<br />Chráněná položka výčtu|![Ikona objektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 -42 _IntelliSenseObject")<br />Objekt|![Ikona šablony technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 -43 _IntelliSenseTemplate")<br />Vzhledu|![Ikona zástupce výjimky technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 -44 _IntelliSenseExceptionShortcut")<br />Zástupce výjimky||

### <a name="notifications"></a>Oznámení
 Oznámení v aplikaci Visual Studio se používají k indikaci stavu. V paletě oznámení se k definování oznámení s následujícími úrovněmi stavu používá následující čtyři barvy a také černé nebo bílé možnosti výplně popředí.

|Použití|Name|Value (všechny motivy)|Barvu|
|-----------|----------|--------------------------|------------|
|Stav: neutrální|Modré oznámení (VS Blue)|1BA1E2/27 161 226|![1BA1E2 vzorníku](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stav: pozitivní|Oznámení zeleně (VS. zeleně)|339933/51153, 51|![Vzorník 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stav: negativní|Oznámení červeně (oproti červené)|E51400/229, 20, 0|![E51400 vzorníku](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stav: upozornění|Žlutý oznámení (VS oranžová)|FFCC00/255204, 0|![FFCC00 vzorníku](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Výplň popředí|Černá oznámení (černá)|000000/0, 0, 0, 0|![000000 &#35;vzorníku](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Výplň popředí|Bílá oznámení (bílá)|FFFFFF/255 255 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Příklady ikon oznámení

|||||
|-|-|-|-|
|![Ikona výstrahy](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 -45 _Alert")<br />Upozornění|![Ikona upozornění](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 -48 _Warning")<br />Upozornění|![Ikona dokončení](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 -46 _Complete")<br />Plňte|![Ikona zastavení](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 -47 _Stop")<br />Zastavit|

### <a name="visual-studio-online"></a>Visual Studio Online
 Obecně platí, že Visual Studio Online se skládá z funkcí hostovaných v prohlížeči. Barva se liší v různých prostředích, ale styl zůstává stejný.

|Skupina|Použití|Name|Value (všechny motivy)|Barvu|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Pozadí|TFSO BG|656565/101, 101, 101|![Vzorník 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Obrys|TFSO VEN|FFFFFF/255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Pozadí|White|FFFFFF/255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monako|Pozadí|White|FFFFFF/255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Kláves|Pozadí|White|FFFFFF/255, 255, 255|![FFFFFF vzorníku](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Kláves|Běžnou|Grey_Primary F12|555555/85, 85, 85|![Vzorník 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|Kláves|Přesunutí|Blue_Hover F12|2279BF/34 121 191|![2279BF vzorníku](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|Kláves|Zabezpečen|LtGrey_Disabled F12|ABABAC/171 171 172|![ABABAC vzorníku](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|Kláves|Pozadí při najetí myší|Najetí myší BG|D9EBF7/217 235 247|![D9EBF7 vzorníku](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|Kláves|Stisknuté pozadí|Po stisknutí BG|B2D7F0/178 215 240|![B2D7F0 vzorníku](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|Kláves|Obrys|OPROTI|F6F6F6/246 246 246|![F6F6F6 vzorníku](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|Kláves|Informace o|Informace o|00BCF2/0188 242|![00BCF2 vzorníku](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|Kláves|Upozornění|Upozornění|F28300/242131, 0|![F28300 vzorníku](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|Kláves|Chyba/záporná|Error_Negative|E81123/232, 17, 35|![E81123 vzorníku](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|Kláves|Počátek/kladné|Start_Positive|009E49/0158, 73|![009E49 vzorníku](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|Kláves|Typ přerušení|Typ přerušení|9B4F96/155, 79150|![9B4F96 vzorníku](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|Kláves|Značka události|Značka události|A51F00/165, 31, 0|![A51F00 vzorníku](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|Kláves|Značka uživatele|Značka uživatele|F16220/241, 98, 32|![F16220 vzorníku](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Příklady ikon služby Visual Studio Online

|TFS online||||
|----------------|-|-|-|
|![Ikona týmu TFS online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 -49 _TFSOnlineTeam")<br />Online tým|![Informační ikona TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 -50 _TFSInformation")<br />Informace o|![Ikona historie TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 -51 _TFSHistory")<br />Historie|![Ikona větve TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 -52 _TFSBranch")<br />Větvení.|

|Napa||||
|----------|-|-|-|
|![Ikona obsahu Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 -53 _NapaContent")<br />Obsah|![Ikona poštovního Napa Office](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 -54 _NapaOfficeMail")<br />Poštovní schránka Office|![Ikona služby SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 -55 _NapaSharePoint")<br />SharePoint|![Ikona podokna úloh Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 -56 _NapaTaskPane")<br />Podokno úloh|

|Monako||||
|------------|-|-|-|
|![Ikona soubory Monako](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 -57 _MonacoFiles")<br />Soubory|![Monako – ikona Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 -58 _MonacoGit")<br />Git|![Ikona hledání Monako](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 -59 _MonacoSearch")<br />Hledat|![Ikona pro text Monako](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 -60 _MonacoText")<br />Text|

|Kláves|||
|---------|-|-|
|![Přezdívka F12 – ikona kódu](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 -61 _F12PrettyCode")<br />Poměrně kód|![Ikona upozornění F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 -62 _F12Warning")<br />Upozornění|![Ikona emulace F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 -63 _F12Emulate")<br />Emulovat|