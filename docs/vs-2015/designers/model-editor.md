---
title: Editor modelů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e947793dff1f0068c1341ba6b70c21df07463f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844082"
---
# <a name="model-editor"></a>Editor modelů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje, jak pracovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru modelů pro zobrazení, vytváření a upravování 3D modelů.  
  
 Editor modelů můžete použít k vytvoření základních 3D modelů od začátku nebo k zobrazení a úpravám složitějších 3D modelů, které byly vytvořeny pomocí plnohodnotných nástrojů pro 3D modelování. Editor modelů podporuje několik formátů 3D modelů, které jsou používány při vývoji aplikace v rozhraní DirectX.  
  
## <a name="supported-formats"></a>Podporované formáty  
 Editor modelů podporuje tyto formáty modelů:  
  
|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, vytváření)|  
|-----------------|--------------------|-------------------------------------------------|  
|Soubor AutoDesk FBX Interchange|.fbx|Zobrazení, úpravy, vytváření|  
|Soubor DAE standardu Collada|.dae|Zobrazení, úpravy (změny DAE standardu Collada jsou uloženy ve formátu FBX.)|  
|OBJ|.obj|Zobrazení, úpravy (změny souborů OBJ jsou uloženy ve formátu FBX.)|  
  
## <a name="getting-started"></a>Začínáme  
 Tato část popisuje postup přidání 3D modelu do vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu a poskytuje základní informace potřebné pro zahájení práce.  
  
#### <a name="to-add-a-3-d-model-to-your-project"></a>Přidání 3D modelu do projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete přidat obrázek a klikněte na tlačítko **přidat**, **nová položka**.  
  
2.  V **přidat novou položku** dialogovém okně **nainstalováno**vyberte **grafiky**a pak vyberte **3D Scéna (.fbx)**.  
  
3.  Zadejte **název** souboru modelu a **umístění** místo se má vytvořit.  
  
4.  Zvolte **přidat** tlačítko.  
  
### <a name="axis-orientation"></a>Orientace osy  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podporuje všechny orientace 3D osy a načítá informace o orientaci OS z formátů souboru modelu, které ho podporují. Pokud není zadána žádná orientace osy, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve výchozím nastavení používá pravoruký systém souřadnic. **Indikátor osy** zobrazuje aktuální orientaci osy v pravém dolním rohu návrhové plochy. Na **indikátor osy**, představuje červená osu x, zelená představuje osy y a modrá osu z.  
  
