---
title: Návrhář shaderů
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85ce7b0f270f0da8728b17610a683dcc17d06189
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589926"
---
# <a name="shader-designer"></a>Návrhář shaderů

Tento dokument popisuje, jak pracovat s **návrhářem shaderu** sady Visual Studio k vytváření, úpravám a exportu vlastních vizuálních efektů, které jsou známé jako *shadery*.

Pomocí **Návrháře shaderu** můžete vytvořit vlastní vizuální efekty pro vaši hru nebo aplikaci, i když nevíte, jak HLSL (High Level shader) seznáme. Chcete-li vytvořit shader v **Návrháři shaderu**, je třeba ho rozvrhnout jako graf. To znamená, že přidáte do *uzlů* návrhové plochy, které reprezentují data a operace, a pak mezi nimi provedete připojení a určíte, jak operace zpracovávají data. V každém uzlu operace je k dispozici náhled efektu až do tohoto bodu, aby bylo možné vizualizovat jeho výsledek. Data procházejí uzly směrem k konečnému uzlu, který představuje výstup shaderu.

## <a name="supported-formats"></a>Podporované formáty

**Návrhář shaderu** podporuje tyto formáty shaderu:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, export)|
|-----------------| - | - |
|Jazyk shaderu řízeného grafu|*. DGSL*|Zobrazit, upravit|
|HLSL shader (zdrojový kód)|*. HLSL*|Export|
|HLSL shader (bytového kódu)|*. CSO*|Export|
|Hlavička jazyka C++ (pole HLSL bytového kódu)|*. h*|Export|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat DGSL shader do projektu Visual Studio C++ a poskytuje základní informace, které vám pomohou začít.

> [!NOTE]
> Automatická integrace sestavení grafických položek, jako jsou grafy shaderu (soubory. DGSL), je podporována pouze pro projekty v jazyce C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Přidání DGSL shaderu do projektu

1. Ujistěte se, že máte nainstalovanou požadovanou součást sady Visual Studio, kterou potřebujete pracovat s grafikou. Tato součást se nazývá **editory obrázků a 3D model**.

   Pokud ho chcete nainstalovat, otevřete instalační program pro Visual Studio tak, že v řádku nabídek vyberete **nástroje**  >  **získat nástroje a funkce** a pak vyberete kartu **jednotlivé součásti** . v kategorii **hry a grafika** vyberte komponentu **image a 3D model editory** a pak vyberte **Upravit**.

   ![Součást Editor obrázků a 3D model](media/image-3d-model-editors-component.png)

2. V **Průzkumník řešení**otevřete místní nabídku pro projekt C++, ke kterému chcete shader přidat, a pak zvolte možnost **Přidat**  >  **novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte v části **nainstalovaná**možnost **Grafika**a pak vyberte **Visual shader Graph (. DGSL)**.

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **grafiky** a máte nainstalovanou komponentu **image a 3D model editory** , pro váš typ projektu se nepodporují grafické položky.

4. Zadejte **název** souboru shaderu a **umístění** , kde se má vytvořit.

5. Vyberte tlačítko **Přidat**.

### <a name="the-default-shader"></a>Výchozí shader

Pokaždé, když vytvoříte DGSL shader, začíná jako minimální shader, který má pouze uzel **barevného bodu** , který je připojen k **konečnému uzlu Color** . I když je tento shader dokončený a funkční, nemá mnoho. Proto první krok při vytváření funkčního shaderu často odstraní uzel **Color Point** nebo ho odpojí od **posledního barevného** uzlu, aby uvolnil místo pro ostatní uzly.

## <a name="work-with-the-shader-designer"></a>Práce s návrhářem shaderů

Následující části popisují, jak používat návrháře shaderu pro práci s vlastními shadery.

### <a name="shader-designer-toolbars"></a>Panely nástrojů Návrháře shaderu

Panely nástrojů Návrháře shaderu obsahují příkazy, které vám pomůžou pracovat s grafy DGSL shaderu.

