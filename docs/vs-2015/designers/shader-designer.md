---
title: Návrhář shaderů | Dokumentace Microsoftu
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
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac752d0b85a45193fe4aafb55e33ec23e26aed6a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942007"
---
# <a name="shader-designer"></a>Návrhář shaderů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje, jak pracovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] návrháře shaderu k vytváření, úpravě a exportovat vlastní vizuální efekty, které jsou označovány jako *shadery*.  
  
 Návrháře shaderu můžete použít k vytvoření vlastní vizuálních efektů pro vaše hry nebo aplikace, i pokud si nejste jisti HLSL programování. V Návrháři shaderu vytvořit shader, stačí rozložení si to jako graf; To znamená, přidat na návrhovou plochu *uzly* , která představují data a operace a pak proveďte připojení mezi nimi k definování, jak operace zpracovat data. V každém uzlu operace je k dispozici ve verzi preview efekt až k danému bodu tak, aby můžete vizualizovat jeho výsledek. Data prochází uzly směrem k poslední uzel, který představuje výstup shaderu.  
  
## <a name="supported-formats"></a>Podporované formáty  
 Návrhář shaderu podporuje tyto formáty shaderu:  
  
|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, Export)|  
|-----------------|--------------------|-------------------------------------------------|  
|Orientovaný graf shaderu jazyka|.dgsl|Zobrazení pro úpravy|  
|Shader HLSL (zdrojového kódu)|.hlsl|Export|  
|Shader HLSL (bajtového kódu)|.CSO|Export|  
|Hlaviček jazyka C++ (pole bajtového kódu HLSL)|.h|Export|  
  
## <a name="getting-started"></a>Začínáme  
 Tato část popisuje, jak přidat DGSL shader, který má vaše [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu a poskytuje základní informace, které vám pomůžou začít.  
  
#### <a name="to-add-a-dgsl-shader-to-your-project"></a>Chcete-li přidat do projektu DGSL shader  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete přidat shader tak a klikněte na tlačítko **přidat**, **nová položka**.  
  
2.  V **přidat novou položku** dialogovém okně **nainstalováno**vyberte **grafiky**a pak vyberte **vizuální graf shaderu (.dgsl)**.  
  
3.  Zadejte **název** souboru shaderu a **umístění** místo se má vytvořit.  
  
4.  Zvolte **přidat** tlačítko.  
  
### <a name="the-default-shader"></a>Výchozí shader  
 Pokaždé, když vytvořte DGSL shader, začne jako minimální shader, který má právě **barva bodu** uzel, který je připojený k **konečnou barvu** uzlu. I když tento shader je úplné a funkční, mnoho neprovádí. Proto je prvním krokem při vytváření shaderu pracovní často odstranit **barva bodu** uzlu nebo odpojte ho od **konečnou barvu** uzel, aby uvolnil prostor pro další uzly.  
  
## <a name="working-with-the-shader-designer"></a>Práce s návrháře shaderu  
 Následující části popisují způsob použití návrháře shaderu pro práci se shadery vlastní.  
  
### <a name="shader-designer-toolbars"></a>Panely nástrojů návrháře shaderu  
 Návrháře shaderu, které obsahují panely nástrojů příkazy, které pomohou při práci s grafy DGSL shader.  
  
 Příkazy, které mají vliv na stav návrháře shaderu jsou umístěny na **režim návrháře shaderu** nástrojů v hlavním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna. Návrhářské nástroje a příkazy jsou umístěny na **návrháře shaderu** nástrojů na návrhové ploše návrháře shaderu.  
  
 Tady je **režim návrháře shaderu** nástrojů:  
  
 ![Modální okno nástrojů návrháře shaderu. ](../designers/media/digit-dsd-modal-toolbar.png "Číslice DSD modální okno nástrojů")  
  
 Tato tabulka popisuje položky panelu **režim návrháře shaderu** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny zleva doprava:  
  
|Položka na panelu nástrojů|Popis|  
|------------------|-----------------|  
|**Vyberte**|Umožňuje interakci s uzly a hran do grafu. V tomto režimu můžete vybrat uzly a přesunout nebo odstranit, a můžete vytvořit okraje nebo rozdělit je.|  
|**Posouvání**|Umožňuje pohyb graf shaderu relativně k rámu okna. K posouvání vyberte bod na návrhové ploše a pohybujte jím.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením klávesy Ctrl aktivovat **Pan** dočasně režimu.|  
|**Přiblížení**|Umožňuje zobrazení více či méně detailů graf shaderu relativně k rámu okna. V **přiblížení** režimu, vyberte bod na návrhové ploše a poté jej přesunutím vpravo dolů zvětšete nebo přesunutím vlevo či nahoru out.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením klávesy Ctrl přiblížení nebo oddálení použít kolečko myši.|  
|**Přizpůsobit zobrazení**|Zobrazí graf úplné shaderu v rámci okna.|  
|**Režim vykreslování v reálném čase**|Pokud je povoleno vykreslení v reálném čase, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] překreslí plochu návrhu, i když je provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|  
|**Náhled pomocí koule**|Při povolení modelu koule slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Náhled pomocí krychle**|Pokud povolená, model datové krychle se používá k náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Náhled pomocí válce**|Při povolení modelu válec slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Náhled pomocí kužele**|Při povolení modelu kužel slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Náhled pomocí čajové konvice**|Pokud povolená, modelu čajovou konvici slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Náhled pomocí roviny**|Při povolení modelu rovinou slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|  
|**Panel nástrojů**|Střídavě zobrazí a skryje **nástrojů**.|  
|**Vlastnosti**|Můžete také zobrazí nebo skryje **vlastnosti** okna.|  
|**Pokročilé**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Exportovat**: umožňuje exportovat shader v různých formátech.<br /><br /> **Exportovat jako**: Exportuje shaderu jako zdrojový kód buď HLSL nebo jako hodnota bytecode funkce shader kompilované. Další informace o tom, jak exportovat shader, naleznete v tématu [postupy: exportování shaderu](../designers/how-to-export-a-shader.md).<br /><br /> **Grafické moduly**: umožňuje výběr renderer, který se používá k zobrazení návrhové ploše.<br /><br /> **Vykreslení s D3D11**: používá rozhraní Direct3D 11 k vykreslení plochy návrhu Návrháře shaderu.<br /><br /> **Vykreslení s D3D11WARP**: používá rozhraní Direct3D 11 Windows Advanced Rasterizační platformě WARP () k vykreslení plochy návrhu Návrháře shaderu.<br /><br /> **Zobrazení**: umožňuje výběr další informace o návrháři shaderu.<br /><br /> **Frekvence snímků**: Pokud povolená, zobrazí aktuální frekvenci snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu.  Tato možnost je užitečná, když povolíte **režim vykreslování v reálném čase** možnost.|  
  