### <a name="beginning-your-3-d-model"></a>Zahájení 3D modelu  
 V editoru modelů každý nový objekt vždy začíná jako jeden ze základních tvarů 3D, nebo *primitiv*– které jsou integrovány do editoru modelů. Chcete-li vytvořit nové a jedinečné objekty, přidáte ke scéně primitiv a změníte jeho tvar úpravou vrcholů. U složitých tvarů přidáte další vrcholy pomocí vysunutí nebo dílčího dělení a následnou úpravou. Informace o tom, jak ke scéně přidat objekt primitiva, naleznete v tématu [vytváření a import 3D objektů](#Adding3DObjects). Informace o tom, jak přidat další vrcholy objektu najdete v tématu [úprav objektů](#ModifyingObjects).  
  
## <a name="working-with-the-model-editor"></a>Práce s editorem modelů  
 Následující části popisují způsob použití editoru modelů pro práci s 3D modely.  
  
### <a name="model-editor-toolbars"></a>Panely nástrojů editoru modelů  
 Panely nástrojů Editoru modelů obsahují příkazy, které vám pomohou pracovat se 3D modely.  
  
 Příkazy, které ovlivňují stav editoru modelů jsou umístěny na **režim editoru modelů** nástrojů v hlavním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna. Nástroje pro modelování a skriptované příkazy jsou umístěny na **editoru modelů** nástrojů na návrhové ploše editoru modelů.  
  
 Tady je **režim editoru modelů** nástrojů:  
  
 ![Modální okno nástrojů Prohlížeč modelu. ](../designers/media/digit-mre-modal-toolbar.png "Číslice MRE modální okno nástrojů")  
  
 Tato tabulka popisuje položky panelu **režim editoru modelů** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny zleva doprava.  
  
|Položka na panelu nástrojů|Popis|  
|------------------|-----------------|  
|**Vyberte**|Umožňuje výběr bodů, okrajů, ploch nebo objektů ve scéně podle aktivního režimu výběru.|  
|**Posouvání**|Umožňuje pohyb 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením klávesy Ctrl aktivovat **Pan** dočasně režimu.|  
|**Přiblížení**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V **přiblížení** režimu, vyberte bod ve scéně a poté jej přesunutím vpravo dolů zvětšete nebo přesunutím vlevo či nahoru out.<br /><br /> V **vyberte** režimu, provést přiblížení nebo oddálení pomocí kolečka myši při stisknuté klávese Ctrl.|  
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:** tento režim nemá žádný vliv při **pravoúhle** projekce je povolená.|  
|**Globální místní**|Pokud je tato položka povolena, transformace na vybraném objektu pobíhají v globálním prostoru. Jinak transformace na vybraném objektu probíhají v místním prostoru.|  
|**Režim pivotu**|Pokud je tato položka povolena, transformace ovlivní umístění a orientaci ovládacího prvku *bodu otáčení* vybraného objektu (bod otáčení definuje střed operací překladu, měřítko a otočení). Transformace jinak ovlivní umístění a orientaci geometrie objektu ve vztahu k bodu otáčení.|  
|**Uzamknout osu X**|Omezuje manipulaci s objekty na ose x. Platí pouze při použití prostřední části pomůcky manipulátoru.|  
|**Uzamknout osu Y**|Omezuje manipulaci s objekty na ose y. Platí pouze při použití prostřední části pomůcky manipulátoru.|  
|**Uzamknout osu Z**|Omezuje manipulaci s objekty na ose z. Platí pouze při použití prostřední části pomůcky manipulátoru.|  
|**Orámovat objekt**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|  
|**Zobrazení**|Nastaví orientaci zobrazení. Zde jsou dostupné orientace:<br /><br /> **Přední**<br /> Umístí zobrazení před scénu.<br /><br /> **Zpět**<br /> Umístí zobrazení za scénu.<br /><br /> **doleva**<br /> Umístí zobrazení vlevo od scény.<br /><br /> **doprava**<br /> Umístí zobrazení vpravo od scény.<br /><br /> **nahoru**<br /> Umístí zobrazení nad scénu.<br /><br /> **dolní**<br /> Umístí zobrazení pod scénu. **Poznámka:** Toto je jediný způsob, jak změnit směr zobrazení při **pravoúhle** projekce je povolená.|  
|**Projekce**|Nastaví druh projekce použitý pro vykreslení scény. Zde jsou dostupné projekce:<br /><br /> **Perspektivy**<br /> V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.<br /><br /> **Pravoúhlé**<br /> V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když **pravoúhle** projekce je povolená, nemůžete použít **obíhání** režim zobrazení.|  
|**Styl kreslení**|Nastaví, jak jsou objekty ve scéně vykresleny. Zde jsou dostupné styly:<br /><br /> **Drátový model**<br /> Je-li tato možnost povolena, objekty jsou vykresleny jako objekty wireframe.<br /><br /> **Overdraw**<br /> Pokud je tato možnost povolena, objekty jsou vykreslovány pomocí doplňkového prolnutí. Tuto možnost můžete použít k zobrazení rozsahu překreslování, ke kterému dochází na scéně.<br /><br /> **Plochý stín**<br /> Je-li tato možnost povolena, objekty jsou vykreslovány základním světelným modelem s plochým stínem. Tuto možnost můžete použít k jednoduššímu zobrazení ploch objektu.<br /><br /> Pokud žádná z těchto možností není povolena, každý objekt je vykreslen pomocí materiálu, který je na něj použit.|  
|**Režim vykreslování v reálném čase**|Pokud je povoleno vykreslení v reálném čase, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] překreslí plochu návrhu, i když je provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|  
|**Přepnout mřížku**|Po povolení této položky se zobrazí mřížka. Jinak se mřížka nezobrazí.|  
|**Panel nástrojů**|Střídavě zobrazí a skryje **nástrojů**.|  
|**Osnova dokumentu**|Střídavě zobrazí a skryje **Osnova dokumentu** okna.|  
|**Vlastnosti**|Střídavě zobrazí a skryje **vlastnosti** okna.|  
|**Pokročilé**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Grafické moduly**<br /><br /> **Vykreslení s D3D11**<br /> Používá rozhraní Direct3D 11 k vykreslení plochy návrhu editoru modelů.<br /><br /> **Vykreslení s D3D11WARP**<br /> Používá rozhraní Direct3D 11 WARP (Windows Advanced Rasterization Platform) k vykreslení plochy návrhu editoru modelů.<br /><br /> **Správa scény**<br /><br /> **Import**<br /> Importuje objekty z jiného souboru 3D modelu do aktuální scény.<br /><br /> **Připojit k nadřazenému**<br /> Určí první z více vybraných objektů jako nadřazený objekt zbývajících vybraných objektů.<br /><br /> **Odpojit od nadřazeného**<br /> Odpojí vybraný objekt od nadřazeného objektu. Vybraný objekt se stane *kořenový objekt* ve scéně. Kořenový objekt nemá nadřazený objekt.<br /><br /> **Vytvoření skupiny**<br /> Seskupí vybrané objekty na stejné úrovni.<br /><br /> **Sloučit objekty**<br /> Kombinuje vybrané objekty do jednoho objektu.<br /><br /> **Vytvořit nový objekt z mnohoúhelníkového výběru**<br /> Odebere vybrané plochy z aktuálního objektu a přidá na scénu nový objekt, který tyto plochy obsahuje.<br /><br /> **Nástroje**<br /><br /> **Převrátit Obtáčení mnohoúhelníků**<br /> Převrátí vybrané mnohoúhelníky tak, že jejich pořadí obtáčení a normála povrchu se převrátí.<br /><br /> **Odebrat všechny animace**<br /> Odebere data animace z objektů.<br /><br /> **Triangulovat**<br /> Převede vybraný objekt na trojúhelníky.<br /><br /> **Zobrazení**<br /><br /> Odstranění odvrácených stran<br /> Povolí nebo zakáže odstranění odvrácených stran.<br /><br /> **Snímková frekvence**<br /> Zobrazí frekvenci snímků v pravém horním rohu plochy návrhu. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu.<br /><br /> Tato možnost je užitečná, když povolíte **režim vykreslování v reálném čase** možnost.<br /><br /> **Zobrazit vše**<br /> Zobrazí všechny objekty ve scéně. To obnoví **skryté** vlastnost každého objektu na **False**.<br /><br /> **Zobrazit normály povrchu**<br /> Zobrazí normály pro každou plochu.<br /><br /> **Zobrazit chybějící materiály**<br /> Zobrazí speciální texturu u objektů, ke kterým není přiřazen materiál.<br /><br /> **Zobrazit bod otáčení**<br /> Povolí nebo zakáže zobrazení značky na osách 3D v bodě otáčení aktivního výběru.<br /><br /> **Zobrazit uzly zástupných symbolů**<br /> Zobrazí zástupné uzly. Zástupný uzel je vytvořen při seskupení objektů.<br /><br /> **Zobrazit normály vrcholů**<br /> Zobrazí normálu každého vrcholu. **Tip:** můžete použít **skripty** tlačítko znovu spustit poslední skript.|  
  
 Tady je **editoru modelů** nástrojů:  
  
 ![Model nástrojů prohlížeče](../designers/media/digit-mre-toolbar.png "číslice. MRE nástrojů")  
  
 Následující tabulka popisuje položky panelu **editoru modelů** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny shora dolů.  
  