Příkazy, které ovlivňují stav návrháře shaderu, jsou umístěny na panelu nástrojů **režimu návrháře shaderu** v hlavním okně aplikace Visual Studio. Nástroje a příkazy pro návrh jsou umístěné na panelu nástrojů **Návrháře shaderu** na návrhové ploše návrháře shaderu.

Tady je panel nástrojů **režim návrháře shaderu** :

![Modální panel nástrojů návrháře shaderů](../designers/media/digit-dsd-modal-toolbar.png)

V této tabulce jsou popsány položky na panelu nástrojů **režimu návrháře shaderu** , které jsou uvedeny v pořadí, ve kterém se zobrazí zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Výběr**|Umožňuje interakci s uzly a hranami v grafu. V tomto režimu můžete vybrat uzly a přesunout je nebo odstranit, a můžete také vytvořit okraje nebo je rozdělit.|
|**Posouvání**|Umožňuje přesun grafu shaderu relativně k rámečku okna. Pro posouvání vyberte bod na návrhové ploše a přesuňte ho kolem.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu **CTRL** a dočasně aktivovat režim **posouvání** .|
|**Zoom**|Povoluje zobrazení více nebo méně podrobností shaderového grafu vzhledem k rámečku okna. V režimu **zvětšení** vyberte bod na návrhové ploše a pak ho přesuňte doprava nebo dolů, abyste se přiblížili nebo ponechali oddálit nebo zmenšení.<br /><br /> V režimu **výběru** můžete stisknout a podržet klávesu **CTRL** pro přiblížení nebo oddálení pomocí kolečka myši.|
|**Přizpůsobit zobrazení**|Zobrazí úplný graf shaderu v rámci okna.|
|**Režim vykreslování v reálném čase**|Když je povoleno vykreslování v reálném čase, Visual Studio překreslí návrhovou plochu i v případě, že není provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Náhled pomocí koule**|Pokud je tato možnost povolena, použije se k náhledu shaderu model koule. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Náhled pomocí datové krychle**|Když je tato možnost povolená, použije se k zobrazení náhledu shaderu model datové krychle. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Náhled pomocí válce**|Pokud je tato možnost povolena, použije se k zobrazení náhledu shaderu model lahve. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Náhled pomocí kužele**|Pokud je tato možnost povolena, použije se k zobrazení náhledu shaderu model kužele. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Náhled pomocí konvice**|Pokud je tato možnost povolena, použije se k zobrazení náhledu shaderu model konvice. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Náhled s rovinou**|Pokud je tato možnost povolena, použije se k zobrazení náhledu shaderu model roviny. V jednom okamžiku může být povolen pouze jeden obrazec náhledu.|
|**Sada nástrojů**|Alternativně zobrazí nebo skryje **panel nástrojů**.|
|**Vlastnosti**|Případně se zobrazí nebo skryje okno **vlastnosti** .|
|**Pokročilý**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Export**: povoluje export shaderu v několika formátech.<br /><br /> **Exportovat jako**: exportuje shader jako buď zdrojový kód HLSL, nebo jako zkompilovaný kód kompilovaného shaderu. Další informace o tom, jak exportovat shadery, naleznete v tématu [How to: Export shader](../designers/how-to-export-a-shader.md).<br /><br /> **Grafické moduly**: umožňuje výběr vykreslovacího modulu, který se používá k zobrazení návrhové plochy.<br /><br /> **Render with D3D11**: pomocí Direct3D 11 vykreslí plochu návrhu Návrháře shaderu.<br /><br /> **Rendering with D3D11WARP**: používá rozhraní Direct3D 11 Windows Advanced rastring Platform (osnova) k vykreslení plochy návrhu Návrháře shaderu.<br /><br /> **Zobrazení**: umožňuje výběr dalších informací o Návrháři shaderů.<br /><br /> **Snímková frekvence**: když je povolená, zobrazí aktuální kmitočet snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. Tato možnost je užitečná, když povolíte možnost **režim vykreslování v reálném čase** .|

> [!TIP]
> Můžete zvolit tlačítko **Upřesnit** a znovu spustit poslední příkaz.

### <a name="work-with-nodes-and-connections"></a>Práce s uzly a připojeními