> [!TIP]
>  Můžete použít **Upřesnit** tlačítko poslední příkaz spustit znovu.  
  
### <a name="working-with-nodes-and-connections"></a>Práce s uzly a připojení  
 Použití **vyberte** režimu k přidání, odebrání, změna umístění, připojení a konfigurace uzlů. Tady je postup pro provádění těchto základních operací:  
  
##### <a name="to-perform-basic-operations-in-select-mode"></a>K provádění základních operací v režim výběru  
  
-   Tady je způsob:  
  
    -   Pokud chcete přidat uzel do grafu, vyberte ji v **nástrojů** a přesuňte jej na návrhovou plochu.  
  
    -   Odebrání uzlu z grafu, vyberte ji a stiskněte klávesu Delete.  
  
    -   Chcete-li změnit umístění uzlu, vyberte ho a přesuňte ho do nového umístění.  
  
    -   Pro připojení dvou uzlů, přesuňte výstupní terminál jednoho z uzlů do vstupní terminálu z jiného uzlu. Můžete připojit pouze terminály, které mají nekompatibilní typy. Čáry mezi terminály zobrazuje připojení.  
  
    -   Chcete-li odebrat připojení, na místní nabídku pro jednu z připojených terminály, zvolte **přerušit odkazy**.  
  
    -   Chcete-li konfigurovat vlastnosti uzlu, vyberte uzel a pak na **vlastnosti** okno, zadejte nové hodnoty pro vlastnosti.  
  
### <a name="previewing-shaders"></a>Zobrazení náhledu shaderů  
 Na vám pomohou pochopit, jak bude vypadat shaderu ve vaší aplikaci, můžete nakonfigurovat, jak je zobrazen váš vliv. K odhadu vaší aplikace, zvolte jeden z několika obrazců vykreslení textury a další parametry materiálu, povolit animace založené na čase efekty a konfigurovat zkontrolujte ve verzi preview z různých úhlů.  
  
#### <a name="shapes"></a>Obrazce  
 Návrháře shaderu obsahuje šest obrazce – kouli, datové krychle, válec, kužel, čajovou konvici a rovinou –, můžete použít k náhledu vašeho shaderu. V závislosti na shader určité tvary může získáte lepší náhled.  
  
###### <a name="to-choose-a-preview-shape"></a>Zvolit tvar náhled  
  
-   Na **režimy návrháře shaderu** nástrojů, zvolte na tvar, který chcete.  
  
####  <a name="WWS_MaterialParameters"></a> Textury a materiálu parametry  
 Mnoho shadery využívají textury a vlastností materiálu vytvořit jedinečný vzhled pro každý druh objektu ve vaší aplikaci. Zobrazíte vašeho shaderu bude vypadat ve vaší aplikaci můžete nastavit textury a vlastností materiálu, které slouží k vykreslení náhledu tak, aby odpovídaly textury a parametry, které můžete použít ve vaší aplikaci.  
  
###### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Svázat různé textury registr textur, nebo upravte ostatní parametry materiálu  
  
1. V **vyberte** režimu, vyberte prázdnou oblast návrhové plochy. To způsobí, že **vlastnosti** okno k zobrazení vlastností globální shaderu.  
  
2. V **vlastnosti** okno, zadejte nové hodnoty pro textury a parametru vlastnosti, které chcete změnit.  
  
   Tady jsou parametry shaderu, které můžete upravit:  
  
