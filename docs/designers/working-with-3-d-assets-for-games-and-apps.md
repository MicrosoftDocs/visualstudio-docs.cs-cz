---
title: Práce s 3D prostředky pro hry a aplikace
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c86b5ec3918526f461b39080967d5bc4a8a32e30
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079471"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace

Tento dokument popisuje nástroje sady Visual Studio, které můžete použít k vytvoření nebo úpravě 3D modelů, textury a shadery založené na rozhraní DirectX her a aplikací.

## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací rozhraní DirectX v sadě Visual Studio
 Aplikace DirectX obvykle kombinuje programovou logiku, API rozhraní DirectX a programy stínování jazyka HLSL (High Level), společně s prezentovat bohatých, interaktivních multimediální zvuk a 3D vizuální prostředky. Visual Studio obsahuje nástroje, které můžete použít pro práci s imagí a textury, 3D modely a shadery, aniž byste museli opustit integrované vývojové prostředí použít jiný nástroj. Nástroje sady Visual Studio jsou obzvláště vhodný pro vytváření *zástupný symbol* prostředky, které můžete použít k testování kódu nebo vytvářet prototypy, před Komise assety připravené pro produkční prostředí a pro prohlížení a úpravy připravené pro produkční prostředí prostředky při ladění aplikace.

 Tady je další informace o druzích prostředků, můžete pracovat v sadě Visual Studio.

### <a name="images-and-textures"></a>Obrazů a textur
 Obrazů a textur poskytují barvu a vizuální podrobně hry a aplikace. V 3D grafiky pocházejí textury v různých formátech, typy a geometrie podporují různá použití. Například map normál poskytují jednotlivých pixelů normály pro podrobnější osvětlení 3D modelů a poskytují krychlové mapy textury pro použití jako sky zabalení, odrazů a mapování textur na kulovité všechny směry. Textury může poskytnout mipmapy pro podporu efektivního vykreslování na různých úrovních podrobností a může podporovat kanály různých barev a pořadí, které se barva. Textury mohou být uloženy v různých komprimovaných formátů, které zabírají méně vyhrazená paměť grafiky a pomáhají textury přístup GPU efektivněji.

 Můžete použít Editor obrázků Visual Studia pro práci s obrazů a textur v mnoha běžné typy a formáty.

### <a name="3d-models"></a>3D modely
 3D modely vytvoření místa a tvar v hry a aplikace. Minimálně modely kódování pozice body v 3D prostoru – což se označuje jako *vrcholy*– spolu s indexování dat k definování čáry nebo trojúhelníky, které představují tvar objektu modelu. Další data můžou být spojené s těmito vrcholy – například barev informace, běžné vektory nebo atributy specifické pro aplikaci. Každý model lze také definovat celý objekt atributy – například, shader, který slouží k výpočtu vzhled surface, nebo objektu textury, které se použije na ni.

 Model editoru sady Visual Studio můžete použít pro práci s 3D modely v několika běžných formátů.

### <a name="shaders"></a>Shadery
 Shadery jsou malé, specifického pro doménu programy, které běží na grafický procesor (GPU). Shadery určit, jak 3D modelů se transformují na obrazovce tvarů a jak jsou zobrazeny každý pixel v těchto tvarů. Vytvořením shaderu a jeho použití na objekt ve hře nebo aplikaci, můžete zadat objekt jedinečný vzhled.

 Shader Návrhář Visual Studio, které je založené na grafu shaderu návrhářský nástroj, můžete použít k vytvoření vlastních efektů bez znalosti programování HLSL.

> [!NOTE]
> Další informace o tom, jak začít s programování pro rozhraní DirectX, naleznete v tématu [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Další informace o tom, jak ladit aplikaci založené na rozhraní DirectX naleznete v tématu [diagnostiky grafiky (ladění grafiky DirectX)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX
 Visual Studio používá k vykreslení 2D a 3D prostředky rozhraní DirectX. Můžete vybrat zobrazovací jednotky rozhraní DirectX 11 nebo zobrazovací jednotky softwaru Windows Advanced Rasterizační platformě WARP (). Renderer rozhraní DirectX 11 poskytuje vysoce výkonné, hardwarově urychlené vykreslování na rozhraní DirectX 11 a DirectX 10 GPU. WARP renderer pomáhá, ujistěte se, že vaše prostředky fungovat s širokou škálu počítače – to zahrnuje počítače, které nemají moderní grafický hardware a počítače, které jste integrovali hardwarovou akceleraci. Další informace o WARP najdete v tématu [Windows Advanced Rasterizační platformě WARP () průvodce](http://go.microsoft.com/fwlink/p/?LinkId=224634).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje, jak pomocí sady Visual Studio pro práci s obrazů a textur.|
|[Práce se 3D modely](../designers/working-with-3-d-models.md)|Popisuje, jak pomocí sady Visual Studio pro práci s 3D modely.|
|[Práce se shadery](../designers/working-with-shaders.md)|Popisuje způsob použití návrháře shaderu Visual Studio k vytvoření a úprava efekty shaderu vlastní.|
|[Používání 3D prostředků ve hře nebo aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje postup používání prostředků, které jste vytvořili pomocí editoru obrázků, editoru modelů nebo návrháře shaderu ve hře nebo aplikaci.|