Pomocí režimu **Select** můžete přidat, odebrat, přemístit, připojit a nakonfigurovat uzly. Tady je postup, jak provádět tyto základní operace:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Postup při provádění základních operací v režimu výběru

- Zde je uveden postup:

  - Chcete-li přidat uzel do grafu, vyberte ho v **panelu nástrojů** a pak ho přesuňte na návrhovou plochu.

  - Chcete-li odebrat uzel z grafu, vyberte jej a stiskněte klávesu **Delete**.

  - Chcete-li změnit umístění uzlu, vyberte jej a přesuňte jej do nového umístění.

  - Chcete-li připojit dva uzly, přesuňte výstupní terminál jednoho uzlu do vstupního terminálu druhého uzlu. Připojit lze pouze terminály, které mají kompatibilní typy. Čára mezi terminály zobrazuje připojení.

  - Chcete-li odebrat připojení, vyberte v místní nabídce některého z připojených terminálů možnost **přerušení propojení**.

  - Chcete-li konfigurovat vlastnosti uzlu, vyberte uzel a poté v okně **vlastnosti** zadejte nové hodnoty vlastností.

### <a name="preview-shaders"></a>Shadery ve verzi Preview

Abychom vám pomohli pochopit, jak se shader zobrazí v aplikaci, můžete nakonfigurovat, jak se má váš efekt zobrazovat. K aproximaci aplikace můžete zvolit jeden z několika tvarů, které se mají vykreslovat, konfigurovat textury a další parametry materiálu, Povolit animaci efektů založených na čase a kontrolovat náhledy z různých úhlů.

#### <a name="shapes"></a>Obrazce

Návrhář shaderu obsahuje šest tvarů – koule, datovou krychli, válec, kuželový, konvice a rovinu, kterou můžete použít k zobrazení náhledu shaderu. V závislosti na shaderu vám některé tvary můžou poskytnout lepší náhled.

Chcete-li zvolit obrazec náhledu, vyberte na panelu nástrojů **režimy návrháře shaderů** požadovaný tvar.

#### <a name="textures-and-material-parameters"></a>Textury a parametry materiálu

Mnohé shadery spoléhají na textury a vlastnosti materiálu k vytvoření jedinečného vzhledu pro každý druh objektu v aplikaci. Chcete-li zjistit, jak váš shader bude ve vaší aplikaci vypadat, můžete nastavit textury a vlastnosti materiálu, které se použijí k vykreslení náhledu tak, aby odpovídaly texturám a parametrům, které můžete ve své aplikaci použít.

Svázání jiné textury s registrem textury nebo úpravou jiných parametrů pro materiál:

1. V režimu **výběru** vyberte prázdnou oblast návrhové plochy. To způsobí, že okno **vlastnosti** zobrazí vlastnosti globálního shaderu.

2. V okně **vlastnosti** zadejte nové hodnoty vlastností textury a parametru, které chcete změnit.

V následující tabulce jsou uvedeny parametry shaderu, které lze upravit:

|Parametr|Vlastnosti|
|---------------|----------------|
|**Textura 1**  -  **Textura 8**|**Přístup**:                             **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Filename**: úplná cesta k souboru textury, která je přidružena k tomuto registru textury.|
|**Okolí materiálu**|**Přístup**:                             **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Value**: barva difúze aktuálního pixelu z důvodu nepřímého nebo okolního osvětlení.|
|**Materiálové difúze**|**Přístup**: **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.|
|**Vyzařující materiálu**|**Přístup**:                              **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Value (hodnota**): podíl barvy aktuálního pixelu z důvodu samostatně poskytnutého osvětlení.|
|**Odlesky materiálu**|**Přístup**:                              **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|
|**Materiálově odlesky energie**|**Přístup**:                             **veřejné** , aby bylo možné vlastnost nastavit z editoru modelů; v opačném případě **Private**.<br /><br /> **Value (hodnota**): exponent definující intenzitu zrcadlových světel na aktuálním pixelu.|

#### <a name="time-based-effects"></a>Efekty založené na čase