|Položka na panelu nástrojů|Popis|  
|------------------|-----------------|  
|**Překlad**|Posune výběr.|  
|**Škálování**|Změní velikost výběru.|  
|**Otočit o**|Otočí výběr.|  
|**Vybrat bod**|Nastaví **režim výběru** k výběru jednotlivých bodů objektu.|  
|**Vybrat hranu**|Nastaví **režim výběru** k výběru hrany (čáry mezi dvěma vrcholy) na objekt.|  
|**Vybrat plochu**|Nastaví **režim výběru** k výběru plochy objektu.|  
|**Vyberte objekt**|Nastaví **režim výběru** k výběru celého objektu.|  
|**Vyloučit**|Vytvoří další plochu a připojí ji k vybrané ploše.|  
|**Rozdělit**|Rozdělí každou vybranou plochu na více ploch. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy.|  
  
### <a name="controlling-the-view"></a>Ovládání zobrazení  
 3D scéna je vykreslena podle zobrazení, které si lze představit jako virtuální fotoaparát obsahující umístění a orientaci. Chcete-li změnit umístění a orientaci, použijte ovládací prvky zobrazení na **režim editoru modelů** nástrojů.  
  
 Následující tabulka popisuje primární ovládací prvky zobrazení.  
  
|Ovládací prvek zobrazení|Popis|  
|------------------|-----------------|  
|**Posouvání**|Umožňuje pohyb 3D scény relativně k rámu okna. K posouvání vyberte bod ve scéně a pohybujte jím.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením klávesy Ctrl aktivovat **Pan** dočasně režimu.|  
|**Přiblížení**|Umožňuje zobrazení více či méně detailů scény relativně k rámu okna. V **přiblížení** režimu, vyberte bod ve scéně a poté jej přesunutím vpravo dolů zvětšete nebo přesunutím vlevo či nahoru out.<br /><br /> V **vyberte** režimu, provést přiblížení nebo oddálení pomocí kolečka myši při stisknuté klávese Ctrl.|  
|**Obíhání**|Umístí zobrazení na kruhovou dráhu okolo vybraného objektu. Pokud není vybrán žádný objekt, středem trasy je počátek scény. **Poznámka:** tento režim nemá žádný vliv při **pravoúhle** projekce je povolená.|  
|**Orámovat objekt**|Orámuje vybraný objekt, aby se nacházel ve středu zobrazení.|  
  
 Zobrazení je vytvořeno virtuálním fotoaparátem, ale je také definováno projekcí. Projekce definuje, jaké tvary a objekty v zobrazení jsou přeloženy do pixelů na povrchu návrhu. Na **editoru modelů** nástrojů, můžete použít buď **perspektivy** nebo **pravoúhle** projekce.  
  
