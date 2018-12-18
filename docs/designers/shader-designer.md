---
title: Návrhář shaderů
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f2f53e801df70345e34c14c15d4456e39561623
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847627"
---
# <a name="shader-designer"></a>Návrhář shaderů

Tento dokument popisuje způsob práce se sadou Visual Studio **návrháře shaderu** Pokud chcete vytvořit, upravit a exportovat vlastní vizuální efekty, které jsou označovány jako *shadery*.

Můžete použít **návrháře shaderu** k vytvoření vlastní vizuálních efektů pro vaše hry nebo aplikace, i pokud si nejste jisti vysoké úrovně shader language (HLSL) programování. K vytvoření shaderu ve **návrháře shaderu**, si to rozložení jako graf. To znamená, přidat na návrhovou plochu *uzly* , která představují data a operace a pak proveďte připojení mezi nimi k definování, jak operace zpracovat data. V každém uzlu operace je k dispozici ve verzi preview efekt až k danému bodu tak, aby můžete vizualizovat jeho výsledek. Data prochází uzly směrem k poslední uzel, který představuje výstup shaderu.

## <a name="supported-formats"></a>Podporované formáty

**Návrháře shaderu** podporuje tyto formáty shaderu:

|Název formátu|Přípona souboru|Podporované operace (zobrazení, úpravy, Export)|
|-----------------| - | - |
|Orientovaný graf shaderu jazyka|*.dgsl*|Zobrazení pro úpravy|
|Shader HLSL (zdrojového kódu)|*.hlsl*|Export|
|Shader HLSL (bajtového kódu)|*.CSO*|Export|
|Hlaviček jazyka C++ (pole bajtového kódu HLSL)|*.h*|Export|

## <a name="get-started"></a>Začínáme

Tato část popisuje, jak přidat do projektu Visual Studio C++ DGSL shader a obsahuje základní informace, které vám pomůžou začít.

> [!NOTE]
> Automatické sestavení integrace grafiky různé věci, třeba grafy shaderu (.dgsl souborů) je podporována pouze pro projekty C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Chcete-li přidat do projektu DGSL shader

1. Ujistěte se, že máte požadované sady Visual Studio nainstalována součást potřebné pro práci s grafikou. Komponenta nazývá **obrázků a 3D modelů editory**.

   Ho Pokud chcete nainstalovat, spusťte instalační program sady Visual Studio tak, že vyberete **nástroje** > **stažení nástrojů a funkcí** z nabídky panelu a pak vyberte **jednotlivé komponenty**kartu. Vyberte **obrázků a 3D modelů editory** komponentu pod **hry a grafika** kategorie a pak vyberte **změnit**.

   ![Obrázků a 3D modelů editory komponenty](media/image-3d-model-editors-component.png)

2. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt jazyka C++, ke kterému chcete přidat shaderu a klikněte na tlačítko **přidat** > **nová položka**.

3. V **přidat novou položku** dialogovém okně **nainstalováno**vyberte **grafiky**a pak vyberte **vizuální graf shaderu (.dgsl)**.

   > [!NOTE]
   > Pokud se nezobrazí **grafiky** v kategorii **přidat novou položku** dialogových oken a budete mít **obrázků a 3D modelů editory** nainstalována součást grafické položky nejsou podporovány pro typ vašeho projektu.

4. Zadejte **název** souboru shaderu a **umístění** místo se má vytvořit.

5. Zvolte **přidat** tlačítko.

### <a name="the-default-shader"></a>Výchozí shader

Pokaždé, když vytvořte DGSL shader, začne jako minimální shader, který má právě **barva bodu** uzel, který je připojený k **konečnou barvu** uzlu. I když tento shader je úplné a funkční, mnoho neprovádí. Proto je prvním krokem při vytváření shaderu pracovní často odstranit **barva bodu** uzlu nebo odpojte ho od **konečnou barvu** uzel, aby uvolnil prostor pro další uzly.

## <a name="work-with-the-shader-designer"></a>Práce s návrháře shaderu

Následující části popisují způsob použití návrháře shaderu pro práci se shadery vlastní.

### <a name="shader-designer-toolbars"></a>Panely nástrojů návrháře shaderu

