---
title: Editor obrázků
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd7d9aed75876b47a6574d46b226f5baec336883
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589315"
---
# <a name="image-editor"></a>editor obrázků

Tento článek popisuje, jak pracovat s **editorem imagí** sady Visual Studio k zobrazení a úpravě prostředků textury a obrázků.

**Editor obrázků** můžete použít pro práci s typy bohatých textur a formátů obrázků používaných při vývoji aplikací DirectX. To zahrnuje podporu oblíbených formátů souborů obrázků a barevného kódování, funkcí jako alfa kanálů a mapování MIP a mnoha vysoce komprimovaných formátů hardwarových a akcelerovaných textur, které podporuje DirectX.

## <a name="supported-formats"></a>Podporované formáty

**Editor obrázků** podporuje následující formáty obrázků:

|Název formátu|Přípona názvu souboru|
|-----------------| - |
|Formát PNG|*.png*|
|JPEG|*. jpg*, *. jpeg*, *. JPE*, *. jfif*|
|Přímo nakreslit plochu|*. DDS*|
|Formát GIF|*. gif*|
|Monochromatick|*. bmp*, *. DIB*|
|Formát tagovaného obrázkového souboru|*. tif*, *. TIFF*|
|TGA (Targa)|*. TGA*|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat obrázek do projektu aplikace Visual Studio a nakonfigurovat ho pro vaše požadavky.

