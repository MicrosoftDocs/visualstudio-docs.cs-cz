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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589315"
---
# <a name="image-editor"></a>editor obrázků

Tento článek popisuje, jak pracovat s Visual Studio **Image Editor** zobrazit a upravit textury a obrazové prostředky.

**Editor obrázků** můžete použít k práci s druhy bohatých textur a obrazových formátů, které se používají při vývoji aplikací DirectX. To zahrnuje podporu pro populární formáty obrazových souborů a kódování barev, funkce, jako jsou alfa kanály a mapování MIP, a mnoho vysoce komprimovaných, hardwarově akcelerovaných formátů textur, které rozhraní DirectX podporuje.

## <a name="supported-formats"></a>Podporované formáty

**Editor obrázků** podporuje následující formáty obrázků:

|Název formátu|Přípona názvu souboru|
|-----------------| - |
|Formát PNG|*Png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Přímý nakreslování povrchu|*.dds*|
|Formát GIF|*Gif*|
|Bitmapové|*.bmp*, *.dib*|
|Formát souboru označeného obrázku|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat bitovou kopii do projektu sady Visual Studio a nakonfigurovat ji pro vaše požadavky.

### <a name="add-an-image-to-your-project"></a>Přidání obrázku do projektu

1. V **Průzkumníku řešení**otevřete místní nabídku projektu, do kterého chcete obrázek přidat, a pak zvolte **Přidat** > **novou položku**.

