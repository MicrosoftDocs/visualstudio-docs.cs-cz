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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302418"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrázky a ikony pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Použití obrázků v sadě Visual Studio
 Před vytvořením kresby zvažte využití více než 1 000 obrázků v [knihovně obrázků sady Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy obrázků

- **Ikony**. Malé obrázky, které se zobrazují v příkazech, hierarchiích, šablonách a tak dále. Výchozí velikost ikony použitá v sadě Visual Studio je 16x16 PNG. Ikony vytvořené službou image automaticky generují formát XAML pro podporu HDPI.

     **POZNÁMKA:** Zatímco obrázky se používají v systému nabídek, neměli byste vytvářet ikonu pro každý příkaz. Podívejte se do [nabídek a příkazů pro Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) a zjistěte, jestli má váš příkaz získat ikonu.

- **Miniatury.** Obrázky použité v oblasti náhledu dialogového okna, například v dialogovém okně Nový projekt.

- **Obrázky dialogů.** Obrázky, které se zobrazují v dialogových oknech nebo čarodějích, buď jako popisné grafiky nebo indikátory zpráv. Používejte zřídka a pouze v případě, že je to nutné k ilustraci obtížného konceptu nebo získání pozornosti uživatele (výstraha, upozornění).

- **Animované obrázky.** Používá se v indikátorech průběhu, stavových panelech a dialogových oknech operací.

- **Kurzory.** Slouží k označení, zda je operace povolena pomocí myši, kde může být objekt vynechán a tak dále.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Návrh ikony

### <a name="overview"></a>Přehled
 Visual Studio používá ikony v moderním stylu, které mají čistou geometrii a 50/50 rovnováhu kladné/negativní (světlé/tmavé) a používají přímé, srozumitelné metafory. Klíčové body návrhu ikon se soustředí na srozumitelnost, zjednodušení a kontext.

- **Jasnost:** zaměřte se na základní metaforu, která dává ikoně její význam a individualitu.

- **Zjednodušení:** zmenšete ikonu na její základní význam - získejte téma pouze s potřebnými prvky a bez ozdůbek.

- **Kontext:** zvažte všechny aspekty role ikony během vývoje konceptu, což je zásadní při rozhodování, které prvky tvoří základní metaforu ikony.

  S ikonami existuje řada bodů návrhu, kterým je třeba se vyhnout:

- Nepoužívejte ikony, které označují prvky uživatelského rozhraní, s výjimkou případů, kdy je to vhodné. Zvolte abstraktnější nebo symbolický přístup, když prvek ui není ani běžné, zřejmé, ani jedinečné.

- Nepoužívejte nadužívání běžných prvků, jako jsou dokumenty, složky, šipky a lupa. Tyto prvky používejte pouze v případě, že jsou nezbytné pro význam ikony. Například lupa směřující doprava by měla označovat pouze funkce Hledat, Procházet a Hledat.

- Přestože některé starší prvky ikon zachovat použití perspektivy, nevytvářejte nové ikony s perspektivou, pokud prvek postrádá jasnost bez něj.

- Nenacpejte příliš mnoho informací do ikony. Jednoduchý obraz, který lze snadno rozpoznat nebo se naučit jako rozpoznatelný symbol, je mnohem užitečnější než příliš složitý obraz. Ikona nemůže vyprávět celý příběh.

### <a name="icon-creation"></a>Vytvoření ikony

#### <a name="concept-development"></a>Vývoj koncepce
 Visual Studio má v rámci svého ui širokou škálu typů ikon. Pečlivě zvažte typ ikony během vývoje. Nepoužívejte nejasné nebo neobvyklé objekty uživatelského rozhraní pro prvky ikony. V těchto případech se rozhodněte pro symbolické, například s ikonou inteligentní značky. Všimněte si, že význam abstraktní značky na levé straně je více zřejmé, než vágní, Verze založené na ui na pravé straně:

|||
|-|-|
|**Správné používání symbolických snímků**|**Nesprávné použití symbolických snímků**|
|![Ikona Opravit inteligentní značku](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nesprávná ikona inteligentní značky](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Existují případy, ve kterých standardní, snadno rozpoznatelné prvky uživatelského rozhraní fungují dobře pro ikony. Přidat okno je jedním z takových příkladů:

|||
|-|-|
|**Opravit prvek ui v ikoně**|**Nesprávný prvek rozhraní v ikoně**|
|![Ikona Opravit přidat okno](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![Ikona Nesprávný přidat okno](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nepoužívejte dokument jako základní prvek, pokud není nezbytný pro význam ikony. Bez prvku dokumentu na Přidat dokument (níže) význam je ztracen, vzhledem k tomu, že s Aktualizovat prvek dokumentu není nutné sdělit význam.

|||
|-|-|
|**Správné používání ikony dokumentu**|**Nesprávné použití ikony dokumentu**|
|![Ikona Opravit dokument](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Ikona Nesprávného dokumentu](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Koncept "show" by měl být reprezentován ikonou, která nejlépe ilustruje, co je zobrazeno, například v příkladu Zobrazit všechny soubory. Metafora objektivu může být použita k označení pojmu "zobrazení", pokud je to nutné, například v příkladu zobrazení prostředků.

|||
|-|-|
|**"Zobrazit"**|**"Zobrazit"**|
|![Ikona Zobrazit](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![Ikona Zobrazit](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|

 Ikona lupy směřující doprava by měla představovat pouze funkce Hledat, Najít a Procházet. Levá varianta se znaménkem plus nebo mínus by měla představovat pouze přiblížení/oddálení.

|||
|-|-|
|**"Hledat"**|**"Přiblížení"**|
|![Ikona Hledat](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![Ikona lupy](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|

 Ve stromových zobrazeních nepoužívejte ikonu složky ani modifikátor. Pokud je k dispozici, použijte pouze modifikátor.

|||
|-|-|
|**Opravit ikony zobrazení stromu**|**Nesprávné ikony stromového zobrazení**|
|![Opravit ikonu zobrazení stromu &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Ikona zobrazení správného stromu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Nesprávná ikona zobrazení stromu &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Nesprávná ikona zobrazení stromu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Podrobnosti stylu

#### <a name="layout"></a>Rozložení
 Prvky zásobníku, jak je znázorněno na standardních ikonách 16x16:

 ![Rozložení zásobníku pro ikony 16x16](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")

 **Rozložení zásobníku pro ikony 16x16**

 Prvky oznámení o stavu jsou lépe používány jako samostatné ikony. Existují však kontexty, ve kterých by mělo být oznámení stohovat na základním prvku, například s ikonou Dokončení úkolu:

 ![Samostatná oznámení v sadě Visual Studio](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")

 **Samostatné ikony oznámení**

 ![Ikona Dokončení úkolu](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")

 **Ikona Dokončení úkolu**

 Ikony projektu jsou obvykle soubory ICO, které obsahují více velikostí. Většina ikon 16x16 obsahuje stejné prvky. Verze 32x32 mají další podrobnosti, včetně typu projektu, pokud je to možné.

 ![Ikony projektů v sadě Visual Studio](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")

 **Ikony projektu knihovny ovládacího prvku Systému Windows, 16x16 a 32x32**

 Vystředit ikonu v rámci jejího rámečku obrazového bodu. Pokud to není možné, zarovnejte ikonu s horním nebo pravým rámečkem.

 ![Ikona vystředěná v rámci rámečku obrazového bodu](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")

 **Ikona vystředěná v rámci rámečku obrazového bodu**

 ![Ikona zarovnaná k pravému hornímu rohu rámečku obrazového bodu](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")

 **Ikona zarovnaná k pravému hornímu rohu rámečku**

 ![Ikona vystředěná a zarovnaná k horní části rámečku obrazového bodu](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")

 **Ikona vystředěná a zarovnaná k horní části rámečku**

 Chcete-li dosáhnout ideálního zarovnání a vyvážení, vyhněte se zablokování základního prvku ikony pomocí akčních glyfů. Umístěte glyf v levém horním rohu základního prvku. Při přidávání dalšího prvku zvažte zarovnání a vyvážení ikony.

|||
|-|-|
|**Správné zarovnání a vyvážení**|**Nesprávné zarovnání a vyvážení**|
|![Správné vyvážení a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Nesprávné vyvážení a zarovnání ikon](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Zajistěte paritu velikosti ikon, které sdílejí prvky a používají se v sadách. Všimněte si, že při nesprávném párování jsou kruh a šipka nadrozměrné a neshodují se.

|||
|-|-|
|**Správná velikost parity**|**Nesprávná parita velikosti**|
|![Správná velikost ikony a parita](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nesprávná velikost ikony a parita](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Používejte konzistentní čáry a vizuální závaží. Vyhodnoťte, jak se vytvářená ikona porovnává s ostatními ikonami pomocí porovnání vedle sebe. Nikdy nepoužívejte celý rám 16x16, použijte 15x15 nebo menší. Poměr záporně k pozitivnímu (tmavý/světlý) by měl být 50/50.

|||
|-|-|
|**Správný poměr záporně k kladnému**|**Nesprávný poměr záporně k kladnému**|
|![Správná vizuální hmotnost ikon &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Správná vizuální hmotnost ikon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Správná vizuální hmotnost ikon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nesprávná vizuální hmotnost ikon](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Pomocí jednoduchých, srovnatelných tvarů a doplňkových úhlů můžete vytvářet prvky, aniž byste obětovali integritu prvků. Pokud je to možné, použijte úhly 45° nebo 90°.

 ![Správné úhly ikon](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektiva
 Udržujte ikonu jasnou a srozumitelnou. Perspektivu a světelný zdroj používejte pouze v případě potřeby. I když použití perspektivy na prvky ikony je třeba se vyhnout, některé prvky jsou k nepoznání bez něj. V takových případech stylizovaná perspektiva sděluje čistotu prvku.

 ![3&#45;bodová perspektiva](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")

 **3bodová perspektiva**

 ![1&#45;bod ová perspektiva](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")

 **Perspektiva 1 bodů**

 Většina prvků by měla směřovat nebo šikmé doprava.

 ![Ikony šikmé vpravo](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")

 Zdroje světla používejte pouze při přidávání nezbytné čistoty objektu.

|||
|-|-|
|**Správný zdroj světla**|**Nesprávný světelný zdroj**|
|![Správné zdroje světla pro ikony](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nesprávné světelné zdroje pro ikony](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Obrysy používejte pouze ke zvýšení čitelnosti nebo k lepší komunikaci metafory. Záporná kladná (tmavá světlá) rovnováha by měla být 50/50.

|||
|-|-|
|**Správné použití obrysů**|**Nesprávné použití obrysů**|
|![Opravit obrysy](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![Nesprávné obrysy](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 Ikony **řídicího prostředí a panelu příkazů** se skládají z maximálně tří následujících prvků: jedna základna, jeden modifikátor, jedna akce nebo jeden stav.

 ![Ikony prostředí a panelu příkazů](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")

 **Příklady ikon prostředí a panelu příkazů**

 Ikony **panelu příkazů okna nástroje** se skládají z maximálně tří následujících prvků: jedné základny, jednoho modifikátoru, jedné akce nebo jednoho stavu.

 ![Ikony panelu příkazů okna nástroje](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")

 **Příklady ikon panelu příkazů okna nástrojů**

 **Ikony rozdvojení zobrazení stromu** se skládají z maximálně tří následujících prvků: jedna základna, jeden modifikátor, jedna akce nebo jeden stav.

 ![Ikony disambiguátoru zobrazení stromu](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")

 **Příklady ikon nejednoznačnce zobrazení stromu**

 Ikony **taxonomie založené na stavu** existují v následujících stavech: aktivní, aktivní zakázáno a neaktivní zakázáno.

 ![Ikony hodnot na základě hodnoty taxonomie na základě&#45;stavu](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")

 **Příklady ikon státní taxonomie hodnot**

 **Ikony Technologie IntelliSense** se skládají z maximálně tří následujících prvků: jedné základny, jednoho modifikátoru a jednoho stavu.

 ![Ikony technologie IntelliSense](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")

 **Příklady ikon Technologie IntelliSense**

 **Malé (16x16)** ikony projektu by neměly mít více než dva prvky: jednu základnu a jeden modifikátor.

 ![Ikona projektu 16x16 &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![ikona projektu 16x16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ikona projektu ![16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")

 **Příklady malých ikon projektů (16x16)**

 **Velké (32x32)** ikony projektu se skládají z více než čtyři z následujících prvků: jeden základ, jeden až dva modifikátory a jeden jazyk překrytí.

 ![Ikony projektu 32x32](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")

 **Příklady velkých (32x32) ikon projektů**

### <a name="production-details"></a>Podrobnosti o výrobě
 Všechny nové prvky uživatelského rozhraní by měly být vytvořeny pomocí Windows Presentation Foundation (WPF) a všechny nové ikony pro WPF by měly být ve formátu 32bitový PNG. 24bitový formát PNG je starší formát, který nepodporuje průhlednost, a proto se nedoporučuje pro ikony.

 Uložte rozlišení na 96 DPI.

#### <a name="file-types"></a>Typy souborů

- **32bitový formát PNG:** preferovaný formát pro ikony. Bezztrátový formát souboru komprese dat, který může uložit jeden rastrový obraz (pixel). 32bitové soubory PNG podporují průhlednost alfa kanálů, korekci gama a prokládání.

- **32bitový bmp:** pro jiné ovládací prvky než WPF. 32bitový BMP, nazývaný také XP nebo vysoká barva, je formát obrazu RGB/A, což je obraz s věrnými barvami s průhledností alfa kanálů. Alfa kanál je vrstva průhlednosti určená v aplikaci Adobe Photoshop, která je pak uložena v bitmapě jako další (čtvrtý) barevný kanál. Černé pozadí je přidáno během výroby kresby do všech 32bitových souborů BMP, aby poskytlo rychlý vizuální podnět o hloubce barev. Toto černé pozadí představuje oblast, která má být maskována v ui.

- **32bitová ICO:** pro ikony projektu a Přidat položku. Všechny soubory ICO jsou 32bitové věrné barvy s průhledností alfa kanálů (RGB/A). Vzhledem k tomu, že soubory ICO mohou ukládat více velikostí a hloubky barev, jsou ikony systému Vista často ve formátu ICO obsahujícím velikost obrázků 16x16, 32x32, 48x48 a 256x256. Aby bylo možné zobrazit správně v Průzkumníkovi Windows, musí být soubory ICO uloženy na 24bitové a 8bitové barevné hloubky pro každou velikost obrazu.

- **XAML:** pro návrhové plochy a windows adornery. Ikony XAML jsou vektorové obrazové soubory, které podporují změnu měřítka, otáčení, archivace a průhlednost. Nejsou běžné v sadě Visual Studio dnes, ale jsou stále populárnější z důvodu jejich flexibility.

- **Svg**

- **24bitový bmp:** pro panel příkazů sady Visual Studio. True-color RGB formát obrazu, 24-bit BMP je ikona konvence, která vytváří vrstvu průhlednosti pomocí purpurové (R = 255, G = 0, B = 255) jako barevný klíč pro knock-out vrstvy průhlednosti. V 24bitovém bmp jsou všechny purpurové povrchy zobrazeny pomocí barvy pozadí.

- **24bitový soubor GIF:** pro panel příkazů sady Visual Studio. Formát obrazu RGB s věrnými barvami, který podporuje průhlednost. Soubory GIF se často používají v kresbě Průvodce a animacích GIF.

### <a name="icon-construction"></a>Konstrukce ikon
 Nejmenší velikost ikony v sadě Visual Studio je 16x16. Největší běžné použití je 32x32. Mějte na paměti, že při navrhování ikony nevyplňujte celý rámeček 16x16, 24x24 nebo 32x32. Čitelná, jednotná konstrukce ikon je nezbytná pro rozpoznání uživatele. Při vytváření ikon dodržujte následující body.

- Ikony by měly být jasné, srozumitelné a konzistentní.

- Je lepší použít prvky oznámení o stavu jako jednotlivé ikony a ne je skládat na základní prvek ikony. V určitých kontextech může ui vyžadovat, aby byl prvek stavu spárován se základním prvkem.

- Ikony projektu jsou obvykle soubory .ico, které obsahují několik velikostí. Aktualizovány jsou pouze ikony 16x16, 24x24 a 32x32. Většina ikon 16x16 a 24x24 bude obsahovat stejné prvky. Ikony 32x32 obsahují další podrobnosti, včetně typu jazyka projektu, pokud je to možné.

- U ikon 32 x 32 mají základní prvky obvykle tloušťku čáry 2 pixely. Pro prvky podrobností lze použít tloušťku čáry 1 nebo 2 pixely. Použijte svůj nejlepší úsudek k určení, který je vhodnější.

- Měj mezi elementy pro ikony 16x16 a 24 x 24 mezi prvky alespoň 1 obrazové úhly. Pro ikony 32 x 32 použijte mezery o 2 obrazové body mezi prvky a mezi modifikátorem a základním elementem.

  ![Rozteč prvků pro ikony 16x16, 24x24 a 32x32](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")

  **Rozteč prvků pro ikony velikosti 16x16, 24x24 a 32x32**

#### <a name="color-and-accessibility"></a>Barva a přístupnost
 Visual Studio dodržování zásady vyžadují, aby všechny ikony v produktu projít požadavky na usnadnění pro barvu a kontrast. Toho je dosaženo inverzí ikony a při navrhování byste si měli být vědomi toho, že budou v produktu programově obráceni.

 Další informace o používání barev v ikonách sady Visual Studio najdete v tématu [Použití barev v obrázcích](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Použití barev v obrazech

### <a name="overview"></a>Přehled
 Ikony v sadě Visual Studio jsou primárně monochromatické. Barva je vyhrazena pro předávání konkrétních informací a nikdy pro dekoraci. Barva se používá:

- pro označení akce

- upozornění uživatele na oznámení o stavu

- pro určení jazykové příslušnosti

- rozlišení položek v rámci technologie IntelliSense

### <a name="accessibility"></a>Přístupnost
 Visual Studio dodržování zásady vyžadují, aby všechny ikony zaškrtnuté do produktu projít požadavky na usnadnění pro barvu a kontrast. Barvy v paletě vizuálních jazyků byly testovány a splňují tyto požadavky.

#### <a name="color-inversion-for-dark-themes"></a>Barevná inverze pro tmavé motivy
 Chcete-li, aby se ikony zobrazovaly se správným kontrastním poměrem v tmavém motivu sady Visual Studio, je inverze použita programově. Barvy v této příručce byly vybrány částečně tak, aby se invertovat správně. Omezte použití barvy na tuto paletu, nebo budete mít nepředvídatelné výsledky při použití inverze.

 ![Příklady ikon, jejichž barvy byly obráceny](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **Příklady ikon, u kterých byly jejich barvy obrácené**

### <a name="base-palette"></a>Základní paleta
 Všechny standardní ikony obsahují tři základní barvy. Ikony neobsahují žádné přechody nebo vržené stíny, s jednou nebo dvěma výjimkami pro ikony 3D nástrojů.

|Využití|Name (Název)|Hodnota (světlý motiv)|Políčko|Příklad|
|-----------|----------|---------------------------|------------|-------------|
|Pozadí/Tmavá|VS BG|424242 / 66,66,66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Příklad základní palety](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|Popředí/světlo|VS FG|F0EFF1 / 240 239 241|![Vzorník F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Obrys|VS ven|F6F6F6 / 246 246 246|![Vzorník F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Kromě základních barev může každá ikona obsahovat jednu další barvu z rozšířené palety.

### <a name="extended-palette"></a>Rozšířená paleta

#### <a name="action-modifiers"></a>Modifikátory akce
 Čtyři níže uvedené barvy označují typy akcí vyžadované modifikátory akcí:

|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|
|-----------|----------|--------------------------|------------|
|Kladné|VS Akce zelená|388A34 / 56 138,52|![Vzorník 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Záporný|VS akce červená|A1260D / 161,38,13|![Políčko A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Neutral|VS Akce Modrá|00539C / 0,83 156|![Políčko 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Vytvořit/Nový|VS Akce Oranžová|C27D1A / 194 156,26|![Políčko C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Příklady
 Zelená se používá pro modifikátory pozitivní akce, jako je "Přidat", "Spustit", "Přehrát" a "Ověřit".

|||||
|-|-|-|-|
|![Spustit ikonu](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Spustit**|![Spustit ikonu](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery") **spouštění dotazu**|![Přehrát ikonu Přehrát všechny kroky](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **Přehrát všechny kroky**|![Přidat ikonu ovládacího prvku](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") **Přidat ovládací prvek**|

 Červená se používá pro modifikátory negativní akce, jako je "Odstranit", "Zastavit", "Zrušit" a "Zavřít".

|||||
|-|-|-|-|
|![Ikona Odstranit vztah](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") **Odstranit vztah**|![Odstranit ikonu sloupce](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") **Odstranit sloupec**|![Zastavit dotaz na](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") zastavení **dotazu**|![Ikona připojení offline](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") **Připojení offline Připojení offline**|

 Modrá barva se použije na modifikátory neutrální akce, které jsou nejčastěji reprezentovány jako šipky, například "Otevřít", "Další", "Předchozí", Import a Export.

|||||
|-|-|-|-|
|![Přejít na ikonu pole](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") **Přejít na pole**|![Dávková kontrola&#45;v ikoně](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") **Dávkové vrácení se změnami**|![Ikona Editor adresy](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor") **Editor adres**|![Ikona editoru](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor") **přidružení Editor přidružení**|

 Tmavé zlato se používá především pro modifikátor "Nový".

|||||
|-|-|-|-|
|![Ikona nového projektu](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **Nový projekt**|![Vytvořit novou ikonu grafu](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") **Vytvořit nový graf**|![Nová ikona testování jednotky](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") **Nový test jednotky**|![Nová ikona položky seznamu](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") **Nová položka seznamu**|

#### <a name="special-cases"></a>Zvláštní případy
 Ve zvláštních případech může být modifikátor barevné akce použit nezávisle jako samostatná ikona. Barva použitá pro ikonu odráží akce, ke kterým je ikona přidružena. Toto použití je omezeno na malou podmnožinu ikon, včetně:

||||||
|-|-|-|-|-|
|![Spustit ikonu](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Spustit**|![Ikona](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop") **Zastavit**|![Odstranit ikonu](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **Odstranit**|![Ikona Uložit](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **Uložit**|![Přejít zpět ikona](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack") **Přejít zpět**|

### <a name="code-hierarchy-palette"></a>Paleta hierarchie kódu

#### <a name="folder"></a>Složka

|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|Příklad|
|-----------|----------|--------------------------|------------|-------------|
|Složky|Složka|DCB67A / 220 182 122|![Vzorník DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Ikona barvy složky](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Jazyky visual studia
 Každý z běžných jazyků nebo platforem dostupných v sadě Visual Studio má přidruženou barvu. Tyto barvy se používají na základní ikoně nebo na modifikátory jazyka, které se zobrazují v pravém horním rohu složených ikon.

|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF modrá|0095D7 / 0 149 215|![Políčko 0095D7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP Fialová|9B4F96 / 155 79 150|![Vzorník 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS Zelená (VS Akce Zelená)|388A34 / 56 138,52|![Vzorník 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|CSS červená|BD1E2D / 189,30,45|![Políčko BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS Fialová|672878 / 103,40,120|![Vzorník 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|JS Oranžová|F16421 / 241 100,33|![Vzorník F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB modrá (VS Akce Modrá)|00539C / 0,83 156|![Políčko 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|TS oranžová|E04C06 / 224,76,6|![Vzorník E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|PY Zelená|879636 / 135,150,54|![Vzorník 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Příklady ikon s modifikátory jazyka

|||||||
|-|-|-|-|-|-|
|![Ikona jazyka Visual Basic](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![Ikona C&#35;](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **C#**|![Ikona C&#43;&#43; ](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus") **C++**|![F&#35; ikona](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **F#**|![JavaScript ikona](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Ikona Pythonu](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![ASP ikona](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP ASP**|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![Ikona TypeScript typu](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 Ikony Technologie IntelliSense používají exkluzivní paletu barev. Tyto barvy pomáhají uživatelům rychle rozlišovat mezi různými položkami v místní nabídce IntelliSense.

|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|
|-----------|----------|--------------------------|------------|
|Třída, Událost|VS Akce Oranžová|C27D1A / 194 125,26|![Políčko C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Metoda rozšíření, metoda, modul, delegát|VS Akce Fialová|652D90 / 101 45 144|![Vzorník 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Pole, výčet zboží, makro, struktura, typ hodnoty sjednocení, operátor, rozhraní|VS Akce Modrá|00539C / 0,83 156|![Políčko 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Objekt|VS Akce zelená|388A34 / 56 138,52|![Vzorník 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Konstanta, Výjimka, Výčet položky, Mapa, Položka mapy, Obor názvů, Šablona, Definice typu|Pozadí (VS BG)|424242 / 66,66,66|![Vzorník 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Příklady ikon Technologie IntelliSense

||||||
|-|-|-|-|-|
|![Třída třídy IntelliSense](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass") **Class**|![Ikona soukromé události IntelliSense](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Soukromá událost**|![Ikona delegáta IntelliSense](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate") **Delegate Delegate**|![IntelliSense metoda přítel ikona](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Metoda Přítele**|![Ikona pole](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field") **Pole Pole**|
|![Ikona položky výčtu chráněná enum chráněné technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **Protected Enum Item**|![Ikona objektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject") **Object**|**Šablona** ![šablony intelliSense](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate")|**Zástupce** ![výjimky výjimky technologie IntelliSense](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")||

### <a name="notifications"></a>Oznámení
 Oznámení v sadě Visual Studio se používají k označení stavu. Paleta oznámení používá následující čtyři barvy, stejně jako černé nebo bílé možnosti výplně v popředí, k definování oznámení s následujícími úrovněmi stavu.

|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|
|-----------|----------|--------------------------|------------|
|Stav: neutrální|Oznámení modrá (VS Modrá)|1BA1E2 / 27 161 226|![Vzorník 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Stav: pozitivní|Zelená oznámení (vs zelená)|339933 / 51,153,51|![Vzorník 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Stav: negativní|Oznámení červená (vs červená)|E51400 / 229,20,0|![Vzorník E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Stav: upozornění|Oznámení žlutá (vs oranžová)|FFCC00 / 255 204,0|![Vzorník FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Výplň popředí|Oznámení černé (černé)|000000 / 0,0,0|![Políčko &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Výplň popředí|Oznámení bílá (bílá)|FFFFFF / 255 255 255|![Vzorník FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Příklady ikon oznámení

|||||
|-|-|-|-|
|![Výstraha](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert") **Alert**|![Upozornění na ikonu](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning") **Upozornění**|![Kompletní ikona](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **dokončena**|![Ikona](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop") **Zastavit**|

### <a name="visual-studio-online"></a>Visual Studio Online
 Obecně platí Visual Studio Online se skládá z funkcí hostovaných v prohlížeči. Barva se liší v různých prostředích, ale styl zůstává stejný.

|Skupina|Využití|Name (Název)|Hodnota (všechna témata)|Políčko|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Pozadí|TFSO BG|656565/ 101, 101, 101|![Vzorník 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Obrys|TFSO VEN|FFFFFF / 255, 255, 255|![Vzorník FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Pozadí|White|FFFFFF / 255, 255, 255|![Vzorník FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Monako|Pozadí|White|FFFFFF / 255, 255, 255|![Vzorník FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Pozadí|White|FFFFFF / 255, 255, 255|![Vzorník FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normální|F12 Grey_Primary|555555 / 85, 85, 85|![Vzorník 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Hover|F12 Blue_Hover|2279BF / 34 121 191|![Vzorník 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Zakázáno|F12 LtGrey_Disabled|ABABAC / 171 171 172|![Políčko ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Najetí na pozadí|Vznášet se nad bg|D9EBF7 / 217 235 247|![Vzorník D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Stisknuté pozadí|Lisované bg|B2D7F0 / 178 215 240|![Políčko B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Obrys|VS OUT|F6F6F6 / 246 246 246|![Vzorník F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Informace|Informace|00BCF2 / 0 188 242|![Políčko 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Upozornění|Upozornění|F28300 / 242 131,0|![Vzorník F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Chyba / Negativní|Error_Negative|E81123 / 232,17,35|![Vzorník E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Začátek / Pozitivní|Start_Positive|009E49 / 0,158,73|![Políčko 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Typ přerušení|Typ přerušení|9B4F96 / 155 79 150|![Vzorník 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Značka události|Značka události|A51F00 / 165,31,0|![Políčko A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Značka uživatele|Značka uživatele|F16220 / 241,98,32|![Vzorník F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Příklady ikon Visual Studia Online

|TFS Online||||
|----------------|-|-|-|
|![TfS Online ikona týmu](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online team**|![Informační ikona TFS](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation") **Informace**|![Ikona historie TFS](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory") **Historie**|![Větev pobočky TFS](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch") **Branch**|

|Napa||||
|----------|-|-|-|
|![Ikona obsahu Napa](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent") **Obsah**|![Ikona pošty na napa office](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") **Office Mail**|![Ikona Napa SharePoint,](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|**Podokno úloh** ![podokna úloh podokna úloh Napa](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane")|

|Monako||||
|------------|-|-|-|
|![Ikona souborů Monaka](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") **Soubory**|![Monako Git ikona](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![Ikona vyhledávání monaka](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch") **Hledat**|![Ikona textu Monaka](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText") **Text**|

|F12||||
|---------|-|-|-|
|![F12 pěkný kód ikonu](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode") **Pěkný kód**|![F12 Výstražná ikona](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning") **Upozornění Upozornění**|![Ikona Etuace ikony F12](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate") **Emulujte**|
