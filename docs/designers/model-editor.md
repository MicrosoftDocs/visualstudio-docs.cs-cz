---
title: Editor modelů
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
ms.openlocfilehash: 7adee409ff6bb5721724b9acc2e76a11d32a4f54
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589848"
---
# <a name="model-editor"></a>Editor modelů

Tento dokument popisuje, jak pracovat s **Editorem modelů** sady Visual Studio při zobrazení, vytvoření a úpravě 3D modelů.

**Editor modelů** můžete použít k vytvoření základních 3D modelů od začátku nebo k zobrazení a úpravám složitějších 3D modelů, které byly vytvořeny pomocí plně vybavených nástrojů 3D modelování.

## <a name="supported-formats"></a>Podporované formáty

**Editor modelů** podporuje několik formátů 3D modelů, které se používají při vývoji aplikací DirectX:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, vytváření)|
|-----------------| - | - |
|Soubor AutoDesk FBX Interchange|*.fbx*|Zobrazení, úpravy, vytváření|
|Soubor DAE standardu Collada|*.dae*|Zobrazení, úpravy (změny DAE standardu Collada jsou uloženy ve formátu FBX.)|
|Obj|*.obj*|Zobrazení, úpravy (změny souborů OBJ jsou uloženy ve formátu FBX.)|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat 3D model do projektu Visual Studio C++ a další základní informace, které vám pomohou začít.

> [!NOTE]
> Automatická integrace sestavení grafických položek, jako jsou 3D scény (.fbx soubory) je podporována pouze pro projekty C++.

### <a name="to-add-a-3d-model-to-your-project"></a>Přidání 3D modelu do projektu

1. Ujistěte se, že máte nainstalovanou požadovanou součást sady Visual Studio, kterou potřebujete pro práci s grafikou. Komponenta se nazývá **Image a 3D model editory**.

   Chcete-li ji nainstalovat, otevřete instalační službu sady Visual Studio tak, že na řádku nabídek **Image and 3D model editors** vyberete **Nástroje** > získat nástroje **Games and Graphics** a**funkce** a pak vyberte kartu Jednotlivé **součásti.** **Modify**

   ![Komponenta editorů obrazových a 3D modelů](media/image-3d-model-editors-component.png)

   Součást se spustí s instalací.

2. V **Průzkumníku řešení**otevřete místní nabídku pro projekt C++, do kterého chcete obrázek přidat, a pak zvolte **Přidat** > **novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte v kategorii **Grafika** **3D scéna (.fbx).**

   ![Dialogové okno Přidat novou položku s vybranou 3D scénou](media/add-new-3d-scene.png)

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **Grafika** a máte nainstalovanou komponentu **Image a 3D model editory,** nebudou grafické položky pro váš typ projektu podporovány.

4. Zadejte **název** souboru modelu a pak vyberte **Přidat**.

### <a name="axis-orientation"></a>Orientace osy

Visual Studio podporuje každou orientaci 3D osy a načítá informace o orientaci osy z formátů souborů modelu, které ji podporují. Pokud není zadána žádná orientace osy, Visual Studio používá pravotočivý souřadnicový systém ve výchozím nastavení. **Indikátor osy** zobrazuje aktuální orientaci osy v pravém dolním rohu návrhové plochy. Na **ose indikátor**, červená představuje x-osa, zelená představuje osu y, a modrá představuje osu z.

### <a name="begin-your-3d-model"></a>Začněte s 3D modelem