Návrháře shaderu, které obsahují panely nástrojů příkazy, které pomohou při práci s grafy DGSL shader.

Příkazy, které mají vliv na stav návrháře shaderu jsou umístěny na **režim návrháře shaderu** nástrojů v hlavním okně aplikace Visual Studio. Návrhářské nástroje a příkazy jsou umístěny na **návrháře shaderu** nástrojů na návrhové ploše návrháře shaderu.

Tady je **režim návrháře shaderu** nástrojů:

![Modální okno nástrojů návrháře shaderu.](../designers/media/digit-dsd-modal-toolbar.png)

Tato tabulka popisuje položky panelu **režim návrháře shaderu** nástrojů, které jsou uvedeny v pořadí, ve kterém jsou uvedeny zleva doprava:

|Položka na panelu nástrojů|Popis|
|------------------|-----------------|
|**Vyberte**|Umožňuje interakci s uzly a hran do grafu. V tomto režimu můžete vybrat uzly a přesunout nebo odstranit, a můžete vytvořit okraje nebo rozdělit je.|
|**Posouvání**|Umožňuje pohyb graf shaderu relativně k rámu okna. K posouvání vyberte bod na návrhové ploše a pohybujte jím.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením **Ctrl** aktivovat **Pan** dočasně režimu.|
|**Přiblížení**|Umožňuje zobrazení více či méně detailů graf shaderu relativně k rámu okna. V **přiblížení** režimu, vyberte bod na návrhové ploše a poté jej přesunutím vpravo dolů zvětšete nebo přesunutím vlevo či nahoru out.<br /><br /> V **vyberte** režimu, můžete stisknutím a podržením **Ctrl** pro přiblížení nebo oddálení použít kolečko myši.|
|**Přizpůsobit zobrazení**|Zobrazí graf úplné shaderu v rámci okna.|
|**Režim vykreslování v reálném čase**|Pokud je povoleno vykreslení v reálném čase, Visual Studio překreslí plochu návrhu, i když je provedena žádná akce uživatele. Tento režim je užitečný při práci se shadery, které se mění v průběhu času.|
|**Náhled pomocí koule**|Při povolení modelu koule slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Náhled pomocí krychle**|Pokud povolená, model datové krychle se používá k náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Náhled pomocí válce**|Při povolení modelu válec slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Náhled pomocí kužele**|Při povolení modelu kužel slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Náhled pomocí čajové konvice**|Pokud povolená, modelu čajovou konvici slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Náhled pomocí roviny**|Při povolení modelu rovinou slouží náhled shaderu. Je možné povolit tvar náhled pouze jeden po druhém.|
|**Panel nástrojů**|Střídavě zobrazí a skryje **nástrojů**.|
|**Vlastnosti**|Můžete také zobrazí nebo skryje **vlastnosti** okna.|
|**Pokročilé**|Obsahuje pokročilé příkazy a možnosti.<br /><br /> **Exportovat**: umožňuje exportovat shader v různých formátech.<br /><br /> **Exportovat jako**: Exportuje shaderu jako zdrojový kód buď HLSL nebo jako hodnota bytecode funkce shader kompilované. Další informace o tom, jak exportovat shader, naleznete v tématu [postupy: exportování shaderu](../designers/how-to-export-a-shader.md).<br /><br /> **Grafické moduly**: umožňuje výběr renderer, který se používá k zobrazení návrhové ploše.<br /><br /> **Vykreslení s D3D11**: používá rozhraní Direct3D 11 k vykreslení plochy návrhu Návrháře shaderu.<br /><br /> **Vykreslení s D3D11WARP**: používá rozhraní Direct3D 11 Windows Advanced Rasterizační platformě WARP () k vykreslení plochy návrhu Návrháře shaderu.<br /><br /> **Zobrazení**: umožňuje výběr další informace o návrháři shaderu.<br /><br /> **Frekvence snímků**: Pokud povolená, zobrazí aktuální frekvenci snímků v pravém horním rohu návrhové plochy. Frekvence snímků je počet snímků, které jsou zpracovány za sekundu. Tato možnost je užitečná, když povolíte **režim vykreslování v reálném čase** možnost.|