|Parametr|Vlastnosti|  
|---------------|----------------|  
|**Textura 1** – **Texture – 8**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Název souboru**: úplná cesta soubor textury, který je spojen s registrem textur.|  
|**Materiál okolí**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: rozptýlení barvy aktuálního pixelu kvůli nepřímé – nebo okolí – osvětlení.|  
|**Materiál rozptýlení**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.|  
|**Vyzařující materiál**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: podíl barvy aktuálního pixelu kvůli svým zadaná osvětlení.|  
|**Reflexní materiál**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|  
|**Materiál síla odlesku**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: exponent, který udává intenzitu zrcadlových odlesků na aktuální pixel.|  
  
#### <a name="time-based-effects"></a>Účinky podle času  
 Některé shadery mít komponentu podle času, která animuje efekt. Chcete-li zobrazit, jak účinek vypadá v praxi, verze preview musí být aktualizovány několikrát za sekundu. Ve výchozím nastavení ve verzi preview se aktualizují při změně shaderu; ke změně tohoto chování tak, aby se zobrazí podle času efekty, budete muset povolit vykreslování v reálném čase.  
  
###### <a name="to-enable-real-time-rendering"></a>Chcete povolit vykreslování v reálném čase  
  
-   Na panelu nástrojů návrháře shaderu zvolte **vykreslování v reálném čase**.  
  
#### <a name="examining-the-effect"></a>Zkoumání efekt  
 Mnoho shadery jsou ovlivněny proměnných, například zobrazení úhel nebo směrové světlo. Prozkoumat, jak reagovat účinek se tyto proměnné, můžete volně Otočení tvaru ve verzi preview a sledujte chování shaderu.  
  
###### <a name="to-rotate-the-shape"></a>Který tvar otočí  
  
-   Stiskněte a podržte klávesu Alt a potom vyberte libovolného bodu na povrchu návrhu a přesuňte ho.  
  
### <a name="exporting-shaders"></a>Export shaderů  
 Před použitím shaderu ve vaší aplikaci, musíte ho exportovat ve formátu, který se rozumí rozhraní DirectX.  
  
 Jako zdrojový kód HLSL nebo jako hodnota bytecode funkce shader kompilované můžete exportovat shadery. HLSL zdrojový kód je exportovat do textového souboru, který má příponu názvu souboru .hlsl. Hodnota bytecode funkce shader můžete exportovat Nezpracovaná binární soubor, který má příponu názvu souboru .cso nebo soubor hlaviček (.h) jazyka C++, který kóduje hodnota bytecode funkce shader do pole.  
  
 Další informace o tom, jak exportovat shader, naleznete v tématu [postupy: exportování shaderu](../designers/how-to-export-a-shader.md).  
  
## <a name="keyboard-shortcuts"></a>Klávesové zkratky  
  
|Příkaz|Klávesové zkratky|  
|-------------|------------------------|  
|Přepnout na **vyberte** režimu|Ctrl+G, Gtrl+Q<br /><br /> S|  
|Přepnout na **přiblížení** režimu|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Přepnout na **Pan** režimu|Ctrl+G, Ctrl+P<br /><br /> K|  
|Vybrat vše|Ctrl+A|  
|Odstranit aktuální výběr|Odstranit|  
|Zrušit aktuální výběr|Escape|  
|Přiblížit|Ctrl + kolečko myši dopředu<br /><br /> Znaménko plus (+)|  
|Oddálit|Ctrl kolečko myši dozadu<br /><br /> Znaménko minus (-)|  
|Posunout nahoru na návrhovou plochu|Kolečko myši dozadu<br /><br /> PageDown|  
|Posunout návrhové ploše dolů|Kolečko myši dopředu<br /><br /> PageUp|  
|Posunout doleva návrhové ploše|Shift + kolečko myši dozadu<br /><br /> Kolečko myši doleva<br /><br /> Shift + PageDown|  
|Posunout doprava návrhové ploše|Shift + kolečko myši dopředu<br /><br /> Kolečko myši doprava<br /><br /> SHIFT + PAGE UP|  
|Přesunout fokus klávesnice pro jiný uzel|Klávesy se šipkami|  
|Vyberte uzel, který má fokus klávesnice (přidá uzel do výběru skupiny)|SHIFT + MEZERNÍK|  
|Přepnout výběr uzlu, který má fokus klávesnice|Ctrl + mezerník|  
|Přepne aktuální výběr (Pokud je vybráno žádné uzly, vyberte uzel, který má klávesnice fokus)|MEZERNÍK|  
|Aktuální výběr nahoru|Shift + šipka nahoru|  
|Aktuální výběr dolů|Shift + šipka dolů|  
|Aktuální výběr doleva|Shift + šipka doleva|  
|Přesunout aktuální výběr doprava|Shift + šipka doprava.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Najdete zde přehled [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje, které můžete použít pro práci s texturami a obrazy, 3D modely a efekty shaderu.|  
|[Editor obrázků](../designers/image-editor.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor obrázků pro práci s texturami a obrázky.|  
|[Editor modelů](../designers/model-editor.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru modelů pro práci s 3D modely.|



