---
title: 'Návod: vytvoření realistické 3D Kulečníkovéové kuličky'
description: Naučte se vytvářet prostorovou kuličku kulečníkové pomocí Návrháře shaderu a editoru obrázků v aplikaci Visual Studio kombinováním technik shaderu s prostředky textury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5469825b8d81a210fdb699dc9afeb7c6689953b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896453"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Návod: Vytvoření realistické trojrozměrné kulečníkové koule

Tento návod ukazuje, jak vytvořit realistickou kuličku 3D kulečníkové pomocí Návrháře shaderu a editoru obrázků v aplikaci Visual Studio. 3D vzhled kuličky kulečníkové se dosahuje kombinací několika technik shaderu s příslušnými prostředky textury.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete tyto komponenty a dovednosti:

- Nástroj pro sestavení textur do mapy krychle, jako je například nástroj textura DirectX, který je součástí června 2010 DirectX SDK.

- Seznamte se dobře s editorem obrázků v aplikaci Visual Studio.

- Seznamte se se znalostí pro návrháře shaderů v aplikaci Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Vytvoření základního vzhledu pomocí tvaru a textury

V počítačové grafice jsou nejvíc základní prvky vzhledu tvar a barva. V simulaci počítače je běžné použít 3D model k reprezentaci tvaru reálného objektu. Podrobnosti o barvách se pak aplikují na povrch modelu pomocí mapy textury.

Obvykle může být nutné požádat o pomoc autora 3D model, kterou můžete použít, ale vzhledem k tomu, že kulečníkové míč je společný tvar (koule), Designer shaderu již obsahuje vhodný model integrovaný v.

Koule je výchozí tvar náhledu v Návrháři shaderu; Pokud aktuálně používáte jiný tvar k zobrazení náhledu shaderu, přepněte zpět do koule.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Náhled shaderu pomocí koule

- Na panelu nástrojů návrháře shaderů vyberte **Náhled pomocí sphere.**

V dalším kroku vytvoříte program shaderu, který pro model aplikuje texturu, ale nejdřív musíte vytvořit texturu, kterou můžete použít. Tento návod ukazuje, jak vytvořit texturu pomocí editoru obrázků, který je součástí sady Visual Studio, ale můžete použít libovolný editor obrázků, který může texturu uložit ve vhodném formátu.

Ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Vytvoření textury kulečníkové míč pomocí editoru obrázků

