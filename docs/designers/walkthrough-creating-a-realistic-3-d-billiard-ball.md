---
title: 'Návod: Vytvoření realistické 3D kulečníkové koule'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0f8596e8a2064f09ff817a768dd7ec994e3c920
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847640"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Návod: Vytvoření realistické trojrozměrné kulečníkové koule

Tento návod ukazuje, jak vytvořit realistické 3D kulečníkové koule pomocí shaderu Designer a editoru obrázků v sadě Visual Studio. Vzhled 3D kulečníkové koule je dosaženo kombinací několika technik shaderu se vhodnými prostředky textur.

## <a name="prerequisites"></a>Požadavky

Budete potřebovat následující komponenty a dovednosti k dokončení tohoto návodu:

-   Nástroj pro sestavení textur do mapy krychle, jako je například nástroj DirectX Texture, který je součástí červen 2010 rozhraní DirectX SDK.

-   Důvěrně editoru obrázků v sadě Visual Studio.

-   Znalost návrháře shaderu v sadě Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Vytvoření základního vzhledu pomocí tvaru a textury

V počítačové grafice jsou nejzákladnějšími prvky vzhledu tvar a barva. V počítačové simulaci je běžné použití 3D modelu, který zastupuje tvar objektu reálného světa. Barevné detaily jsou pak použity na povrch modelu pomocí mapy textury.

Obvykle budete muset požádat umělce k vytvoření 3D modelu, který můžete použít, ale protože kulečníkové koule jsou běžné obrazce (koule), návrháře shaderu již má vhodný zabudovaný model.

Koule je výchozí tvar náhled v Návrháři shaderu; Pokud aktuálně používáte jiný tvar náhledu vašeho shaderu, přepněte zpět do oblasti.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Náhled shaderu pomocí koule

- Na panelu nástrojů návrháře shaderu zvolte **náhled s koulí.**

V dalším kroku vytvoříte program shaderu, který používá texturu na model, ale nejprve musíte vytvořit texturu, která můžete použít. Tento návod ukazuje, jak vytvořit texturu pomocí editoru obrázků, která je součástí sady Visual Studio, ale můžete použít libovolný editor obrázků, který umožňuje texturu uložit ve vhodném formátu.

Ujistěte se, že **vlastnosti** okno a **nástrojů** jsou zobrazeny.

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Vytvoření textury kulečníkové koule pomocí editoru obrázků