|Projekce|Popis|  
|----------------|-----------------|  
|**Perspektivy**|V perspektivní projekci se objekty více vzdálené od bodu pozorování zdají být menší a sbíhají se k jednomu vzdálenému bodu.|  
|**Pravoúhlé**|V pravoúhlé projekci se objekty jeví jako stejně velké bez ohledu na jejich vzdálenost od bodu pozorování. Není zobrazena žádná konvergence. Když **pravoúhle** projekce je povolená, nemůžete použít **obíhání** režim zobrazení.|  
  
 Může být užitečné zobrazit 3D scénu ze známého umístění a úhlu, například když chcete porovnat dvě podobné scény. V tomto scénáři editor modelů poskytuje několik předdefinovaných zobrazení. Použití předdefinované zobrazení na **režim editoru modelů** nástrojů, zvolte **zobrazení**a poté zvolte požadované předdefinované zobrazení chcete – přední, zadní, levé, pravé, top a bottom. V těchto zobrazeních virtuální kamera snímá přímo počátek scény. Například, pokud se rozhodnete **zobrazit Vrch**, virtuální kamera se podívá na počátek scény z přímo nad ním.  
  
### <a name="viewing-additional-geometry-details"></a>Zobrazení dalších podrobností o geometrii  
 Pro lepší pochopení 3D objektu nebo scény můžete zobrazit další podrobnosti geometrie, jako jsou normály pro každý vrchol, normály pro každou plochu, body otáčení aktivního výběru a další podrobnosti. Povolit nebo zakázat, na **editoru modelů** nástrojů, zvolte **skripty**, **zobrazení**a pak zvolte ten, který chcete.  
  
###  <a name="Adding3DObjects"></a> Vytváření a import 3D objektů  
 Přidat předdefinovaný 3D tvar do scény v **nástrojů**, vybrat ta, kterou chcete a přesuňte jej na návrhovou plochu. Nové tvary jsou umístěny v počátku scény. Editor modelů obsahuje sedm tvarů: **kužel**, **datové krychle**, **válcový**, **disk**, **roviny**,  **Sphere**, a **čajovou Konvici**.  
  
 Pro import 3D objekt ze souboru, na **editoru modelů** nástrojů, zvolte **Upřesnit**, **Správa scén**, **importovat**a poté zadejte soubor, který chcete importovat.  
  
