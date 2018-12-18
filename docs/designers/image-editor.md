---
title: Editor obrázků
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2149410782587d8472faff678cbc20bf1ea577c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878372"
---
# <a name="image-editor"></a>editor obrázků

Tento článek popisuje, jak pracovat se sadou Visual Studio **Editor obrázků** můžete zobrazit a upravit prostředky textury a obrazu.

Můžete použít **Editor obrázků** pro práci s typy bohaté textury a obrázkových formátů, které se používají při vývoji aplikace rozhraní DirectX. To zahrnuje podporu pro image oblíbené formáty souborů a barevné kódování, funkce, jako je alfa kanály a mapování MIP a řadu textury silně komprimovaném, hardwarově urychlené formáty podporujících rozhraní DirectX.

## <a name="supported-formats"></a>Podporované formáty

**Editor obrázků** podporuje následující formáty bitové kopie:

|Název formátu|Přípona názvu souboru|
|-----------------| - |
|Formát PNG|*ve formátu PNG*|
|JPEG|*jpg*, *.jpeg*, *JPE*, *JFIF*|
|Povrch Direct Draw|*.DDS*|
|Formát GIF|*GIF*|
|Rastrový obrázek|*BMP*, *DIB*|
|Tagged Image File Format|*.tif*, *.tiff*|
|TGA (Targa)|*TGA*|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat bitovou kopii do projektu sady Visual Studio a nakonfigurujte ho pro vaše požadavky.

### <a name="add-an-image-to-your-project"></a>Přidat bitovou kopii do svého projektu

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete přidat obrázek a klikněte na tlačítko **přidat** > **nová položka**.

