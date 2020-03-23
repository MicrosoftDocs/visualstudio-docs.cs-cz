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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589926"
---
# <a name="shader-designer"></a>Návrhář shaderů

Tento dokument popisuje, jak pracovat s **návrhářem shaderu** sady Visual Studio při vytváření, úpravách a exportu vlastních vizuálních efektů, které se označují jako *shadéry*.

**Pomocí návrháře shaderů** můžete vytvořit vlastní vizuální efekty pro vaši hru nebo aplikaci, i když neznáte programování jazyka shaderu na vysoké úrovni (HLSL). Chcete-li vytvořit shader v **návrháři shaderu**, rozložte jej jako graf. To znamená, že přidáte do uzlů *návrhového* povrchu, které představují data a operace, a pak mezi nimi vytvoříte spojení, abyste definovali, jak operace zpracovávají data. V každém uzlu operace je k dispozici náhled efektu až do tohoto bodu, takže můžete vizualizovat jeho výsledek. Data toky přes uzly směrem ke konečnému uzlu, který představuje výstup shaderu.

## <a name="supported-formats"></a>Podporované formáty

**Návrhář shaderu** podporuje tyto formáty shaderu:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, export)|
|-----------------| - | - |
|Jazyk shaderu s orientovaným grafem|*.dgsl*|Zobrazení, úpravy|
|HLSL Shader (zdrojový kód)|*.hlsl*|Export|
|Hlsl shader (bytecode)|*.cso*|Export|
|Hlavička Jazyka C++ (pole bajtového kódu HLSL)|*.h*|Export|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat shader DGSL do projektu Sady Visual Studio C++ a poskytuje základní informace, které vám pomohou začít.

> [!NOTE]
> Automatická integrace sestavení grafických položek, jako jsou shader grafy (.dgsl soubory) je podporována pouze pro projekty Jazyka C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Přidání shaderu DGSL do projektu

1. Ujistěte se, že máte nainstalovanou požadovanou součást sady Visual Studio, kterou potřebujete pro práci s grafikou. Komponenta se nazývá **Image a 3D model editory**.

   Chcete-li ji nainstalovat, otevřete instalační službu sady Visual Studio tak, že na řádku nabídek **Image and 3D model editors** vyberete **Nástroje** > získat nástroje **Games and Graphics** a**funkce** a pak vyberte kartu Jednotlivé **součásti.** **Modify**

   ![Komponenta editorů obrazových a 3D modelů](media/image-3d-model-editors-component.png)

2. V **Průzkumníku řešení**otevřete místní nabídku pro projekt C++, do kterého chcete přidat shader, a pak zvolte **Přidat** > **novou položku**.

3. V dialogovém okně **Přidat novou položku** v části **Nainstalováno**vyberte **Grafika**a pak vyberte **Visual Shader Graph (.dgsl)**.

   > [!NOTE]
   > Pokud v dialogovém okně **Přidat novou položku** nevidíte kategorii **Grafika** a máte nainstalovanou komponentu **Image a 3D model editory,** nebudou grafické položky pro váš typ projektu podporovány.

4. Zadejte **název** souboru shaderu a **umístění,** kde má být vytvořen.

5. Vyberte tlačítko **Přidat**.

### <a name="the-default-shader"></a>Výchozí shader

Pokaždé, když vytvoříte shader DGSL, začne jako minimální shader, který má pouze uzel **Bodová barva,** který je připojen k uzlu **Konečné barvy.** I když tento shader je kompletní a funkční, to nedělá moc. Proto prvním krokem při vytváření pracovní shader je často odstranit **uzel Barva bodu** nebo jej odpojit od uzlu Konečné **barva** vytvořit prostor pro jiné uzly.

## <a name="work-with-the-shader-designer"></a>Práce s návrhářem shaderu

Následující části popisují, jak používat Návrhář shaderů pro práci s vlastními shadery.

### <a name="shader-designer-toolbars"></a>Panely nástrojů Návrhář shaderu

Panely nástrojů Návrhář shaderů obsahují příkazy, které vám pomohou pracovat s grafy shaderu Shader.

