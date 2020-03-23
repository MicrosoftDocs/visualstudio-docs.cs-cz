---
title: 'Návod: Vytvoření realistické 3D kulečníkové koule'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 866f91303c224f8330a4d2be76f3d29331fcb346
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589913"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Návod: Vytvoření realistické trojrozměrné kulečníkové koule

Tento návod ukazuje, jak vytvořit realistickou 3D kulečníkovou kouli pomocí návrháře shaderu a editoru obrázků v sadě Visual Studio. 3D vzhled kulečníkové koule je dosaženo kombinací několika technik shaderu s vhodnými texturními zdroji.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu potřebujete následující součásti a dovednosti:

- Nástroj pro sestavení textur do mapy krychle, například nástroj textury DirectX, který je součástí sady DirectX SDK z června 2010.

- Seznamte se s Editorem obrázků v sadě Visual Studio.

- Seznamte se s návrhářem shaderu v sadě Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Vytvoření základního vzhledu s tvarem a texturou

V počítačové grafice jsou nejzákladnějšími prvky vzhledu tvar a barva. V počítačové simulaci je běžné používat 3D model k reprezentaci tvaru objektu reálného světa. Barevné detaily se pak aplikují na povrch modelu pomocí mapy textury.

Obvykle budete muset požádat umělce, aby vytvořil 3D model, který můžete použít, ale protože kulečníková koule je běžný tvar (koule), návrhář shaderu již má vestavěný vhodný model.

Koule je výchozí obrazec náhledu v návrháři shaderu; Pokud aktuálně používáte jiný obrazec k zobrazení náhledu shaderu, přepněte zpět do koule.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Zobrazení náhledu shaderu pomocí koule

- Na panelu nástrojů Návrhář shaderu zvolte **Náhled s koulí.**

V dalším kroku vytvoříte program shaderu, který aplikuje texturu na model, ale nejprve musíte vytvořit texturu, kterou můžete použít. Tento návod ukazuje, jak vytvořit texturu pomocí Editoru obrázků, který je součástí sady Visual Studio, ale můžete použít libovolný editor obrázků, který můžete uložit texturu ve vhodném formátu.

Ujistěte se, že jsou zobrazeny okno **Vlastnosti** a **panel nástrojů.**

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Vytvoření textury kulečníkové koule pomocí Editoru obrázků