### <a name="transforming-objects"></a>Transformace objektů  
 Je možné *transformace* objekt změnou jeho **otočení**, **škálování**, a **překlad** vlastnosti. *Otočení* orientuje objekt průběžným otáčením kolem osy x, y a osy z definovaných jejich bodem otáčení. Každá specifikace otočení má tři komponenty – x, y a z v uvedeném pořadí – které jsou zadány ve stupních. **Škálování** změní velikost objektu jeho roztažením o zadaný faktor podél jedné nebo více OS se středem v jeho bodě otáčení. *Překlad* vyhledá objekt v 3rozměrného prostoru relativně k nadřazenému objektu namísto jeho bodu otáčení.  
  
 Objekt můžete transformovat pomocí nástrojů pro modelování nebo nastavením vlastností.  
  
##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Transformace objektu pomocí nástrojů pro modelování  
  
1.  V **vyberte** režimu, vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.  
  
2.  Na **editoru modelů** nástrojů, zvolte **přeložit**, **škálování**, nebo **otočit** nástroj. Pro vybraný objekt se zobrazí otočení, změna velikosti nebo manipulátor otočení.  
  
3.  K provedení transformace použijte manipulátor. Pro transformace otočení a změny velikosti je manipulátor indikátorem osy. Najednou můžete změnit jen jednu osu nebo všechny osy současně pomocí bílé krychle ve středu indikátoru. Pro otáčení je manipulátor koule tvořená kruhy s kódováním barev, které odpovídají osám x (červená), y (zelená) a z (modrá). K vytvoření požadovaného otočení je třeba změnit každou osu jednotlivě.  
  
##### <a name="to-transform-an-object-by-setting-its-properties"></a>Transformace objektu nastavením jeho vlastností  
  
1. V **vyberte** režimu, vyberte objekt, který chcete transformovat. Překrytí wireframe udává, že objekt je vybrán.  
  
2. V **vlastnosti** okno, zadejte hodnoty **otočení**, **škálování**, a **překlad** vlastnosti.  
  
   > [!IMPORTANT]
   >  Pro **otočení** vlastnost, zadejte úhel otočení kolem každé ze tří OS. Otáčení probíhá postupně. Ujistěte se tedy, že je otáčení správně naplánováno nejprve podle osy x, poté y a poté z.  
  
   Použitím nástrojů modelování můžete vytvářet transformace rychle, ale nikoli přesně. Nastavením vlastností objektu můžete určit transformace přesně, ale nikoli rychle. Doporučujeme použít nástroje modelování tak, abyste se dostali „dostatečně blízko“ k požadovaným transformacím, a poté doladit hodnoty vlastností.  
  
   Pokud nechcete použít manipulátory, můžete povolit režim volného tvaru. Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **manipulace ve volném tvaru** chcete povolit (nebo zakázat) režim volného tvaru. V režimu volného tvaru můžete začít manipulaci v libovolném bodě plochy návrhu namísto bodu manipulátoru. V režimu volného tvaru můžete omezit změny některých os zamčením těch, které nechcete změnit. Na **režim editoru modelů** nástrojů, zvolte libovolnou kombinaci **zámek X**, **zámek Y**, a **zámek Z** tlačítka.  
  
   Může být výhodné pracovat s objekty pomocí přichycení k mřížce. Na **režim editoru modelů** nástrojů, zvolte **Přichytit** chcete povolit (nebo zakázat) přichycení k mřížce. Pokud je povolena možnost přichycení k mřížce, jsou přednastaveny omezené přírůstky pro posunutí, otočení a změnu velikosti.  
  
### <a name="working-with-the-pivot-point"></a>Práce s bodem otáčení  
 Bod otáčení objektu definuje jeho střed rotace a změnu měřítka. Bod otáčení objektu můžete změnit, abyste změnili způsob, jak je objekt ovlivněn transformacemi rotace a měřítka. Na **režim editoru modelů** nástrojů, zvolte **režim Pivotu** chcete povolit (nebo zakázat) režim pivotu. Pokud je povolen režim pivotu, zobrazí se v bodu otáčení vybraného projektu indikátor malé osy. Pak můžete použít **překlad** a **otočení** nástroje pro manipulaci s bodem otáčení.  
  
 Ukázku použití bodu otáčení, naleznete v tématu [postupy: Změna bodu otáčení 3D modelu](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).  
  