Některé shadery mají komponentu založenou na čase, která animaci projeví. Chcete-li zobrazit, jak efekt vypadá v akci, je nutné náhled verze Preview aktualizovat několikrát za sekundu. Ve výchozím nastavení je verze Preview aktualizována pouze v případě, že je shader změněn; Chcete-li toto chování změnit, aby bylo možné zobrazit efekty založené na čase, je nutné povolit vykreslování v reálném čase.

Pokud chcete povolit vykreslování v reálném čase, na panelu nástrojů Návrháře shaderu vyberte **vykreslování v reálném**čase.

#### <a name="examine-the-effect"></a>Kontrola efektu

Mnohé shadery jsou ovlivněny proměnnými, jako je zobrazení úhlu nebo směrového osvětlení. Chcete-li se podívat, jak efekt reaguje, když se tyto proměnné mění, můžete otočit tvar náhledu a sledovat, jak se shader chová.

Chcete-li otočit tvar, stiskněte a podržte klávesu **ALT**a pak vyberte libovolný bod na návrhové ploše a přesuňte ho.

### <a name="export-shaders"></a>Exportovat shadery

Než budete moct v aplikaci použít shader, musíte ho exportovat ve formátu, který rozhraní DirectX zná.

Shadery můžete exportovat jako zdrojový kód HLSL nebo jako kód zkompilovaného kódu shaderu. Zdrojový kód HLSL je exportován do textového souboru, který má příponu názvu souboru *. HLSL* . Bajtový kód shaderu lze exportovat buď do nezpracovaného binárního souboru, který má příponu názvu souboru *. CSO* , nebo do souboru hlaviček jazyka C++ (*. h*), který kóduje bajtový kód shaderu do pole.

Další informace o tom, jak exportovat shadery, naleznete v tématu [How to: Export shader](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnout na režim **výběru**|**CTRL** + **G**, **CTRL** + **Q**<br /><br /> **S**|
|Přepnout do režimu **lupy**|**CTRL** + **G**, **CTRL** + **Z**<br /><br /> **Z**|
|Přepnout do režimu **posouvání**|**CTRL** + **G**, **CTRL** + **P** +<br /><br /> **K**|
|Vybrat vše|**CTRL** + **A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**Řídicí** znak (**ESC**)|
|Přiblížit|**CTRL** + **Kolečko myši – posunutí**<br /><br /> Znaménko plus ( **+** )|
|Oddálit|**CTRL** + **Kolečko myši dozadu**<br /><br /> Symbol mínus ( **-** )|
|Posouvání návrhové plochy nahoru|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posunout plochu návrhu dolů|**Kolečko myši dopředu**<br /><br /> **PageUp**|
|Posunout návrhovou plochu doleva|**Posun** + **Kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **Posun** + **PageDown**|
|Posunout návrhovou plochu doprava|**Posun** + **Kolečko myši – posunutí**<br /><br /> **Kolečko myši doprava**<br /><br /> **Posun** + **PageUp**|
|Přesunutí fokusu klávesnice na jiný uzel|Klávesy se **šipkami**|
|Vyberte uzel, který má fokus klávesnice (přidá uzel do skupiny výběru).|**Posun** + **MEZERNÍK**|
|Přepnout výběr uzlu, který má fokus klávesnice|**CTRL** + **MEZERNÍK**|
|Přepnout aktuální výběr (pokud nejsou vybrané žádné uzly, vyberte uzel, který má fokus klávesnice).|**Mezerník**|
|Přesunout aktuální výběr nahoru|**Posun** + **Šipka nahoru**|
|Přesunout aktuální výběr dolů|**Posun** + **Šipka dolů**|
|Posunout aktuální výběr doleva|**Posun** + **Šipka vlevo**|
|Přesunout aktuální výběr doprava|**Posun** + **Šipka doprava**|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled nástrojů sady Visual Studio, které můžete použít pro práci s texturami a obrázky, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat editor obrázků sady Visual Studio pro práci s texturami a obrázky.|
|[Editor modelů](../designers/model-editor.md)|Popisuje, jak používat Editor modelů sady Visual Studio pro práci s 3D modely.|