1. Vytvořte texturu, se které chcete pracovat. Informace o tom, jak přidat texturu do projektu, naleznete v části Začínáme v [Editoru obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby jeho šířka byla dvakrát větší než jeho výška; to je nezbytné z důvodu způsobu, jakým je textura mapována na sférický povrch kulečníkové koule. Chcete-li změnit velikost obrazu, zadejte v okně **Vlastnosti** nové hodnoty pro vlastnosti **Šířka** a **Výška.** Například nastavte šířku na 512 a výšku na 256.

3. Nakreslete texturu pro kulečníkovou kouli a mějte na paměti, jak je textura mapována na kouli.

    Textura by měla vypadat podobně jako tato:

    ![Textura pro kulečníkovou kouli](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. Volitelně můžete chtít snížit požadavky na úložiště této textury. Můžete to udělat snížením šířky textury tak, aby odpovídala její výšce. To komprimuje texturu podél její šířky, ale vzhledem ke způsobu, jakým je textura mapována na kouli, bude rozšířena, když je vykreslena kulečníková koule. Po změna velikosti by měla textura vypadat podobně jako tato:

    ![Kulečníková textura stlačená do čtverce](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Nyní můžete vytvořit shader, který aplikuje tuto texturu na model.

### <a name="to-create-a-basic-texture-shader"></a>Vytvoření základního shaderu textury

1. Vytvořte shader DGSL, se kterým chcete pracovat. Informace o tom, jak přidat shader SChL do projektu, naleznete v části Začínáme v [návrháři shaderu](../designers/shader-designer.md).

    Ve výchozím nastavení vypadá graf shaderu takto:

    ![Výchozí graf shaderu](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Upravte výchozí shader tak, aby na aktuální obrazový bod aplišoval hodnotu vzorku textury. Graf shaderu by měl vypadat takto:

    ![Graf shaderu, který aplikuje texturu na objekt](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Použijte texturu, kterou jste vytvořili v předchozím postupu, konfigurací vlastností textury. Nastavte hodnotu vlastnosti **Textura** uzlu Vzorek textury na **Texturu1** a pak určete soubor textury pomocí vlastnosti **Název_souboru** skupiny vlastností **Textura1** ve stejném okně vlastností. **Texture1**

   Další informace o použití textury v shaderu najdete v [tématu Postup: Vytvoření základního shaderu textury](../designers/how-to-create-a-basic-texture-shader.md).

   Váš kulečníkový míč by nyní měl vypadat podobně jako tento:

   ![Detailní krok s texturovanou kulečníkovou koulí](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Vytvořte hloubku s modelem osvětlení Lambert

Zatím jste vytvořili snadno rozpoznatelný kulečníkový míč. Zdá se však, že je plochá a nezajímavá - spíše jako kreslený obrázek kulečníkové koule než přesvědčivá replika. Plochý vzhled je výsledkem zjednodušujícího shaderu, který se chová, jako by každý pixel na povrchu kulečníkové koule obdržel stejné množství světla.

V reálném světě se světlo jeví nejjasněji na plochách, které přímo směřují ke zdroji světla, a na plochách, které jsou v šikmém úhlu ke zdroji světla, se zobrazuje méně jasně. Je to proto, že energie v světelných paprscích je rozložena na nejmenší plochu, když povrch přímo směřuje ke zdroji světla. Jak se povrch odvrací od světelného zdroje, stejné množství energie je rozloženo na stále větší plochu. Povrch, který směřuje od světelného zdroje, nepřijímá vůbec žádnou světelnou energii, což má za následek zcela tmavý vzhled. Tato odchylka jasu na povrchu objektu je důležitým vizuálním podnětem, který pomáhá indikovat tvar objektu; bez něj se objekt zobrazí plochý.

V počítačové grafice se *modely osvětlení*– zjednodušené aproximace složitých interakcí osvětlení v reálném světě – používají k replikaci vzhledu reálného osvětlení. Model osvětlení Lambert mění množství rozptýleného odraženého světla na povrchu objektu, jak je popsáno v předchozím odstavci. Do shaderu můžete přidat model osvětlení Lambert, abyste získali kulečníkovou kouli přesvědčivějším 3D vzhledem.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Přidání osvětlení Lambert do shaderu

- Upravte shader, abyste modulovali hodnotu vzorku textury hodnotou Osvětlení Lambert. Graf shaderu by měl vypadat takto:

   ![Shader graf s osvětlením Lambert přidán](../designers/media/gfx_shader_demo_billiard_step_2.png)

- Volitelně můžete upravit chování osvětlení konfigurací **vlastnosti MaterialDiffuse** grafu shaderu. Chcete-li získat přístup k vlastnostem grafu shaderu, zvolte prázdnou oblast návrhového povrchu a vyhledejte vlastnost, ke které chcete získat přístup, v okně **Vlastnosti.**

Další informace o použití osvětlení Lambert v shaderu naleznete v [tématu How to: Create a basic Lambert shader](../designers/how-to-create-a-basic-lambert-shader.md).

S lambert osvětlení použít, váš kulečníkmíč by měl vypadat podobně jako toto:

![Detailní efekt texturované a osvětlené kulečníkové koule](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Vylepšení základního vzhledu pomocí odlesků

Model osvětlení Lambert poskytuje pocit tvaru a rozměru, který chyběl v shaderu pouze pro texturu. Nicméně, kulečníková koule má stále poněkud nudný vzhled.

Skutečný kulečníkový kulička má obvykle lesklý povrch, který odráží část světla, které na něj dopadá. Některé z těchto odražených světel mají za následek odlesky, které simulují odrazné vlastnosti povrchu. V závislosti na vlastnostech povrchové úpravy mohou být zvýraznění lokalizována nebo široká, intenzivní nebo jemná. Tyto zrcadlové odrazy jsou modelovány pomocí vztahu mezi zdrojem světla, orientací povrchu a polohou kamery – to znamená, že zvýraznění je nejintenzivnější, když orientace povrchu odráží světelný zdroj přímo do fotoaparátu a je méně intenzivní, když je odraz méně přímý.

Model osvětlení Phong navazuje na model osvětlení Lambert tak, aby zahrnoval odlesky, jak je popsáno v předchozím odstavci. Do shaderu můžete přidat model osvětlení Phong, abyste získali kulečníkovou kouli simulovanou úpravou, která má za následek zajímavější vzhled.

### <a name="to-add-specular-highlights-to-your-shader"></a>Přidání zrcadlových světel do shaderu

1. Upravte shader tak, aby zahrnoval zrcadlový příspěvek pomocí aditivního prolnutí. Graf shaderu by měl vypadat takto:

    ![Shader graf s zrcadlovým osvětlením přidán](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. Volitelně můžete upravit způsob, jakým se zrcadlové zvýraznění chová, konfigurací zrcadlových vlastností **(MaterialSpecular** a **MaterialSpecularPower)** grafu shaderu. Chcete-li získat přístup k vlastnostem grafu shaderu, zvolte prázdnou oblast návrhového povrchu a pak v okně **Vlastnosti** vyhledejte vlastnost, ke které chcete získat přístup.

   Další informace o použití odlesků v shaderu najdete v [tématu Postup: Vytvoření základního shaderu Phong](../designers/how-to-create-a-basic-phong-shader.md).

   S zrcadlovým zvýrazněním použít, váš kulečníkmíč by měl vypadat podobně jako tento:

   ![Detailní pohled na kulečníkovou kouli s přidaným zrcadlem](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Vytvořte si prostor tím, že odrážíte životní prostředí

S aplikovanými zrcadlovými vrcholy vypadá vaše kulečníková koule docela přesvědčivě. Má správný tvar, správnou barvu a správný povrch. Nicméně, je tu ještě jedna technika, která bude vaše kulečníková koule vypadat spíše jako součást svého prostředí.

Podíváte-li se na skutečnou kulečníkovou kouli, můžete vidět, že její lesklý povrch nevykazuje pouze zrcadlové vrcholy, ale také slabě odráží obraz světa kolem něj. Tento odraz můžete simulovat pomocí obrazu prostředí jako textury a jeho kombinací s vlastní texturou modelu, abyste určili konečnou barvu každého obrazového bodu. V závislosti na požadovaném druhu povrchu můžete kombinovat více či méně textury odrazu spolu se zbytkem shaderu. Například shader, který simuluje vysoce reflexní povrch jako zrcadlo, může používat pouze texturu odrazu, ale shader, který simuluje jemnější odraz, jako je ten, který se nachází na kulečníkové kouli, může kombinovat jen malou část odrazu textury spolu se zbytkem výpočtu shaderu.

Samozřejmě nemůžete na model aplikovat pouze odražený obraz stejným způsobem, jakým aplikujete mapu textury modelu. Pokud ano, odraz světa by se pohyboval s kulečníkovou koulí, jako by k ní byl odraz přilepený. Vzhledem k tomu, že odraz může pocházet z libovolného směru, potřebujete způsob, jak poskytnout hodnotu mapy odrazu pro libovolný úhel a způsob, jak udržet mapu odrazu orientovanou podle světa. Chcete-li tyto požadavky splnit, můžete použít speciální *cube map*druh mapy textury , která poskytuje šest textur uspořádaných tak, aby tvořily strany krychle. Zevnitř této krychle můžete nasměrovat libovolný směr a najít hodnotu textury. Pokud textury na každé straně krychle obsahují obrazy prostředí, můžete simulovat jakýkoli odraz vzorkováním správného umístění na povrchu krychle. Udržováním kostky zarovnané se světem získáte přesný odraz životního prostředí. Chcete-li určit, kde má být datová krychle vzorkována, stačí vypočítat odraz vektoru kamery z povrchu objektu a pak jej použít jako souřadnice 3D textury. Použití krychli mapy tímto způsobem je běžná technika, která je známá jako *mapování prostředí*.

Mapování prostředí poskytuje efektivní aproximaci reálných odrazů, jak je popsáno v předchozích odstavcích. Můžete míchat prostředí-mapované odrazy do vašeho shaderu, aby kulečníková koule simulované povrch, který dělá kulečníkmíč zdá více uzemněný ve scéně.

Prvním krokem je vytvoření textury mapy krychle. V mnoha typech aplikací nemusí být obsah mapy krychle dokonalý, aby byl efektivní, zvláště když je odraz jemný nebo nezabírá prominentní místo na obrazovce. Například mnoho her používá předem vypočítané mapy krychle pro mapování prostředí a stačí použít mapu, která je nejblíže každému reflexnímu objektu, i když to znamená, že odraz není správný. Dokonce i hrubá aproximace je často dost dobrá pro přesvědčivý efekt.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Vytvoření textur pro mapu prostředí pomocí Editoru obrázků

1. Vytvořte texturu, se které chcete pracovat. Informace o tom, jak přidat texturu do projektu, naleznete v části Začínáme v [Editoru obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku tak, aby jeho šířka byla rovna jeho výšce a byla o velikosti dvou; to je nezbytné z důvodu způsobu indexování mapy krychle. Chcete-li změnit velikost obrazu, zadejte v okně **Vlastnosti** nové hodnoty pro vlastnosti **Šířka** a **Výška.** Například nastavte hodnotu vlastností **Šířka** a **Výška** na 256.

3. K vyplnění textury použijte plnou barvu. Tato textura bude spodní části mapy krychle, která odpovídá povrchu kulečníkové tabulky. Mějte na paměti barvu, kterou jste použili pro další texturu.

4. Vytvořte druhou texturu, která má stejnou velikost jako první. Tato textura se bude opakovat na čtyřech stranách mapy krychle, které odpovídají povrchu a bokům kulečníkového stolu, a na oblast kolem kulečníkového stolu. Ujistěte se, že nakreslíte povrch kulečníkové tabulky v této struktuře pomocí stejné barvy jako ve spodní struktuře. Textura by měla vypadat podobně jako tato:

    ![Textura pro strany cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Nezapomeňte, že reflexní mapa nemusí být fotorealistická, aby byla účinná; například mapa krychle použitá k vytvoření obrázků v tomto článku obsahuje pouze čtyři kapsy namísto šesti.

5. Vytvořte třetí texturu, která má stejnou velikost jako ostatní. Tato textura bude v horní části mapy krychle, která odpovídá stropu nad kulečníkovou tabulkou. Chcete-li, aby tato část odrazu byla zajímavější, můžete nakreslit stropní světlo, které posílí odlesky, které jste přidali do shaderu v předchozím postupu. Textura by měla vypadat podobně jako tato:

    ![Textura pro horní část cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Nyní, když jste vytvořili jednotlivé textury pro strany mapy krychle, můžete použít nástroj k jejich sestavení do mapy krychle, která může být uložena v jedné struktuře *.dds.* Můžete použít libovolný program, který chcete vytvořit mapu krychle tak dlouho, dokud může uložit mapu krychle ve formátu textury .dds. Tento návod ukazuje, jak vytvořit texturu pomocí nástroje textury Rozhraní DirectX, který je součástí sady DirectX SDK z června 2010.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Sestavení mapy krychle pomocí nástroje Textura rozhraní DirectX

1. V nástroji Textura directx v hlavní nabídce zvolte **Soubor** > **nové textury**. Zobrazí se dialogové okno **Nová textura.**

2. Ve skupině **Typ textury** zvolte **Cubemap Texture**.

3. Ve skupině **Dimenze** zadejte správnou hodnotu pro **šířku** a **výšku**a pak zvolte **OK**. Zobrazí se nový dokument textury. Ve výchozím nastavení odpovídá textura, která je poprvé zobrazena v dokumentu textury, ploše **krychle Kladné X.**

4. Nanačtěte texturu, kterou jste vytvořili pro stranu krychle textury, na plochu krychle. V hlavní nabídce zvolte **Otevřít soubor** > **na tuto plochu kostky**, vyberte texturu, kterou jste vytvořili pro stranu krychle, a pak zvolte **Otevřít**.

5. Opakujte krok 4 pro **plochy záporné x**, **kladné z**a **záporné z** krychle. Chcete-li tak učinit, je nutné zobrazit plochu, kterou chcete načíst. Chcete-li zobrazit jinou plochu mapy krychle, v hlavní nabídce zvolte **Zobrazit** > **plochu mapy krychle**a pak vyberte plochu, kterou chcete zobrazit.

6. Pro **plochu kladné y** krychle načtěte texturu, kterou jste vytvořili pro horní část krychle textury.

7. Pro **plochu záporné** y krychle načtěte texturu, kterou jste vytvořili pro spodní část krychle textury.

8. Uložte texturu.

   Můžete si představit rozložení mapy krychle takto:

   ![Rozložení mapy krychle prostředí](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Obrázek v horní části je kladný obrázek y (+Y) kostka; uprostřed, zleva doprava, je -X, +Z, +X a -Z kostka tváře; v dolní části je tvář kostky -Y.

   Nyní můžete upravit shader a prolnout vzorek mapy krychle se zbytkem shaderu.

### <a name="to-add-environment-mapping-to-your-shader"></a>Přidání mapování prostředí do shaderu

1. Upravte shader tak, aby zahrnoval příspěvek mapování prostředí pomocí aditivního prolnutí. Graf shaderu by měl vypadat takto:

    ![Detailní uzly obou druhů reflexních shaderů](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Všimněte si, že můžete použít **uzel Multiply-Add** pro zjednodušení grafu shaderu.

    Tady je podrobnější zobrazení uzlů shaderu, které implementují mapování prostředí:

    ![Graf shaderu s přidaným mapováním prostředí](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Použijte texturu, kterou jste vytvořili v předchozím postupu, konfigurací vlastností textury mapy krychle. Nastavte hodnotu vlastnosti **Textura** uzlu **Ukázkový soubor Cubemap** na **Textura2**a pak určete soubor textury pomocí vlastnosti **Název_souboru** skupiny vlastností **Textura2.**

3. Volitelně můžete upravit odrazivost kulečníkové koule konfigurací **Vlastnost Výstup** u uzlu **Konstanta.** Chcete-li získat přístup k vlastnostem uzlu, vyberte jej a potom v okně **Vlastnosti** vyhledejte vlastnost, ke které chcete získat přístup.

   Při mapování prostředí použít, vaše kulečníková koule by měla vypadat podobně jako toto:

   ![Detailní krok prostředí mapoval kulečníkovou kouli](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   V tomto konečném obrázku si všimněte, jak se efekty, které jste přidali, spojují a vytvářejí velmi přesvědčivou kulečníkovou kouli. Tvar, textura a osvětlení vytvářejí základní vzhled 3D objektu a zrcadlové světla a odrazy činí kulečníkovou kouli zajímavější a vypadají jako součást jeho prostředí.

## <a name="see-also"></a>Viz také

- [Postupy: Export shaderu](../designers/how-to-export-a-shader.md)
- [Postupy: Použití shaderu na 3D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Návrhář shaderu](../designers/shader-designer.md)
- [Editor obrázků](../designers/image-editor.md)
- [Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)
