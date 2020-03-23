---
title: Práce s 3D datovými zdroji pro hry a aplikace
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9fc04df3e817730492353e54d74c1e46c3775e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589796"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace

Tento článek popisuje nástroje sady Visual Studio, které můžete použít k vytvoření nebo úpravě 3D modelů, textur a stínítek pro hry a aplikace založené na rozhraní DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací DirectX ve Visual Studiu

Aplikace DirectX obvykle kombinuje programovací logiku, rozhraní DirectX API a programy HLSL (High Level Stínovací jazyk) spolu se zvukovými a 3D vizuálními prostředky, které představují bohaté interaktivní multimediální prostředí. Visual Studio obsahuje nástroje, které můžete použít pro práci s obrázky a texturami, 3D modely a shadery, aniž byste opustili ide a používali jiný nástroj. Nástroje sady Visual Studio jsou obzvláště vhodné pro vytváření *zástupných* datových zdrojů, které můžete použít k testování kódu nebo sestavení prototypů před uvedením prostředků připravených k výrobě a ke kontrole a úpravám prostředků připravených pro produkční prostředí při ladění aplikace.

Tady najdete další informace o typech datových zdrojů, se kterými můžete v sadě Visual Studio pracovat.

### <a name="images-and-textures"></a>Obrázky a textury

Obrázky a textury poskytují barvy a vizuální detaily ve hrách a aplikacích. Ve 3D grafice se textury domýšlet v různých formátech, typech a geometriích, které podporují různá použití. Normální mapy například poskytují normály povrchu na pixel pro podrobnější osvětlení 3D modelů a mapy krychle poskytují texturu ve všech směrech pro použití, jako je zabalení oblohy, odrazy a sférické mapování textur. Textury mohou poskytovat mipmapy pro efektivní vykreslování na různých úrovních detailů a mohou podporovat různé barevné kanály a uspořádání barev. Textury mohou být uloženy v různých komprimovaných formátech, které zabírají méně vyhrazenou grafickou paměť a pomáhají grafickým procesorům efektivněji přistupovat k texturám.

Pomocí editoru obrázků sady Visual Studio můžete pracovat s obrázky a texturami v mnoha běžných typech a formátech.

### <a name="3d-models"></a>3D modely

3D modely vytvářejí prostor a tvar ve hrách a aplikacích. Modely minimálně kódují polohu bodů ve 3D prostoru , spolu s *indexovacími daty*k definování čar nebo trojúhelníků, které představují tvar modelu. K těmto vrcholům lze přidružit další data – například barevné informace, normální vektory nebo atributy specifické pro aplikaci. Každý model může také definovat atributy pro celý objekt – například shader, který se používá k výpočtu vzhledu povrchu objektu nebo která textura je na něj použita.

Editor modelů sady Visual Studio můžete použít k práci s 3D modely v několika běžných formátech.

### <a name="shaders"></a>Shadery

Shadery jsou malé programy specifické pro doménu, které běží na grafické procesorové jednotce (GPU). Shadeři určují, jak se 3D modely transformují do obrazců na obrazovce a jak jsou jednotlivé obrazové body v těchto obrazcích barevné. Vytvořením shaderu a jeho použitím na objekt ve hře nebo aplikaci můžete objektu poskytnout jedinečný vzhled.

Pomocí návrháře shaderu sady Visual Studio, což je nástroj pro návrh shaderu založený na grafech, můžete použít k vytvoření vlastních vizuálních efektů bez znalosti programování HLSL.

> [!NOTE]
> Další informace o tom, jak začít s programováním rozhraní DirectX, naleznete v [tématu DirectX](/windows/win32/directx). Další informace o ladění aplikace založené na rozhraní DirectX naleznete v [tématu Diagnostika grafiky (ladění grafiky DirectX).](../debugger/graphics/visual-studio-graphics-diagnostics.md)

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX

Visual Studio používá DirectX k vykreslení 2D a 3D datových zdrojů. Můžete vybrat vykreslovač directx 11 nebo softwarového vykreslovače Windows Advanced Rasterization Platform (WARP). Vykreslovač Rozhraní DirectX 11 poskytuje vysoce výkonné hardwarově akcelerované vykreslování na grafických procesorech DirectX 11 a DirectX 10. Vykreslovač warp pomáhá zajistit, aby vaše datové zdroje fungovaly s širokou škálou počítačů – to zahrnuje počítače, které nemají moderní grafický hardware a počítače s integrovaným grafickým hardwarem. Další informace o programu WARP naleznete [v příručce Windows Advanced Rasterization Platform (WARP).](/windows/win32/direct3darticles/directx-warp)

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje použití sady Visual Studio pro práci s obrázky a texturami.|
|[Práce s 3D modely](../designers/working-with-3-d-models.md)|Popisuje, jak používat Visual Studio pro práci s 3D modely.|
|[Práce se shadéry](../designers/working-with-shaders.md)|Popisuje, jak pomocí návrháře shaderu sady Visual Studio vytvářet a upravovat vlastní efekty shaderu.|
|[Používání 3D datových zdrojů ve hře nebo v aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje, jak používat datové zdroje, které jste vytvořili pomocí Editoru obrázků, Editoru modelů nebo Návrháře shaderů ve hře nebo aplikaci.|