2. V dialogovém okně **Přidat novou položku** v části **Nainstalováno**vyberte **Grafika**a pak vyberte vhodný formát souboru pro obraz.

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **Grafika,** bude možná nutné nainstalovat komponentu **Image a editory 3D modelů.** Zavřete dialogové okno a potom na řádku nabídek vyberte **Nástroje** > **získat nástroje a funkce,** chcete-li otevřít Instalační **službu sady Visual Studio**. Vyberte kartu **Jednotlivé komponenty** a pak vyberte komponentu **Image a editory 3D modelů** v kategorii Hry a **Grafika.** Vyberte **Změnit**.
   >
   > ![Komponenta editorů obrazových a 3D modelů](media/image-3d-model-editors-component.png)

   Informace o tom, jak zvolit formát souboru na základě vašich požadavků, [najdete v tématu Volba formátu obrázku](#choose-the-image-format).

3. Zadejte **název** obrazového souboru a **umístění,** kde má být vytvořen.

4. Vyberte tlačítko **Přidat**.

### <a name="choose-the-image-format"></a>Volba formátu obrázku

V závislosti na tom, jak chcete obrázek používat, mohou být některé formáty souborů vhodnější než jiné. Některé formáty například nemusí podporovat funkci, kterou potřebujete, například průhlednost nebo určitý barevný formát. Některé formáty nemusí poskytovat vhodnou kompresi pro typ naplánovaného obsahu obrázku.

Následující informace vám mohou pomoci vybrat formát obrázku, který vyhovuje vašim potřebám:

**Bitmapový obraz (.bmp)**

Formát bitmapového obrazu. Nekomprimovaný formát obrazu, který podporuje 24bitové barvy. Formát bitmapy nepodporuje průhlednost.

**Obrázek GIF (.gif)**

Formát obrázku Formát formátu GIF (Graphics Interchange Format). LZW komprimovaný bezeztrátový obrazový formát, který podporuje až 256 barev. Nevhodné pro fotografie a obrazy, které mají značné množství barevných detailů, ale poskytují dobré kompresní poměry pro obrazy s nízkými barvami, které mají vysoký stupeň soudržnosti barev.

**JPG Obrázek (.jpg)**

Formát obrazu Společné fotografické expertní skupiny (JPEG). Vysoce komprimovaný, ztrátový formát obrazu, který podporuje 24bitové barvy a je vhodný pro univerzální kompresi obrazů, které mají vysoký stupeň soudržnosti barev.

**Obrázek PNG (.png)**

Formát obrazu PNG (Portable Network Graphics). Mírně komprimovaný bezeztrátový formát obrazu, který podporuje 24bitovou barevnou a alfa průhlednost. Je vhodný pro přírodní i umělé obrazy, ale neposkytuje kompresní poměry tak dobré jako ztrátové formáty, jako je JPG nebo GIF.

**Obrázek TIFF (.tif)**

Formát obrázku Tagged Image File Format (TIFF nebo TIF). Flexibilní formát obrazu, který podporuje několik kompresních schémat.

**Textura DDS (.dds)**

Formát textury DirectDraw Surface (DDS). Vysoce komprimovaný, ztrátový formát textury, který podporuje 24bitovou barvu a průhlednost alfa. Jeho kompresní poměry mohou být až 8:1. Je založen na kompresi Textury S3, která může být dekomprimována na grafickém hardwaru.

**Obrázek TGA (.tga)**

Formát obrázku Truevision Graphics Adapter (TGA) (také známý jako Targa). Formát obrazu komprimovaný protokolem RLE, který podporuje barevně mapované (barevnou paletu) i obrazy s přímými barvami až 24bitové barvy a alfa průhlednost. Nevhodné pro fotografie a obrazy, které mají značné množství barevných detailů, ale poskytuje dobré kompresní poměry pro obrazy, které mají dlouhé rozsahy identických barev.

### <a name="configure-the-image"></a>Konfigurace bitové kopie

Než začnete pracovat s obrazem, který jste vytvořili, můžete změnit jeho výchozí konfiguraci. Můžete například změnit jeho rozměry nebo formát barvy, který používá. Informace o konfiguraci těchto a dalších vlastností bitové kopie naleznete v tématu [Vlastnosti obrazu](#image-properties).

> [!NOTE]
> Před uložením práce nezapomeňte nastavit vlastnost **Formát barvy,** pokud chcete použít určitý barevný formát. Pokud formát souboru podporuje kompresi, můžete upravit nastavení komprese při prvním uložení souboru nebo při **volbě Uložit jako**.

## <a name="work-with-the-image-editor"></a>Práce s Editorem obrázků

Tato část popisuje, jak pomocí **Editoru obrázků** upravit textury a obrazy.

Příkazy, které ovlivňují stav **Editoru obrázků,** jsou umístěny na panelu nástrojů **Režim editoru obrázků** spolu s rozšířenými příkazy. Panel nástrojů se nachází podél horního okraje návrhové plochy **Editoru obrázků.** Kreslicí nástroje jsou umístěny na panelu nástrojů **Editor obrázků** podél levého okraje návrhové plochy **Editoru obrázků.**

### <a name="image-editor-mode-toolbar"></a>Panel nástrojů Režim editoru obrázků

![Panel nástrojů Editor obrázků v sadě Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

Následující tabulka popisuje položky na panelu nástrojů **Režim editoru obrázků,** které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Vybrat**|Umožňuje výběr obdélníkové oblasti obrazu. Po výběru oblasti ji můžete vyjmout, kopírovat, přesouvat, měnit velikost, otáčet, překlápět nebo odstraňovat. Pokud je aktivní výběr, kreslicí nástroje ovlivní pouze vybranou oblast.|
|**Nepravidelný výběr**|Umožňuje výběr nepravidelné oblasti obrazu. Po výběru oblasti ji můžete vyjmout, kopírovat, přesouvat, měnit velikost, otáčet, překlápět nebo odstraňovat. Pokud je aktivní výběr, kreslicí nástroje ovlivní pouze vybranou oblast.|
|**Výběr hůlky**|Umožňuje výběr podobně barevné oblasti obrazu. *Tolerance*– to znamená maximální rozdíl mezi sousedními barvami, ve kterých jsou považovány za podobné – lze nakonfigurovat tak, aby zahrnovala menší nebo širší rozsah podobných barev. Po výběru oblasti ji můžete vyjmout, kopírovat, přesouvat, měnit velikost, otáčet, překlápět nebo odstraňovat. Pokud je aktivní výběr, kreslicí nástroje ovlivní pouze vybranou oblast.|
|**Posouvání**|Umožňuje pohyb obrazu vzhledem k rámečku okna. V režimu **Posouvání** vyberte bod v obraze a pak ho přesuňte.<br /><br /> Režim **Posouvání** můžete dočasně aktivovat stisknutím a podržením klávesy **Ctrl.**|
|**Zoom**|Umožňuje zobrazení více či méně detailů obrazu vzhledem k rámečku okna. V režimu **Lupa** vyberte bod na obrázku a pak ho přesuňte doprava nebo dolů, abyste zobrazení přiblížili, nebo doleva nebo nahoru pro oddálení.<br /><br /> Přiblížení nebo oddálení můžete přiblížit stisknutím a podržením **klávesy Ctrl,** zatímco používáte kolečko myši nebo stiskněte znaménko plus (**+**) nebo znaménko mínus (**-**).|
|**Zvětšení na skutečnou velikost**|Zobrazí obraz pomocí vztahu 1:1 mezi obrazovými body obrazu a obrazovými body obrazovky.|
|**Přiblížení podle**|Zobrazí celý obraz v rámečku okna.|
|**Zvětšení na šířku**|Zobrazí celou šířku obrazu v rámečku okna.|
|**Mřížka**|Povolí nebo zakáže mřížku, která zobrazuje hranice obrazových bodů. Mřížka se nemusí zobrazit, dokud obraz nepřiblížíte.|
|**Zobrazit další úroveň MIP**|Aktivuje další větší úroveň MIP v řetězci map MIP. Aktivní úroveň MIP se zobrazí na návrhové ploše. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|**Zobrazit předchozí úroveň MIP**|Aktivuje další menší úroveň MIP v řetězci map MIP. Aktivní úroveň MIP se zobrazí na návrhové ploše. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|**Červený kanál**<br /><br /> **Zelený kanál**<br /><br /> **Modrý kanál**<br /><br /> **Alfa kanál**|Povolí nebo zakáže konkrétní barevný kanál. **Poznámka:**  Systematickým povolením nebo zakázáním barevných kanálů můžete izolovat problémy, které souvisejí s jedním nebo více z nich. Můžete například identifikovat nesprávnou průhlednost alfa.|
|**Pozadí**|Povolí nebo zakáže zobrazení pozadí prostřednictvím průhledných částí obrazu. Způsob zobrazení pozadí můžete nakonfigurovat výběrem z těchto možností:<br /><br /> **Šachovnice**<br /> Použije zelenou barvu spolu se zadanou barvou pozadí k zobrazení pozadí jako šachovního vzoru. Pomocí této možnosti můžete přispět k tomu, aby byly průhledné části obrazu viditelnější.<br /><br /> Bílé pozadí<br /> Používá bílou barvu k zobrazení pozadí.<br /><br /> Černé pozadí<br /> Používá černou barvu k zobrazení pozadí.<br /><br /> Animace pozadí<br /> Posouvá šachovní vzor pomalu. Pomocí této možnosti můžete přispět k tomu, aby byly průhledné části obrazu viditelnější.|
|**Vlastnosti**|Střídavě otevře nebo zavře okno **Vlastnosti.**|
|**Pokročilé**|Obsahuje další příkazy a možnosti.<br /><br /> **Filtry**<br /><br /> Poskytuje několik běžných obrazových filtrů: **černá a bílá**, **rozostření**, **zesvětlení**, **detekce** **okrajů**, **reliéf**, **invertní barvy**, **zvlnění**, **sépiový tón**a **zostření**.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení pomocí D3D11**<br /> Používá Direct3D 11 k vykreslení návrhového povrchu **Editoru obrázků.**<br /><br /> **Vykreslení pomocí d3D11WARP**<br /> Používá direct3d 11 Windows Advanced rastrovací platforma (WARP) k vykreslení návrhové plochy **Editoru obrázků.**<br /><br /> **Nástroje**<br /><br /> **Překlopit vodorovně**<br /> Transposes obraz kolem jeho vodorovné nebo x, osy.<br /><br /> **Překlopit svisle**<br /> Transposes obraz kolem jeho svislé nebo y, osy.<br /><br /> **Generovat Mips**<br /> Generuje úrovně MIP pro obraz. Pokud úrovně MIP již existují, jsou znovu vytvořeny z největší úrovně MIP. Všechny změny, které byly provedeny na menší úrovně MIP budou ztraceny. Chcete-li uložit úrovně MIP, které jste vygenerovali, musíte k uložení obrázku použít formát *DDs.*<br /><br /> **Zobrazit**<br /><br /> **Kmitočet**<br /> Pokud je tato možnost povolena, zobrazí kmitočet snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. **Tip:** Chcete-li znovu spustit poslední příkaz, můžete zvolit tlačítko **Upřesnit.**|

### <a name="image-editor-toolbar"></a>Panel nástrojů Editor obrázků

![Panel nástrojů Editor obrázků](../designers/media/digit-tre-toolbar.png)

Následující tabulka popisuje položky na panelu nástrojů **Editor obrázků,** které jsou uvedeny v pořadí, ve kterém se zobrazují shora dolů:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Tužka**|Použije aktivní výběr barev k nakreslení vytaženého vytažení vyhlazení. Barvu a tloušťku tahu můžete nastavit v okně **Vlastnosti.**|
|**Kartáč**|Použije aktivní výběr barev k nakreslení vyhlazeného tahu. Barvu a tloušťku tahu můžete nastavit v okně **Vlastnosti.**|
|**Airbrush**|Použije aktivní výběr barev k nakreslení vyhlazeného tahu, který se prolne s obrazem a stane se sytější jako funkce času. Barvu a tloušťku tahu můžete nastavit v okně **Vlastnosti.**|
|**Kapátko**|Nastaví aktivní výběr barev na barvu vybraného obrazového bodu.|
|**Výplně**|Použije aktivní výběr barev k vyplnění oblasti obrazu. Ovlivněná oblast je definována jako obrazový bod, ve kterém je výplň použita, spolu s každým obrazovým bodem, který je k ní připojen obrazovými body stejné barvy a který má stejnou barvu. Pokud je výplň použita v rámci aktivního výběru, je ovlivněná oblast výběrem omezena.<br /><br /> Ve výchozím nastavení je aktivní výběr barev prolnut společně s postiženou oblastí obrazu podle jeho alfa složky. Chcete-li použít aktivní výběr barev k přepsání postižené oblasti, stiskněte a podržte při použití nástroje výplň klávesu **Shift.**|
|**Guma**|Nastaví obrazové body na plně průhlednou barvu, pokud obraz podporuje alfa kanál. V opačném případě nastaví obrazové body na aktivní barvu pozadí.|
|**Čára**, **obdélník,** **zaoblený obdélník**, **elipsa**|Nakreslí obrazec na obrázek. Barvu a tloušťku obrysu můžete nastavit v okně **Vlastnosti.**<br /><br /> Chcete-li nakreslit primitivu, která má stejnou šířku a výšku, stiskněte a podržte **shift** při kreslení.|
|**Text**|Používá výběr barev popředí k kreslení textu. Barva pozadí je určena výběrem barvy pozadí. U průhledného pozadí musí být hodnota alfa výběru barvy pozadí 0. Když je oblast textu aktivní, můžete nastavit, zda je text nakreslený vyhlazeným tahem, a můžete nastavit text **Hodnota**, **Písmo**, **Velikost**a styl –**Tučné**, **Kurzíva**nebo **Podtrženo**– v okně **Vlastnosti.** Obsah a vzhled textu je dokončen, když oblast textu již není aktivní.|
|**Otočit**|Otočí obraz o 90 stupňů ve směru hodinových ručiček.|
|**Trim**|Ořízne obraz na aktivní výběr.|

### <a name="work-with-mip-levels"></a>Práce s úrovněmi MIP

Některé formáty obrázků, například DirectDraw Surface (*.dds*), podporují úrovně MIP pro úroveň detailu (LOD) textury. Informace o tom, jak generovat a pracovat s úrovněmi MIP, naleznete v [tématu How to: Create and modify MIP levels](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Práce s průhledností

Některé formáty obrázků, například DirectDraw Surface (*.dds*), podporují průhlednost. Průhlednost můžete použít několika způsoby v závislosti na nástroji, který používáte. Chcete-li určit úroveň průhlednosti pro výběr barvy, nastavte v okně **Vlastnosti** komponentu **A** (alfa) výběru barev.

Následující tabulka popisuje, jak různé druhy nástrojů řídí způsob použití průhlednosti:

|Nástroj|Popis|
|----------|-----------------|
|**Tužka,** **štětec,** **rozprašovač,** **čára, obdélník,** **zaoblený obdélník,** **elipsa,** **text** **Line**|Chcete-li prolnout aktivní výběr barev společně s obrazem, rozbalte **Draw** v okně **Vlastnosti** **skupinu vlastností Kanály** a nastavte políčko Kreslit na kanálu **Alfa** a pak nakreslete normálně.<br /><br /> Chcete-li kreslit pomocí aktivního výběru barev a ponechat hodnotu alfa obrazu na místě, **zrušte** zaškrtnutí políčka Kreslit **alfa** kanálu a pak nakreslete normálně.|
|**Výplně**|Chcete-li prolnout aktivní výběr barev společně s obrazem, stačí vybrat oblast, kterou chcete vyplnit.<br /><br /> Chcete-li použít aktivní výběr barev – včetně hodnoty alfa kanálu – k přepsání obrazu, stiskněte a podržte **klávesu Shift** a pak zvolte oblast, kterou chcete vyplnit.|

### <a name="image-properties"></a>Vlastnosti obrazu

Okno **Vlastnosti** můžete použít k určení různých vlastností obrazu. Můžete například nastavit, aby se velikost obrazu měřila, aby se velikost obrazu měřila.

Následující tabulka popisuje vlastnosti obrazu:

|Vlastnost|Popis|
|--------------|-----------------|
|impulzu|Šířka obrázku.|
|Vlastnost Height|Výška obrázku.|
|Bity na pixel|Počet bitů, které představují každý pixel. Hodnota této vlastnosti závisí na **barevném formátu** obrazu.|
|Průhledný výběr|**True** prolnutí vrstvy výběru s hlavním obrazem na základě alfa hodnoty vrstvy výběru; jinak **False**. Tato položka je k dispozici pouze pro obrázky, které podporují alfa.|
|Formát|Barevný formát obrazu. V závislosti na formátu obrazu můžete určit různé barevné formáty. Barevný formát definuje počet a druh barevných kanálů, které jsou zahrnuty v obraze, a také velikost a kódování různých kanálů.|
|Úroveň Mip|Aktivní úroveň MIP. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|Počet úrovní Mip|Celkový počet úrovní MIP v obraze. Tato položka je k dispozici pouze pro textury, které mají úrovně MIP.|
|Počet rámců|Celkový počet snímků v obraze. Tato položka je k dispozici pouze pro obrazy, které podporují pole textury.|
|Rámec|Aktuální snímek. Lze zobrazit pouze první snímek; všechny ostatní snímky budou ztraceny při uložení obrazu.|
|Počet hloubkových řezů|Celkový počet řezů hloubky v obraze. Tato položka je k dispozici pouze pro obrazy, které podporují textury objemu.|
|Hloubkový řez|Aktuální řez hloubky. Lze zobrazit pouze první řez; všechny ostatní řezy se při uložení obrazu ztratí.|

> [!NOTE]
> Protože vlastnost **Otočit podle** se vztahuje na všechny nástroje a vybrané oblasti, vždy se zobrazí v dolní části okna **Vlastnosti** spolu s dalšími vlastnostmi nástroje. **Otočit podle** se vždy zobrazí, protože celý obraz je implicitně vybrán, když není k dispozici žádný jiný výběr nebo aktivní nástroj. Další informace o vlastnosti **Otočit podle** naleznete v tématu [Vlastnosti nástroje](#tool -properties).

### <a name="resize-images"></a>Změna velikosti obrazů

Existují dva způsoby, jak změnit velikost obrázku. V obou případech **editor obrázků** používá k převzorkování obrazu bilineární interpolaci.

- V okně **Vlastnosti** zadejte nové hodnoty pro vlastnosti **Šířka** a **Výška.**

- Vyberte celý obraz a pomocí značek ohraničení změňte velikost obrazu.

### <a name="selected-regions"></a>Vybrané oblasti

Výběry v **Editoru obrázků** definují oblasti obrazu, které jsou aktivní. Aktivní oblasti jsou ovlivněny nástroji a transformacemi. Pokud je aktivní výběr, oblasti mimo vybranou oblast nejsou ovlivněny většinou nástrojů a transformací. Pokud není aktivní výběr, je aktivní celý obraz.

Většina nástrojů (**tužka**, **štětec**, **rozprašovač**, **výplň**, **guma**a 2D primitiva) a transformace **(Otočení**, **Oříznutí**, **Invertní barvy**, **Překlopit vodorovně**a **Překlopit svisle)** jsou omezeny nebo definovány aktivním výběrem. Některé nástroje **(kapátko** a **text)** a transformace **(Generovat mips)** však nejsou ovlivněny žádným aktivním výběrem. Tyto nástroje se vždy chovají, jako by aktivním výběrem byl celý obraz.

Při výběru oblasti můžete stisknutím a podržením **klávesy Shift** provést proporcionální (čtvercový) výběr. V opačném případě není výběr omezen.

#### <a name="resize-selections"></a>Změna velikosti výběrů

Po výběru oblasti můžete změnit její velikost nebo její obsah obrazu změnou velikosti značky výběru. Při změně velikosti vybrané oblasti můžete pomocí následujících modifikačních kláves změnit chování vybrané oblasti při změně její velikosti:

**Ctrl** - Zkopíruje obsah vybrané oblasti před její velikostí. Původní obraz zůstane při velikosti kopie beze změny.

**Shift** - Změní velikost vybrané oblasti v poměru k její původní velikosti.

**Alt** - Změní velikost oblasti výběru. Tím zůstane obraz nezměněn.

Následující tabulka popisuje platné kombinace kláves modifikátoru:

|Ctrl|Shift|Alt|Popis|
|----------|-----------|---------|-----------------|
||||Změní velikost obsahu vybrané oblasti.|
||**Shift**||Proporcionálně změní velikost obsahu vybrané oblasti.|
|||**Alt**|Změní velikost vybrané oblasti. Definuje novou oblast výběru.|
||**Shift**|**Alt**|Proporcionálně změní velikost vybrané oblasti. Definuje novou oblast výběru.|
|**Ctrl**|||Zkopíruje a pak změní velikost obsahu vybrané oblasti.|
|**Ctrl**|**Shift**||Zkopíruje a pak proporcionálně změní velikost obsahu vybrané oblasti.|

### <a name="tool-properties"></a>Vlastnosti nástroje

Když je nástroj vybraný, můžete použít okno **Vlastnosti** k určení podrobností o tom, jak ovlivňuje obraz. Můžete například nastavit tloušťku nástroje **tužka** nebo barvu nástroje **štětec.**

Můžete nastavit barvu popředí i barvu pozadí. Obě podporují alfa kanál k zajištění krytí definovaného uživatelem. Nastavení platí pro všechny nástroje. Pokud používáte myš, levé tlačítko myši odpovídá barvě popředí a pravé tlačítko myši odpovídá barvě pozadí.

Následující tabulka popisuje vlastnosti nástroje:

|Nástroj|Vlastnosti|
|----------|----------------|
|Všechny nástroje a výběry|**Otočit podle**<br /> Definuje velikost ve stupních, ve které se efekt výběru nebo nástroje otáčí ve směru hodinových ručiček.|
|**Tužka,** **štětec,** **rozprašovač,** **guma**|**Tloušťka**<br /> Definuje velikost oblasti, která je nástrojem ovlivněna.|
|**Text**|**Vyhlazení**<br /> Nakreslí text, který má vyhlazené okraje. To dává textu hladší vzhled.<br /><br /> **Hodnotu**<br /> Text, který má být vykreslen.<br /><br /> **Písmo**<br /> Písmo použité k nakreslení textu.<br /><br /> **Velikost**<br /> Velikost textu.<br /><br /> **Tučný**<br /> Vytvoří písmo tučným písmem.<br /><br /> **Kurzíva**<br /> Vytvoří písmo kurzívou.<br /><br /> **Podtržené**<br /> Podpne písmo.|
|**2D primitivní**|**Vyhlazení**<br /> Nakreslí primitiva, které mají vyhlazené hrany. To jim dává hladší vzhled.<br /><br /> **Tloušťka**<br /> Definuje tloušťku čáry, která tvoří hranici primitiva.<br /><br /> **Poloměr X**<br /> (Pouze zaoblený obdélník) Definuje poloměr zaokrouhlení pro horní a dolní okraj primitiva.<br /><br /> **Poloměr Y**<br /> (Pouze zaoblený obdélník) Definuje poloměr zaokrouhlení pro levý a pravý okraj primitiva.|
|**Tužka,** **štětec,** **rozprašovač,** **2D primitiv**|**Kanály**<br /> Povolí nebo zakáže určité barevné kanály pro zobrazení a kreslení. Pokud je **zobrazení** nastaveno pro určitý barevný kanál, je tento kanál viditelný v obraze; v opačném případě není viditelná. Pokud je **draw** nastaven pro určitý barevný kanál, je tento kanál ovlivněn operacemi kreslení; v opačném případě tomu tak není.|
|**Výběr hůlky**, **výplň**|**Tolerance**<br /> Definuje maximální rozdíl mezi sousedními barvami, ve kterých jsou považovány za podobné, takže méně nebo více podobných barev je součástí ovlivněné nebo vybrané oblasti. Ve výchozím nastavení je hodnota 32, což znamená, že sousední obrazové body v rámci 32 odstínů (světlejší nebo tmavší) původní barvy jsou považovány za součást oblasti.|

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnutí do **režimu výběru**|**S**|
|Přepnutí do režimu **lupy**|**Z**|
|Přepnutí do režimu **Pan**|**K**|
|Vybrat vše|**Ctrl**+**A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**Esc** (uniknout)|
|Přiblížit|**Ctrl**+**kolečko myši vpřed**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Znaménko plus (**+**)|
|Oddálit|**Ctrl**-**kolečko myši dozadu**<br /><br /> **Ctrl**-**PageDown**<br /><br /> Znaménko mínus (**-**)|
|Posunení obrázku nahoru|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posunu obrazu dolů|**Kolečko myši dopředu**<br /><br /> **PageUp**|
|Posuzuji obrázek doleva|**Shift**+**kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **Shift**+**PageDown**|
|Posuzuji obrázek doprava|**Shift**+**kolečko myši vpřed**<br /><br /> **Kolečko myši doprava**<br /><br /> **Posunout**+**stránku nahoru**|
|Zvětšení na skutečnou velikost|**Ctrl**+**0** (nula)|
|Přizpůsobit obraz oknu|**Ctrl**+**G**, **Ctrl**+**F**|
|Přizpůsobit obrázek šířce okna|**Ctrl**+**G**, **Ctrl**+**I**|
|Přepnout mřížku|**Ctrl**+**G**, **Ctrl**+**G**|
|Oříznutí obrazu na aktuální výběr|**Ctrl**+**G**, **Ctrl**+**C**|
|Zobrazit další úroveň MIP (vyšší detail)|**Ctrl**+**G**, **Ctrl**+**6**|
|Zobrazit předchozí úroveň MIP (nižší detail)|**Ctrl**+**G**, **Ctrl**+**7**|
|Přepnout červený barevný kanál|**Ctrl**+**G**, **Ctrl**+**1**|
|Přepnout kanál zelené barvy|**Ctrl**+**G**, **Ctrl**+**2**|
|Přepnout kanál modré barvy|**Ctrl**+**G**, **Ctrl**+**3**|
|Přepnout alfa (průhledný) kanál|**Ctrl**+**G**, **Ctrl**+**4**|
|Přepnout vzor šachovní desky alfa|**Ctrl**+**G**, **Ctrl**+**B**|
|Přepnutí na nástroj pro nepravidelný výběr|**L**|
|Přepnout na nástroj pro výběr hůlky|**M**|
|Přepnout na nástroj tužka|**P**|
|Přepnout na nástroj štětec|**B**|
|Přepnout na výplň|**F**|
|Přepnout na nástroj pro vymazání|**E**|
|Přepnout na textový nástroj|**T**|
|Přepnout na nástroj pro výběr barev (kapátko)|**I**|
|Přesuňte aktivní výběr a jeho obsah.|**Klávesy se šipkami.**|
|Změňte velikost aktivního výběru a jeho obsahu.|**Ctrl**+**Klávesy Ctrl**|
|Přesunutí aktivního výběru, nikoli však jeho obsahu.|**Klávesy**+**se šipkami**|
|Změňte velikost aktivního výběru, ale ne jeho obsahu.|**Klávesy**+**Ctrl**+**Se šipkami**|
|Potvrzení aktuální vrstvy|**Vrátit**|
|Zmenšit tloušťku nástroje|**[**|
|Zvětšit tloušťku nástroje|**]**|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D datovými zdroji pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Obsahuje přehled nástrojů, které můžete použít v sadě Visual Studio pro práci s grafickými prostředky, jako jsou textury a obrazy, 3D modely a efekty shaderu.|
|[Editor modelů](../designers/model-editor.md)|Popisuje, jak používat Visual Studio Editor modelů pro práci s 3D modely.|
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje, jak používat Návrhář shaderu sady Visual Studio pro práci se stínidly.|
