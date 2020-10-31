---
title: Práce s 3D prostředky pro hry a aplikace
description: Seznamte se s nástroji sady Visual Studio, které můžete použít k vytvoření nebo úpravě 3D modelů, textur a shaderů pro hry a aplikace založené na rozhraní DirectX.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 11f031aa3e3767af3132e68f92c492dc7e3fae6f
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134547"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace

Tento článek popisuje nástroje sady Visual Studio, které můžete použít k vytvoření nebo úpravě 3D modelů, textur a shaderů pro hry a aplikace založené na rozhraní DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací DirectX v aplikaci Visual Studio

Aplikace DirectX obvykle kombinuje programovací logiku, rozhraní DirectX API a programy HLSL (High Level prostíning Language) spolu se zvukovým a 3D vizuálními prostředky a prezentuje bohatá interaktivní multimediální prostředí. Visual Studio obsahuje nástroje, které můžete použít pro práci s imagemi a texturami, 3D modely a shadery bez nutnosti opustit rozhraní IDE, aby bylo možné použít jiný nástroj. Nástroje sady Visual Studio jsou zvláště vhodné pro vytváření *zástupných* prostředků, které můžete použít k testování kódu nebo prototypů sestavení před tím, než provedete proaktivované prostředky pro produkční prostředí, a pro kontrolu a úpravy prostředků připravených k produkci při ladění aplikace.

Zde jsou další informace o druzích prostředků, se kterými můžete pracovat v aplikaci Visual Studio.

### <a name="images-and-textures"></a>Obrázky a textury

Obrázky a textury poskytují barvy a vizuální podrobnosti ve hrách a aplikacích. V 3D grafice přicházejí textury v nejrůznějších formátech, typech a geometrií pro podporu různých použití. Například normální mapy poskytují normální plochu pro podrobnější osvětlení 3D modelů a mapy datových krychlí poskytují texturu ve všech směrech pro použití, jako jsou například nebe – zabalení, odrazy a mapování kulové textury. Textury můžou poskytovat mipmapy pro podporu efektivního vykreslování na různých úrovních podrobností a můžou podporovat různé barevné kanály a barevné pořadí barev. Textury lze uložit v nejrůznějších komprimovaných formátech, které zabírají méně vyhrazenou paměť grafiky a umožňují efektivnější přístup k texturám GPU.

Editor obrázků sady Visual Studio můžete použít pro práci s obrázky a texturami v mnoha běžných typech a formátech.

### <a name="3d-models"></a>3D modely

3D modely vytvářejí prostor a tvar v hrách a aplikacích. Modely kódují místo bodů v prostorovém prostoru, které jsou známé jako *vrcholy* , společně s indexovanými daty k definování řádků nebo trojúhelníků, které představují tvar modelu. K těmto vrcholům lze přidružit další data, například informace o barvách, normální vektory nebo atributy specifické pro aplikaci. Každý model může také definovat atributy v rámci objektu, například, který shader slouží k výpočtu vzhledu povrchu objektu nebo na který texturu, na kterou se aplikuje.

Editor modelů sady Visual Studio můžete použít pro práci s 3D modely v několika běžných formátech.

### <a name="shaders"></a>Shadery

Shadery jsou malé, programy specifické pro doménu, které běží na grafické jednotce procesoru (GPU). Shadery určují, jak se 3D modely transformují do tvarů na obrazovce a jak jsou jednotlivé pixely v těchto obrazcích barvy. Vytvořením shaderu a jeho aplikováním na objekt ve hře nebo aplikaci můžete objektu dát jedinečný vzhled.

K vytváření vlastních vizuálních efektů bez znalosti programování v HLSL můžete použít Visual Studio Shader Designer, což je nástroj pro návrh shaderu založený na grafu.

> [!NOTE]
> Další informace o tom, jak začít s programováním v rozhraní DirectX, najdete v tématu [DirectX](/windows/win32/directx). Další informace o ladění aplikace založené na rozhraní DirectX najdete v tématu [Diagnostika grafiky (ladění grafiky DirectX)](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX

Visual Studio používá rozhraní DirectX k vykreslování 2D a 3D prostředků. Můžete vybrat buď vykreslovací modul rozhraní DirectX 11, nebo systém Windows Advanced Rastring Platform (pokřivení) softwaru. Vykreslovací modul rozhraní DirectX 11 poskytuje vysoce výkonné vykreslování s hardwarovou akcelerací na procesorech DirectX 11 a DirectX 10. Zobrazovací jednotka pro pokřivení pomáhá zajistit, aby vaše prostředky pracovaly s širokou škálou počítačů – to zahrnuje počítače, které nemají moderní grafický hardware a počítače s integrovaným grafickým hardwarem. Další informace o prostudování najdete v tématu [Příručka k platformě Windows Advanced rastring Platform (POkřivení)](/windows/win32/direct3darticles/directx-warp).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje, jak používat Visual Studio k práci s imagemi a texturami.|
|[Práce s 3D modely](../designers/working-with-3-d-models.md)|Popisuje, jak používat Visual Studio pro práci s 3D modely.|
|[Práce s shadery](../designers/working-with-shaders.md)|Popisuje způsob použití návrháře shaderu sady Visual Studio k vytvoření a úpravě efektů vlastního shaderu.|
|[Použití 3D prostředků ve hře nebo aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje, jak používat assety, které jste vytvořili pomocí editoru obrázků, editoru modelů nebo návrháře shaderu ve vaší hře nebo aplikaci.|