Příkazy, které ovlivňují stav návrháře shaderů, jsou umístěny na panelu nástrojů **režimu návrháře shaderu** v hlavním okně sady Visual Studio. Návrhové nástroje a příkazy jsou umístěny na panelu nástrojů **Návrhář shaderu** na návrhové ploše návrháře shaderu.

Zde je panel nástrojů **režimu návrháře shaderu:**

![Modální panel nástrojů Návrhář shaderu.](../designers/media/digit-dsd-modal-toolbar.png)

Tato tabulka popisuje položky na panelu nástrojů **Režim návrháře shaderu,** které jsou uvedeny v pořadí, ve kterém se zobrazují zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Vybrat**|Umožňuje interakci s uzly a hranami v grafu. V tomto režimu můžete vybrat uzly a přesunout nebo odstranit a můžete vytvořit hrany nebo je přerušit.|
|**Posouvání**|Umožňuje pohyb grafu shaderu vzhledem k rámečku okna. Chcete-li posouvat, vyberte bod na návrhové ploše a přesuňte ho.<br /><br /> V režimu **výběru** můžete dočasně aktivovat režim **Posouvání** stisknutím a podržením **klávesy Ctrl.**|
|**Zoom**|Umožňuje zobrazení více či méně shader-graph detail vzhledem k rámečku okna. V režimu **Lupa** vyberte bod na návrhové ploše a pak ho přesuňte doprava nebo dolů, abyste zobrazení přiblížili, nebo doleva nebo nahoru pro oddálení.<br /><br /> V režimu **výběru** můžete stisknutím a podržením **klávesy Ctrl** zobrazení přiblížit nebo oddálit pomocí kolečka myši.|
|**Přiblížení podle vhod**|Zobrazí úplný graf shaderu v rámečku okna.|
|**Režim vykreslování v reálném čase**|Pokud je povoleno vykreslování v reálném čase, Visual Studio překreslí návrhový povrch, i když se provádí žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Náhled s koulí**|Pokud je tato možnost povolena, zobrazí se náhled náhledu shaderu model emotiky. Současně lze povolit pouze jeden obrazec náhledu.|
|**Náhled s krychli**|Pokud je tato možnost povolena, model krychle se používá k zobrazení náhledu shaderu. Současně lze povolit pouze jeden obrazec náhledu.|
|**Náhled s válcem**|Pokud je povoleno, model válce se používá k náhledu shaderu. Současně lze povolit pouze jeden obrazec náhledu.|
|**Náhled s kuželem**|Pokud je tato možnost povolena, model kužele se používá k zobrazení náhledu shaderu. Současně lze povolit pouze jeden obrazec náhledu.|
|**Náhled s čajovou konvicí**|Pokud je tato možnost povolena, model konvice se používá k náhledu shaderu. Současně lze povolit pouze jeden obrazec náhledu.|
|**Náhled s rovinou**|Pokud je tato možnost povolena, model roviny se používá k zobrazení náhledu shaderu. Současně lze povolit pouze jeden obrazec náhledu.|
|**Sada nástrojů**|Střídavě zobrazuje nebo skryje **panel nástrojů**.|
|**Vlastnosti**|Alternativně zobrazí nebo skryje okno **Vlastnosti.**|
|**Pokročilé**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Export**: Umožňuje export shaderu v několika formátech.<br /><br /> **Exportovat jako**: Exportuje shader jako zdrojový kód HLSL nebo jako zkompilovaný bytekód shaderu. Další informace o exportu shaderů naleznete v [tématu How to: Export shader](../designers/how-to-export-a-shader.md).<br /><br /> **Grafické moduly**: Umožňuje výběr vykreslovače, který se používá k zobrazení návrhové plochy.<br /><br /> **Vykreslení pomocí D3D11**: K vykreslení návrhové plochy návrháře shaderu používá rozhraní Direct3D 11.<br /><br /> **Vykreslení pomocí d3D11WARP:** K vykreslení návrhové plochy návrháře shaderu používá platformu Direct3D 11 Advanced Rasterization Platform (WARP).<br /><br /> **Zobrazení**: Umožňuje výběr dalších informací o návrháři shaderu.<br /><br /> **Kmitočet snímků**: Pokud je povolena možnost, zobrazí aktuální kmitočet snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. Tato volba je užitečná, když povolíte **volbu režimu vykreslování** v reálném čase.|