### <a name="world-and-local-modes"></a>Globální a místní režimy  
 Posunutí a otočení lze provést buď v místním souřadnicovém systému (nebo *místní snímek referenčního*) objektu, nebo systém souřadnic světa (nebo *world rámce referenčního*). Otáčení globálního referenčního snímku je nezávislé na otáčení objektu. Výchozí nastavení je místní režim. Chcete-li povolit (nebo zakázat) globální režim na **režim editoru modelů** nástrojů, zvolte **WorldLocal** tlačítko.  
  
###  <a name="ModifyingObjects"></a> Změny objektů  
 Tvar 3D objektu můžete změnit přesunutím nebo odstraněním jeho vrcholů, hran a ploch. Ve výchozím nastavení je Editor modelů v *režimu objektu*, takže můžete vybírat a transformovat celé objekty. Pokud chcete vybrat body, okraje nebo plochy, zvolte příslušný režim výběru. Na **režim editoru modelů** nástrojů, zvolte **režimy výběru**a pak zvolte režim, ve kterém chcete.  
  
 Vyloučením nebo dělením můžete vytvořit další vrcholy. Vyloučení duplikuje vrcholy plochy (koplanární sadu vrcholů), které zůstávají spojeny duplikovanými vrcholy. Dělení přidá vrcholy pro vytvoření několika ploch tam, kde byla dříve jen jedna. Pro vytvoření nových ploch se přidají nové vrcholy – jeden uprostřed původní plochy a jeden uprostřed každé hrany – které jsou poté spojeny s původními vrcholy. Počet přidaných ploch se rovná počtu hran původní plochy. V obou případech můžete nové vrcholy posunout, otočit a změnit jejich velikost, čímž změníte geometrii celého objektu.  
  
##### <a name="to-extrude-a-face-from-an-object"></a>Vyloučení plochy z objektu  
  
1.  V režimu výběru plochy vyberte plochu, kterou chcete vyloučit.  
  
2.  Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **vyloučit**.  
  
##### <a name="to-subdivide-faces"></a>Rozdělení ploch  
  
1. V režimu výběru plochy vyberte plochy, které chcete rozdělit. Protože rozdělení vytváří nová data hrany, rozdělení všech ploch současně poskytuje konzistentnější výsledky, když plochy sousedí.  
  
2. Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **rozdělit**.  
  
   Můžete také triangulovat plochy, sloučit objekty a převést mnohoúhelníkové výběry do nových objektů. Triangulace vytvoří další hrany, takže jiné než trojúhelníkové plochy jsou převedeny na optimální počet trojúhelníků; neposkytuje však další podrobnosti o geometrii. Slučování kombinuje vybrané objekty do jednoho objektu. Nové objekty je možné vytvořit pomocí mnohoúhelníkového výběru.  
  
##### <a name="to-triangulate-a-face"></a>Postup triangulace plochy  
  
1.  V režimu výběru plochy vyberte plochu, kterou chcete triangulovat.  
  
2.  Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **Triangulovat**.  
  
##### <a name="to-merge-objects"></a>Sloučení objektů  
  
1.  V režimu výběru objektů vyberte objekty, které chcete sloučit.  
  
2.  Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **sloučit objekty**.  
  
##### <a name="to-create-an-object-from-a-polygon-selection"></a>Vytvoření objektu z mnohoúhelníkového výběru  
  
1.  V režimu výběru plochy vyberte plochy, ze kterých chcete vytvořit nový objekt.  
  