> [!TIP]
> Můžete použít **Upřesnit** tlačítko poslední příkaz spustit znovu.

### <a name="work-with-nodes-and-connections"></a>Práce s uzly a připojení

Použití **vyberte** režimu k přidání, odebrání, změna umístění, připojení a konfigurace uzlů. Tady je postup pro provádění těchto základních operací:

#### <a name="to-perform-basic-operations-in-select-mode"></a>K provádění základních operací v režim výběru

- Tady je způsob:

   - Pokud chcete přidat uzel do grafu, vyberte ji v **nástrojů** a přesuňte jej na návrhovou plochu.

   - Odebrání uzlu z grafu, vyberte ho a potom stiskněte klávesu **odstranit**.

   - Chcete-li změnit umístění uzlu, vyberte ho a přesuňte ho do nového umístění.

   - Pro připojení dvou uzlů, přesuňte výstupní terminál jednoho z uzlů do vstupní terminálu z jiného uzlu. Můžete připojit pouze terminály, které mají nekompatibilní typy. Čáry mezi terminály zobrazuje připojení.

   - Chcete-li odebrat připojení, na místní nabídku pro jednu z připojených terminály, zvolte **přerušit odkazy**.

   - Chcete-li konfigurovat vlastnosti uzlu, vyberte uzel a pak na **vlastnosti** okno, zadejte nové hodnoty pro vlastnosti.

### <a name="preview-shaders"></a>Shader ve verzi Preview.

Na vám pomohou pochopit, jak bude vypadat shaderu ve vaší aplikaci, můžete nakonfigurovat, jak je zobrazen váš vliv. K odhadu vaší aplikace, zvolte jeden z několika obrazců vykreslení textury a další parametry materiálu, povolit animace založené na čase efekty a konfigurovat zkontrolujte ve verzi preview z různých úhlů.

#### <a name="shapes"></a>Obrazce

Návrháře shaderu obsahuje šest obrazce – kouli, datové krychle, válec, kužel, čajovou konvici a rovinou –, můžete použít k náhledu vašeho shaderu. V závislosti na shader určité tvary může získáte lepší náhled.

Zvolit tvar náhled na **režimy návrháře shaderu** nástrojů, vyberte obrazec, který chcete.

#### <a name="textures-and-material-parameters"></a>Textury a materiálu parametry

Mnoho shadery využívají textury a vlastností materiálu vytvořit jedinečný vzhled pro každý druh objektu ve vaší aplikaci. Zobrazíte vašeho shaderu bude vypadat ve vaší aplikaci můžete nastavit textury a vlastností materiálu, které slouží k vykreslení náhledu tak, aby odpovídaly textury a parametry, které můžete použít ve vaší aplikaci.

Registr textur svázat různé textury, nebo upravte ostatní materiálu parametry:

1. V **vyberte** režimu, vyberte prázdnou oblast návrhové plochy. To způsobí, že **vlastnosti** okno k zobrazení vlastností globální shaderu.

2. V **vlastnosti** okno, zadejte nové hodnoty pro textury a parametru vlastnosti, které chcete změnit.

V následující tabulce jsou uvedeny shaderu parametry, které můžete upravit:

|Parametr|Vlastnosti|
|---------------|----------------|
|**Textura 1** - **Texture – 8**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Název souboru**: úplná cesta soubor textury, který je spojen s registrem textur.|
|**Materiál okolí**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: rozptýlení barvy aktuálního pixelu kvůli nepřímé - nebo okolí - osvětlení.|
|**Materiál rozptýlení**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel rozptýlí přímé osvětlení.|
|**Vyzařující materiál**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: podíl barvy aktuálního pixelu kvůli svým zadaná osvětlení.|
|**Reflexní materiál**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: barva, která popisuje, jak aktuální pixel odráží přímé osvětlení.|
|**Materiál síla odlesku**|**Přístup**: **veřejné** umožňující vlastnost, která má být z editoru modelů jinak **privátní**.<br /><br /> **Hodnota**: exponent, který udává intenzitu zrcadlových odlesků na aktuální pixel.|

#### <a name="time-based-effects"></a>Účinky podle času