> [!TIP]
> Chcete-li znovu spustit poslední příkaz, můžete zvolit tlačítko **Upřesnit.**

### <a name="work-with-nodes-and-connections"></a>Práce s uzly a připojeními

Pomocí režimu **Výběr** můžete přidávat, odebírat, přemísťovat, připojovat a konfigurovat uzly. Zde je návod, jak provádět tyto základní operace:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Provádění základních operací v režimu výběru

- Zde je uveden postup:

  - Chcete-li do grafu přidat uzel, vyberte jej v **panelu nástrojů** a pak jej přesuňte na návrhovou plochu.

  - Chcete-li uzel z grafu odebrat, vyberte jej a stiskněte **klávesu Delete**.

  - Chcete-li změnit umístění uzlu, vyberte jej a přesuňte jej do nového umístění.

  - Chcete-li připojit dva uzly, přesuňte výstupní terminál jednoho uzlu do vstupního terminálu druhého uzlu. Lze připojit pouze terminály, které mají kompatibilní typy. Linka mezi terminály ukazuje spojení.

  - Chcete-li připojení odebrat, zvolte v místní nabídce jednoho z připojených terminálů **možnost Přerušit propojení**.

  - Chcete-li konfigurovat vlastnosti uzlu, vyberte uzel a v okně **Vlastnosti** zadejte nové hodnoty vlastností.

### <a name="preview-shaders"></a>Náhled stínidla

Abyste pochopili, jak se ve vaší aplikaci zobrazí shader, můžete nakonfigurovat, jak bude váš efekt zobrazen v náhledu. Chcete-li aplikaci přiblížit, můžete zvolit jeden z několika obrazců, který chcete vykreslit, nakonfigurovat textury a další parametry materiálu, povolit animaci efektů založených na čase a prozkoumat náhled z různých úhlů.

#### <a name="shapes"></a>Obrazce

Návrhář shaderu obsahuje šest tvarů – kouli, kostku, válec, kužel, konvici a rovinu – které můžete použít k zobrazení náhledu shaderu. V závislosti na shaderu vám některé obrazce mohou poskytnout lepší náhled.

Chcete-li zvolit obrazec náhledu, zvolte na panelu nástrojů **Režimy návrháře shaderu** požadovaný tvar.

#### <a name="textures-and-material-parameters"></a>Textury a parametry materiálu

Mnoho stínidla spoléhají na textury a vlastnosti materiálu, aby vytvořily jedinečný vzhled pro každý druh objektu ve vaší aplikaci. Chcete-li zjistit, jak bude váš shader vypadat ve vaší aplikaci, můžete nastavit textury a vlastnosti materiálu, které se používají k vykreslení náhledu tak, aby odpovídaly texturám a parametrům, které můžete použít ve vaší aplikaci.

Chcete-li svázat jinou texturu s registrem textury nebo upravit jiné parametry materiálu:

1. V režimu **výběru** vyberte prázdnou oblast návrhové plochy. To **způsobí, že okno Vlastnosti** zobrazí vlastnosti globálního shaderu.

2. V okně **Vlastnosti** zadejte nové hodnoty pro vlastnosti textury a parametru, které chcete změnit.

V následující tabulce jsou uvedeny parametry shaderu, které můžete upravit:

|Parametr|Vlastnosti|
|---------------|----------------|
|**Textura 1** - **Textura 8**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Název souboru**: Úplná cesta k souboru textury, který je přidružen k tomuto registru textur.|
|**Okolní materiál**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnota**: Difuzní barva aktuálního obrazového bodu z důvodu nepřímého nebo okolního osvětlení.|
|**Materiál Difuzní**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnota**: Barva, která popisuje, jak aktuální obrazový bod rozptyluje přímé osvětlení.|
|**Materiál emisivní**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnota**: Barevný příspěvek aktuálního obrazového bodu díky samoobslužnému osvětlení.|
|**Materiál zrcadlový**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnota**: Barva, která popisuje, jak aktuální obrazový bod odráží přímé osvětlení.|
|**Zrcadlová síla materiálu**|**Přístup**: **Veřejné** povolit vlastnost, která má být nastavena z Editoru modelů; jinak **Private**.<br /><br /> **Hodnota**: Exponent, který definuje intenzitu odlesků na aktuálním obrazovém bodu.|