1. Vytvořte textur pro práci s. Informace o tom, jak přidat do projektu texturu naleznete v části Začínáme v [Editor obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby jeho šířka byla dvojnásobkem výšky; To je nezbytné vzhledem ke způsobu, že je textura mapována ke kulovému povrchu kulečníkové koule. Změna velikosti obrázku, v **vlastnosti** okno, zadejte nové hodnoty pro **šířka** a **výška** vlastnosti. Například nastavte šířku na 512 a výšku na 256.

3. Nakreslete texturu pro kulečníkovou kouli, přitom na to, jak je textura mapována na kouli.

    Textura by měl vypadat nějak takto:

    ![Texturu pro kulečníkovou kouli](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. Volitelně můžete snížit požadavky na úložiště této textury. Můžete tak učinit snížením šířky textury, aby odpovídala její výšce. Tím jsou komprimovány textury podél své šířky, ale kvůli způsobu, že je textura je mapována na kouli, ji budou rozšířeny při vykreslení kulečníkové koule. Po změně velikosti, by měla textura vypadat nějak takto:

    ![Textury kulečníkové komprimována do čtverec](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Nyní můžete vytvořit shader, který použije tuto texturu na model.

### <a name="to-create-a-basic-texture-shader"></a>K vytvoření shaderu základní textury

1. Vytvořte shader DGSL se kterým chcete pracovat. Informace o tom, jak přidat do projektu DGSL shader naleznete v části Začínáme v [návrháře shaderu](../designers/shader-designer.md).

    Standardně vypadá graf shaderu takto:

    ![Výchozí graf shaderu](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Upravte výchozí shader tak, aby použil hodnotu vzorku textury na aktuální pixel. Graf shaderu by měl vypadat takto:

    ![Graf shaderu, která se vztahuje k objektu textury](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Použijte texturu, kterou jste vytvořili v předchozím postupu konfigurací vlastností textury. Nastavte hodnotu **textury** vlastnost **vzorek textury** uzlu **Texture1**a poté určete soubor textury s použitím **Filename**vlastnost **Texture1** skupinu vlastností ve stejném okně s vlastnostmi.

   Další informace o tom, jak aplikovat texturu na shader, naleznete v tématu [postupy: vytvoření shaderu základní textury](../designers/how-to-create-a-basic-texture-shader.md).

   Vaše kulečníková koule by teď měl vypadat nějak takto:

   ![Detail textury kulečníkové koule](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Vytvoření hloubky pomocí Lambertova modelu osvětlení

Zatím jste vytvořili snadno rozpoznatelnou kulečníkovou kouli. Se zdá ploché a nezajímavé – spíše jako komiksový obrázek kulečníkové koule než její věrná replika. Zobrazení plochých výsledků ze shaderu simplistic, který se chová jako každý pixel na povrchu kulečníkové koule, obdrží stejné množství světla.

V reálném světě se světlo zdá být jasnější na površích, které přímo zdroj světla a zobrazí se méně jasné na površích, které jsou v úhlu vůči zdroji světla. Je to proto, že energie v paprscích světla je rozvržena nejmenší oblastí povrchu, pokud povrch směřuje přímo ke zdroji světla. Když se povrch otočí od světla, stejné množství energie je distribuovaná napříč stále větší plochu povrchu. Povrch, který směřuje od zdroje světla obdrží žádnou světelnou energii vůbec, výsledkem je zcela tmavý vzhled. Odchylka v jasu na povrchu objektu je důležitou vizuální nápovědou, která pomáhá určit tvar objektu; bez něj se objekt jeví plochý.

V počítačové grafice *modely osvětlení*– zjednodušené, přibližně nakreslené reálné, komplexní světelných interakcí, se používají k napodobení vzhledu skutečného osvětlení. Jak je popsáno v předchozím odstavci, Lambertova modelu osvětlení se liší v množství rozptýleně odraženého světla na povrchu objektu. Můžete přidat model osvětlení Lambert k shaderu a dát tak kulečníkové kouli přesvědčivější vzhled 3D.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Přidání Lambertova světla do vašeho shaderu

- Upravte svůj shader tak, aby moduloval hodnotu vzorku textury Lambertovou hodnotou osvětlení. Shader graf by měl vypadat takto:

   ![Graf shaderu s použitím osvětlení Lambert přidán](../designers/media/gfx_shader_demo_billiard_step_2.png)

- Volitelně můžete upravit, jak se osvětlení chová odlesk, konfigurací **MaterialDiffuse** vlastnost grafu shaderu. Přístup k vlastnostem grafu shader zvolte na prázdnou oblast návrhové plochy a potom vyhledejte vlastnost, ke které chcete získat přístup v **vlastnosti** okna.

Další informace o tom, jak aplikovat Lambert osvětlení na shader, naleznete v tématu [postupy: vytvoření základního Lambertova shaderu](../designers/how-to-create-a-basic-lambert-shader.md).

S použitím osvětlení Lambert by měla vaše kulečníková koule vypadat nějak takto:

![Detail textury a po kulečníkové koule](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Vylepšení základního vzhledu pomocí zrcadlového osvětlení

Model Lambertova osvětlení poskytuje tvar a dimenze, která chybí v shaderu pouhých textur. Kulečníkové koule stále má však poněkud matné.

Skutečné kulečníkové koule má obvykle lesklý povrch, který odráží část světla, které na ni dopadá. Některé z odráženy výsledky světla v odlesky, které simulují vlastnosti odrazného povrchu. V závislosti na vlastnostech dokončení mohou být světelné lokalizované nebo široké, intenzivní nebo malý. Tyto zrcadlové odlesky jsou modelovány pomocí vztahu mezi zdrojem světla, orientace povrchu a polohy kamery – zvýraznění je nejintenzivnější když orientace povrchu odráží světelný zdroj přímo do fotoaparát, a je méně velké zatížení při zrcadlení je méně přímé.

Model osvětlení Phong je založena na modelu osvětlení Lambert k zahrnoval odlesky, jak je popsáno v předchozím odstavci. Můžete přidat model osvětlení Phong k shaderu a dát tak kulečníkové kouli umělý povrch, jehož výsledkem zajímavější vzhled.

### <a name="to-add-specular-highlights-to-your-shader"></a>Přidání odlesků do vašeho shaderu

1. Upravte svůj shader tak, aby zahrnoval příspěvek lesku pomocí aditivního míchání. Shader graf by měl vypadat takto:

    ![Graf shaderu pomocí zrcadlového osvětlení přidat](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. Volitelně můžete upravit způsob, jakým chová odlesk, konfigurací vlastností odlesků (**MaterialSpecular** a **MaterialSpecularPower**) grafu shaderu. Chcete-li získat přístup k vlastnostem grafu shader zvolte na prázdnou oblast návrhové plochy a pak v **vlastnosti** okna, vyhledejte vlastnost, ke které chcete získat přístup.

   Další informace o tom, jak aplikovat Zrcadlové osvětlení na shader, naleznete v tématu [postupy: vytvoření základního Phongova shaderu](../designers/how-to-create-a-basic-phong-shader.md).

   S zvýrazňujících vaše kulečníková koule by měl vypadat nějak takto:

   ![Přidání detail kulečníkové koule pomocí odlesku](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Vytváření vnímání prostoru pomocí odrazu prostředí

Vaše kulečníková koule vypadá s odlesků poměrně přesvědčivě. Má obor správný tvar, správnou malbu a správné konečné propracování. Existuje však ještě jedna další metoda, která způsobí, že vaše kulečníková koule vypadat více jako součást prostředí.

Pokud byste pečlivě zkontrolovat skutečné kulečníkové koule, uvidíte, že její lesklý povrch není právě světla, ale také prohlédnete odráží obrázek svět. Tento odraz můžete simulovat pomocí bitové kopie prostředí jako texturu a kombinaci s vlastní texturou modelu k určení konečné barvy jednotlivých obrazových bodů. V závislosti na druhu dokončení, které chcete, můžete kombinovat více nebo méně odrazové textury se zbytkem shaderu. Například shader, který simuluje vysoce odrazivý povrch, jako je zrcadlení může použít pouze pro texturu odrazu, ale shader, který simuluje jemnější odraz, jako je na kulečníkové kouli, lze kombinovat s pouze malou část odrazu hodnoty textury, spolu s ostatními výpočty shaderu.

Samozřejmě nestačí pouze použít zrcadlený obraz modelu stejným způsobem, že použijete mapu textur modelu. Pokud jste provedli, odraz světa by posunula s kulečníkovou koulí, jako kdyby ni odraz byl přilepen k němu. Protože odraz může pocházet z libovolného směru, je třeba poskytnout hodnotu mapy odrazů pro každý úhel a způsob, jak mapu odrazu globálně orientovat. Pokud chcete splnit tyto požadavky můžete použít speciální typ mapy textury – volána *stranou mapy krychle*–, který poskytuje šest textur uspořádaných tak, aby tvořily strany krychle. Z vnitřního prostoru této krychle můžete ukázat v libovolném směru a najít tak hodnotu textury. Když textury na každé straně krychle obsahují obrázky prostředí, můžete simulovat jakýkoli odraz vzorkováním správného umístění na povrch datové krychle. Udržováním krychle zarovnán na světě, získáte přesný odraz prostředí. Pokud chcete zjistit, kde datové krychle vzorkování, stačí vypočítat odraz vektoru fotoaparátu povrchu objektu a použít jej jako souřadnice 3D textury. Použití mapy krychle tímto způsobem je běžná technika, která se označuje jako *mapování prostředí*.

Mapování prostředí poskytuje efektivní přiblížení skutečným odrazům popsaným v předchozích odstavcích. Odrazy mapovaného prostředí lze smíchat vašeho shaderu a dát tak kulečníkové kouli, které umělý povrch, který umožňuje kulečníkové kouli dojem, že další začleněna ve scéně.

Prvním krokem je vytvoření textury mapy krychle. U mnoha druhů aplikací obsah krychlové mapy nemusí být dokonalý, aby byl efektivní, zejména v případě, je odraz slabý nebo nezaujímá nápadné místo na obrazovce. Například, mnoho her například používá předvypočtenou krychli pro mapování prostředí a pouze ten nejbližší odrazný objekt, ač to znamená, že odraz není správný. I hrubé přiblížení je často dostatečné pro dosažení přesvědčivého efektu.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Tvorba textur pro mapování prostředí pomocí editoru obrázků

1. Vytvořte textur pro práci s. Informace o tom, jak přidat do projektu texturu naleznete v části Začínáme v [Editor obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby jeho šířka rovná jeho výška a je mocninou čísla 2 velikosti; To je nezbytné vzhledem ke způsobu, že se indexuje zpětně mapy krychle. Změna velikosti obrázku, v **vlastnosti** okno, zadejte nové hodnoty pro **šířka** a **výška** vlastnosti. Například nastavte hodnotu **šířka** a **výška** na 256.

3. K vyplnění textury použijte plnou barvu. Tato textura bude spodní stranou mapy krychle, která odpovídá povrchu kulečníkového stolu. Mějte barvu, kterou jste použili pro další textury.

4. Vytvořte druhou texturu, která má stejnou velikost jako první. Tato textura bude opakována na čtyřech stranách mapy krychle, které odpovídají povrchu a po stranách kulečníkového stolu a oblasti kolem kulečníkového stolu. Ujistěte se, že nakreslete povrch kulečníkového stolu v této textuře s použitím stejné barvy jako u spodní textury. Textura by měl vypadat nějak takto:

    ![Textury pro strany mapy krychle](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Mějte na paměti, že mapa odrazů nemusí být fotorealistická, aby byla platná; například mapa krychle použitá k vytvoření obrázků v tomto článku obsahuje pouze čtyři kapsy místo šesti.

5. Vytvořte třetí texturu, která má stejnou velikost jako ostatní. Tato textura bude horní stranou mapy krychle, která odpovídá povrchu stropu nad kulečníkovým stolem. Chcete-li tuto část odrazu zajímavější, můžete nakreslit režijní světlo, aby byly posíleny odlesky, které jste přidali k shaderu v předchozím postupu. Textura by měl vypadat nějak takto:

    ![Textury v horní části cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Teď, když jste vytvořili individuální textury pro strany krychlové mapy, můžete použít nástroje sestavit do krychlové mapy, která mohou být uloženy v jednom *.dds* textury. Můžete použít libovolný program, kterou chcete vytvořit stranou mapy krychle, tak dlouho, dokud ho uložit stranou mapy krychle do formátu textury .dds. Tento návod ukazuje, jak vytvořit texturu pomocí nástroje textury rozhraní DirectX, který je součástí červen 2010 DirectX SDK.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>K sestavení mapy krychle pomocí nástroje textury rozhraní DirectX

1. V nástroji pro textury DirectX v hlavní nabídce zvolte **souboru** > **Nová textura**. **Nová textura** zobrazí se dialogové okno.

2. V **typ textury** skupině, zvolte **textura Cubemap**.

3. V **dimenze** skupině, zadejte správné hodnoty pro **šířka** a **výška**a klikněte na tlačítko **OK**. Zobrazí se nový dokument textury. Ve výchozím nastavení, odpovídá textury prvním zobrazení v dokumentu **kladná X** krychle.

4. Načtěte texturu, kterou jste vytvořili pro boční část texturové krychle do ploška krychle. V hlavní nabídce zvolte **souboru** > **otevřít na tuto plošku**, vyberte texturu vytvořenou pro stranu krychle a pak zvolte **otevřít**.

5. Opakujte krok 4 pro **záporné X**, **kladné Z**, a **záporné Z** plošky krychle. Uděláte to tak, musíte zobrazíte plošku, kterou chcete načíst. Zobrazíte jinou ploška mapy, v hlavní nabídce zvolte **zobrazení** > **mapa plošek krychle**a poté vyberte plošku, kterou chcete zobrazit.

6. Pro **Y pozitivní** krychle, načtěte texturu, kterou jste vytvořili pro horní část texturové krychle.

7. Pro **Y negativní** krychle, načtěte texturu, kterou jste vytvořili pro dolní část texturové krychle.

8. Uložte texturu.

   Můžete si představit rozložení cubemap takto:

   ![Rozložení cubemap prostředí](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Obrázek navrchu je pozitivní ploška krychle Y (+ Y); uprostřed zleva doprava je -X, + Z, + X a -Z datové krychle tváří; dole je ploška krychle -Y.

   Nyní můžete upravit shader tak zapojil vzorek mapy krychle do zbytku shaderu.

### <a name="to-add-environment-mapping-to-your-shader"></a>Přidání mapování prostředí vašeho shaderu

1. Upravte svůj shader tak zahrnoval příspěvek mapování prostředí pomocí aditivního míchání. Shader graf by měl vypadat takto:

    ![Detail oba uzly druh reflektivní shaderu](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Všimněte si, že můžete použít **vynásobit-přidat** uzlu ke zjednodušení grafu shaderu.

    Tady je podrobnější zobrazení uzlů shaderu, které implementují mapování prostředí:

    ![Graf shaderu se přidá mapování prostředí](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Použijte texturu, kterou jste vytvořili v předchozím postupu konfigurací vlastností textury mapy krychle. Nastavte hodnotu **textury** vlastnost **vzorek Cubemap** uzlu **Texture2**a poté určete soubor textury s použitím **Filename**vlastnost **Texture2** skupiny vlastností.

3. Volitelně můžete upravit Odrazivost kulečníkové koule konfigurací **výstup** vlastnost **konstantní** uzlu. Pokud chcete získat přístup k vlastnostem uzlu, vyberte ji a pak v **vlastnosti** okno, vyhledejte vlastnost, ke které chcete získat přístup.

   S použitím mapování prostředí použít, vaše kulečníková koule by měl vypadat nějak takto:

   ![Detail z namapované kulečníkové koule prostředí](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   V tomto konečném obrazu si všimněte si, jak efekty, které jste přidali setkávají, aby se vytvoření velmi přesvědčivou kulečníkovou kouli. Tvar, textury a osvětlení tvoří základní vzhled 3D objektu a zrcadlové odlesky nebo odrazy zkontrolujte kulečníkovou kouli zajímavější a začleňují svého prostředí.

## <a name="see-also"></a>Viz také:

- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Návrhář shaderů](../designers/shader-designer.md)
- [Editor obrázků](../designers/image-editor.md)
- [Uzly návrháře shaderů](../designers/shader-designer-nodes.md)