Některé shadery mít komponentu podle času, která animuje efekt. Chcete-li zobrazit, jak účinek vypadá v praxi, verze preview musí být aktualizovány několikrát za sekundu. Ve výchozím nastavení ve verzi preview se aktualizují při změně shaderu; ke změně tohoto chování tak, aby se zobrazí podle času efekty, budete muset povolit vykreslování v reálném čase.

Chcete-li povolit vykreslování v reálném čase, na panelu nástrojů návrháře shaderu zvolte **vykreslování v reálném čase**.

#### <a name="examine-the-effect"></a>Zkontrolujte účinek

Mnoho shadery jsou ovlivněny proměnných, například zobrazení úhel nebo směrové světlo. Prozkoumat, jak reagovat účinek se tyto proměnné, můžete volně Otočení tvaru ve verzi preview a sledujte chování shaderu.

Který tvar otočí, stiskněte a podržte **Alt**a potom vyberte libovolného bodu na povrchu návrhu a přesuňte ho.

### <a name="export-shaders"></a>Exportovat shader.

Před použitím shaderu ve vaší aplikaci, musíte ho exportovat ve formátu, který se rozumí rozhraní DirectX.

Jako zdrojový kód HLSL nebo jako hodnota bytecode funkce shader kompilované můžete exportovat shadery. HLSL zdrojový kód je exportovat do textového souboru, který má *.hlsl* příponu názvu souboru. Hodnota bytecode funkce shader může být buď Nezpracovaná binární soubor, který je exportován *.cso* příponu názvu souboru nebo hlaviček jazyka C++ (*.h*) soubor, který kóduje hodnota bytecode funkce shader do pole.

Další informace o tom, jak exportovat shader, naleznete v tématu [postupy: exportování shaderu](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

|Příkaz|Klávesové zkratky|
|-------------| - |
|Přepnout na **vyberte** režimu|**CTRL**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Přepnout na **přiblížení** režimu|**CTRL**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Přepnout na **Pan** režimu|**CTRL**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Vybrat vše|**CTRL**+**A**|
|Odstranit aktuální výběr|**Delete**|
|Zrušit aktuální výběr|**Řídicí** (**Esc**)|
|Přiblížit|**CTRL**+**kolečko myši dopředu**<br /><br /> Znaménko plus (**+**)|
|Oddálit|**CTRL**+**kolečko myši dozadu**<br /><br /> Znaménko minus (**-**)|
|Posunout nahoru na návrhovou plochu|**Kolečko myši dozadu**<br /><br /> **PageDown**|
|Posunout návrhové ploše dolů|**Kolečko myši dopředu**<br /><br /> **Page Up**|
|Posunout doleva návrhové ploše|**SHIFT**+**kolečko myši dozadu**<br /><br /> **Kolečko myši doleva**<br /><br /> **SHIFT**+**PageDown**|
|Posunout doprava návrhové ploše|**SHIFT**+**kolečko myši dopředu**<br /><br /> **Kolečko myši doprava**<br /><br /> **SHIFT**+**PageUp**|
|Přesunout fokus klávesnice pro jiný uzel|**Šipku** klíče|
|Vyberte uzel, který má fokus klávesnice (přidá uzel do výběru skupiny)|**SHIFT**+**MEZERNÍK**|
|Přepnout výběr uzlu, který má fokus klávesnice|**CTRL**+**MEZERNÍK**|
|Přepne aktuální výběr (Pokud je vybráno žádné uzly, vyberte uzel, který má klávesnice fokus)|**MEZERNÍK**|
|Aktuální výběr nahoru|**SHIFT**+**šipka nahoru**|
|Aktuální výběr dolů|**SHIFT**+**šipka dolů**|
|Aktuální výběr doleva|**SHIFT**+**šipka vlevo**|
|Přesunout aktuální výběr doprava|**SHIFT**+**šipka doprava**.|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Poskytuje přehled nástroje sady Visual Studio, které můžete použít pro práci s texturami a obrazy, 3D modely a efekty shaderu.|
|[Editor obrázků](../designers/image-editor.md)|Popisuje způsob použití editoru obrázků Visual Studia pro práci s texturami a obrázky.|
|[Editor modelů](../designers/model-editor.md)|Popisuje způsob použití editoru Visual Studio Model pro práci s 3D modely.|