### <a name="add-an-image-to-your-project"></a>Přidání obrázku do projektu

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt, do kterého chcete přidat obrázek, a pak zvolte možnost **Přidat**  >  **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte v části **nainstalováno**možnost **Grafika**a pak pro obrázek vyberte příslušný formát souboru.

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **grafiky** , možná budete muset nainstalovat součást **image a 3D model editory** . Zavřete dialogové okno a pak na panelu nabídek vyberte **nástroje**  >  **získat nástroje a funkce** . tím otevřete **instalační program pro Visual Studio**. Vyberte kartu **jednotlivé komponenty** a potom vyberte součást **image a 3D model editory** v kategorii **hry a grafiky** . Vyberte **Upravit**.
   >
   > ![Součást Editor obrázků a 3D model](media/image-3d-model-editors-component.png)

   Informace o tom, jak zvolit formát souboru podle vašich požadavků, najdete v tématu [Volba formátu obrázku](#choose-the-image-format).

3. Zadejte **název** souboru obrázku a **umístění** , kde se má vytvořit.

4. Vyberte tlačítko **Přidat**.

### <a name="choose-the-image-format"></a>Volba formátu obrázku

V závislosti na tom, jak plánujete použít image, můžou být některé formáty souborů vhodnější než jiné. Některé formáty například nemusí podporovat funkci, kterou potřebujete, například průhlednost nebo konkrétní formát barvy. Některé formáty nemusí poskytovat vhodnou kompresi pro druh obsahu bitové kopie, který jste naplánovali.

Následující informace vám pomohou zvolit formát obrázku, který vyhovuje vašim potřebám:

**Rastrový obrázek (. bmp)**

Formát rastrového obrázku. Nekomprimovaný formát obrázku, který podporuje 24bitové barvy. Formát rastrového obrázku nepodporuje průhlednost.

**Obrázek GIF (. gif)**

Formát obrázku ve formátu GIF (Graphics Interchange Format). Bezeztrátový formát komprimovaný ve formátu LZW, který podporuje až 256 barev. Nevhodné pro fotografie a obrázky, které mají velký objem detailů barev, ale poskytuje dobré kompresní poměry pro obrázky s nízkými barvami, které mají vysoký stupeň provázanosti barev.

**Obrázek JPG (. jpg)**

Formát obrázku ve formátu JPEG (společný fotografický Experts Group). Vysoce komprimovaný formát neztrátového obrazu, který podporuje 24bitové barvy a je vhodný pro účely běžné komprese imagí s vysokým stupněm provázanosti barev.

**Obrázek PNG (. png)**

Formát obrázku PNG (Portable Network Graphics). Středně komprimovaný a bezeztrátový formát obrazu, který podporuje 24bitové barvy a alfa průhlednost. Je vhodný pro přirozené i umělé bitové kopie, ale neposkytuje kompresní poměry tak, jak jsou, stejně jako formáty ztrát, jako je JPG nebo GIF.

**Obrázek TIFF (. tif)**

Formát obrázku TIFF nebo TIF (Tagged Image File Format). Flexibilní formát obrázku, který podporuje několik schémat komprese.

**Textura DDS (. DDS)**

Formát textury sady DirectDraw (DDS surfing). Vysoce komprimovaný formát struktury s neztrátou, který podporuje 24bitové barvy a alfa průhlednost. Jeho kompresní poměry můžou být vysoké jako 8:1. Je založený na kompresi textury S3, která se dá dekomprimovat na hardwaru grafiky.

**Obrázek TGA (. TGA)**

Formát obrázku TGA (Truevision Graphics Adapter) (označovaný také jako Targa). Bezeztrátový formát komprimovaný ve formátu RLE, který podporuje barevně namapovanou barvu (paletu barev) nebo přímý barevný obraz až na 24 bitů barev a alfa fólie. Nevhodné pro fotografie a obrázky, které mají velký objem detailů barev, ale poskytuje dobré kompresní poměry pro obrázky, které mají dlouhé rozpětí stejných barev.

### <a name="configure-the-image"></a>Konfigurace image

Než začnete pracovat s bitovou kopií, kterou jste vytvořili, můžete změnit její výchozí konfiguraci. Můžete například změnit jeho rozměry nebo formát barvy, který používá. Informace o tom, jak nakonfigurovat tyto a další vlastnosti obrázku, najdete v tématu [Vlastnosti obrázku](#image-properties).

> [!NOTE]
> Před uložením práce nezapomeňte nastavit vlastnost **formát barev** , pokud chcete použít konkrétní formát barvy. Pokud formát souboru podporuje kompresi, můžete nastavení komprese upravit při prvním uložení souboru nebo když zvolíte možnost **Uložit jako**.

## <a name="work-with-the-image-editor"></a>Práce s editorem obrázků

Tato část popisuje, jak použít **Editor obrázků** k úpravě textur a imagí.

Příkazy, které mají vliv na stav **editoru obrázků** , jsou umístěny na panelu nástrojů **režim editoru obrázků** spolu s pokročilými příkazy. Panel nástrojů se nachází podél horního okraje návrhové plochy **editoru obrázků** . Nástroje pro kreslení jsou umístěné na panelu nástrojů **Editor obrázků** podél levého okraje návrhové plochy **editoru obrázků** .

### <a name="image-editor-mode-toolbar"></a>Panel nástrojů Režim editoru obrázků

![Panel nástrojů Režim editoru obrázků v sadě Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

Následující tabulka popisuje položky na panelu nástrojů **režim editoru obrázků** , které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Výběr**|Umožňuje výběr obdélníkové oblasti obrázku. Po výběru oblasti ji můžete vyjmout, kopírovat, přesunout, škálovat, otočit, překlopit nebo odstranit. Pokud existuje aktivní výběr, nástroje pro kreslení ovlivní pouze vybranou oblast.|
|**Nepravidelný výběr**|Umožňuje výběr nepravidelné oblasti obrázku. Po výběru oblasti ji můžete vyjmout, kopírovat, přesunout, škálovat, otočit, překlopit nebo odstranit. Pokud existuje aktivní výběr, nástroje pro kreslení ovlivní pouze vybranou oblast.|
|**Výběr hůlka**|Umožňuje výběr podobně barevné oblasti obrázku. *Tolerance*– tedy maximální rozdíl mezi sousedícími barvami, ve kterých jsou považovány za podobné, lze nakonfigurovat tak, aby zahrnovaly menší nebo širší rozsah podobných barev. Po výběru oblasti ji můžete vyjmout, kopírovat, přesunout, škálovat, otočit, překlopit nebo odstranit. Pokud existuje aktivní výběr, nástroje pro kreslení ovlivní pouze vybranou oblast.|
|**Posouvání**|Povoluje přesun obrázku relativně k rámečku okna. V režimu **posouvání** vyberte v imagi nějaký bod a pak ho přesuňte kolem.<br /><br /> Režim **posouvání** můžete dočasně aktivovat tak, že stisknete a podržíte klávesu **CTRL** .|
|**Zoom**|Povoluje zobrazení více nebo méně podrobností obrázku relativně k rámečku okna. V režimu **zvětšení** vyberte bod na obrázku a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali zmenšení.<br /><br /> Můžete přiblížit nebo oddálit stisknutím a podržením klávesy **CTRL** , když buď použijete kolečko myši, nebo stisknete znaménko plus () **+** nebo mínus znaménko ( **-** ).|
|**Zvětšit na skutečnou velikost**|Zobrazí obrázek pomocí vztahu 1:1 mezi pixely obrázku a pixely obrazovky.|
|**Přizpůsobit zobrazení**|Zobrazí celý obrázek v rámci okna.|
|**Zvětšit na šířku**|Zobrazí celou šířku obrázku v rámci okna.|
|**Mřížka**|Povolí nebo zakáže mřížku, která zobrazuje hranice v pixelech. Mřížka se nemusí zobrazit, dokud nezměníte zobrazení obrázku.|
|**Zobrazit další úroveň MIP**|Aktivuje další větší úroveň MIP v řetězci mapy MIP. Na návrhové ploše se zobrazí aktivní úroveň MIP. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|**Zobrazit předchozí úroveň MIP**|Aktivuje další menší úroveň MIP v řetězci mapy MIP. Na návrhové ploše se zobrazí aktivní úroveň MIP. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|**Červený kanál**<br /><br /> **Zelený kanál**<br /><br /> **Modrý kanál**<br /><br /> **Kanál alfa**|Povolí nebo zakáže konkrétní barevný kanál. **Poznámka:**  Když systematicky povolíte nebo zakážete barevné kanály, můžete izolovat problémy, které souvisí s jedním nebo více z nich. Můžete například identifikovat nesprávnou průhlednost alfa.|
|**Pozadí**|Povolí nebo zakáže zobrazení pozadí prostřednictvím průhledných částí obrázku. Způsob zobrazení pozadí můžete nakonfigurovat výběrem z těchto možností:<br /><br /> **Šachovnicový**<br /> Používá zelenou barvu společně se zadanou barvou pozadí k zobrazení pozadí jako šachovnicového vzoru. Tuto možnost můžete použít, chcete-li lépe poznat průhledné části obrázku.<br /><br /> Bílé pozadí<br /> Používá bílou barvu k zobrazení pozadí.<br /><br /> Černé pozadí<br /> Použije barvu černou k zobrazení pozadí.<br /><br /> Animovat pozadí<br /> Sevýšení šachovnicového vzoru pomalu. Tuto možnost můžete použít, chcete-li lépe poznat průhledné části obrázku.|
|**Vlastnosti**|Alternativně otevře nebo zavře okno **vlastnosti** .|
|**Pokročilý**|Obsahuje další příkazy a možnosti.<br /><br /> **Filtry**<br /><br /> Nabízí několik běžných filtrů obrázků: **černou a bílá**, **Rozostřit**, **zesvětlit**, **ztmavit**, **detekce hran**, **reliéf**, **invertování barev**, **Ripple**, **Sépiový tón tón**a **Zostřit**.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení pomocí D3D11**<br /> Vykreslí návrhovou plochu **editoru obrázků** pomocí Direct3D 11.<br /><br /> **Vykreslení pomocí D3D11WARP**<br /> Vykreslí návrhovou plochu **editoru obrázků** pomocí Direct3D 11 Windows Advanced rastring Platform (osnova).<br /><br /> **Nástroje**<br /><br /> **Překlopit vodorovně**<br /> Předává obraz kolem jeho vodorovné osy nebo osy x.<br /><br /> **Převrátit svisle**<br /> Předává obraz kolem jeho vertikálního nebo osy y.<br /><br /> **Generovat MIPS**<br /> Vygeneruje úrovně MIP pro obrázek. Pokud úrovně MIP již existují, budou znovu vytvořeny z nejvyšší úrovně MIP. Všechny změny, které byly provedeny v menších úrovních MIP, budou ztraceny. Chcete-li uložit úrovně MIP, které jste vygenerovali, je nutné použít formát *. dds* k uložení obrázku.<br /><br /> **Zobrazení**<br /><br /> **Snímková frekvence**<br /> Pokud je tato možnost povolená, zobrazí kmitočet snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. **Tip:** Můžete zvolit tlačítko **Upřesnit** a znovu spustit poslední příkaz.|

### <a name="image-editor-toolbar"></a>Panel nástrojů Editor obrázků

![Panel nástrojů Editor obrázků](../designers/media/digit-tre-toolbar.png)

Následující tabulka popisuje položky na panelu nástrojů **editoru obrázků** , které jsou uvedeny v pořadí, ve kterém se zobrazují shora dolů:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Tužky**|Pomocí výběru aktivní barvy nakreslí tah s aliasem. Můžete nastavit barvu a tloušťku tahu v okně **vlastnosti** .|
|**Cest**|Použije aktivní výběr barvy k nakreslení tahu proti vyhlazení. Můžete nastavit barvu a tloušťku tahu v okně **vlastnosti** .|
|**Rozprašovač**|Použije aktivní výběr barvy k nakreslení tahu proti vyhlazení, který se společně s obrázkem rozroste a má větší sytost jako funkce času. Můžete nastavit barvu a tloušťku tahu v okně **vlastnosti** .|
|**Nástrojem**|Nastaví aktivní výběr barvy na barvu vybraného pixelu.|
|**Výplň**|Použije aktivní výběr barvy k vyplnění oblasti obrázku. Ovlivněná oblast je definována jako pixel, ve kterém je výplň použita, spolu s každým pixelem, který je k němu připojen, v pixelech stejné barvy, což je stejná barva. Pokud je výplň použita v rámci aktivního výběru, bude ovlivněná oblast omezena výběrem.<br /><br /> Ve výchozím nastavení je aktivní výběr barvy Blendem spolu s ovlivněnou oblastí obrázku podle jeho komponenty alfa. Chcete-li použít aktivní výběr barvy k přepsání příslušné oblasti, stiskněte a podržte klávesu **SHIFT** při použití nástroje Fill.|
|**Guma**|Nastaví pixely na plně průhlednou barvu, pokud obrázek podporuje alfa kanál. V opačném případě nastaví pixely na aktivní barvu pozadí.|
|**Čára**, **obdélník**, **Zaoblený obdélník**, **Elipsa**|Nakreslí obrazec na obrázku. Můžete nastavit barvu a tloušťku obrysu v okně **vlastnosti** .<br /><br /> Chcete-li nakreslit primitivní, který má stejnou šířku a výšku, stiskněte a podržte při kreslení klávesu **SHIFT** .|
|**Text**|Vykreslí text pomocí výběru barvy popředí. Barva pozadí je určena výběrem barvy pozadí. U průhledných pozadí hodnota alfa výběru barvy pozadí musí být 0. Když je oblast textu aktivní, můžete nastavit, zda je text vykreslen pomocí vyhlazení, a můžete nastavit textovou **hodnotu**, **písmo**, **Velikost**a styl –**tučné**, **kurzíva**nebo **podtržení**– v okně **vlastnosti** . Obsah a vzhled textu je finalizován, když textová oblast již není aktivní.|
|**Otočit**|Otočí obrázek 90 stupňů po směru hodinových ručiček.|
|**Sklon**|Ořízne obrázek na aktivní výběr.|

### <a name="work-with-mip-levels"></a>Práce s úrovněmi MIP

Některé formáty obrázků, například textura DirectDraw (*. dds*), podporují úrovně MIP pro úroveň rozsahu minimálních hodnot v podrobnostech (LOD). Informace o tom, jak vygenerovat a pracovat s úrovněmi MIP, najdete v tématu [Postupy: vytváření a úpravy úrovní MIP.](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Práce s transparentností

Některé formáty obrázků, například plocha DirectDraw (*. dds*), podporují transparentnost. Transparentnost lze použít několika způsoby v závislosti na použitém nástroji. Chcete-li určit úroveň transparentnosti výběru barvy, v okně **vlastnosti** nastavte pro výběr barvy komponentu **a** (alfa).

Následující tabulka popisuje, jak různé druhy nástrojů řídí použití průhlednosti:

|Nástroj|Popis|
|----------|-----------------|
|**Tužka**, **štětec**, **sprej**, **čára**, **obdélník**, **Zaoblený obdélník**, **Elipsa**, **text**|Chcete-li prolnout aktivní výběr barev společně s obrázkem, v okně **vlastnosti** rozbalte skupinu vlastností **kanály** a nastavte zaškrtávací políčko **kreslit** na **alfa** kanálu a pak normálně kreslete.<br /><br /> Chcete-li kreslit pomocí výběru aktivní barvy a ponechání hodnoty alfa obrázku, zrušte zaškrtnutí políčka **Draw** kanálu **alfa** a pak vykreslete normálně.|
|**Výplň**|Chcete-li prolnout aktivní výběr barev spolu s obrázkem, stačí zvolit oblast, která má být vyplněna.<br /><br /> Chcete-li použít aktivní výběr barvy – včetně hodnoty alfa kanál – k přepsání obrázku, stiskněte a podržte klávesu **SHIFT** a zvolte oblast, která má být vyplněna.|

### <a name="image-properties"></a>Vlastnosti obrázku

K určení různých vlastností obrázku můžete použít okno **vlastnosti** . Můžete například nastavit vlastnosti Width a Height pro změnu velikosti obrázku.

Následující tabulka obsahuje popis vlastností obrázku:

|Vlastnost|Popis|
|--------------|-----------------|
|Width (Šířka)|Šířka obrázku|
|Height (Výška)|Výška obrázku|
|Bitů na pixel|Počet bitů, které reprezentují jednotlivé pixely. Hodnota této vlastnosti závisí na **formátu barvy** obrázku.|
|Transparentní výběr|**True** pro prolnutí vrstvy výběru společně s hlavním obrázkem na základě hodnoty alfa vrstvy výběru; v opačném případě **false**. Tato položka je k dispozici pouze pro obrázky, které podporují alfa.|
|Formát|Formát barvy obrázku V závislosti na formátu obrázku můžete zadat nejrůznější formáty barev. Formát barvy definuje počet a druh barevných kanálů, které jsou zahrnuty v obrázku, a také velikost a kódování různých kanálů.|
|Úroveň MIP|Aktivní úroveň MIP. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|Počet úrovní MIP|Celkový počet úrovní MIP v obrázku. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|Počet snímků|Celkový počet snímků v obrázku. Tato položka je k dispozici pouze pro obrázky, které podporují pole textury.|
|Rámec|Aktuální rámec. Lze zobrazit pouze první rámec. všechny ostatní snímky jsou ztraceny, když je obrázek uložen.|
|Počet hloubek řezu|Celkový počet hloubkových řezů v obrázku. Tato položka je k dispozici pouze pro image, které podporují textury svazků.|
|Hloubka řezu|Aktuální Hloubka řezu. Lze zobrazit pouze první řez. Při uložení obrázku dojde ke ztrátě všech ostatních řezů.|

> [!NOTE]
> Vzhledem k tomu, že vlastnost **otočit by** se vztahuje na všechny nástroje a vybrané oblasti, vždy se zobrazí v dolní části okna **vlastnosti** spolu s dalšími vlastnostmi nástroje. Možnost **Otočit o** je vždy zobrazená, protože celá Image je implicitně vybraná, když není k dispozici jiný výběr nebo aktivní nástroj. Další informace o vlastnosti **otočit** o vlastnost naleznete v tématu [Vlastnosti nástroje](#tool -properties).

### <a name="resize-images"></a>Změna velikosti obrázků

Existují dva způsoby, jak změnit velikost obrázku. V obou případech **Editor obrázků** používá interpolaci varianty k převzorkování obrázku.

- V okně **vlastnosti** zadejte nové hodnoty vlastností **Width** a **Height** .

- Vyberte celý obrázek a pomocí značek ohraničení změňte velikost obrázku.

### <a name="selected-regions"></a>Vybrané oblasti

Výběry v **editoru obrázků** definují oblasti obrázku, které jsou aktivní. Aktivní oblasti jsou ovlivněny pomocí nástrojů a transformací. Pokud existuje aktivní výběr, oblasti mimo vybranou oblast nejsou ovlivněny většinou nástrojů a transformací. Pokud není aktivní výběr, je aktivní celý obrázek.

Většina nástrojů (**Tužka**, **štětec**, **sprej**, **výplň**, **mazání**a 2D primitiv) a transformace (**otočení**, **ořezávání**, **invertování barev**, překlopení **vodorovně**a **Překlopit svisle**) jsou omezené nebo definované aktivním výběrem. Některé nástroje (**kapátko** a **text**) a transformace (**generování MIPS**) ale neovlivňují žádný aktivní výběr. Tyto nástroje se vždy chovají, jako by byl celý obrázek aktivním výběrem.

Když vybíráte oblast, můžete stisknout a podržet klávesu **SHIFT** k provedení proporčního (čtvercového) výběru. V opačném případě výběr není omezen.

#### <a name="resize-selections"></a>Změnit velikost výběru

Po výběru oblasti můžete změnit její velikost nebo její obsah tak, že změníte velikost značky výběru. Když měníte velikost vybrané oblasti, můžete pro změnu chování vybrané oblasti při změně velikosti použít následující modifikační klávesy:

**CTRL** – zkopíruje obsah vybrané oblasti předtím, než se změní jeho velikost. Původní obrázek zůstane beze změny v době, kdy se změnila velikost kopie.

**SHIFT** – změní velikost vybrané oblasti v poměru k původní velikosti.

**ALT** – změní velikost oblasti výběru. Obrázek zůstane beze změny.

Následující tabulka popisuje platné kombinace klávesových zkratek:

|Podržte|Posouvá|Alt|Popis|
|----------|-----------|---------|-----------------|
||||Změní velikost obsahu vybrané oblasti.|
||**Posouvá**||Proporcionálně mění velikost obsahu vybrané oblasti.|
|||**ALT**|Změní velikost vybrané oblasti. Tato definice definuje novou oblast výběru.|
||**Posouvá**|**ALT**|Proporcionálně mění velikost vybrané oblasti. Tato definice definuje novou oblast výběru.|
|**Podržte**|||Zkopíruje a změní velikost obsahu vybrané oblasti.|
|**Podržte**|**Posouvá**||Kopie a pak proporcionálně mění velikost obsahu vybrané oblasti.|

### <a name="tool-properties"></a>Vlastnosti nástroje

Když je vybraný nástroj, můžete použít okno **vlastnosti** k zadání podrobností o tom, jak má obrázek vliv. Například můžete nastavit tloušťku nástroje **tužky** nebo barvu nástroje **štětec** .

Můžete nastavit barvu popředí i barvu pozadí. Oba podporují alfa kanál k poskytnutí neprůhlednosti definované uživatelem. Nastavení platí pro všechny nástroje. Pokud používáte myš, levé tlačítko myši odpovídá barvě popředí a pravé tlačítko myši odpovídá barvě pozadí.

Následující tabulka popisuje vlastnosti nástroje:

|Nástroj|Vlastnosti|
|----------|----------------|
|Všechny nástroje a výběry|**Otočit o**<br /> Definuje velikost ve stupních, po kterou je výběr nebo efekt nástroje otočen po směru hodinových ručiček.|
|**Tužka**, **štětec**, **sprej**, **Guma**|**Tloušťka**<br /> Definuje velikost oblasti, která je ovlivněná nástrojem.|
|**Text**|**Anti-alias**<br /> Vykreslí text, který obsahuje okraje s vyhlazením. To dává text hladšímu vzhledu.<br /><br /> **Hodnota**<br /> Text, který se má vykreslit<br /><br /> **Písmo**<br /> Písmo použité k vykreslení textu<br /><br /> **Velikost**<br /> Velikost textu<br /><br /> **Bold**<br /> Nastaví písmo tučně.<br /><br /> **Kurzíva**<br /> Převede písmo na kurzívu.<br /><br /> **Podtržené**<br /> Vytvoří podtržené písmo.|
|**2D primitiva**|**Anti-alias**<br /> Kreslí primitivní prvky, které mají okraje se vyhlazením. Díky tomu je jejich plynulejší vzhled.<br /><br /> **Tloušťka**<br /> Definuje tloušťku čáry, která tvoří hranici primitivního.<br /><br /> **Poloměr X**<br /> (Jenom zaoblený obdélník) Definuje poloměr zaoblení pro horní a dolní okraj primitivního rozhraní.<br /><br /> **Poloměr Y**<br /> (Jenom zaoblený obdélník) Definuje poloměr zaoblení pro levý a pravý okraj primitivního rozhraní.|
|**Tužka**, **štětec**, **sprej**, **2D primitiva**|**Kanály**<br /> Povoluje nebo zakazuje konkrétní barevné kanály pro zobrazení a vykreslení. Pokud je **zobrazení** nastavené pro konkrétní barevný kanál, tento kanál se v imagi zobrazuje. v opačném případě se nezobrazí. Pokud je pro konkrétní barevný kanál nastavená sada **Draw** , je tento kanál ovlivněn operacemi vykreslování. v opačném případě není.|
|**Výběr hůlka**, **výplň**|**Odolnost**<br /> Definuje maximální rozdíl mezi sousedícími barvami, ve kterých jsou považovány za podobné, takže méně nebo více podobných barev tvoří součást ovlivněné nebo vybrané oblasti. Ve výchozím nastavení je hodnota 32, což znamená, že sousední pixely v rámci 32 odstínů (světlejší nebo tmavší) původní barvy se považují za součást oblasti.|

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnout na režim **výběru**|**S**|
|Přepnout do režimu **lupy**|**Z**|
|Přepnout do režimu **posouvání**|**K**|
|Vybrat vše|**CTRL** + **A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**ESC** (řídicí znak)|
|Přiblížit|**CTRL** + **Kolečko myši – posunutí**<br /><br /> **CTRL** + **PageUp**<br /><br /> Znaménko plus ( **+** )|
|Oddálit|**CTRL** - **Kolečko myši dozadu**<br /><br /> **CTRL** - **PageDown**<br /><br /> Symbol mínus ( **-** )|
|Posunout obrázek nahoru|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posunout obrázek dolů|**Kolečko myši dopředu**<br /><br /> **PageUp**|
|Posunout obrázek doleva|**Posun** + **Kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **Posun** + **PageDown**|
|Posunout obrázek vpravo|**Posun** + **Kolečko myši – posunutí**<br /><br /> **Kolečko myši doprava**<br /><br /> **Posun** + **PageUp**|
|Zvětšit na skutečnou velikost|**CTRL** + **0** (nula)|
|Přizpůsobit obrázek oknu|**CTRL** + **G**, **CTRL** + **F**|
|Přizpůsobit obraz šířce okna|**CTRL** + **G**, **CTRL** + **I**|
|Přepnout mřížku|**CTRL** + **G**, **CTRL** + **g**|
|Oříznout obraz na aktuální výběr|**CTRL** + **G**, **CTRL** + **C**|
|Zobrazit další (vyšší podrobnosti) Úroveň MIP|**CTRL** + **G**, **CTRL** + **6**|
|Zobrazit předchozí (nižší podrobnosti) Úroveň MIP|**CTRL** + **G**, **CTRL** + **7**|
|Přepnout červený barevný kanál|**CTRL** + **G**, **CTRL** + **1**|
|Přepnout zelený barevný kanál|**CTRL** + **G**, **CTRL** + **2**|
|Přepnout modrý barevný kanál|**CTRL** + **G**, **CTRL** + **3**|
|Přepínání kanálu alfa (transparentnost)|**CTRL** + **G**, **CTRL** + **4**|
|Přepnout šachovnicový vzor pro alfa|**CTRL** + **G**, **CTRL** + **B**|
|Přepnout na nástroj pro výběr nepravidelného výběru|**L**|
|Přepnout na nástroj pro výběr na hůlka|**M**|
|Přepnout na nástroj tužka|**P**|
|Přepnout na nástroj štětec|**B**|
|Přepnout na nástroj Fill|**FJ**|
|Přepnout na nástroj mazání|**Cerebrální**|
|Přepnout na textový nástroj|**T**|
|Přepnout na nástroj Color-Select (kapátko)|**I**|
|Přesune aktivní výběr a jeho obsah.|Klávesy se **šipkami** .|
|Změní velikost aktivního výběru a jeho obsah.|**CTRL** + Klávesy se **šipkami**|
|Přesune aktivní výběr, ale ne jeho obsah.|**Posun** + Klávesy se **šipkami**|
|Změní velikost aktivního výběru, ale ne jeho obsah.|**Posun** + **CTRL** + Klávesy se **šipkami**|
|Potvrdit aktuální vrstvu|**Vrátit**|
|Zmenšit tloušťku nástroje|**[**|
|Zvětšit tloušťku nástroje|**]**|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled nástrojů, které lze použít v aplikaci Visual Studio pro práci s grafickými prostředky, jako jsou textury a obrázky, 3D modely a efekty shaderu.|
|[Editor modelů](../designers/model-editor.md)|Popisuje, jak používat Editor modelů sady Visual Studio pro práci s 3D modely.|
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje, jak používat návrháře shaderu sady Visual Studio pro práci s shadery.|