2.  Na **editoru modelů** nástrojů, zvolte **skripty**, **nástroje**, **vytvořit nový objekt z mnohoúhelníkového výběru**.  
  
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
  
 V závislosti na tom, co materiál podporuje, můžete změnit jeho vlastnosti osvětlení, textury a další data. V **vyberte** režimu, vyberte objekt, jehož materiál chcete změnit, a pak v **vlastnosti** okno Změnit **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, nebo jinou dostupnou vlastnost. Materiál může vystavit až osm textur, jejichž vlastnosti jsou postupně pojmenované od **Texture1** k **textura8**.  
  
 Odebrat všechny materiály z objektu, na **editoru modelů** nástrojů, zvolte **skripty**, **materiály**, **odebrat materiály**.  
  
 Můžete použít **návrháře shaderu** k tvorbě vlastních materiálů shaderu, které lze aplikovat na objekty ve 3D scéně. Informace o vytváření vlastních uživatelských materiálů shader naleznete v tématu [návrháře shaderu](../designers/shader-designer.md). Informace o tom, jak používat vlastního materiálu shaderu na objekt, najdete v části [postupy: použití shaderu na 3D Model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
### <a name="scene-management"></a>Správa scény  
 Scény můžete spravovat jako hierarchii objektů. Pokud je v hierarchii uspořádáno více objektů, jakékoli posunutí, změna velikosti nebo otočení nadřazeného uzlu ovlivní také podřízené objekty. To je užitečné, když chcete vytvořit složité objekty nebo scény z více základních objektů.  
  
 Můžete použít **Osnova dokumentu** okno k zobrazení hierarchie scény a výběru uzlů scény. Při výběru uzlu osnovy můžete použít **vlastnosti** okna k úpravě jeho vlastností.  
  
 Hierarchii objektů můžete vytvořit buď tím, že jeden z nich stanovíte nadřazený ostatním, nebo jejich seskupením společně jako uzly na stejné úrovni zástupného symbolu, které fungují jako nadřazené.  
  
##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Vytvoření hierarchie, která má nadřazený objekt  
  
1.  V **vyberte** režimu, vyberte dvě nebo více objektů. První, který vyberete, bude nadřazený objekt.  
  
2.  Na **editoru modelů** nástrojů, zvolte **skripty**, **Správa scén**, **připojit k nadřazenému**.  
  
##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Vytvoření hierarchie objektů na stejné úrovni  
  
1. V **vyberte** režimu, vyberte dvě nebo více objektů. Vytvoří se zástupný objekt, který se stane jejich nadřazeným objektem.  
  
2. Na **editoru modelů** nástrojů, zvolte **skripty**, **Správa scén**, **vytvořit skupinu**.  
  
   Editor modelů používá k identifikaci prvního vybraného objektu, který se stane nadřazeným, bílý objekt wireframe. Ostatní objekty ve výběru mají modrý objekt wireframe. Ve výchozím nastavení nejsou uzly zástupných symbolů zobrazeny. Chcete-li zobrazit uzly zástupných symbolů, na **editoru modelů** nástrojů, zvolte **skripty**, **Správa scén**, **zobrazit uzly zástupných symbolů**. S uzly zástupných symbolů můžete pracovat stejně jako při práci s objekty bez zástupných symbolů.  
  
   Odebrat přidružení nadřazený podřízený mezi dvěma objekty, vyberte podřízený objekt a potom na **editoru modelů** nástrojů, zvolte **skripty**, **Správa scén**, **Odpojit od nadřazeného**. Pokud odpojíte od podřízeného objektu nadřazený, podřízený objekt se stane kořenovým objektem scény.  
  
## <a name="keyboard-shortcuts"></a>Klávesové zkratky  
  
|Příkaz|Klávesové zkratky|  
|-------------|------------------------|  
|Přepnout na **vyberte** režimu|Ctrl+G, Gtrl+Q<br /><br /> S|  
|Přepnout na **přiblížení** režimu|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Přepnout na **Pan** režimu|Ctrl+G, Ctrl+P<br /><br /> K|  
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
|Vybrat další objekt na scéně|Tabulátor|  
|Vybrat předchozí objekt na scéně|Shift+Tab|  
|Manipulovat s vybraným objektem na základě aktuálního nástroje|Klávesy se šipkami|  
|Deaktivovat aktuální manipulátor|Q|  
|Otočit kameru|Alt + přetažení levým tlačítkem myši|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Najdete zde přehled [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje, které můžete použít pro práci se zdroji grafiky například textury a obrázky, 3D modely a efekty shaderu.|  
|[Editor obrázků](../designers/image-editor.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor obrázků pro práci s texturami a obrázky.|  
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] návrháře shaderu pro práci se shadery.|