1. Vytvořte texturu, se kterou chcete pracovat. Informace o tom, jak přidat texturu do projektu, naleznete v části Začínáme v [editoru obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby jeho šířka byla dvojnásobnou výškou. To je nezbytné z důvodu, že textura je namapována na kulové plochu kulečníkové kuličky. Chcete-li změnit velikost obrázku, v okně **vlastnosti** zadejte nové hodnoty vlastností **Width** a **Height** . Nastavte například šířku na 512 a výšku na 256.

3. Nakreslete texturu pro kulečníkové kuličku a mějte na paměti, jak je textura namapována na objekt sphere.

    Textura by měla vypadat nějak takto:

    ![Textura pro kulečníkové míč](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. Volitelně můžete chtít snížit požadavky na úložiště této textury. To můžete udělat tak, že zmenšíte šířku textury tak, aby odpovídala její výšce. Tím se komprimuje textura podél šířky, ale kvůli způsobu, jakým je textura namapována na koulí, se rozšíří při vykreslení kuličky kulečníkové. Po změně velikosti by textura měla vypadat nějak takto:

    ![Kulečníkové textura komprimovaná do čtverce](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Nyní můžete vytvořit shader, který aplikuje tuto texturu na model.

### <a name="to-create-a-basic-texture-shader"></a>Vytvoření základního shaderu textury

1. Vytvořte DGSL shader, který bude fungovat. Informace o tom, jak přidat DGSL shader do projektu, naleznete v části Začínáme v [Návrháři shaderu](../designers/shader-designer.md).

    Ve výchozím nastavení vypadá graf shaderu takto:

    ![Výchozí graf shaderu](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Upravte výchozí shader tak, aby se hodnota vzorku textury naplatila na aktuální pixel. Graf shaderu by měl vypadat takto:

    ![Graf shaderu, který aplikuje texturu na objekt](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Použijte texturu, kterou jste vytvořili v předchozím postupu konfigurací vlastností textury. Nastavte hodnotu vlastnosti **Textura** uzlu **Ukázka textury** na **Texture1** a pak zadejte soubor textury pomocí vlastnosti **filename** skupiny vlastností **Texture1** ve stejném okně vlastností.

   Další informace o tom, jak použít texturu v shaderu, naleznete v tématu [How to: Create a Basic textur shader](../designers/how-to-create-a-basic-texture-shader.md).

   Kulečníkové míč by teď měl vypadat nějak takto:

   ![Closeup kulečníkovéé kuličky s texturou](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Vytvoření hloubky pomocí modelu osvětlení Lambert

Zatím jste vytvořili snadno rozpoznatelnou kulečníkové míč. Vypadá to ale plochý a nezajímavý – víc jako kreslený obrázek kulečníkovéové kuličky než přesvědčit se o replice. Plochý vzhled výsledků shaderu zjednodušený, který se chová, jako by každý pixel na povrchu kuličky kulečníkové získal stejné množství světla.

V reálném světě se světlo jeví jasně na površích, které přímo čelí zdroji světla a jsou méně jasné na površích, které jsou v nakloněném úhlu ke zdroji světla. Důvodem je to, že energie v lehkých paprskech je distribuována v nejmenší oblasti povrchu, když povrch přímo čelí zdroji světla. Když se povrch odrazí od zdroje světla, stejné množství energie je distribuované napříč stále větší oblastí povrchu. Plocha, kterou čelí zdroji světla, nepřijímá vůbec žádnou světlou energií, což má za následek zcela tmavý vzhled. Tato variance v jasu napříč povrchem objektu je důležitý vizuální signál, který pomáhá indikovat tvar objektu. bez něj je objekt zobrazen plochý.

*Modely osvětlení* v počítačové grafice – zjednodušené sbližování komplexních a reálných světelných interakcí – slouží k replikaci vzhledu reálného osvětlení. Model osvětlení Lambert se liší v množství rozptýleného světla v rámci povrchu objektu, jak je popsáno v předchozím odstavci. K shaderu můžete přidat model osvětlení Lambert, aby kulička kulečníkové lépe přesvědčila 3D vzhled.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Přidání osvětlení Lambert do shaderu

- Upravte svůj shader tak, aby moduloval hodnotu vzorku textury Lambert světelným hodnotou. Váš graf shaderu by měl vypadat takto:

   ![Graf shaderu s přidaným osvětlením Lambert](../designers/media/gfx_shader_demo_billiard_step_2.png)

- Volitelně můžete upravit způsob chování osvětlení konfigurací vlastnosti **MaterialDiffuse** grafu shaderu. Chcete-li získat přístup k vlastnostem grafu shader, zvolte prázdnou oblast návrhové plochy a poté v okně **vlastnosti** vyhledejte vlastnost, ke které chcete získat přístup.

Další informace o tom, jak použít Lambert osvětlení v shaderu, naleznete v tématu [How to: Create a Basic Lambert Shader](../designers/how-to-create-a-basic-lambert-shader.md).

V případě použití osvětlení Lambert by vaše kulečníkovéová kulička měla vypadat nějak takto:

![Closeup kuličky s texturou a osvětlenou kulečníkovéou](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Vylepšení základního vzhledu pomocí zrcadlových světel

Model osvětlení Lambert poskytuje smysl tvar a dimenze, které nebyly přítomny v shaderu pouze s texturou. Kulička kulečníkové však stále obsahuje trochu tlumený vzhled.

Skutečná kulečníkové kulička má obvykle lesklý povrch, který odráží část světla, která je na ní. Některé z nich reflektují světlé výsledky na zrcadlové světla, které simulují reflektování vlastností povrchu. V závislosti na vlastnostech dokončení je možné hlavní a široké, náročné nebo jemné. Tato zrcadlová odrazy jsou modelovány pomocí vztahu mezi zdrojem světla, orientace povrchu a polohy kamery – to znamená, že zvýraznění je nejvýraznější, pokud orientace povrchu odráží zdroj světla přímo do kamery a je méně velký, pokud je odraz méně přímý.

Model osvětlení Phongova sestaví na modelu osvětlení Lambert, aby zahrnoval odlesky, jak je popsáno v předchozím odstavci. K shaderu můžete přidat model osvětlení Phongova a dát kuličku kulečníkové simulované dokončení, které má za následek zajímavější vzhled.

### <a name="to-add-specular-highlights-to-your-shader"></a>Přidání zrcadlových světel do shaderu

1. Upravte svůj shader tak, aby zahrnoval odleskový příspěvek pomocí doplňkového míchání. Váš graf shaderu by měl vypadat takto:

    ![Graf shaderu s přidaným odleskem světla](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. Volitelně můžete upravit způsob, jakým se zrcadlové zvýrazňování chová, konfigurací zrcadlových vlastností (**MaterialSpecular** a **MaterialSpecularPower**) v grafu shaderu. Chcete-li získat přístup k vlastnostem grafu shader, zvolte prázdnou oblast návrhové plochy a poté v okně **vlastnosti** vyhledejte vlastnost, ke které chcete získat přístup.

   Další informace o tom, jak použít odlesky v shaderu, naleznete v tématu [How to: Create a Basic Phongova shader](../designers/how-to-create-a-basic-phong-shader.md).

   V případě použití zrcadlového zvýraznění by vaše kulečníkovéová kulička měla vypadat nějak takto:

   ![Closeup kuličky kulečníkové s přidanými odlesky](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Vytvoření smyslu prostoru díky reflektování prostředí

V případě, že se odlesky aplikují, vaše kulečníkovéová kulička vypadá poměrně přesvědčivě. Máte správný tvar, pravou úlohu Malování a správné dokončení. Je však stále ještě jedna další technika, která bude kulečníkové míč vypadat lépe jako součást svého prostředí.

Pokud prohlížíte skutečnou kulečníkovéou kuličku, uvidíte, že jeho lesklý povrch se neprojeví pouze odlesky, ale také nezřetelně odráží obrázek celého světa. Tento odraz můžete simulovat použitím obrázku prostředí jako textury a jeho kombinací s vlastní texturou modelu pro určení konečné barvy jednotlivých pixelů. V závislosti na typu požadovaného dokončení můžete kombinovat více nebo méně textur odrazu spolu se zbytkem shaderu. Například shader, který simuluje vysoce odrážetelné plochy, jako je například zrcadlo, může používat pouze texturu reflexe, ale shader, který simuluje jemnější odraz, jako ten, který se nachází na kulečníkové míč, může kombinovat pouze malou část hodnoty textury reflexe spolu se zbytkem výpočtu shaderu.

Samozřejmě nemůžete pouze použít reflektující obraz na model stejným způsobem jako texturová mapa modelu. Pokud jste to dělali, odraz světa by se přesunul s kulečníkové kuličkou, jako kdyby k němu byl odraz připevněný. Vzhledem k tomu, že odraz může přijít z libovolného směru, potřebujete způsob, jak poskytnout hodnotu mapy reflexe pro libovolný úhel a způsob, jak udržet mapu odrazů orientované podle světa. Aby bylo možné tyto požadavky splnit, můžete použít speciální druh mapy textury, která se nazývá *mapa krychle*, která poskytuje šest textur uspořádaných pro vytvoření stran datové krychle. V rámci této krychle můžete Ukázat libovolným směrem, abyste našli hodnotu textury. Pokud textury na každé straně krychle obsahují obrázky prostředí, můžete simulovat jakýkoli odraz vzorkováním správného umístění na povrchu krychle. Udržováním krychle zarovnané na světě získáte přesný odraz prostředí. Chcete-li určit, kde by měla být datová krychle Navzorkovaná, stačí vypočítat odraz vektoru kamery mimo povrch objektu a pak ho použít jako 3D souřadnice textury. Použití map krychle tímto způsobem je běžnou technikou, která se označuje jako *mapování prostředí*.

Mapování prostředí poskytuje efektivní aproximaci skutečných odrazů, jak je popsáno v předchozích odstavcích. Odrazy namapované do prostředí můžete prolnout do svého shaderu, aby kulečníkové míč bylo simulované dokončení, které povede k většímu rozmístění kuličky kulečníkové na scéně.

Prvním krokem je vytvoření textury mapy krychle. V mnoha typech aplikací nemusí být obsah mapy krychle účinný, zejména v případě, že je odraz nekvalitní nebo na obrazovce nezaujímají výrazné místo. Mnoho her například používá předem vypočtené mapy krychlí pro mapování prostředí a stačí použít nejbližší objekt, který je nejblíže každému odrážející objekt, i když to znamená, že odraz není správný. I hrubá aproximace je často dostatečně dobrá pro přepřesvědčivý účinek.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Vytvoření textur pro mapu prostředí pomocí editoru obrázků

1. Vytvořte texturu, se kterou chcete pracovat. Informace o tom, jak přidat texturu do projektu, naleznete v části Začínáme v [editoru obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby se jeho šířka rovnala výšce, a má velikost mocniny dvě. To je nezbytné z důvodu způsobu, jakým je mapa krychle indexována. Chcete-li změnit velikost obrázku, v okně **vlastnosti** zadejte nové hodnoty vlastností **Width** a **Height** . Například nastavte hodnotu vlastnosti **Width** a **Height** na 256.

3. K vyplnění textury použijte plnou barvu. Tato textura bude dolní část mapy krychle, která odpovídá povrchu tabulky kulečníkové. Mějte na paměti, že na další texturu jste použili barvu.

4. Vytvořte druhou texturu, která má stejnou velikost jako první. Tato textura se bude opakovat na čtyřech stranách mapy krychle, která odpovídá povrchu a stěnám tabulky kulečníkové a oblasti kolem tabulky kulečníkové. Nezapomeňte nakreslit plochu tabulky kulečníkové v této textuře pomocí stejné barvy jako v dolní textuře. Textura by měla vypadat nějak takto:

    ![Textura pro strany cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Pamatujte, že mapa odrazů nemusí být fotorealistické, aby byla účinná; Například mapa krychle použitá k vytvoření imagí v tomto článku obsahuje pouze čtyři kapsy místo šesti.

5. Vytvořte třetí texturu, která má stejnou velikost jako ostatní. Tato textura bude horní částí mapy krychle, která odpovídá hornímu hranici nad tabulkou kulečníkové. Chcete-li tuto část reflexe udělat zajímavější, můžete vykreslit režijní světlo, abyste posílili odlesky, které jste přidali do shaderu v předchozím postupu. Textura by měla vypadat nějak takto:

    ![Textura horní části cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Nyní, když jste vytvořili jednotlivé textury pro strany mapy krychle, můžete použít nástroj k jejich sestavení do mapy krychle, která může být uložena v jedné textuře *. dds* . Můžete použít libovolný program, který chcete vytvořit mapa krychle, pokud je možné uložit mapu krychle ve formátu. DDS Texture. Tento návod ukazuje, jak vytvořit texturu pomocí nástroje DirectX textur, který je součástí června 2010 SDK pro DirectX.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Sestavení mapy krychle pomocí nástroje DirectX textur Tool

1. V nástroji pro texturu DirectX v hlavní nabídce vyberte možnost **soubor**  >  **Nová textura**. Zobrazí se dialogové okno **Nová textura** .

2. Ve skupině **Typ textury** vyberte **cubemap textura**.

3. Ve skupině **dimenze** zadejte správnou hodnotu pro **šířku** a **výšku** a pak zvolte **OK**. Zobrazí se nový dokument textury. Ve výchozím nastavení textura zobrazená jako první v dokumentu textury odpovídá pozitivní ploše krychle **X** .

4. Načtěte texturu, kterou jste vytvořili pro stranu datové krychle textury, na plochu krychle. V hlavní nabídce zvolte **soubor**  >  **otevřít na tuto cubemap plochu**, vyberte texturu, kterou jste vytvořili pro stranu datové krychle, a pak zvolte **otevřít**.

5. Opakujte krok 4 pro plošky krychlí **záporné X**, **kladné Z** a **záporné** . K tomu je třeba zobrazit plošku, kterou chcete načíst. Chcete-li zobrazit jinou plošku mapy krychle, zvolte v hlavní nabídce možnost **Zobrazit**  >  **mapu krychle** a potom vyberte plošku, kterou chcete zobrazit.

6. Pro plošku **pozitivní osy Y** načtěte texturu, kterou jste vytvořili pro začátek datové krychle textury.

7. Pro obličej **záporné** krychle Y načtěte texturu, kterou jste vytvořili pro dolní část datové krychle textury.

8. Uložte texturu.

   Můžete si představit, jak vypadá rozvržení krychle:

   ![Rozložení mapy krychle prostředí](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Obrázek v horní části je pozitivní obličej krychle Y (+ Y); uprostřed zleva doprava jsou plošky krychle-X, + Z, + X a-Z. v dolní části je vzhled datové krychle-Y.

   Nyní můžete upravit shader tak, aby byl vzorek mapy krychle smíchán do zbytku shaderu.

### <a name="to-add-environment-mapping-to-your-shader"></a>Přidání mapování prostředí do shaderu

1. Upravte svůj shader tak, aby zahrnoval příspěvek mapování prostředí pomocí doplňkového míchání. Váš graf shaderu by měl vypadat takto:

    ![Closeup druhu odrážejících uzlů shaderu](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Všimněte si, že k zjednodušení grafu shaderu můžete použít uzel **násobný přidat** .

    Zde je podrobnější zobrazení uzlů shaderu, které implementují mapování prostředí:

    ![Graf shaderu s přidaným mapováním prostředí](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Použijte texturu, kterou jste vytvořili v předchozím postupu konfigurací vlastností textury mapy krychle. Nastavte hodnotu vlastnosti **Textura** **cubemap uzlu Sample** na **Texture2** a pak zadejte soubor textury pomocí vlastnosti **filename** skupiny vlastností **Texture2** .

3. Volitelně můžete upravit odrazivost kuličky kulečníkové tak, že nakonfigurujete vlastnost **Output** pro **konstantní** uzel. Chcete-li získat přístup k vlastnostem uzlu, vyberte jej a potom v okně **vlastnosti** vyhledejte vlastnost, ke které chcete získat přístup.

   Po použití mapování prostředí by vaše kulečníkovéová kulička měla vypadat nějak takto:

   ![Closeup prostředí mapované kulečníkovéé kuličky](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   V tomto finálním obrázku si všimněte, jak přidávané efekty společně vytvářejí kulečníkové míč. Tvar, textura a osvětlení vytvoří základní vzhled 3D objektu a zrcadlové světla a odrazy usnadňují kulečníkové míč zajímavější a vypadají jako součást svého prostředí.

## <a name="see-also"></a>Viz také

- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Editor obrázků](../designers/image-editor.md)
- [Uzly návrháře shaderu](../designers/shader-designer-nodes.md)
