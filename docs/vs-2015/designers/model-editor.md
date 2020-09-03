---
title: Editor modelů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ede47ea89030aed0298961599f09df6444ed968
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664209"
---
# <a name="model-editor"></a>Editor modelů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje, jak pracovat s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editorem modelů k zobrazení, vytvoření a úpravám 3D modelů.

 Editor modelů můžete použít k vytvoření základních 3D modelů od začátku nebo k zobrazení a úpravám složitějších 3D modelů, které byly vytvořeny pomocí plnohodnotných nástrojů pro 3D modelování. Editor modelů podporuje několik formátů 3D modelů, které jsou používány při vývoji aplikace v rozhraní DirectX.

## <a name="supported-formats"></a>Podporované formáty
 Editor modelů podporuje tyto formáty modelů:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, vytváření)|
|-----------------|--------------------|-------------------------------------------------|
|Soubor AutoDesk FBX Interchange|.fbx|Zobrazení, úpravy, vytváření|
|Soubor DAE standardu Collada|.dae|Zobrazení, úpravy (změny DAE standardu Collada jsou uloženy ve formátu FBX.)|
|OBJEKTU|.obj|Zobrazení, úpravy (změny souborů OBJ jsou uloženy ve formátu FBX.)|

## <a name="getting-started"></a>Začínáme
 Tato část popisuje, jak přidat do projektu 3D model [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a poskytuje základní informace, které potřebujete, abyste mohli začít.

#### <a name="to-add-a-3-d-model-to-your-project"></a>Přidání 3D modelu do projektu

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt, do kterého chcete přidat obrázek, a poté zvolte možnost **Přidat**, **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte v části **nainstalováno**možnost **Grafika**a potom vyberte **3D scéna (. FBX)**.

3. Zadejte **název** souboru modelu a **umístění** , kde se má vytvořit.

4. Vyberte tlačítko **Přidat**.

### <a name="axis-orientation"></a>Orientace osy
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje každou orientaci 3D osy a načítá informace o orientaci osy z formátů souborů modelu, které ji podporují. Pokud není zadána žádná orientace osy, nástroj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve výchozím nastavení použije systém souřadnic na pravé straně. **Indikátor osy** zobrazuje aktuální orientaci osy v pravém dolním rohu návrhové plochy. Na **indikátoru osy**červená znázorňuje osu x, zelená znázorňuje osu y a modrá představuje osu z.

### <a name="beginning-your-3-d-model"></a>Zahájení 3D modelu
 V editoru modelů každý nový objekt vždy začíná jako jeden ze základních 3D tvarů – neboli *primitivních*objektů, které jsou integrovány do editoru modelů. Chcete-li vytvořit nové a jedinečné objekty, přidáte ke scéně primitiv a změníte jeho tvar úpravou vrcholů. U složitých tvarů přidáte další vrcholy pomocí vysunutí nebo dílčího dělení a následnou úpravou. Informace o tom, jak přidat primitivní objekt do scény, najdete v tématu [vytváření a import 3D objektů](#Adding3DObjects). Informace o tom, jak přidat další vrcholy do objektu, naleznete v tématu [Úprava objektů](#ModifyingObjects).

## <a name="working-with-the-model-editor"></a>Práce s editorem modelů
 Následující části popisují způsob použití editoru modelů pro práci s 3D modely.

### <a name="model-editor-toolbars"></a>Panely nástrojů editoru modelů
 Panely nástrojů Editoru modelů obsahují příkazy, které vám pomohou pracovat se 3D modely.

 Příkazy, které mají vliv na stav editoru modelů, jsou umístěny na panelu nástrojů **režimu editoru modelů** v hlavním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okně. Nástroje pro modelování a skriptované příkazy jsou umístěny na panelu nástrojů **editoru modelů** na návrhové ploše editoru modelů.

 Tady je panel nástrojů **režim editoru modelů** :

 ![Modální panel nástrojů prohlížeče modelů](../designers/media/digit-mre-modal-toolbar.png "Číslice – MRE – modální – panel nástrojů")

 Tato tabulka popisuje položky na panelu nástrojů **režimu editoru modelů** , které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava.

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Výběr**|Umožňuje výběr bodů, okrajů, ploch nebo objektů ve scéně podle aktivního režimu výběru.|
|**Posouvání**|Umožňuje pohyb 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu CTRL a dočasně aktivovat režim **posouvání** .|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **zvětšení** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali oddálit nebo zmenšení.<br /><br /> V režimu **výběru** můžete přiblížit nebo oddálit pomocí kolečka myši při stisknutí a podržení klávesy CTRL.|
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je povolená projekce **pravoúhle** .|
|**Celosvětový místní**|Pokud je tato položka povolena, transformace na vybraném objektu pobíhají v globálním prostoru. Jinak transformace na vybraném objektu probíhají v místním prostoru.|
|**Režim pivotu**|Pokud je tato položka povolena, transformace ovlivní umístění a orientaci *bodu otáčení* vybraného objektu (bod otáčení definuje střed operací překladu, škálování a rotace.) V opačném případě transformace ovlivní umístění a orientaci geometrie objektu vzhledem k bodu otáčení.|
|**Uzamknout osu X**|Omezuje manipulaci s objekty na ose x. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Y**|Omezuje manipulaci s objekty na ose y. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Zamknout osu Z**|Omezuje manipulaci s objekty na ose z. Platí pouze při použití prostřední části pomůcky manipulátoru.|
|**Objekt Frame**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|
|**Zobrazení**|Nastaví orientaci zobrazení. Zde jsou dostupné orientace:<br /><br /> **Front**<br /> Umístí zobrazení před scénu.<br /><br /> **Zpět**<br /> Umístí zobrazení za scénu.<br /><br /> **Zbývá**<br /> Umístí zobrazení vlevo od scény.<br /><br /> **Kliknutím**<br /> Umístí zobrazení vpravo od scény.<br /><br /> **Vrchol**<br /> Umístí zobrazení nad scénu.<br /><br /> **Dolů**<br /> Umístí zobrazení pod scénu. **Poznámka:**  Toto je jediný způsob, jak změnit směr zobrazení, když je povolená projekce **pravoúhle** .|
|**Projekce**|Nastaví druh projekce použitý pro vykreslení scény. Zde jsou dostupné projekce:<br /><br /> **Perspektiva**<br /> V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.<br /><br /> **Pravoúhle**<br /> V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když je povolená projekce **pravoúhle** , nemůžete použít režim **ovál** k umístění zobrazení.|
|**Styl vykreslování**|Nastaví, jak jsou objekty ve scéně vykresleny. Zde jsou dostupné styly:<br /><br /> **Drátěný rámec**<br /> Je-li tato možnost povolena, objekty jsou vykresleny jako objekty wireframe.<br /><br /> **Překreslování**<br /> Pokud je tato možnost povolena, objekty jsou vykreslovány pomocí doplňkového prolnutí. Tuto možnost můžete použít k zobrazení rozsahu překreslování, ke kterému dochází na scéně.<br /><br /> **Plochý stínový stín**<br /> Je-li tato možnost povolena, objekty jsou vykreslovány základním světelným modelem s plochým stínem. Tuto možnost můžete použít k jednoduššímu zobrazení ploch objektu.<br /><br /> Pokud žádná z těchto možností není povolena, každý objekt je vykreslen pomocí materiálu, který je na něj použit.|
|**Režim vykreslování v reálném čase**|Když je povoleno vykreslování v reálném čase, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] překreslí návrhovou plochu i v případě, že není provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Přepnout mřížku**|Po povolení této položky se zobrazí mřížka. Jinak se mřížka nezobrazí.|
|**Sada nástrojů**|Alternativně zobrazí nebo skryje **panel nástrojů**.|
|**Osnova dokumentu**|Střídavě zobrazí nebo skryje okno **Osnova dokumentu** .|
|**Vlastnosti**|Střídavě zobrazí nebo skryje okno **vlastnosti** .|
|**Pokročilý**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení pomocí D3D11**<br /> Používá rozhraní Direct3D 11 k vykreslení plochy návrhu editoru modelů.<br /><br /> **Vykreslení pomocí D3D11WARP**<br /> Používá rozhraní Direct3D 11 WARP (Windows Advanced Rasterization Platform) k vykreslení plochy návrhu editoru modelů.<br /><br /> **Správa scén**<br /><br /> **Import**<br /> Importuje objekty z jiného souboru 3D modelu do aktuální scény.<br /><br /> **Připojit k nadřazenému**<br /> Určí první z více vybraných objektů jako nadřazený objekt zbývajících vybraných objektů.<br /><br /> **Odpojit od nadřazené položky**<br /> Odpojí vybraný objekt od nadřazeného objektu. Vybraný objekt se z scény stal *kořenovým objektem* . Kořenový objekt nemá nadřazený objekt.<br /><br /> **Vytvořit skupinu**<br /> Seskupí vybrané objekty na stejné úrovni.<br /><br /> **Sloučit objekty**<br /> Kombinuje vybrané objekty do jednoho objektu.<br /><br /> **Vytvořit nový objekt z mnohoúhelníkového výběru**<br /> Odebere vybrané plochy z aktuálního objektu a přidá na scénu nový objekt, který tyto plochy obsahuje.<br /><br /> **Nástroje**<br /><br /> **Převrátit vinutí mnohoúhelníku**<br /> Převrátí vybrané mnohoúhelníky tak, že jejich pořadí obtáčení a normála povrchu se převrátí.<br /><br /> **Odebrat všechny animace**<br /> Odebere data animace z objektů.<br /><br /> **Triangulovat**<br /> Převede vybraný objekt na trojúhelníky.<br /><br /> **Zobrazení**<br /><br /> Odstranění odvrácených stran<br /> Povolí nebo zakáže odstranění odvrácených stran.<br /><br /> **Snímková frekvence**<br /> Zobrazí frekvenci snímků v pravém horním rohu plochy návrhu. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu.<br /><br /> Tato možnost je užitečná, když povolíte možnost **režim vykreslování v reálném čase** .<br /><br /> **Zobrazit vše**<br /> Zobrazí všechny objekty ve scéně. Tím se obnoví vlastnost **Hidden** každého objektu na **hodnotu false**.<br /><br /> **Zobrazit normální výrazy**<br /> Zobrazí normály pro každou plochu.<br /><br /> **Zobrazit chybějící materiály**<br /> Zobrazí speciální texturu u objektů, ke kterým není přiřazen materiál.<br /><br /> **Zobrazit kontingenční tabulku**<br /> Povolí nebo zakáže zobrazení značky na osách 3D v bodě otáčení aktivního výběru.<br /><br /> **Zobrazit zástupné uzly**<br /> Zobrazí zástupné uzly. Zástupný uzel je vytvořen při seskupení objektů.<br /><br /> **Zobrazit normální vrcholy**<br /> Zobrazí normálu každého vrcholu. **Tip:**  Kliknutím na tlačítko **skripty** můžete znovu spustit poslední skript.|

 Tady je panel nástrojů **editoru modelů** :

 ![Panel nástrojů prohlížeč modelů](../designers/media/digit-mre-toolbar.png "Číslice – MRE – panel nástrojů")

 Následující tabulka popisuje položky na panelu nástrojů **editoru modelů** , které jsou uvedeny v pořadí, ve kterém se zobrazují shora dolů.

|Položka na panelu nástrojů|Popis|
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

### <a name="controlling-the-view"></a>Ovládání zobrazení
 3D scéna je vykreslena podle zobrazení, které si lze představit jako virtuální fotoaparát obsahující umístění a orientaci. Chcete-li změnit polohu a orientaci, použijte ovládací prvky zobrazení na panelu nástrojů **režim editoru modelů** .

 Následující tabulka popisuje primární ovládací prvky zobrazení.

|Ovládací prvek zobrazení|Popis|
|------------------|-----------------|
|**Posouvání**|Umožňuje pohyb 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu CTRL a dočasně aktivovat režim **posouvání** .|
|**Zoom**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V režimu **zvětšení** vyberte bod ve scéně a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali oddálit nebo zmenšení.<br /><br /> V režimu **výběru** můžete přiblížit nebo oddálit pomocí kolečka myši při stisknutí a podržení klávesy CTRL.|
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:**  Tento režim nemá žádný vliv, pokud je povolená projekce **pravoúhle** .|
|**Objekt Frame**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|

 Zobrazení je vytvořeno virtuálním fotoaparátem, ale je také definováno projekcí. Projekce definuje, jaké tvary a objekty v zobrazení jsou přeloženy do pixelů na povrchu návrhu. Na panelu nástrojů **editoru modelů** můžete vybrat buď **perspektivu** , nebo **pravoúhle** projekci.

|Projekce|Popis|
|----------------|-----------------|
|**Perspektiva**|V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.|
|**Pravoúhle**|V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když je povolená projekce **pravoúhle** , nemůžete použít režim **ovál** k umístění pohledu.|

 Může být užitečné zobrazit 3D scénu ze známého umístění a úhlu, například když chcete porovnat dvě podobné scény. V tomto scénáři editor modelů poskytuje několik předdefinovaných zobrazení. Chcete-li použít předdefinované zobrazení, na panelu nástrojů **režim editoru modelů** zvolte možnost **zobrazení**a zvolte požadované předdefinované zobrazení – vpřed, zpět, vlevo, vpravo, nahoře nebo dole. V těchto zobrazeních virtuální kamera snímá přímo počátek scény. Pokud například vyberete **zobrazení nahoře**, virtuální kamera se dohlíží na počátek scény přímo nad ním.

### <a name="viewing-additional-geometry-details"></a>Zobrazení dalších podrobností o geometrii
 Pro lepší pochopení 3D objektu nebo scény můžete zobrazit další podrobnosti geometrie, jako jsou normály pro každý vrchol, normály pro každou plochu, body otáčení aktivního výběru a další podrobnosti. Pokud je chcete povolit nebo zakázat, na panelu nástrojů **editoru modelů** zvolte možnosti **skripty**, **zobrazení**a pak vyberte požadovanou položku.

### <a name="creating-and-importing-3-d-objects"></a><a name="Adding3DObjects"></a> Vytváření a import 3D objektů
 Chcete-li do scény přidat předdefinovaný 3D tvar, vyberte v **soupravě nástrojů**ten, který chcete, a pak ho přesuňte na návrhovou plochu. Nové tvary jsou umístěny v počátku scény. Editor modelů nabízí sedm tvarů: **kuželový**, **krychlový**, **válcový**, **disk**, **rovina**, **koule**a **konvice**.

 Chcete-li importovat 3D objekt ze souboru, na panelu nástrojů **editoru modelů** zvolte možnost **Upřesnit**, **Správa scén**, **importovat**a pak zadejte soubor, který chcete importovat.

### <a name="transforming-objects"></a>Transformace objektů
 Můžete *transformovat* objekt změnou jeho vlastností **otočení**, **škálování**a **posunutí** . *Rotace* orientuje objekt tím, že aplikuje po sobě jdoucí otočení kolem osy x, osy y a osy z jeho středu. Každá specifikace otočení má tři komponenty – x, y a z v uvedeném pořadí – které jsou zadány ve stupních. **Změna** velikosti objektu se mění tak, že ho roztáhnete podle zadaného faktoru podél jedné nebo více OS na střed svého bodu otáčení. *Překlad* vyhledá objekt v trojrozměrném prostoru relativně vzhledem k jeho nadřazenému objektu místo jeho středu.

 Objekt můžete transformovat pomocí nástrojů pro modelování nebo nastavením vlastností.

##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Transformace objektu pomocí nástrojů pro modelování

1. V režimu **výběru** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. Na panelu nástrojů **editoru modelů** vyberte nástroj pro **posunutí**, **škálování**nebo **otočení** . Pro vybraný objekt se zobrazí otočení, změna velikosti nebo manipulátor otočení.

3. K provedení transformace použijte manipulátor. Pro transformace otočení a změny velikosti je manipulátor indikátorem osy. Najednou můžete změnit jen jednu osu nebo všechny osy současně pomocí bílé krychle ve středu indikátoru. Pro otáčení je manipulátor koule tvořená kruhy s kódováním barev, které odpovídají osám x (červená), y (zelená) a z (modrá). K vytvoření požadovaného otočení je třeba změnit každou osu jednotlivě.

##### <a name="to-transform-an-object-by-setting-its-properties"></a>Transformace objektu nastavením jeho vlastností

1. V režimu **výběru** vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.

2. V okně **vlastnosti** zadejte hodnoty pro vlastnosti **otočení**, **škálování**a **posunutí** .

   > [!IMPORTANT]
   > Pro vlastnost **otočení** zadejte stupeň otočení kolem každé ze tří os. Otáčení probíhá postupně. Ujistěte se tedy, že je otáčení správně naplánováno nejprve podle osy x, poté y a poté z.

   Použitím nástrojů modelování můžete vytvářet transformace rychle, ale nikoli přesně. Nastavením vlastností objektu můžete určit transformace přesně, ale nikoli rychle. Doporučujeme použít nástroje modelování tak, abyste se dostali „dostatečně blízko“ k požadovaným transformacím, a poté doladit hodnoty vlastností.

   Pokud nechcete použít manipulátory, můžete povolit režim volného tvaru. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **manipulace s volnou formou** , aby bylo možné (nebo zakázat) režim volného tvaru. V režimu volného tvaru můžete začít manipulaci v libovolném bodě plochy návrhu namísto bodu manipulátoru. V režimu volného tvaru můžete omezit změny některých os zamčením těch, které nechcete změnit. Na panelu nástrojů **režim editoru modelů** vyberte libovolnou kombinaci tlačítek **Zamknout X**, **Zamknout Y**a **Zamknout z** .

   Může být výhodné pracovat s objekty pomocí přichycení k mřížce. Na panelu nástrojů **režimu editoru modelů** vyberte možnost **Přichytit** a povolte (nebo zakažte) přichycení k mřížce. Pokud je povolena možnost přichycení k mřížce, jsou přednastaveny omezené přírůstky pro posunutí, otočení a změnu velikosti.

### <a name="working-with-the-pivot-point"></a>Práce s bodem otáčení
 Bod otáčení objektu definuje jeho střed rotace a změnu měřítka. Bod otáčení objektu můžete změnit, abyste změnili způsob, jak je objekt ovlivněn transformacemi rotace a měřítka. Na panelu nástrojů **režimu editoru modelů** vyberte možnost **režim pivotu** , která povolí (nebo zakáže) režim pivotu. Pokud je povolen režim pivotu, zobrazí se v bodu otáčení vybraného projektu indikátor malé osy. Pak můžete pomocí nástrojů pro **posunutí** a **otočení** manipulovat s bodem otáčení.

 Ukázku, která ukazuje, jak použít bod otáčení, naleznete v tématu [How to: Modify a body pivot of a 3D model](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Globální a místní režimy
 K překladu a rotaci může dojít buď v místním systémovém systému (nebo v *místním referenčním rámci*) objektu, nebo v souřadnicovém systému celého světa (nebo *světa referenčního rámce*). Otáčení globálního referenčního snímku je nezávislé na otáčení objektu. Výchozí nastavení je místní režim. Pokud chcete povolit (nebo zakázat) režim světa, klikněte na panelu nástrojů **režimu editoru modelů** na tlačítko **WorldLocal** .

### <a name="modifying-objects"></a><a name="ModifyingObjects"></a> Úprava objektů
 Tvar 3D objektu můžete změnit přesunutím nebo odstraněním jeho vrcholů, hran a ploch. Ve výchozím nastavení je Editor modelů v *režimu objektů*, takže můžete vybrat a transformovat celé objekty. Pokud chcete vybrat body, okraje nebo plochy, zvolte příslušný režim výběru. Na panelu nástrojů **režim editoru modelů** zvolte možnost **režimy výběru**a pak zvolte požadovaný režim.

 Vyloučením nebo dělením můžete vytvořit další vrcholy. Vyloučení duplikuje vrcholy plochy (koplanární sadu vrcholů), které zůstávají spojeny duplikovanými vrcholy. Dělení přidá vrcholy pro vytvoření několika ploch tam, kde byla dříve jen jedna. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy. V obou případech můžete nové vrcholy posunout, otočit a změnit jejich velikost, čímž změníte geometrii celého objektu.

##### <a name="to-extrude-a-face-from-an-object"></a>Vyloučení plochy z objektu

1. V režimu výběru plochy vyberte plochu, kterou chcete vyloučit.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **vytlačení**.

##### <a name="to-subdivide-faces"></a>Rozdělení ploch

1. V režimu výběru plochy vyberte plochy, které chcete rozdělit. Protože rozdělení vytváří nová data hrany, rozdělení všech ploch současně poskytuje konzistentnější výsledky, když plochy sousedí.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **rozdělit**.

   Můžete také triangulovat plochy, sloučit objekty a převést mnohoúhelníkové výběry do nových objektů. Triangulace vytvoří další hrany, takže jiné než trojúhelníkové plochy jsou převedeny na optimální počet trojúhelníků; neposkytuje však další podrobnosti o geometrii. Slučování kombinuje vybrané objekty do jednoho objektu. Nové objekty je možné vytvořit pomocí mnohoúhelníkového výběru.

##### <a name="to-triangulate-a-face"></a>Postup triangulace plochy

1. V režimu výběru plochy vyberte plochu, kterou chcete triangulovat.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **triangulovat**.

##### <a name="to-merge-objects"></a>Sloučení objektů

1. V režimu výběru objektů vyberte objekty, které chcete sloučit.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **Sloučit objekty**.

##### <a name="to-create-an-object-from-a-polygon-selection"></a>Vytvoření objektu z mnohoúhelníkového výběru

1. V režimu výběru plochy vyberte plochy, ze kterých chcete vytvořit nový objekt.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **nástroje**, **vytvořit nový objekt z mnohoúhelníkového výběru**.

### <a name="working-with-materials-and-shaders"></a>Práce s materiály a shadery
 Vzhled objektu je určen interakcí osvětlení scény a materiálu objektu. Materiály jsou definovány vlastnostmi, které popisují, jak povrch reaguje na různé typy světla, a programem shader, který vypočítá konečnou barvu každého obrazového bodu na povrchu objektu na základě informací o osvětlení, map textur, map normál a dalších dat.

 Editor modelů poskytuje tyto výchozí materiály:

|Materiál|Popis|
|--------------|-----------------|
|Ztemnit|Vykreslí povrch bez jakéhokoli simulovaného světla.|
|Lambert|Vykreslí povrch se simulovaným osvětlením okolí a difúzním světlem.|
|Phong|Vykreslí povrch se simulovaným osvětlením okolí, difúzním světlem a se zrcadlovými světly.|

 Každý z těchto materiálů použije jednu texturu na povrch objektu. Můžete nastavit různé textury pro každý objekt, který používá materiál.

 Pokud chcete upravit, jak daný objekt reaguje na různé zdroje světla ve scéně, můžete změnit vlastnosti osvětlení materiálu nezávisle na jiných objektech, které materiál používají. Tato tabulka popisuje běžné vlastnosti osvětlení:

|Vlastnost osvětlení|Popis|
|-----------------------|-----------------|
|Okolní|Popisuje, jakým způsobem je povrch ovlivněn okolním osvětlením.|
|Rozptýlené|Popisuje, jakým způsobem je povrch ovlivněn směrovými a bodovými světly.|
|Zářivé|Popisuje, jak povrch vyzařuje světlo, nezávisle na ostatním osvětlení.|
|Odlesk|Popisuje, jakým způsobem povrch odráží směrová a bodová světla.|
|Síla odlesku|Popisuje šířku a intenzitu odlesků.|

 V závislosti na tom, co materiál podporuje, můžete změnit jeho vlastnosti osvětlení, textury a další data. V režimu **výběru** vyberte objekt, jehož materiál chcete změnit, a poté v okně **vlastnosti** změňte vlastnost **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**nebo jiná dostupná vlastnost. Materiál může vystavit až osm textur, jejichž vlastnosti se pojmenují postupně z **Texture1** na **Texture8**.

 Chcete-li odebrat všechny materiály z objektu, na panelu nástrojů **editoru modelů** vyberte možnost **skripty**, **materiály**, **Odebrat materiály**.

 Můžete použít **Návrháře shaderu** k vytvoření vlastních materiálů shaderu, které lze použít na objekty ve 3D scéně. Informace o tom, jak vytvořit vlastní materiály shaderu, najdete v tématu [Shader Designer](../designers/shader-designer.md). Informace o tom, jak použít vlastní materiál shaderu pro objekt, naleznete v tématu [How to: Apply shader to a 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Správa scény
 Scény můžete spravovat jako hierarchii objektů. Pokud je v hierarchii uspořádáno více objektů, jakékoli posunutí, změna velikosti nebo otočení nadřazeného uzlu ovlivní také podřízené objekty. To je užitečné, když chcete vytvořit složité objekty nebo scény z více základních objektů.

 Pomocí okna **Osnova dokumentu** můžete zobrazit hierarchii scény a vybrat uzly scény. Když vyberete uzel v osnově, můžete použít okno **vlastnosti** a upravit jeho vlastnosti.

 Hierarchii objektů můžete vytvořit buď tím, že jeden z nich stanovíte nadřazený ostatním, nebo jejich seskupením společně jako uzly na stejné úrovni zástupného symbolu, které fungují jako nadřazené.

##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Vytvoření hierarchie, která má nadřazený objekt

1. V režimu **výběru** vyberte dva nebo více objektů. První, který vyberete, bude nadřazený objekt.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **Správa scén**, **připojit k nadřazenému**.

##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Vytvoření hierarchie objektů na stejné úrovni

1. V režimu **výběru** vyberte dva nebo více objektů. Vytvoří se zástupný objekt, který se stane jejich nadřazeným objektem.

2. Na panelu nástrojů **editoru modelů** vyberte možnosti **skripty**, **Správa scén**, **vytvořit skupinu**.

   Editor modelů používá k identifikaci prvního vybraného objektu, který se stane nadřazeným, bílý objekt wireframe. Ostatní objekty ve výběru mají modrý objekt wireframe. Ve výchozím nastavení nejsou uzly zástupných symbolů zobrazeny. Chcete-li zobrazit zástupné uzly, na panelu nástrojů **editoru modelů** vyberte možnost **skripty**, **Správa scén**, **Zobrazit zástupné uzly**. S uzly zástupných symbolů můžete pracovat stejně jako při práci s objekty bez zástupných symbolů.

   Chcete-li odebrat přidružení typu nadřazený-podřízený mezi dvěma objekty, vyberte podřízený objekt a poté na panelu nástrojů **editoru modelů** zvolte možnost **skripty**, **Správa scén**, **Odpojit od nadřazené položky**. Pokud odpojíte od podřízeného objektu nadřazený, podřízený objekt se stane kořenovým objektem scény.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------|------------------------|
|Přepnout na režim **výběru**|Ctrl+G, Gtrl+Q<br /><br /> S|
|Přepnout do režimu **lupy**|Ctrl+G, Ctrl+Z<br /><br /> Z|
|Přepnout do režimu **posouvání**|Ctrl+G, Ctrl+P<br /><br /> K|
|Vybrat vše|Ctrl+A|
|Odstranit aktuální výběr|Odstranit|
|Zrušit aktuální výběr|Escape|
|Přiblížit|Kolečko myši dopředu<br /><br /> Ctrl + kolečko myši dopředu<br /><br /> Shift + kolečko myši dopředu<br /><br /> Ctrl+PageUp<br /><br /> Znaménko plus (+)|
|Oddálit|Kolečko myši dozadu<br /><br /> Ctrl + kolečko myši dozadu<br /><br /> Shift + kolečko myši dozadu<br /><br /> Ctrl+PageDown<br /><br /> Znaménko minus (-)|
|Posunout kameru nahoru|PageDown|
|Posunout kameru dolů|PageUp|
|Posunout kameru vlevo|Kolečko myši doleva<br /><br /> Ctrl+PageDown|
|Posunout kameru vpravo|Kolečko myši doprava<br /><br /> Ctrl+PageDown|
|Zobrazit horní stranu modelu|Ctrl+L, Ctrl+T<br /><br /> T|
|Zobrazit spodní stranu modelu|Ctrl+L, Ctrl+U|
|Zobrazit levou stranu modelu|Ctrl+L, Ctrl+L|
|Zobrazit pravou stranu modelu|Ctrl+L, Ctrl+R|
|Zobrazit čelní stranu modelu|Ctrl+L, Ctrl+F|
|Zobrazit zadní stranu modelu|Ctrl+L, Ctrl+B|
|Orámovat objekt v okně|F|
|Přepnout režim wireframe|Ctrl+L, Ctrl+W|
|Přepnout přichycení k mřížce|Ctrl+G, Ctrl+N|
|Přepnout režim pivotu|Ctrl+G, Ctrl+V|
|Přepnout omezení osy x|Ctrl+L, Ctrl+X|
|Přepnout omezení osy y|Ctrl+L, Ctrl+Y|
|Přepnout omezení osy z|Ctrl+L, Ctrl+Z|
|Přepnout do režimu posunutí|Ctrl+G, Ctrl+W<br /><br /> W|
|Přepnout do režimu měřítka|Ctrl+G, Ctrl+E<br /><br /> E|
|Přepnout do režimu otočení|Ctrl+G, Ctrl+R<br /><br /> R|
|Přepnout do režimu výběru bodu|Ctrl+L, Ctrl+1|
|Přepnout do režimu výběru okrajů|Ctrl+L, Ctrl+2|
|Přepnout do režimu výběru ploch|Ctrl+L, Ctrl+3|
|Přepnout do režimu výběru objektů|Ctrl+L, Ctrl+4|
|Přepnout do režimu (kamera) orbit|Ctrl+G, Ctrl+O|
|Vybrat další objekt na scéně|Karta|
|Vybrat předchozí objekt na scéně|Shift+Tab|
|Manipulovat s vybraným objektem na základě aktuálního nástroje|Klávesy se šipkami|
|Deaktivovat aktuální manipulátor|Q|
|Otočit kameru|Alt + přetažení levým tlačítkem myši|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů, které lze použít pro práci s grafickými prostředky, jako jsou textury a obrázky, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor obrázků pro práci s texturami a obrázky.|
|[Návrhář shaderu](../designers/shader-designer.md)|Popisuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Návrháře shaderu pro práci s shadery.|
