---
title: Editor modelů
description: Naučte se pracovat s editorem modelů sady Visual Studio, abyste mohli zobrazovat, vytvářet a upravovat 3D modely ze začátku nebo složitějších 3D modelů vytvořených pomocí nástrojů pro modelování.
ms.custom: SEO-VS-2020
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aacd72629a393f22a447895d64cbe07d29b5a711
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134417"
---
# <a name="model-editor"></a>Editor modelů

Tento dokument popisuje, jak pracovat s **editorem modelů** sady Visual Studio k zobrazení, vytvoření a úpravám 3D modelů.

**Editor modelů** můžete použít k vytvoření základních 3D modelů od začátku nebo k zobrazení a úpravě složitějších 3D modelů, které byly vytvořeny pomocí plnohodnotných nástrojů 3D modelování.

## <a name="supported-formats"></a>Podporované formáty

**Editor modelů** podporuje několik formátů 3D model používaných při vývoji aplikací pro DirectX:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, vytváření)|
|-----------------| - | - |
|Soubor AutoDesk FBX Interchange|*.fbx*|Zobrazení, úpravy, vytváření|
|Soubor DAE standardu Collada|*.dae*|Zobrazení, úpravy (změny DAE standardu Collada jsou uloženy ve formátu FBX.)|
|OBJEKTU|*.obj*|Zobrazení, úpravy (změny souborů OBJ jsou uloženy ve formátu FBX.)|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat 3D model do projektu Visual Studio C++ a další základní informace, které vám pomohou začít.

> [!NOTE]
> Automatická integrace sestavování grafických položek, jako jsou 3D scény (soubory. FBX), je podporována pouze pro projekty v jazyce C++.

### <a name="to-add-a-3d-model-to-your-project"></a>Přidání 3D model do projektu

1. Ujistěte se, že máte nainstalovanou požadovanou součást sady Visual Studio, kterou potřebujete pracovat s grafikou. Tato součást se nazývá **editory obrázků a 3D model** .

   Pokud ho chcete nainstalovat, otevřete instalační program pro Visual Studio tak, že v řádku nabídek vyberete **nástroje**  >  **získat nástroje a funkce** a pak vyberete kartu **jednotlivé součásti** . v kategorii **hry a grafika** vyberte komponentu **image a 3D model editory** a pak vyberte **Upravit** .

   ![Součást Editor obrázků a 3D model](media/image-3d-model-editors-component.png)

   Spustí se instalace součásti.

2. V **Průzkumník řešení** otevřete místní nabídku pro projekt C++, do které chcete obrázek přidat, a pak zvolte možnost **Přidat**  >  **novou položku** .

3. V dialogovém okně **Přidat novou položku** v kategorii **Grafika** vyberte **3D scéna (. FBX)** .

   ![Dialogové okno Přidat novou položku s vybranou 3D scénou](media/add-new-3d-scene.png)

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **grafiky** a máte nainstalovanou komponentu **image a 3D model editory** , pro váš typ projektu se nepodporují grafické položky.

4. Zadejte **název** souboru modelu a pak vyberte **Přidat** .

### <a name="axis-orientation"></a>Orientace osy

Visual Studio podporuje každou orientaci trojrozměrné osy a načítá informace o orientaci osy z formátů souborů modelu, které ho podporují. Pokud není zadána žádná orientace osy, aplikace Visual Studio ve výchozím nastavení použije systémovou souřadnici na pravé straně. **Indikátor osy** zobrazuje aktuální orientaci osy v pravém dolním rohu návrhové plochy. Na **indikátoru osy** červená znázorňuje osu x, zelená znázorňuje osu y a modrá představuje osu z.

### <a name="begin-your-3d-model"></a>Začněte 3D model