V Editoru modelů každý nový objekt vždy začíná jako jeden ze základních 3D tvarů nebo *primitiv*, které jsou integrovány do Editoru modelů. Chcete-li vytvořit nové a jedinečné objekty, přidáte ke scéně primitiv a změníte jeho tvar úpravou vrcholů. U složitých tvarů přidáte další vrcholy pomocí vysunutí nebo dílčího dělení a následnou úpravou. Informace o přidání primitivního objektu do scény naleznete v [tématu Vytvoření a import 3D objektů](#Adding3DObjects). Informace o přidání dalších vrcholů k objektu naleznete v [tématu Úpravy objektů](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Práce s Editorem modelů

Následující části popisují, jak používat Editor modelů pro práci s 3D modely.

### <a name="model-editor-toolbars"></a>Panely nástrojů editoru modelů

Panely nástrojů Editor u modelu obsahují příkazy, které vám pomohou pracovat s 3D modely.

Příkazy, které ovlivňují stav Editoru modelů, jsou umístěny na panelu nástrojů **Režim editoru modelů** v hlavním okně sady Visual Studio. Nástroje pro modelování a skriptované příkazy jsou umístěny na panelu nástrojů **Editor modelů** na návrhové ploše Editoru modelů.

Zde je panel nástrojů **Režim editoru modelů:**

![Modální panel nástrojů Prohlížeč modelů.](../designers/media/digit-mre-modal-toolbar.png)

Tato tabulka popisuje položky na panelu nástrojů **Režim editoru modelů,** které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava.

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Vybrat**|Umožňuje výběr bodů, okrajů, ploch nebo objektů ve scéně podle aktivního režimu výběru.|
|**Posouvání**|Umožňuje pohyb 3D scény vzhledem k rámečku okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete dočasně aktivovat režim **Posouvání** stisknutím a podržením **klávesy Ctrl.**|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **lupy** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste zobrazení přiblížili, nebo doleva nebo nahoru pro oddálení.<br /><br /> V režimu **výběru** můžete zobrazení přiblížit nebo oddálit pomocí kolečka myši, když stisknete a podržíte **klávesu Ctrl**.|
|**Oběžné dráze**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je **povolena ortografická** projekce.|
|**Svět místní**|Pokud je tato položka povolena, transformace na vybraném objektu pobíhají v globálním prostoru. Jinak transformace na vybraném objektu probíhají v místním prostoru.|
|**Kontingenční režim**|Pokud je tato položka povolena, transformace ovlivní umístění a orientaci *otočného bodu* vybraného objektu (Pivotpoint definuje střed operací posunutí, změny měřítka a otočení.) V opačném případě transformace ovlivní umístění a orientaci geometrie objektu vzhledem k bodu otáčení.|
|**Uzamknout osu X**|Omezuje manipulaci s objekty na ose x. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Y**|Omezuje manipulaci s objekty na ose y. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Z**|Omezuje manipulaci s objekty na ose z. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Objekt rámce**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|
|**Zobrazit**|Nastaví orientaci zobrazení. Zde jsou dostupné orientace:<br /><br /> **Front**<br /> Umístí zobrazení před scénu.<br /><br /> **Zpět**<br /> Umístí zobrazení za scénu.<br /><br /> **Vlevo**<br /> Umístí zobrazení vlevo od scény.<br /><br /> **Právo**<br /> Umístí zobrazení vpravo od scény.<br /><br /> **Top**<br /> Umístí zobrazení nad scénu.<br /><br /> **Dolní části**<br /> Umístí zobrazení pod scénu. **Poznámka:**  Toto je jediný způsob, jak změnit směr pohledu, když je **povolena ortografická** projekce.|
|**Projekce**|Nastaví druh projekce použitý pro vykreslení scény. Zde jsou dostupné projekce:<br /><br /> **Perspektiva**<br /> V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.<br /><br /> **Pravoúhlé**<br /> V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když **je ortografická** projekce povolena, nemůžete k umístění pohledu použít režim **Oběžné dráhy.**|
|**Styl kreslení**|Nastaví, jak jsou objekty ve scéně vykresleny. Zde jsou dostupné styly:<br /><br /> **Drátěný rám**<br /> Je-li tato možnost povolena, objekty jsou vykresleny jako objekty wireframe.<br /><br /> **Překreslení**<br /> Pokud je tato možnost povolena, objekty jsou vykreslovány pomocí doplňkového prolnutí. Tuto možnost můžete použít k zobrazení rozsahu překreslování, ke kterému dochází na scéně.<br /><br /> **Plochý stín**<br /> Je-li tato možnost povolena, objekty jsou vykreslovány základním světelným modelem s plochým stínem. Tuto možnost můžete použít k jednoduššímu zobrazení ploch objektu.<br /><br /> Pokud žádná z těchto možností není povolena, každý objekt je vykreslen pomocí materiálu, který je na něj použit.|
|**Režim vykreslování v reálném čase**|Pokud je povoleno vykreslování v reálném čase, Visual Studio překreslí návrhový povrch, i když se provádí žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Přepnout mřížku**|Po povolení této položky se zobrazí mřížka. Jinak se mřížka nezobrazí.|
|**Sada nástrojů**|Střídavě zobrazuje nebo skryje **panel nástrojů**.|
|**Osnova dokumentu**|Střídavě zobrazí nebo skryje okno **Osnova dokumentu.**|
|**Vlastnosti**|Střídavě zobrazí nebo skryje okno **Vlastnosti.**|
|**Pokročilé**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení pomocí D3D11**<br /> Používá rozhraní Direct3D 11 k vykreslení plochy návrhu editoru modelů.<br /><br /> **Vykreslení pomocí d3D11WARP**<br /> Používá rozhraní Direct3D 11 WARP (Windows Advanced Rasterization Platform) k vykreslení plochy návrhu editoru modelů.<br /><br /> **Správa scény**<br /><br /> **Import**<br /> Importuje objekty z jiného souboru 3D modelu do aktuální scény.<br /><br /> **Připojit k nadřazené**<br /> Určí první z více vybraných objektů jako nadřazený objekt zbývajících vybraných objektů.<br /><br /> **Odpojit od rodiče**<br /> Odpojí vybraný objekt od nadřazeného objektu. Vybraný objekt se stane *kořenovým objektem* ve scéně. Kořenový objekt nemá nadřazený objekt.<br /><br /> **Vytvořit skupinu**<br /> Seskupí vybrané objekty na stejné úrovni.<br /><br /> **Sloučit objekty**<br /> Kombinuje vybrané objekty do jednoho objektu.<br /><br /> **Vytvořit nový objekt z polygonového výběru**<br /> Odebere vybrané plochy z aktuálního objektu a přidá na scénu nový objekt, který tyto plochy obsahuje.<br /><br /> **Nástroje**<br /><br /> **Překlopit polygon vinutí**<br /> Převrátí vybrané mnohoúhelníky tak, že jejich pořadí obtáčení a normála povrchu se převrátí.<br /><br /> **Odebrat všechny animace**<br /> Odebere data animace z objektů.<br /><br /> **Triangulovat**<br /> Převede vybraný objekt na trojúhelníky.<br /><br /> **Zobrazit**<br /><br /> Odstranění odvrácených stran<br /> Povolí nebo zakáže odstranění odvrácených stran.<br /><br /> **Kmitočet**<br /> Zobrazí frekvenci snímků v pravém horním rohu plochy návrhu. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu.<br /><br /> Tato volba je užitečná, když povolíte **volbu režimu vykreslování** v reálném čase.<br /><br /> **Zobrazit vše**<br /> Zobrazí všechny objekty ve scéně. Tím se obnoví **vlastnost Hidden** každého objektu na **hodnotu False**.<br /><br /> **Zobrazit normály ploch**<br /> Zobrazí normály pro každou plochu.<br /><br /> **Zobrazit chybějící materiály**<br /> Zobrazí speciální texturu u objektů, ke kterým není přiřazen materiál.<br /><br /> **Zobrazit kontingenční k**<br /> Povolí nebo zakáže zobrazení značky 3D osy v otočném bodu aktivního výběru.<br /><br /> **Zobrazit zástupné uzly**<br /> Zobrazí zástupné uzly. Zástupný uzel je vytvořen při seskupení objektů.<br /><br /> **Zobrazit normály vrcholů**<br /> Zobrazí normálu každého vrcholu. **Tip:**  Chcete-li znovu spustit poslední skript, můžete zvolit tlačítko **Skripty.**|

Zde je panel nástrojů **Editor modelů:**

![Panel nástrojů Prohlížeč modelů](../designers/media/digit-mre-toolbar.png)

Další tabulka popisuje položky na panelu nástrojů **Editor modelů,** které jsou uvedeny v pořadí, ve kterém se zobrazují shora dolů.

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Překlad**|Posune výběr.|
|**Měřítko**|Změní velikost výběru.|
|**Otočit**|Otočí výběr.|
|**Vybrat bod**|Nastaví **režim výběru** tak, aby vyberte jednotlivé body na objektu.|
|**Vybrat hranu**|Nastaví **režim výběru** tak, aby na objektu vyberte hranu (čáru mezi dvěma vrcholy).|
|**Vybrat plochu**|Nastaví **režim výběru** tak, aby vyberte plochu na objektu.|
|**Vybrat objekt**|Nastaví **režim výběru** tak, aby vyberte celý objekt.|
|**Vytlačení**|Vytvoří další plochu a připojí ji k vybrané ploše.|
|**Rozdělit**|Rozdělí každou vybranou plochu na více ploch. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy.|

### <a name="control-the-view"></a>Ovládání zobrazení

3D scéna je vykreslena podle pohledu, který si lze myslet jako virtuální kameru, která má polohu a orientaci. Chcete-li změnit polohu a orientaci, použijte ovládací prvky pohledu na panelu nástrojů **Režim editoru modelů.**

Následující tabulka popisuje primární ovládací prvky zobrazení.

|Ovládací prvek zobrazení|Popis|
|------------------|-----------------|
|**Posouvání**|Umožňuje pohyb 3D scény vzhledem k rámečku okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete dočasně aktivovat režim **Posouvání** stisknutím a podržením **klávesy Ctrl.**|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **lupy** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste zobrazení přiblížili, nebo doleva nebo nahoru pro oddálení.<br /><br /> V režimu **výběru** můžete zobrazení přiblížit nebo oddálit pomocí kolečka myši, když stisknete a podržíte **klávesu Ctrl**.|
|**Oběžné dráze**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je **povolena ortografická** projekce.|
|**Objekt rámce**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|

Zobrazení je vytvořeno virtuálním fotoaparátem, ale je také definováno projekcí. Projekce definuje, jaké tvary a objekty v zobrazení jsou přeloženy do pixelů na povrchu návrhu. Na panelu nástrojů **Editor modelů** můžete zvolit **perspektivní** nebo **ortografickou** projekci.

|Projekce|Popis|
|----------------|-----------------|
|**Perspektiva**|V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.|
|**Pravoúhlé**|V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když **je ortografická** projekce povolena, nemůžete použít režim **Oběžné dráhy** k libovolnému umístění pohledu.|

Může být užitečné zobrazit 3D scénu ze známé polohy a úhlu, například když chcete porovnat dvě podobné scény. V tomto scénáři editor modelů poskytuje několik předdefinovaných zobrazení. Chcete-li použít předdefinovaný pohled, zvolte na panelu nástrojů **Režim editoru modelu** **zobrazení**a pak zvolte požadované předdefinované zobrazení – přední, zadní, levé, pravé, horní nebo dolní. V těchto zobrazeních virtuální kamera snímá přímo počátek scény. Pokud například zvolíte **Zobrazit nahoře**, virtuální kamera se podívá na počátek scény přímo nad ní.

### <a name="view-additional-geometry-details"></a>Zobrazit další podrobnosti o geometrii

Chcete-li lépe porozumět 3D objektu nebo scéně, můžete zobrazit další detaily geometrie, jako jsou normály podle vrcholu, normály na plochu, body otáčení aktivního výběru a další podrobnosti. Chcete-li je povolit nebo zakázat, zvolte na panelu nástrojů **Editor modelů** **zobrazení** **skriptů** > a pak zvolte požadovaný.

### <a name="create-and-import-3d-objects"></a>Vytváření a import 3D objektů<a name="Adding3DObjects"></a>

Chcete-li do scény přidat předdefinovaný 3D obrazec, vyberte v **panelu nástrojů**požadovaný obrazec a pak ho přesuňte na návrhovou plochu. Nové tvary jsou umístěny v počátku scény. Editor modelů poskytuje sedm tvarů: **Kužel**, **Kostka**, **Válec**, **Disk**, **Rovina**, **Koule**a **Konvice**.

Chcete-li importovat 3D objekt ze souboru, zvolte na panelu nástrojů **Editor modelů** možnost **Rozšířený** > **import** **správě** > scén > a zadejte soubor, který chcete importovat.

### <a name="transform-objects"></a>objekty transformace

Objekt můžete *transformovat* změnou jeho vlastností **Natočení**, **Měřítko**a **Převod.** *Otočení* orientuje objekt použitím po sobě jdoucích otočení kolem osy x, osy y a osy z definované jeho otočným bodem. Každá specifikace otočení má tři komponenty – x, y a z v uvedeném pořadí – které jsou zadány ve stupních. **Změna velikosti** objektu změní jeho roztažením o zadaný faktor podél jedné nebo více os vystředěných na jeho otočný bod. *Překlad* vyhledá objekt v trojrozměrném prostoru vzhledem k jeho nadřazenému objektu namísto jeho otočného bodu.

Objekt můžete transformovat pomocí nástrojů pro modelování nebo nastavením vlastností.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Transformace objektu pomocí nástrojů pro modelování

1. V režimu **Výběr** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. Na panelu nástrojů **Editor modelů** zvolte nástroj **Přeložit**, **Změnit měřítko**nebo **Otočit.** Pro vybraný objekt se zobrazí otočení, změna velikosti nebo manipulátor otočení.

3. K provedení transformace použijte manipulátor. Pro transformace otočení a změny velikosti je manipulátor indikátorem osy. Najednou můžete změnit jen jednu osu nebo všechny osy současně pomocí bílé krychle ve středu indikátoru. Pro otáčení je manipulátor koule tvořená kruhy s kódováním barev, které odpovídají osám x (červená), y (zelená) a z (modrá). K vytvoření požadovaného otočení je třeba změnit každou osu jednotlivě.

#### <a name="transform-an-object-by-setting-its-properties"></a>Transformace objektu nastavením jeho vlastností

1. V režimu **Výběr** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. V okně **Vlastnosti** zadejte hodnoty vlastností **Otočení**, **Měřítko**a **Posunutí.**

    > [!IMPORTANT]
    > Pro **Rotation** vlastnost, určete stupeň otáčení kolem každé ze tří os. Otáčení probíhá postupně. Ujistěte se tedy, že je otáčení správně naplánováno nejprve podle osy x, poté y a poté z.

Použitím nástrojů modelování můžete vytvářet transformace rychle, ale nikoli přesně. Nastavením vlastností objektu můžete určit transformace přesně, ale nikoli rychle. Doporučujeme použít nástroje modelování tak, abyste se dostali „dostatečně blízko“ k požadovaným transformacím, a poté doladit hodnoty vlastností.

Pokud nechcete použít manipulátory, můžete povolit režim volného tvaru. Na panelu nástrojů **Editor modelů** zvolte **Skripty** > **Nástroje** > **volné manipulace s volným tvarem,** chcete-li povolit (nebo zakázat) volný režim. V režimu volného tvaru můžete začít manipulaci v libovolném bodě plochy návrhu namísto bodu manipulátoru. V režimu volného tvaru můžete omezit změny některých os zamčením těch, které nechcete změnit. Na panelu nástrojů **Režim editoru modelů** zvolte libovolnou kombinaci tlačítek **Zámek X**, Zámek **Y**a **Zamknout Z.**

Může být výhodné pracovat s objekty pomocí přichycení k mřížce. Na panelu nástrojů **Režim editoru modelu** zvolte **Přichytit,** chcete-li povolit (nebo zakázat) přichycení k mřížce. Pokud je povolena možnost přichycení k mřížce, jsou přednastaveny omezené přírůstky pro posunutí, otočení a změnu velikosti.

### <a name="work-with-the-pivot-point"></a>Práce s otočným bodem

Bod otáčení objektu definuje jeho střed rotace a změnu měřítka. Bod otáčení objektu můžete změnit, abyste změnili způsob, jak je objekt ovlivněn transformacemi rotace a měřítka. Na panelu nástrojů **Režim editoru modelu** zvolte **Režim kontingenčního režimu,** aby byl režim otáčení povolen (nebo zakázán). Pokud je povolen režim pivotu, zobrazí se v bodu otáčení vybraného projektu indikátor malé osy. Potom můžete použít nástroje **Posunutí** a **otočení** k manipulaci s otočným bodem.

Ukázka, která ukazuje, jak používat otočný bod, najdete v [tématu Postup: Úprava otočného bodu 3D modelu](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Globální a místní režimy

K posunutí a rotaci může dojít buď v místním souřadnicovém systému (nebo *v místním referenčním rámci)* objektu, nebo v souřadnicovém systému světa (nebo *ve světovém referenčním rámci).* Otáčení globálního referenčního snímku je nezávislé na otáčení objektu. Výchozí nastavení je místní režim. Chcete-li povolit (nebo zakázat) světový režim, zvolte na panelu nástrojů **Režim editoru modelů** tlačítko **WorldLocal.**

### <a name="modify-objects"></a>Úprava objektů<a name="ModifyingObjects"></a>

Tvar 3D objektu můžete změnit přesunutím nebo odstraněním jeho vrcholů, hran a ploch. Ve výchozím nastavení je Editor modelů v *režimu objektu*, takže můžete vybírat a transformovat celé objekty. Pokud chcete vybrat body, okraje nebo plochy, zvolte příslušný režim výběru. Na panelu nástrojů **Režim editoru modelů** zvolte **režimy výběru**a pak zvolte požadovaný režim.

Vyloučením nebo dělením můžete vytvořit další vrcholy. Vyloučení duplikuje vrcholy plochy (koplanární sadu vrcholů), které zůstávají spojeny duplikovanými vrcholy. Dělení přidá vrcholy pro vytvoření několika ploch tam, kde byla dříve jen jedna. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy. V obou případech můžete nové vrcholy posunout, otočit a změnit jejich velikost, čímž změníte geometrii celého objektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Vyloučení plochy z objektu

1. V režimu výběru plochy vyberte plochu, kterou chcete vyloučit.

2. Na panelu nástrojů **Editor modelů** zvolte Nástroje**vysunutí nástrojů** > **Extrude** **skriptů** > .

#### <a name="to-subdivide-faces"></a>Rozdělení ploch

1. V režimu výběru plochy vyberte plochy, které chcete rozdělit. Protože rozdělení vytváří nová data hrany, rozdělení všech ploch současně poskytuje konzistentnější výsledky, když plochy sousedí.

2. Na panelu nástrojů **Editor modelů** zvolte **Skripty** > **Nástroje** > **rozdělit**.

Můžete také triangulovat plochy, sloučit objekty a převést mnohoúhelníkové výběry do nových objektů. Triangulace vytvoří další hrany, takže jiné než trojúhelníkové plochy jsou převedeny na optimální počet trojúhelníků; neposkytuje však další podrobnosti o geometrii. Slučování kombinuje vybrané objekty do jednoho objektu. Nové objekty je možné vytvořit pomocí mnohoúhelníkového výběru.

#### <a name="triangulate-a-face"></a>Triangulujte obličej

1. V režimu výběru plochy vyberte plochu, kterou chcete triangulovat.

2. Na panelu nástrojů**Tools** >  **Editor modelů** zvolte Nástroje **skriptů** > **triangulovat**.

#### <a name="merge-objects"></a>Sloučení objektů

1. V režimu výběru objektů vyberte objekty, které chcete sloučit.

2. Na panelu nástrojů **Editor modelů** zvolte **Nástroje skriptů** > **Tools** > **Slučovat objekty**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Vytvoření objektu z výběru polygonu

1. V režimu výběru plochy vyberte plochy, ze kterých chcete vytvořit nový objekt.

2. Na panelu nástrojů**Tools** >  **Editor modelů** zvolte Nástroje **skriptů** > vytvořit nový objekt z**výběru polygonu**.

### <a name="work-with-materials-and-shaders"></a>Práce s materiály a shadéry

Vzhled objektu je určen interakcí osvětlení scény a materiálu objektu. Materiály jsou definovány vlastnostmi, které popisují, jak povrch reaguje na různé typy světla, a programem shader, který vypočítá konečnou barvu každého obrazového bodu na povrchu objektu na základě informací o osvětlení, map textur, map normál a dalších dat.

Editor modelů poskytuje tyto výchozí materiály:

|Materiál|Popis|
|--------------|-----------------|
|**Ztemnit**|Vykreslí povrch bez jakéhokoli simulovaného světla.|
|**Lambert**|Vykreslí povrch se simulovaným osvětlením okolí a difúzním světlem.|
|**Phong**|Vykreslí povrch se simulovaným osvětlením okolí, difúzním světlem a se zrcadlovými světly.|

Každý z těchto materiálů použije jednu texturu na povrch objektu. Můžete nastavit různé textury pro každý objekt, který používá materiál.

Pokud chcete upravit, jak daný objekt reaguje na různé zdroje světla ve scéně, můžete změnit vlastnosti osvětlení materiálu nezávisle na jiných objektech, které materiál používají. Tato tabulka popisuje běžné vlastnosti osvětlení:

|Vlastnost osvětlení|Popis|
| - |-----------------|
|**Okolní**|Popisuje, jakým způsobem je povrch ovlivněn okolním osvětlením.|
|**Rozptýlené**|Popisuje, jakým způsobem je povrch ovlivněn směrovými a bodovými světly.|
|**Zářivé**|Popisuje, jak povrch vyzařuje světlo, nezávisle na ostatním osvětlení.|
|**Odlesk**|Popisuje, jakým způsobem povrch odráží směrová a bodová světla.|
|**Síla odlesku**|Popisuje šířku a intenzitu odlesků.|

V závislosti na tom, co materiál podporuje, můžete změnit jeho vlastnosti osvětlení, textury a další data. V režimu **Výběr** vyberte objekt, jehož materiál chcete změnit, a pak v okně **Vlastnosti** změňte **materiálAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**nebo jinou dostupnou vlastnost. Materiál může vystavit až osm textur, jejichž vlastnosti jsou pojmenovány postupně od **Texture1** do **Texture8**.

Chcete-li odstranit všechny materiály z objektu, zvolte na panelu nástrojů **Editor modelů** možnost**Odstranit materiály** **skripty** > **Materials** > .

**Návrhář shaderu** můžete použít k vytvoření vlastních materiálů shaderu, které můžete použít na objekty ve 3D scéně. Informace o vytváření vlastních materiálů shaderu naleznete v [tématu Shader Designer](../designers/shader-designer.md). Informace o použití vlastního materiálu shaderu na objekt naleznete v tématu [Jak: Aplikování shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Správa scény

Scény můžete spravovat jako hierarchii objektů. Pokud je v hierarchii uspořádáno více objektů, jakékoli posunutí, změna velikosti nebo otočení nadřazeného uzlu ovlivní také podřízené objekty. To je užitečné, když chcete vytvořit složité objekty nebo scény z více základních objektů.

Okno **Osnova dokumentu** můžete použít k zobrazení hierarchie scény a výběru uzlů scény. Když vyberete uzel v osnově, můžete použít okno **Vlastnosti** k úpravě jeho vlastností.

Hierarchii objektů můžete vytvořit buď tím, že jeden z nich stanovíte nadřazený ostatním, nebo jejich seskupením společně jako uzly na stejné úrovni zástupného symbolu, které fungují jako nadřazené.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Vytvoření hierarchie s nadřazeným objektem

1. V režimu **výběru** vyberte dva nebo více objektů. První, který vyberete, bude nadřazený objekt.

2. Na panelu nástrojů **Editor modelů** zvolte **Skripty Správu** > **Scene Management** > scény Připojit k**nadřazené**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Vytvoření hierarchie objektů na stejné úrovni

1. V režimu **výběru** vyberte dva nebo více objektů. Vytvoří se zástupný objekt, který se stane jejich nadřazeným objektem.

2. Na panelu nástrojů **Editor modelů** zvolte **Scripts** > **Scene Management** > **Create Group**.

Editor modelů používá k identifikaci prvního vybraného objektu, který se stane nadřazeným, bílý objekt wireframe. Ostatní objekty ve výběru mají modrý objekt wireframe. Ve výchozím nastavení nejsou uzly zástupných symbolů zobrazeny. Chcete-li zobrazit zástupné uzly, zvolte na panelu nástrojů **Editor modelů** možnost **Skripty** > **Zobrazit** > **zástupné uzly**. S uzly zástupných symbolů můžete pracovat stejně jako při práci s objekty bez zástupných symbolů.

Chcete-li odebrat přidružení nadřazený podřízený mezi dvěma objekty, vyberte podřízený objekt a potom na panelu nástrojů **Editor modelů** zvolte **Scripts** > **Scene Management** > **Detach from Parent**. Pokud odpojíte od podřízeného objektu nadřazený, podřízený objekt se stane kořenovým objektem scény.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnutí do **režimu výběru**|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Přepnutí do režimu **lupy**|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Přepnutí do režimu **Pan**|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Vybrat vše|**Ctrl**+**A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**Útěk** (**Esc**)|
|Přiblížit|**Kolečko myši dopředu**<br /><br /> **Ctrl**+**kolečko myši vpřed**<br /><br /> **Shift**+**kolečko myši vpřed**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Znaménko plus (**+**)|
|Oddálit|**Kolečko myši dozadu**<br /><br /> **Ctrl**+**kolečko myši dozadu**<br /><br /> **Shift**+**kolečko myši dozadu**<br /><br /> **Ctrl**+**PageDown**<br /><br /> Znaménko mínus (**-**)|
|Posunout kameru nahoru|**PageDown**|
|Posunout kameru dolů|**PageUp**|
|Posunout kameru vlevo|**Kolečko myši doleva**<br /><br /> **Ctrl**+**PageDown**|
|Posunout kameru vpravo|**Kolečko myši doprava**<br /><br /> **Ctrl**+**PageDown**|
|Zobrazit horní stranu modelu|**Ctrl**+**L**, **Ctrl**+**T**<br /><br /> **T**|
|Zobrazit spodní stranu modelu|**Ctrl**+**L**, **Ctrl**+**U**|
|Zobrazit levou stranu modelu|**Ctrl**+**L**, **Ctrl**+**L**|
|Zobrazit pravou stranu modelu|**Ctrl**+**L**, **Ctrl**+**R**|
|Zobrazit čelní stranu modelu|**Ctrl**+**L**, **Ctrl**+**F**|
|Zobrazit zadní stranu modelu|**Ctrl**+**L**, **Ctrl**+**B**|
|Orámovat objekt v okně|**F**|
|Přepnout režim wireframe|**Ctrl**+**L**, **Ctrl**+**W**|
|Přepnout přichycení k mřížce|**Ctrl**+**G**, **Ctrl**+**N**|
|Přepnout režim pivotu|**Ctrl**+**G**, **Ctrl**+**V**|
|Přepnout omezení osy x|**Ctrl**+**L**, **Ctrl**+**X**|
|Přepnout omezení osy y|**Ctrl**+**L**, **Ctrl**+**Y**|
|Přepnout omezení osy z|**Ctrl**+**L**, **Ctrl**+**Z**|
|Přepnout do režimu posunutí|**Ctrl**+**G**, **Ctrl**+**W**<br /><br /> **W**|
|Přepnout do režimu měřítka|**Ctrl**+**G**, **Ctrl**+**E**<br /><br /> **E**|
|Přepnout do režimu otočení|**Ctrl**+**G**, **Ctrl**+**R**<br /><br /> **R**|
|Přepnout do režimu výběru bodu|**Ctrl**+**L**, **Ctrl**+**1**|
|Přepnout do režimu výběru okrajů|**Ctrl**+**L**, **Ctrl**+**2**|
|Přepnout do režimu výběru ploch|**Ctrl**+**L**, **Ctrl**+**3**|
|Přepnout do režimu výběru objektů|**Ctrl**+**L**, **Ctrl**+**4**|
|Přepnout do režimu (kamera) orbit|**Ctrl**+**G**, **Ctrl**+**O**|
|Vybrat další objekt na scéně|**Karta**|
|Vybrat předchozí objekt na scéně|**Shift**+**Karta** Shift|
|Manipulovat s vybraným objektem na základě aktuálního nástroje|Klávesy **se šipkami**|
|Deaktivovat aktuální manipulátor|**Q**|
|Otočit kameru|**Alt**+**Přetáhnout** levým tlačítkem myši|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D datovými zdroji pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Obsahuje přehled nástrojů sady Visual Studio, které můžete použít k práci s grafickými prostředky, jako jsou textury a obrazy, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat Visual Studio Image Editor pro práci s texturami a obrázky.|
|[Návrhář shaderu](../designers/shader-designer.md)|Popisuje, jak používat Návrhář shaderu sady Visual Studio pro práci se stínidly.|