2. V **přidat novou položku** dialogovém okně **nainstalováno**vyberte **grafiky**a pak vyberte příslušný formát pro bitovou kopii.

   > [!NOTE]
   > Pokud se nezobrazí **grafiky** kategorii **přidat novou položku** dialogového okna, je nutné nainstalovat **obrázků a 3D modelů editory** komponenty. Zavřete dialogové okno a potom vyberte **nástroje** > **stažení nástrojů a funkcí** z řádku nabídek otevřete **instalační program sady Visual Studio**. Vyberte **jednotlivé komponenty** kartu a potom vyberte **obrázků a 3D modelů editory** komponentu pod **hry a grafika** kategorie. Vyberte **upravit**.
   >
   > ![Obrázků a 3D modelů editory komponenty](media/image-3d-model-editors-component.png)

   Informace o tom, jak vybrat formát souboru na základě vašich požadavků najdete v tématu [vyberte formát obrázku](#choose-the-image-format).

3. Zadejte **název** souboru bitové kopie a **umístění** místo se má vytvořit.

4. Zvolte **přidat** tlačítko.

### <a name="choose-the-image-format"></a>Zvolte formát obrázku

V závislosti na tom, jak budete chtít použít bitovou kopii může být vhodnější než jiné určité formáty souborů. Například některé formáty nemusí podporovat formátu určitá barva, průhlednost nebo funkce, které potřebujete, třeba. Některé formáty nemusí poskytnout vhodný komprese pro typ obsahu bitové kopie, které jste naplánovali.

Následující informace můžou pomoct vybrat formátu obrázku, který bude vyhovovat vašim potřebám:

**Rastrový obrázek (BMP)**

Formát obrázku rastrového obrázku. Nekomprimovaný bitové kopie formátu, který podporuje 24 bitů barev. Průhlednost nepodporují formát rastrového obrázku.

**Obrázek GIF (*.gif)**

Formát obrázku formátu GIF (Graphics Interchange). Komprimované LZW, beze ztrát bitové kopie formátu, který podporuje až 256 barev. Nevhodné pro Image, které mají významné množství podrobností, barvy, ale poskytuje dobré Kompresní poměry pro bitové kopie nízká color, které mají vysoký stupeň barva koherence a fotografie.

**Obrázek JPG (JPG)**

Formát obrázku odborníků skupiny JPEG (Joint Photographic). Silně komprimovaném, míru ztrát bitové kopie formátu, který podporuje 24 bitů barev a je vhodný pro obecné účely komprese imagí, které mají vysoký stupeň koherence barvu.

**Obrázek PNG (.png)**

Formát obrázku Portable Network Graphics (PNG). Středně komprimovaný, beze ztrát bitové kopie formátu, který podporuje 24 bitů barev a alfa transparentnost. Je vhodný pro fyzické i umělé bitové kopie, ale neposkytuje Kompresní poměry tak dobré, jako míru ztrát formáty, jako je například JPG či GIF.

**Obrázek TIFF (.tif)**

Formát obrázku Tagged Image File Format (ve formátu TIFF nebo TIF). Flexibilní bitové kopie formátu, který podporuje několik komprese schémat.

**Textura DDS (.dds)**

Formát textury DirectDraw Surface (DDS). Silně komprimovaném, míru ztrát texturu formátu, který podporuje 24 bitů barev a alfa transparentnost. Jeho Kompresní poměry může být až 8:1. Je založen na komprese textur S3, která mohou na hardwarovou akceleraci dekomprimovat.

**Obrázek TGA (TGA)**

Formát obrázku Truevision grafický adaptér (TGA) (označované také jako Targa). Obrázek komprimované RLE, beze ztrát formátu, který podporuje obě mapované na barvy (barevná paleta) nebo obrázky až 24 bitů barev a alfa transparentnosti přímo color. Nevhodné pro fotografie a bitové kopie, které mají významné množství podrobností, barvy, ale poskytuje dobré Kompresní poměry pro bitové kopie, které mají dlouhé rozsahy stejné barvy.

### <a name="configure-the-image"></a>Obrázek konfigurace

Než začnete pracovat s bitovou kopii, kterou jste vytvořili, můžete změnit její výchozí konfiguraci. Například můžete změnit jeho rozměry nebo formát barev, které používá. Informace o konfiguraci těchto a dalších vlastností bitové kopie, naleznete v tématu [obrázku vlastnosti](#image-properties).

> [!NOTE]
> Před uložením svou práci, nezapomeňte nastavit **formát barev** vlastnosti, pokud chcete použít formát konkrétní barev. Pokud formát souboru podporuje kompresi, můžete upravit nastavení komprese při ukládání souboru poprvé nebo když zvolíte **uložit jako**.

## <a name="work-with-the-image-editor"></a>Práce pomocí editoru obrázků

Tato část popisuje způsob použití **Editor obrázků** upravit texturami a obrázky.

Příkazy, které mají vliv na stav **Editor obrázků** jsou umístěny na **režim editoru obrázků** nástrojů spolu s pokročilé příkazy. Panel nástrojů se nachází na okraji nejvyššího **Editor obrázků** návrhovou plochu. Kreslení nástrojů jsou umístěny na **Editor obrázků** nástrojů sledovat levému okraji **Editor obrázků** návrhovou plochu.

### <a name="image-editor-mode-toolbar"></a>Režim editoru obrázků panelu nástrojů

![Panel nástrojů režim editoru obrázků v sadě Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

Následující tabulka popisuje položky panelu **režim editoru obrázků** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Vyberte**|Umožňuje výběr obdélníkové bitovou kopii. Po výběru oblasti můžete vyjmout, kopírovat, přesunout, škálování, otočení, překlopit nebo ho odstranit. Když je aktivní výběr, nástrojů pro kreslení ovlivní pouze vybrané oblasti.|
|**Volný výběr**|Umožňuje výběr nestandardní oblasti obrázku. Po výběru oblasti můžete vyjmout, kopírovat, přesunout, škálování, otočení, překlopit nebo ho odstranit. Když je aktivní výběr, nástrojů pro kreslení ovlivní pouze vybrané oblasti.|
|**Výběr hůlka**|Umožňuje výběr podobně barevný oblasti obrázku. *Tolerance*– to znamená maximální rozdíl mezi sousedící barvy, ve kterém jsou považovány za podobné – dá použít menší nebo větší řadu podobné barvy. Po výběru oblasti můžete vyjmout, kopírovat, přesunout, škálování, otočení, překlopit nebo ho odstranit. Když je aktivní výběr, nástrojů pro kreslení ovlivní pouze vybrané oblasti.|
|**Posouvání**|Umožňuje pohyb image relativně k rámu okna. V **Pan** režimu, vyberte bod na obrázku a potom pohybovat.<br /><br /> Můžete dočasně aktivovat **Pan** režimu stisknutím a podržením **Ctrl** klíč.|
|**Přiblížení**|Umožňuje zobrazení více či méně detailů image relativně k rámu okna. V **přiblížení** režimu, vyberte bod na obrázku a poté jej přesunutím vpravo dolů zvětšete nebo přesunutím vlevo či nahoru out.<br /><br /> Provést přiblížení nebo oddálení podle stisknutím a podržením **Ctrl** použít kolečko myši nebo klepněte na znaménko plus (**+**) nebo minus (**-**) .|
|**Na skutečnou velikost**|Pomocí vztahu 1:1 mezi pixely obrázku a pixelů na obrazovce zobrazí obrázek.|
|**Přizpůsobit zobrazení**|Zobrazí úplnou bitovou kopii v rámci okna.|
|**Přiblížit na šířku**|Zobrazí celou šířku obrázku v rámci okna.|
|**Mřížka**|Povolí nebo zakáže mřížky, která zobrazuje hranice pixelů. Mřížka neobjeví, dokud zvětšení obrázku.|
|**Zobrazit další úroveň MIP**|Aktivuje další vyšší úroveň MIP v řetěz MIP map. Aktivní úroveň MIP je zobrazena na návrhové ploše. Tato položka je dostupná pouze pro textury, které mají úrovní MIP.|
|**Zobrazit předchozí úroveň MIP**|Aktivuje další menší úroveň MIP v řetěz MIP map. Aktivní úroveň MIP je zobrazena na návrhové ploše. Tato položka je dostupná pouze pro textury, které mají úrovní MIP.|
|**Červený kanál**<br /><br /> **Zelený kanál**<br /><br /> **Modrý kanál**<br /><br /> **Alfa kanál**|Povolí nebo zakáže určité barevného kanálu. **Poznámka:** systematicky povolením nebo zakázáním barevného kanálu, můžete izolovat problémy, které se vztahují na jeden nebo více z nich. Můžete například zjistit, průhlednost nesprávné alfa.|
|**Na pozadí**|Povolí nebo zakáže zobrazení prostřednictvím transparentní části obrázku na pozadí. Můžete nakonfigurovat, jak se zobrazí na pozadí volbou z následujících možností:<br /><br /> **Šachovnice**<br /> Používá k zobrazení na pozadí jako vzor šachovnice zelenou barvu, která spolu s barvu pozadí zadané. Abyste se mohli lépe poznat transparentní části obrázku můžete použít tuto možnost.<br /><br /> Bílé pozadí<br /> Používá k zobrazení na pozadí bílou barvu.<br /><br /> Černé pozadí<br /> Černá barva se používá k zobrazení na pozadí.<br /><br /> Animovat pozadí<br /> Vzor šachovnice posouvá pomalu. Abyste se mohli lépe poznat transparentní části obrázku můžete použít tuto možnost.|
|**Vlastnosti**|Střídavě otevře a ukončí **vlastnosti** okna.|
|**Pokročilé**|Obsahuje další příkazy a možnosti.<br /><br /> **Filtry**<br /><br /> Poskytuje několik běžné filtry image: **černá a bílá**, **rozostření**, **Brighten**, **ztmavit**, **detekce hran**, **Stínovaný**, **Invertovat barvy**, **Ripple**, **sépiový tón**, a **zdokonalení**.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení s D3D11**<br /> Používá rozhraní Direct3D 11 k vykreslení **Editor obrázků** návrhovou plochu.<br /><br /> **Vykreslení s D3D11WARP**<br /> Používá rozhraní Direct3D 11 Windows Advanced Rasterizační platformě WARP () k vykreslení **Editor obrázků** návrhovou plochu.<br /><br /> **Nástroje**<br /><br /> **Převrátit vodorovně**<br /> Transponuje image kolem jeho horizontal nebo x, osy.<br /><br /> **Převrátit svisle**<br /> Transponuje image kolem své osy svislé nebo y.<br /><br /> **Generovat Mips**<br /> Generuje úrovní MIP pro bitovou kopii. Pokud úrovní MIP ještě neexistuje, jsou znovu vytvořena z nejvyšší úrovně MIP. Všechny změny, které byly provedeny na menší MIP úrovních se ztratí. K uložení úrovní MIP, které jste vygenerovali, je nutné použít *.dds* formátu chcete uložit obrázek.<br /><br /> **Zobrazení**<br /><br /> **Snímková frekvence**<br /> Pokud povolená, zobrazí frekvenci snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. **Tip:** můžete použít **Upřesnit** tlačítko poslední příkaz spustit znovu.|

### <a name="image-editor-toolbar"></a>Panel nástrojů editoru obrázků

![Panel nástrojů editoru obrázků](../designers/media/digit-tre-toolbar.png)

Následující tabulka popisuje položky panelu **Editor obrázků** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny shora dolů:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Tužky**|Výběr aktivního používá k vykreslení tahu alias. Můžete nastavit barvu a tloušťku stroke v **vlastnosti** okna.|
|**Štětec**|Chcete-li nakreslit tahu vyhlazené používá výběr aktivního. Můžete nastavit barvu a tloušťku stroke v **vlastnosti** okna.|
|**Rozprašovač**|Výběr aktivního používá k vykreslení tahu vyhlazené prolnutí spolu s bitovou kopii, která změní sytější jako funkce času. Můžete nastavit barvu a tloušťku stroke v **vlastnosti** okna.|
|**Kapátko**|Nastaví výběr aktivního barvu vybraný pixel.|
|**Výplň**|Výběr aktivního se použije k vyplnění oblasti obrázku. Ovlivněné oblasti je definován jako pixel, kde výplně použít společně s každý pixel, který je připojený ke stejné barvy v pixelech a, který má stejnou barvu samotný. Výplň je použit v rámci aktivní výběr, je omezen ovlivněné oblasti podle výběru.<br /><br /> Ve výchozím nastavení je výběr aktivního prolnuty spolu s ovlivněné oblasti bitovou kopii podle jeho hodnota alfa. Chcete-li použít výběr aktivního k přepsání ovlivněné oblasti, stiskněte a podržte **Shift** klíč použijete nástroj pro vyplnění.|
|**Guma**|Nastaví pixelů na plně průhlednou barvu, pokud image podporuje alfa kanál. Jinak nastaví pixely na barvu pozadí aktivní.|
|**Řádek**, **obdélník**, **zaoblený obdélník**, **elipsa**|Nakreslí obrazec na obrázku. Můžete nastavit barvu a tloušťku obrysu v **vlastnosti** okna.<br /><br /> Chcete-li nakreslit jednoduchého typu, který má stejnou šířku a výšku, stiskněte a podržte **Shift** při kreslení.|
|**Text**|Výběr barvy popředí používá k vykreslení textu. Barva pozadí je určena výběr barvy pozadí. Průhledné pozadí alfa výběr barvy pozadí musí být 0. Oblast textu je aktivní, můžete nastavit, zda text je vykreslen s tahu vyhlazené a můžete nastavit text **hodnotu**, **písmo**, **velikost**a styl –**Tučné**, **Kurzíva**, nebo **podtržené**– v **vlastnosti** okna. Obsah a vzhled textu je dokončené, když už není aktivní oblast textu.|
|**Otočit o**|Otočí obrázek 90 stupňů po směru hodinových ručiček.|
|**Trim**|Ořízne obrázek, který se aktivního výběru.|

### <a name="work-with-mip-levels"></a>Práce s úrovní MIP

Některé bitové kopie například formáty DirectDraw Surface (*.dds*), podpory úrovně MIP pro textury místa úrovně of-Detail lod (Level). Informace o tom, jak vytvořit a pracovat s úrovní MIP, naleznete v tématu [postupy: vytvoření a úprava úrovní MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Práce s transparentnosti

Některé bitové kopie například formáty DirectDraw Surface (*.dds*), podporují průhlednost. Existuje několik způsobů, jak můžete použít transparentnosti, v závislosti na nástroj, který používáte. Chcete-li určit úroveň průhlednosti pro výběr barev, v **vlastnosti** okno, nastavte **A** (alfa) součást výběr barvy.

Následující tabulka popisuje, jak různé druhy nástroje pro řízení použití průhlednosti:

|Nástroj|Popis|
|----------|-----------------|
|**Tužky**, **štětce**, **rozprašovač**, **řádku**, **obdélník**, **zaoblený obdélník** , **Elipsa**, **Text**|Pro výběr aktivního spolu s bitovou kopii, v blendu **vlastnosti** okna, rozbalte **kanály** skupiny vlastností a nastavte **nakreslit** zaškrtávací políčko na  **Systém Alpha** channel a následně nakreslete normálně.<br /><br /> Kreslení pomocí aktivního výběru a ponechte hodnotu alfa bitové kopie na místě, zrušte **nakreslit** zaškrtávací políčko z **alfa** channel a následně nakreslete normálně.|
|**Výplň**|Přizpůsobte výběr aktivního spolu s bitovou kopii, prostě vyberte oblasti tak, aby vyplnil.<br /><br /> Chcete použít výběr aktivního – včetně hodnoty alfa kanál – přepsat bitovou kopii, stiskněte a podržte **Shift** a klikněte na tlačítko oblasti tak, aby vyplnil.|

### <a name="image-properties"></a>Vlastnosti bitové kopie

Můžete použít **vlastnosti** okno zadat různé vlastnosti bitové kopie. Například můžete nastavit vlastnosti šířku a výšku obrázku.

Následující tabulka popisuje vlastnosti bitové kopie:

|Vlastnost|Popis|
|--------------|-----------------|
|Šířka|Šířka obrázku.|
|Výška|Výška obrázku.|
|Počet bitů na Pixel|Počet bitů, které představují každý pixel. Hodnota této vlastnosti závisí **formát barev** bitové kopie.|
|Průhledný výběr|**Hodnota TRUE** zapojil obrázek výběru vrstvy spolu s hlavním podle hodnoty alfa výběr vrstvy; v opačném případě **False**. Tato položka je pouze k dispozici pro obrázky podporující alfa.|
|Formát|Formát barev obrázku. Můžete určit různé barvy formátů, v závislosti na formát obrázku. Formát barev definuje počet a druh barevného kanálu, které jsou zahrnuty v obrázku a také velikost a kódování různých kanálů.|
|Úroveň MIP|Aktivní úroveň MIP. Tato položka je dostupná pouze pro textury, které mají úrovní MIP.|
|Počet úrovní MIP|Celkový počet úrovní MIP v bitové kopii. Tato položka je dostupná pouze pro textury, které mají úrovní MIP.|
|Počet snímků|Celkový počet snímků na obrázku. Tato položka je pouze pro obrázky podporující textury pole k dispozici.|
|Rámec|Aktuální rámec. Je možné zobrazit pouze první snímek; všechny ostatní snímky budou ztraceny, při uložení image.|
|Počet hloubek řezu|Celkový počet hloubka řezů v bitové kopii. Tato položka je pouze k dispozici pro obrázky podporující svazku textury.|
|Hloubka řezu|Aktuální hloubce řezu. Je možné zobrazit pouze první řez; všechny ostatní řezy budou ztraceny, při uložení image.|

> [!NOTE]
> Vzhledem k tomu, **otočit o** vlastnost se vztahuje na všechny nástroje a vybrané oblasti se vždy zobrazí v dolní části **vlastnosti** okno společně s další vlastnosti nástroje. **Otočit o** je vždy zobrazen, protože celého obrázku je implicitně vybrána, když není žádný výběr nebo aktivní nástroj. Další informace o **otočit o** vlastnost, naleznete v tématu [nástroj vlastnosti](#tool -properties).

### <a name="resize-images"></a>Změna velikosti obrázků

Existují dva způsoby, jak změnit velikost obrázku. V obou případech platí **Editor obrázků** pomocí interpolace varianty Převzorkovat na obrázku.

- V **vlastnosti** okno, zadejte nové hodnoty **šířka** a **výška** vlastnosti.

- Vyberte celého obrázku a můžete změnit velikost obrázku ohraničení značky.

### <a name="selected-regions"></a>Vybrané oblasti

Požadovaná nastavení **Editor obrázků** definování oblastí bitové kopie, které jsou aktivní. Aktivní oblasti jsou ovlivněny nástroje a transformace. Když je aktivní výběr, oblasti mimo vybrané oblasti nejsou ovlivněny většiny nástrojů a transformace. Pokud neexistuje aktivní výběr, celého obrázku je aktivní.

Většina nástrojů (**tužky**, **štětce**, **rozprašovač**, **vyplnit**, **gumy**a 2D primitivy) a transformace (**otočit**, **Trim**, **Invertovat barvy**, **Převrátit vodorovně**, a **Převrátit svisle** ) jsou omezené nebo určené aktivního výběru. Nicméně některé nástroje (**kapátko** a **Text**) a transformace (**generovat Mips**) nejsou ovlivněny žádné aktivní výběr. Tyto nástroje vždy chovat, jako je aktivní výběr celého obrázku.

Když vybíráte oblasti, můžete stisknutím a podržením **Shift** na příslušnou úměrný (čtvereček). V opačném případě není omezen výběr.

#### <a name="resize-selections"></a>Změnit velikost výběru

Po výběru oblasti, můžete změnit velikost nebo jeho obsahu obrázku tak, že změníte velikost značky výběru. Zatímco vybrané oblasti se změnou velikosti, můžete použít následující modifikační klávesy změnit chování vybrané oblasti při změně velikosti:

**CTRL** – zkopíruje obsah vybrané oblasti, než je velikost. To ale původní bitové kopie ponechá beze změny při změně velikosti kopie.

**SHIFT** – změní velikost vybrané oblasti výkonový zisk původní velikost.

**ALT** – změní velikost výběru oblasti. Kvůli tomu image bez jakýchkoli úprav.

Následující tabulka popisuje kombinace kláves Neplatný modifikátor:

|CTRL|SHIFT|ALT|Popis|
|----------|-----------|---------|-----------------|
||||Změní velikost obsahu vybrané oblasti.|
||**SHIFT**||Proporcionálně změní velikost obsahu vybrané oblasti.|
|||**ALT**|Změní velikost vybrané oblasti. Definuje novou oblast výběru.|
||**SHIFT**|**ALT**|Úměrně mění velikost vybrané oblasti. Definuje novou oblast výběru.|
|**CTRL**|||Zkopíruje a pak změní velikost obsahu vybrané oblasti.|
|**CTRL**|**SHIFT**||Zkopíruje a proporcionálně změní obsah vybrané oblasti.|

### <a name="tool-properties"></a>Vlastnosti nástroje

Nástroj je vybraná, ale můžete použít **vlastnosti** okno a zadejte podrobnosti o tom, jak ovlivňuje bitovou kopii. Například můžete nastavit tloušťku **tužky** nástroje nebo barvu **štětce** nástroj.

Můžete nastavit barvu popředí a barvu pozadí. Obě podporují alfa kanálu poskytnout uživatelský neprůhlednosti. Bude nastavení platit pro všechny nástroje. Pokud používáte myš, levým tlačítkem myši odpovídá barvu popředí a odpovídá pravým tlačítkem myši na barvu pozadí.

Následující tabulka popisuje vlastnosti nástroje:

|Nástroj|Vlastnosti|
|----------|----------------|
|Všechny nástroje a možnosti|**Otočit o**<br /> Definuje velikost, ve stupních, že je efekt výběr nebo nástroj Otočit ve směru hodinových ručiček.|
|**Tužky**, **štětce**, **rozprašovač**, **guma**|**Tloušťka**<br /> Definuje velikost oblasti, která jsou ovlivněná nástroj.|
|**Text**|**Vyhlazení**<br /> Kreslení textu, který má vyhlazené okraje. To dává hladší vzhled textu.<br /><br /> **Hodnota**<br /> Text, který chcete kreslit.<br /><br /> **Písma**<br /> Písmo použité k vykreslování textu.<br /><br /> **Velikost**<br /> Velikost textu.<br /><br /> **Tučné**<br /> Díky tučné písmo.<br /><br /> **Kurzíva**<br /> Díky písmo kurzíva.<br /><br /> **Podtržený**<br /> Díky písmo podtržené.|
|**2D primitivní**|**Vyhlazení**<br /> Nakreslí primitivních elementů, které mají vyhlazené okraje. To jim umožňuje zajistit plynulejší vzhled.<br /><br /> **Tloušťka**<br /> Určuje tloušťku čáry, která tvoří hranici primitivní vlastnost.<br /><br /> **Poloměr X**<br /> (Pouze zakulacený obdélník) Definuje zaokrouhlení radius horním a dolním okrajem primitivní vlastnost.<br /><br /> **Poloměr Y**<br /> (Pouze zakulacený obdélník) Definuje zaokrouhlení radius levých a pravých okrajů primitivní vlastnost.|
|**Tužky**, **štětce**, **rozprašovač**, **2D primitivní**|**kanály**<br /> Povolí nebo zakáže specifického barevného kanálu pro zobrazení a kreslení. Pokud **zobrazení** je nastavit pro konkrétní barevného kanálu, tento kanál je vidět na obrázku; v opačném případě není viditelný. Pokud **nakreslit** nastavený pro určitá barva kanál, kanál je ovlivněné kreslením operace; jinak vrátí hodnotu, není.|
|**Výběr hůlka**, **Fill**|**Proti chybám**<br /> Definuje maximální rozdíl mezi sousedící barvy, ve kterém jsou považovány za podobné, tak, aby méně nebo více podobné barvy byly součástí ovlivněných nebo vybrané oblasti. Hodnota je ve výchozím nastavení, 32, což znamená, že sousední pixelů v rámci 32 odstínů původní barvy (světlejší nebo tmavší) jsou považovány za součást do oblasti.|

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnout na **vyberte** režimu|**S**|
|Přepnout na **přiblížení** režimu|**Z**|
|Přepnout na **Pan** režimu|**K**|
|Vybrat vše|**CTRL**+**A**|
|Odstranit aktuální výběr|**Delete**|
|Zrušit aktuální výběr|**ESC** (ESC)|
|Přiblížit|**CTRL**+**kolečko myši dopředu**<br /><br /> **CTRL**+**PageUp**<br /><br /> Znaménko plus (**+**)|
|Oddálit|**CTRL**-**kolečko myši dozadu**<br /><br /> **CTRL**-**PageDown**<br /><br /> Znaménko minus (**-**)|
|Posunout nahoru obrázek|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posunout dolů na obrázku|**Kolečko myši dopředu**<br /><br /> **Page Up**|
|Posunout obrázek vlevo|**SHIFT**+**kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **SHIFT**+**PageDown**|
|Posunout doprava bitové kopie|**SHIFT**+**kolečko myši dopředu**<br /><br /> **Kolečko myši doprava**<br /><br /> **SHIFT**+**PageUp**|
|Na skutečnou velikost|**CTRL**+**0** (nula)|
|Přizpůsobení bitové kopie do okna|**CTRL**+**G**, **Ctrl**+**F**|
|Přizpůsobit obrázek šířce okna|**CTRL**+**G**, **Ctrl**+**mi**|
|Přepnout mřížku|**CTRL**+**G**, **Ctrl**+**G**|
|Oříznutí obrázku aktuálního výběru|**CTRL**+**G**, **Ctrl**+**C**|
|Zobrazit další (vyšší podrobnosti) úroveň MIP|**CTRL**+**G**, **Ctrl**+**6**|
|Zobrazit předchozí (nižší podrobností) úroveň MIP|**CTRL**+**G**, **Ctrl**+**7**|
|Přepnout červený kanál|**CTRL**+**G**, **Ctrl**+**1**|
|Přepnout zelenou barvu, která kanál|**CTRL**+**G**, **Ctrl**+**2**|
|Přepnout modrou barvou kanálu|**CTRL**+**G**, **Ctrl**+**3**|
|Kanál alfa (průhlednost) přepínací tlačítko|**CTRL**+**G**, **Ctrl**+**4**|
|Přepnout šachovnicový alfa vzor|**CTRL**+**G**, **Ctrl**+**B**|
|Nástroj Volný výběr|**L**|
|Přepnout výběr hůlka|**M**|
|Přepínač tak, aby nástroj tužka|**P**|
|Přepnout na štětec|**B**|
|Přepnout na vyplnit – nástroj|**F**|
|Nástroj guma|**E**|
|Přepnout na text|**T**|
|Nástroj Výběr barvy (kapátko)|**I**|
|Přesunutí aktivního výběru a jeho obsah.|**Šipka** klíče.|
|Změna velikosti aktivního výběru a jeho obsah.|**CTRL**+**šipku** klíče|
|Přesunutí aktivního výběru, ale ne jeho obsah.|**SHIFT**+**šipku** klíče|
|Změna velikosti aktivního výběru, ale ne jeho obsah.|**SHIFT**+**Ctrl**+**šipku** klíče|
|Potvrdit aktuální vrstva|**Vrátí**|
|Tloušťka nástroje snížení|**[**|
|Tloušťka nástroje zvýšení|**]**|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled nástroje, které můžete použít v sadě Visual Studio pro práci se zdroji grafiky, jako je například textury a obrázky, 3D modely a efekty shaderu.|
|[Editor modelů](../designers/model-editor.md)|Popisuje způsob použití editoru Visual Studio Model pro práci s 3D modely.|
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje způsob použití návrháře shaderu Visual Studio pro práci se shadery.|