V editoru modelů každý nový objekt vždy začíná jako jeden ze základních 3D tvarů – neboli *primitivních* objektů, které jsou integrovány do editoru modelů. Chcete-li vytvořit nové a jedinečné objekty, přidáte ke scéně primitiv a změníte jeho tvar úpravou vrcholů. U složitých tvarů přidáte další vrcholy pomocí vysunutí nebo dílčího dělení a následnou úpravou. Informace o tom, jak přidat primitivní objekt do scény, najdete v tématu [vytváření a import 3D objektů](#Adding3DObjects). Informace o tom, jak přidat další vrcholy do objektu, naleznete v tématu [upravit objekty](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Práce s editorem modelů

Následující části popisují, jak používat Editor modelů pro práci s 3D modely.

### <a name="model-editor-toolbars"></a>Panely nástrojů editoru modelů

Panely nástrojů editoru modelů obsahují příkazy, které vám pomůžou pracovat s 3D modely.

Příkazy, které mají vliv na stav editoru modelů, jsou umístěny na panelu nástrojů **režim editoru modelů** v hlavním okně aplikace Visual Studio. Nástroje pro modelování a skriptované příkazy jsou umístěny na panelu nástrojů **editoru modelů** na návrhové ploše editoru modelů.

Tady je panel nástrojů **režim editoru modelů** :

![Modální panel nástrojů prohlížeče modelů](../designers/media/digit-mre-modal-toolbar.png)

Tato tabulka popisuje položky na panelu nástrojů **režimu editoru modelů** , které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava.

|Položka na panelu nástrojů|Description|
|------------------|-----------------|
|**Výběr**|Umožňuje výběr bodů, okrajů, ploch nebo objektů ve scéně podle aktivního režimu výběru.|
|**Posouvání**|Umožňuje přesun 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu **CTRL** a dočasně aktivovat režim **posouvání** .|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **zvětšení** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali oddálit nebo zmenšení.<br /><br /> V režimu **výběru** můžete přiblížit nebo oddálit pomocí kolečka myši při stisknutí a podržení klávesy **CTRL** .|
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je povolená projekce **pravoúhle** .|
|**Celosvětový místní**|Pokud je tato položka povolena, transformace na vybraném objektu pobíhají v globálním prostoru. Jinak transformace na vybraném objektu probíhají v místním prostoru.|
|**Režim pivotu**|Pokud je tato položka povolena, transformace ovlivní umístění a orientaci *bodu otáčení* vybraného objektu (bod otáčení definuje střed operací překladu, škálování a rotace.) V opačném případě transformace ovlivní umístění a orientaci geometrie objektu vzhledem k bodu otáčení.|
|**Uzamknout osu X**|Omezuje manipulaci s objekty na ose x. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Y**|Omezuje manipulaci s objekty na ose y. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Z**|Omezuje manipulaci s objekty na ose z. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Objekt Frame**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|
|**Zobrazení**|Nastaví orientaci zobrazení. Zde jsou dostupné orientace:<br /><br /> **Front**<br /> Umístí zobrazení před scénu.<br /><br /> **Zpět**<br /> Umístí zobrazení za scénu.<br /><br /> **Zbývá**<br /> Umístí zobrazení vlevo od scény.<br /><br /> **Kliknutím**<br /> Umístí zobrazení vpravo od scény.<br /><br /> **Nahoře**<br /> Umístí zobrazení nad scénu.<br /><br /> **Dole**<br /> Umístí zobrazení pod scénu. **Poznámka:**  Toto je jediný způsob, jak změnit směr zobrazení, když je povolená projekce **pravoúhle** .|
|**Projekce**|Nastaví druh projekce použitý pro vykreslení scény. Zde jsou dostupné projekce:<br /><br /> **Perspektiva**<br /> V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.<br /><br /> **Pravoúhle**<br /> V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když je povolená projekce **pravoúhle** , nemůžete použít režim **ovál** k umístění zobrazení.|
|**Styl vykreslování**|Nastaví, jak jsou objekty ve scéně vykresleny. Zde jsou dostupné styly:<br /><br /> **Drátěný rámec**<br /> Je-li tato možnost povolena, objekty jsou vykresleny jako objekty wireframe.<br /><br /> **Překreslování**<br /> Pokud je tato možnost povolena, objekty jsou vykreslovány pomocí doplňkového prolnutí. Tuto možnost můžete použít k zobrazení rozsahu překreslování, ke kterému dochází na scéně.<br /><br /> **Plochý stínový stín**<br /> Je-li tato možnost povolena, objekty jsou vykreslovány základním světelným modelem s plochým stínem. Tuto možnost můžete použít k jednoduššímu zobrazení ploch objektu.<br /><br /> Pokud žádná z těchto možností není povolena, každý objekt je vykreslen pomocí materiálu, který je na něj použit.|
|**Režim vykreslování v reálném čase**|Když je povoleno vykreslování v reálném čase, Visual Studio překreslí návrhovou plochu i v případě, že není provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Přepnout mřížku**|Po povolení této položky se zobrazí mřížka. Jinak se mřížka nezobrazí.|
|**Sada nástrojů**|Alternativně zobrazí nebo skryje **panel nástrojů** .|
|**Osnova dokumentu**|Střídavě zobrazí nebo skryje okno **Osnova dokumentu** .|
|**Vlastnosti**|Střídavě zobrazí nebo skryje okno **vlastnosti** .|
|**Pokročilý**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení pomocí D3D11**<br /> Používá rozhraní Direct3D 11 k vykreslení plochy návrhu editoru modelů.<br /><br /> **Vykreslení pomocí D3D11WARP**<br /> Používá rozhraní Direct3D 11 WARP (Windows Advanced Rasterization Platform) k vykreslení plochy návrhu editoru modelů.<br /><br /> **Správa scén**<br /><br /> **Import**<br /> Importuje objekty z jiného souboru 3D model do aktuální scény.<br /><br /> **Připojit k nadřazenému**<br /> Určí první z více vybraných objektů jako nadřazený objekt zbývajících vybraných objektů.<br /><br /> **Odpojit od nadřazené položky**<br /> Odpojí vybraný objekt od nadřazeného objektu. Vybraný objekt se z scény stal *kořenovým objektem* . Kořenový objekt nemá nadřazený objekt.<br /><br /> **Vytvořit skupinu**<br /> Seskupí vybrané objekty na stejné úrovni.<br /><br /> **Sloučit objekty**<br /> Kombinuje vybrané objekty do jednoho objektu.<br /><br /> **Vytvořit nový objekt z mnohoúhelníkového výběru**<br /> Odebere vybrané plochy z aktuálního objektu a přidá na scénu nový objekt, který tyto plochy obsahuje.<br /><br /> **Nástroje**<br /><br /> **Převrátit vinutí mnohoúhelníku**<br /> Převrátí vybrané mnohoúhelníky tak, že jejich pořadí obtáčení a normála povrchu se převrátí.<br /><br /> **Odebrat všechny animace**<br /> Odebere data animace z objektů.<br /><br /> **Triangulovat**<br /> Převede vybraný objekt na trojúhelníky.<br /><br /> **Zobrazení**<br /><br /> Odstranění odvrácených stran<br /> Povolí nebo zakáže odstranění odvrácených stran.<br /><br /> **Snímková frekvence**<br /> Zobrazí frekvenci snímků v pravém horním rohu plochy návrhu. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu.<br /><br /> Tato možnost je užitečná, když povolíte možnost **režim vykreslování v reálném čase** .<br /><br /> **Zobrazit vše**<br /> Zobrazí všechny objekty ve scéně. Tím se obnoví vlastnost **Hidden** každého objektu na **hodnotu false** .<br /><br /> **Zobrazit normální výrazy**<br /> Zobrazí normály pro každou plochu.<br /><br /> **Zobrazit chybějící materiály**<br /> Zobrazí speciální texturu u objektů, ke kterým není přiřazen materiál.<br /><br /> **Zobrazit kontingenční tabulku**<br /> Povolí nebo zakáže zobrazení značky 3D osy v bodě otáčení aktivního výběru.<br /><br /> **Zobrazit zástupné uzly**<br /> Zobrazí zástupné uzly. Zástupný uzel je vytvořen při seskupení objektů.<br /><br /> **Zobrazit normální vrcholy**<br /> Zobrazí normálu každého vrcholu. **Tip:**  Kliknutím na tlačítko **skripty** můžete znovu spustit poslední skript.|

Tady je panel nástrojů **editoru modelů** :

![Panel nástrojů prohlížeč modelů](../designers/media/digit-mre-toolbar.png)

Následující tabulka popisuje položky na panelu nástrojů **editoru modelů** , které jsou uvedeny v pořadí, ve kterém se zobrazují shora dolů.

|Položka na panelu nástrojů|Description|
|------------------|-----------------|
|**Posunut**|Posune výběr.|
|**Škálování**|Změní velikost výběru.|
|**Otočit**|Otočí výběr.|
|**Vybrat bod**|Nastaví **režim výběru** tak, aby bylo možné vybrat jednotlivé body objektu.|
|**Vybrat hranu**|Nastaví **režim výběru** tak, aby vybral okraj (čáru mezi dvěma vrcholy) u objektu.|
|**Vybrat obličej**|Nastaví **režim výběru** tak, aby se na objekt vybrala plocha.|
|**Vybrat objekt**|Nastaví **režim výběru** tak, aby vybral celý objekt.|
|**Vyloučit**|Vytvoří další plochu a připojí ji k vybrané ploše.|
|**Rozdělit**|Rozdělí každou vybranou plochu na více ploch. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy.|

### <a name="control-the-view"></a>Řízení zobrazení

3D scéna se vykreslí podle zobrazení, které se dá představit jako virtuální kamera, která má pozici a orientaci. Chcete-li změnit polohu a orientaci, použijte ovládací prvky zobrazení na panelu nástrojů **režim editoru modelů** .

Následující tabulka popisuje primární ovládací prvky zobrazení.

|Ovládací prvek zobrazení|Description|
|------------------|-----------------|
|**Posouvání**|Umožňuje přesun 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu **CTRL** a dočasně aktivovat režim **posouvání** .|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **zvětšení** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali oddálit nebo zmenšení.<br /><br /> V režimu **výběru** můžete přiblížit nebo oddálit pomocí kolečka myši při stisknutí a podržení klávesy **CTRL** .|
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je povolená projekce **pravoúhle** .|
|**Objekt Frame**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|

Zobrazení je vytvořeno virtuálním fotoaparátem, ale je také definováno projekcí. Projekce definuje, jaké tvary a objekty v zobrazení jsou přeloženy do pixelů na povrchu návrhu. Na panelu nástrojů **editoru modelů** můžete vybrat buď **perspektivu** , nebo **pravoúhle** projekci.

|Projekce|Description|
|----------------|-----------------|
|**Perspektiva**|V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.|
|**Pravoúhle**|V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když je povolená projekce **pravoúhle** , nemůžete použít režim **ovál** k umístění pohledu.|

Může to být užitečné k zobrazení 3D scény ze známé polohy a úhlu, například když chcete porovnat dvě podobné scény. V tomto scénáři editor modelů poskytuje několik předdefinovaných zobrazení. Chcete-li použít předdefinované zobrazení, na panelu nástrojů **režim editoru modelů** zvolte možnost **zobrazení** a zvolte požadované předdefinované zobrazení – vpřed, zpět, vlevo, vpravo, nahoře nebo dole. V těchto zobrazeních virtuální kamera snímá přímo počátek scény. Pokud například vyberete **zobrazení nahoře** , virtuální kamera se dohlíží na počátek scény přímo nad ním.

### <a name="view-additional-geometry-details"></a>Zobrazit další podrobnosti geometrie

Pro lepší pochopení 3D objektu nebo scény můžete zobrazit další podrobné informace o geometrii, jako jsou normální hodnoty pro jednotlivé vrcholy, normální hodnoty pro jednotlivé obličeje, body otáčení aktivního výběru a další podrobnosti. Pokud je chcete povolit nebo zakázat, na panelu nástrojů **editoru modelů** zvolte **Scripts** možnost  >  **zobrazení** skriptů a pak zvolte požadovanou možnost.

### <a name="create-and-import-3d-objects"></a>Vytváření a import 3D objektů <a name="Adding3DObjects"></a>

Chcete-li do scény přidat předdefinovaný 3D tvar, vyberte v **soupravě nástrojů** ten, který chcete, a pak ho přesuňte na návrhovou plochu. Nové tvary jsou umístěny v počátku scény. Editor modelů nabízí sedm tvarů: **kuželový** , **krychlový** , **válcový** , **disk** , **rovina** , **koule** a **konvice** .

Chcete-li importovat 3D objekt ze souboru, na panelu nástrojů **editoru modelů** zvolte možnost **Pokročilá**  >  **Správa scény**  >  **Import** > a pak zadejte soubor, který chcete importovat.

### <a name="transform-objects"></a>objekty transformace

Můžete *transformovat* objekt změnou jeho vlastností **otočení** , **škálování** a **posunutí** . *Rotace* orientuje objekt tím, že aplikuje po sobě jdoucí otočení kolem osy x, osy y a osy z jeho středu. Každá specifikace otočení má tři komponenty – x, y a z v uvedeném pořadí – které jsou zadány ve stupních. **Změna** velikosti objektu se mění tak, že ho roztáhnete podle zadaného faktoru podél jedné nebo více OS na střed svého bodu otáčení. *Překlad* vyhledá objekt v trojrozměrném prostoru relativně vzhledem k jeho nadřazenému objektu místo jeho středu.

Objekt můžete transformovat pomocí nástrojů pro modelování nebo nastavením vlastností.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Transformace objektu pomocí nástrojů pro modelování

1. V režimu **výběru** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. Na panelu nástrojů **editoru modelů** vyberte nástroj pro **posunutí** , **škálování** nebo **otočení** . Pro vybraný objekt se zobrazí otočení, změna velikosti nebo manipulátor otočení.

3. K provedení transformace použijte manipulátor. Pro transformace otočení a změny velikosti je manipulátor indikátorem osy. Najednou můžete změnit jen jednu osu nebo všechny osy současně pomocí bílé krychle ve středu indikátoru. Pro otáčení je manipulátor koule tvořená kruhy s kódováním barev, které odpovídají osám x (červená), y (zelená) a z (modrá). K vytvoření požadovaného otočení je třeba změnit každou osu jednotlivě.

#### <a name="transform-an-object-by-setting-its-properties"></a>Transformace objektu nastavením jeho vlastností

1. V režimu **výběru** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. V okně **vlastnosti** zadejte hodnoty pro vlastnosti **otočení** , **škálování** a **posunutí** .

    > [!IMPORTANT]
    > Pro vlastnost **otočení** zadejte stupeň otočení kolem každé ze tří os. Otáčení probíhá postupně. Ujistěte se tedy, že je otáčení správně naplánováno nejprve podle osy x, poté y a poté z.

Použitím nástrojů modelování můžete vytvářet transformace rychle, ale nikoli přesně. Nastavením vlastností objektu můžete určit transformace přesně, ale nikoli rychle. Doporučujeme použít nástroje modelování tak, abyste se dostali „dostatečně blízko“ k požadovaným transformacím, a poté doladit hodnoty vlastností.

Pokud nechcete použít manipulátory, můžete povolit režim volného tvaru. Pokud **Scripts** **Model Editor**  >  **Tools**  >  chcete povolit (nebo zakázat) režim volného tvaru, na panelu nástrojů editoru modelů vyberte nástroje skripty **volná manipulace** . V režimu volného tvaru můžete začít manipulaci v libovolném bodě plochy návrhu namísto bodu manipulátoru. V režimu volného tvaru můžete omezit změny některých os zamčením těch, které nechcete změnit. Na panelu nástrojů **režim editoru modelů** vyberte libovolnou kombinaci tlačítek **Zamknout X** , **Zamknout Y** a **Zamknout z** .

Může být výhodné pracovat s objekty pomocí přichycení k mřížce. Na panelu nástrojů **režimu editoru modelů** vyberte možnost **Přichytit** a povolte (nebo zakažte) přichycení k mřížce. Pokud je povolena možnost přichycení k mřížce, jsou přednastaveny omezené přírůstky pro posunutí, otočení a změnu velikosti.

### <a name="work-with-the-pivot-point"></a>Práce s bodem otáčení

Bod otáčení objektu definuje jeho střed rotace a změnu měřítka. Bod otáčení objektu můžete změnit, abyste změnili způsob, jak je objekt ovlivněn transformacemi rotace a měřítka. Na panelu nástrojů **režimu editoru modelů** vyberte možnost **režim pivotu** , která povolí (nebo zakáže) režim pivotu. Pokud je povolen režim pivotu, zobrazí se v bodu otáčení vybraného projektu indikátor malé osy. Pak můžete pomocí nástrojů pro **posunutí** a **otočení** manipulovat s bodem otáčení.

Ukázku, která ukazuje, jak použít bod otáčení, naleznete v tématu [How to: Modify a body pivot of 3D model](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Globální a místní režimy

K překladu a rotaci může dojít buď v místním systémovém systému (nebo v *místním referenčním rámci* ) objektu, nebo v souřadnicovém systému celého světa (nebo *světa referenčního rámce* ). Otáčení globálního referenčního snímku je nezávislé na otáčení objektu. Výchozí nastavení je místní režim. Pokud chcete povolit (nebo zakázat) režim světa, klikněte na panelu nástrojů **režimu editoru modelů** na tlačítko **WorldLocal** .

### <a name="modify-objects"></a>Upravit objekty <a name="ModifyingObjects"></a>

Můžete změnit tvar 3D objektu přesunutím nebo odstraněním jeho vrcholů, okrajů a plošek. Ve výchozím nastavení je Editor modelů v *režimu objektů* , takže můžete vybrat a transformovat celé objekty. Pokud chcete vybrat body, okraje nebo plochy, zvolte příslušný režim výběru. Na panelu nástrojů **režim editoru modelů** zvolte možnost **režimy výběru** a pak zvolte požadovaný režim.

Vyloučením nebo dělením můžete vytvořit další vrcholy. Vyloučení duplikuje vrcholy plochy (koplanární sadu vrcholů), které zůstávají spojeny duplikovanými vrcholy. Dělení přidá vrcholy pro vytvoření několika ploch tam, kde byla dříve jen jedna. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy. V obou případech můžete nové vrcholy posunout, otočit a změnit jejich velikost, čímž změníte geometrii celého objektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Vyloučení plochy z objektu

1. V režimu výběru plochy vyberte plochu, kterou chcete vyloučit.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty** –  >  **Tools**  >  **vytlačení** .

#### <a name="to-subdivide-faces"></a>Rozdělení ploch

1. V režimu výběru plochy vyberte plochy, které chcete rozdělit. Protože rozdělení vytváří nová data hrany, rozdělení všech ploch současně poskytuje konzistentnější výsledky, když plochy sousedí.

2. Na panelu nástrojů **editoru modelů** vyberte možnost **Scripts**  >  **Tools**  >  **rozdělit** nástroje skriptů.

Můžete také triangulovat plochy, sloučit objekty a převést mnohoúhelníkové výběry do nových objektů. Triangulace vytvoří další hrany, takže jiné než trojúhelníkové plochy jsou převedeny na optimální počet trojúhelníků; neposkytuje však další podrobnosti o geometrii. Slučování kombinuje vybrané objekty do jednoho objektu. Nové objekty je možné vytvořit pomocí mnohoúhelníkového výběru.

#### <a name="triangulate-a-face"></a>Triangulovat obličej

1. V režimu výběru plochy vyberte plochu, kterou chcete triangulovat.

2. Na panelu nástrojů **editoru modelů** vyberte nástroje **skripty**  >  **Tools**  >  **triangulovat** .

#### <a name="merge-objects"></a>Sloučit objekty

1. V režimu výběru objektů vyberte objekty, které chcete sloučit.

2. Na panelu nástrojů **editoru modelů** vyberte nástroje **skripty**  >  **Tools**  >  **Sloučit objekty** .

#### <a name="create-an-object-from-a-polygon-selection"></a>Vytvoření objektu z mnohoúhelníkového výběru

1. V režimu výběru plochy vyberte plochy, ze kterých chcete vytvořit nový objekt.

2. Na panelu nástrojů **editoru modelů** vyberte možnost **Scripts**  >  **nástroje** skripty  >  **vytvořit nový objekt z mnohoúhelníkového výběru** .

### <a name="work-with-materials-and-shaders"></a>Práce s materiály a shadery

Vzhled objektu je určen interakcí osvětlení scény a materiálu objektu. Materiály jsou definovány vlastnostmi, které popisují, jak povrch reaguje na různé typy světla, a programem shader, který vypočítá konečnou barvu každého obrazového bodu na povrchu objektu na základě informací o osvětlení, map textur, map normál a dalších dat.

Editor modelů poskytuje tyto výchozí materiály:

|Materiál|Description|
|--------------|-----------------|
|**Ztemnit**|Vykreslí povrch bez jakéhokoli simulovaného světla.|
|**Lambert**|Vykreslí povrch se simulovaným osvětlením okolí a difúzním světlem.|
|**Phong**|Vykreslí povrch se simulovaným osvětlením okolí, difúzním světlem a se zrcadlovými světly.|

Každý z těchto materiálů použije jednu texturu na povrch objektu. Můžete nastavit různé textury pro každý objekt, který používá materiál.

Pokud chcete upravit, jak daný objekt reaguje na různé zdroje světla ve scéně, můžete změnit vlastnosti osvětlení materiálu nezávisle na jiných objektech, které materiál používají. Tato tabulka popisuje běžné vlastnosti osvětlení:

|Vlastnost osvětlení|Description|
| - |-----------------|
|**Okolní**|Popisuje, jakým způsobem je povrch ovlivněn okolním osvětlením.|
|**Rozptýlené**|Popisuje, jakým způsobem je povrch ovlivněn směrovými a bodovými světly.|
|**Zářivé**|Popisuje, jak povrch vyzařuje světlo, nezávisle na ostatním osvětlení.|
|**Odlesk**|Popisuje, jakým způsobem povrch odráží směrová a bodová světla.|
|**Síla odlesku**|Popisuje šířku a intenzitu odlesků.|

V závislosti na tom, co materiál podporuje, můžete změnit jeho vlastnosti osvětlení, textury a další data. V režimu **výběru** vyberte objekt, jehož materiál chcete změnit, a poté v okně **vlastnosti** změňte vlastnost **MaterialAmbient** , **MaterialDiffuse** , **MaterialEmissive** , **MaterialSpecular** , **MaterialSpecularPower** nebo jiná dostupná vlastnost. Materiál může vystavit až osm textur, jejichž vlastnosti se pojmenují postupně z **Texture1** na **Texture8** .

Chcete-li odebrat všechny materiály z objektu, na panelu nástrojů **editoru modelů** vyberte možnost **skripty**  >  **materiály**  >  **Odebrat materiály** .

Můžete použít **Návrháře shaderu** k vytvoření vlastních materiálů shaderu, které lze použít na objekty ve 3D scéně. Informace o tom, jak vytvořit vlastní materiály shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md). Informace o tom, jak použít vlastní materiál shaderu pro objekt, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Správa scény

Scény můžete spravovat jako hierarchii objektů. Pokud je v hierarchii uspořádáno více objektů, jakékoli posunutí, změna velikosti nebo otočení nadřazeného uzlu ovlivní také podřízené objekty. To je užitečné, když chcete vytvořit složité objekty nebo scény z více základních objektů.

Pomocí okna **Osnova dokumentu** můžete zobrazit hierarchii scény a vybrat uzly scény. Když vyberete uzel v osnově, můžete použít okno **vlastnosti** a upravit jeho vlastnosti.

Hierarchii objektů můžete vytvořit buď tím, že jeden z nich stanovíte nadřazený ostatním, nebo jejich seskupením společně jako uzly na stejné úrovni zástupného symbolu, které fungují jako nadřazené.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Vytvoření hierarchie s nadřazeným objektem

1. V režimu **výběru** vyberte dva nebo více objektů. První, který vyberete, bude nadřazený objekt.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**  >  **Správa scény**  >  **připojit k nadřazenému** .

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Vytvoření hierarchie objektů na stejné úrovni

1. V režimu **výběru** vyberte dva nebo více objektů. Vytvoří se zástupný objekt, který se stane jejich nadřazeným objektem.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**  >  **Správa scén**  >  **vytvořit skupinu** .

Editor modelů používá k identifikaci prvního vybraného objektu, který se stane nadřazeným, bílý objekt wireframe. Ostatní objekty ve výběru mají modrý objekt wireframe. Ve výchozím nastavení nejsou uzly zástupných symbolů zobrazeny. Chcete-li zobrazit zástupné uzly, vyberte na panelu nástrojů **editoru modelů** možnost **skripty**  >  . **Správa scén**  >  **Zobrazit zástupné uzly** . S uzly zástupných symbolů můžete pracovat stejně jako při práci s objekty bez zástupných symbolů.

Chcete-li odebrat přidružení typu nadřazený-podřízený mezi dvěma objekty, vyberte podřízený objekt a poté na panelu nástrojů **editoru modelů** zvolte příkaz **skripty**  >  **Správa scén**  >  **Odpojit z nadřazené položky** . Pokud odpojíte od podřízeného objektu nadřazený, podřízený objekt se stane kořenovým objektem scény.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnout na režim **výběru**|**CTRL** + **G** , **CTRL** + **Q**<br /><br /> **S**|
|Přepnout do režimu **lupy**|**CTRL** + **G** , **CTRL** + **Z**<br /><br /> **Z**|
|Přepnout do režimu **posouvání**|**CTRL** + **G** , **CTRL** + **P** +<br /><br /> **K**|
|Vybrat vše|**CTRL** + **A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**Řídicí** znak ( **ESC** )|
|Přiblížit|**Kolečko myši dopředu**<br /><br /> **CTRL** + **Kolečko myši – posunutí**<br /><br /> **Posun** + **Kolečko myši – posunutí**<br /><br /> **CTRL** + **PageUp**<br /><br /> Znaménko plus ( **+** )|
|Oddálit|**Kolečko myši dozadu**<br /><br /> **CTRL** + **Kolečko myši dozadu**<br /><br /> **Posun** + **Kolečko myši dozadu**<br /><br /> **CTRL** + **PageDown**<br /><br /> Symbol mínus ( **-** )|
|Posunout kameru nahoru|**PageDown**|
|Posunout kameru dolů|**PageUp**|
|Posunout kameru vlevo|**Kolečko myši doleva**<br /><br /> **CTRL** + **PageDown**|
|Posunout kameru vpravo|**Kolečko myši doprava**<br /><br /> **CTRL** + **PageDown**|
|Zobrazit horní stranu modelu|**CTRL** + **L** , **CTRL** + **T**<br /><br /> **T**|
|Zobrazit spodní stranu modelu|**CTRL** + **L** , **CTRL** + **U**|
|Zobrazit levou stranu modelu|**CTRL** + **L** , **CTRL** + **l**|
|Zobrazit pravou stranu modelu|**CTRL** + **L** , **CTRL** + **R**|
|Zobrazit čelní stranu modelu|**CTRL** + **L** , **CTRL** + **F**|
|Zobrazit zadní stranu modelu|**CTRL** + **L** , **CTRL** + **B**|
|Orámovat objekt v okně|**FJ**|
|Přepnout režim wireframe|**CTRL** + **L** , **CTRL** + **W**|
|Přepnout přichycení k mřížce|**CTRL** + **G** , **CTRL** + **N**|
|Přepnout režim pivotu|**CTRL** + **G** , **CTRL** + **V**|
|Přepnout omezení osy x|**CTRL** + **L** , **CTRL** + **X**|
|Přepnout omezení osy y|**CTRL** + **L** , **CTRL +** + **a**|
|Přepnout omezení osy z|**CTRL** + **L** , **CTRL** + **Z**|
|Přepnout do režimu posunutí|**CTRL** + **G** , **CTRL** + **W**<br /><br /> **W**|
|Přepnout do režimu měřítka|**CTRL** + **G** , **CTRL** + **E**<br /><br /> **E**|
|Přepnout do režimu otočení|**CTRL** + **G** , **CTRL** + **R**<br /><br /> **R**|
|Přepnout do režimu výběru bodu|**CTRL** + **L** , **CTRL** + **1**|
|Přepnout do režimu výběru okrajů|**CTRL** + **L** , **CTRL** + **2**|
|Přepnout do režimu výběru ploch|**CTRL** + **L** , **CTRL** + **3**|
|Přepnout do režimu výběru objektů|**CTRL** + **L** , **CTRL** + **4**|
|Přepnout do režimu (kamera) orbit|**CTRL** + **G** , **CTRL** + **O**|
|Vybrat další objekt na scéně|**Rážky**|
|Vybrat předchozí objekt na scéně|**Posun** + **Karta**|
|Manipulovat s vybraným objektem na základě aktuálního nástroje|Klávesy se **šipkami**|
|Deaktivovat aktuální manipulátor|**Č**|
|Otočit kameru|**ALT** + **Přetažení** levým tlačítkem myši|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled nástrojů sady Visual Studio, které můžete použít pro práci s grafickými prostředky, jako jsou textury a obrázky, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat editor obrázků sady Visual Studio pro práci s texturami a obrázky.|
|[Návrhář shaderu](../designers/shader-designer.md)|Popisuje, jak používat návrháře shaderu sady Visual Studio pro práci s shadery.|