#### <a name="time-based-effects"></a>Efekty založené na čase

Některé stínidla mají součást založenou na čase, která animuje efekt. Chcete-li zobrazit, jak efekt vypadá v akci, náhled musí být aktualizován několikrát za sekundu. Ve výchozím nastavení je náhled aktualizován pouze při změně shaderu; chcete-li toto chování změnit tak, aby bylo možné zobrazit efekty založené na čase, je třeba povolit vykreslování v reálném čase.

Chcete-li povolit vykreslování v reálném čase, zvolte na panelu nástrojů Návrhář shaderů **možnost Vykreslování v reálném čase**.

#### <a name="examine-the-effect"></a>Zkontrolujte účinek

Mnoho stínidla jsou ovlivněny proměnnými, jako je úhel pohledu nebo směrové osvětlení. Chcete-li prozkoumat, jak efekt reaguje při změně těchto proměnných, můžete obrazec náhledu volně otáčet a sledovat, jak se shader chová.

Chcete-li obrazec otočit, stiskněte a podržte **klávesu Alt**a pak vyberte libovolný bod na návrhové ploše a posuňte jej.

### <a name="export-shaders"></a>Exportové stínidla

Než budete moci v aplikaci použít shader, musíte ho exportovat ve formátu, kterému Rozhraní DirectX rozumí.

Shadery můžete exportovat jako zdrojový kód HLSL nebo jako zkompilovaný bytekód shaderu. Zdrojový kód HLSL je exportován do textového souboru, který má příponu *.hlsl.* Bytecode shaderu lze exportovat buď do nezpracovaného binárního souboru, který má příponu *cso,* nebo do souboru hlavičky C++ (*H),* který kóduje bytekód shaderu do pole.

Další informace o exportu shaderů naleznete v [tématu How to: Export shader](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnutí do **režimu výběru**|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Přepnutí do režimu **lupy**|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Přepnutí do režimu **Pan**|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Vybrat vše|**Ctrl**+**A**|
|Odstranit aktuální výběr|**Odstranit**|
|Zrušit aktuální výběr|**Útěk** (**Esc**)|
|Přiblížit|**Ctrl**+**kolečko myši vpřed**<br /><br /> Znaménko plus (**+**)|
|Oddálit|**Ctrl**+**kolečko myši dozadu**<br /><br /> Znaménko mínus (**-**)|
|Posuneme návrhovou plochu nahoru|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posuzte návrhovou plochu dolů|**Kolečko myši dopředu**<br /><br /> **PageUp**|
|Posuzte návrhovou plochu doleva|**Shift**+**kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **Shift**+**PageDown**|
|Posuzte návrhovou plochu doprava|**Shift**+**kolečko myši vpřed**<br /><br /> **Kolečko myši doprava**<br /><br /> **Posunout**+**stránku nahoru**|
|Přesunutí fokusu klávesnice do jiného uzlu|Klávesy **se šipkami**|
|Vyberte uzel, který má fokus klávesnice (přidá uzel do skupiny výběru)|**Posunový**+**mezerník**|
|Přepnout výběr uzlu s fokusem klávesnice|**Mezerník se stisknutou klávesou Ctrl**+**Spacebar**|
|Přepnout aktuální výběr (pokud nejsou vybrány žádné uzly, vyberte uzel s fokusem klávesnice)|**Mezerník**|
|Přesunutí aktuálního výběru nahoru|**Šipka shift**+**nahoru**|
|Přesunutí aktuálního výběru dolů|**Šipka**+**shift dolů**|
|Přesunutí aktuálního výběru doleva|**Šipka**+**doleva**|
|Přesunutí aktuálního výběru doprava|**Šipka**+**doprava**shift .|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s 3D datovými zdroji pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Obsahuje přehled nástrojů sady Visual Studio, které můžete použít k práci s texturami a obrazy, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje, jak používat Visual Studio Image Editor pro práci s texturami a obrázky.|
|[Editor modelů](../designers/model-editor.md)|Popisuje, jak používat Visual Studio Editor modelů pro práci s 3D modely.|
