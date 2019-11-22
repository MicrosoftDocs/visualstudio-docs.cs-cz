---
title: Práce s 3D prostředky pro hry a aplikace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cc4f8038906de89afd86fd666fbb011e974362d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298092"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje nástroje pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], které můžete použít k vytvoření nebo úpravě 3D modelů, textur a shaderů pro hry a aplikace založené na rozhraní DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací DirectX v aplikaci Visual Studio
 Aplikace DirectX obvykle kombinuje programovací logiku, rozhraní DirectX API a programy HLSL (High Level prostíning Language) spolu se zvukovým a 3D vizuálními prostředky a prezentuje bohatá interaktivní multimediální prostředí.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsahuje nástroje, které můžete použít pro práci s imagemi a texturami, 3D modely a shadery, aniž byste opustili rozhraní IDE, aby používaly jiný nástroj. Nástroje sady Visual Studio jsou zvláště vhodné pro vytváření *zástupných* prostředků, které můžete použít k testování kódu nebo prototypů sestavení před tím, než provedete proaktivované prostředky pro produkční prostředí, a pro kontrolu a úpravy prostředků připravených k produkci při ladění aplikace.

 Zde jsou další informace o druzích assetů, se kterými můžete pracovat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

### <a name="images-and-textures"></a>Obrázky a textury
 Obrázky a textury poskytují barvy a vizuální podrobnosti ve hrách a aplikacích. V 3D grafice přicházejí textury v nejrůznějších formátech, typech a geometrií pro podporu různých použití. Například normální mapy poskytují normální plochu pro podrobnější osvětlení 3D modelů a mapy datových krychlí poskytují texturu ve všech směrech pro použití, jako jsou například Nebeský zabalení, odrazy a mapování kulové textury. Textury můžou poskytovat mapy MIP, aby podporovaly efektivní vykreslování na různých úrovních podrobností a můžou podporovat různé barevné kanály a barevné pořadí barev. Textury lze uložit v nejrůznějších komprimovaných formátech, které zabírají méně vyhrazenou paměť grafiky a umožňují efektivnější přístup k texturám GPU.

 Editor obrázků [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete použít pro práci s obrázky a texturami v mnoha běžných typech a formátech.

### <a name="3-d-models"></a>3D modely
 3D modely vytvářejí prostor a tvar v hrách a aplikacích. Modely zakódují pozici bodů v prostorech v 3D prostoru, které jsou známé jako *vrcholy*, spolu s indexovanými daty k definování řádků nebo trojúhelníků, které představují tvar modelu. K těmto vrcholům lze přidružit další data, například informace o barvách, normální vektory nebo atributy specifické pro aplikaci. Každý model může také definovat atributy v rámci objektu, například, který shader slouží k výpočtu vzhledu povrchu objektu nebo na který texturu, na kterou se aplikuje.

 Editor modelů [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete použít pro práci s 3D modely v několika běžných formátech.

### <a name="shaders"></a>Shadery
 Shadery jsou malé, programy specifické pro doménu, které běží na grafické jednotce procesoru (GPU). Shadery určují, jak se modely 3D modelů transformují do tvarů na obrazovce a jak jsou jednotlivé pixely v těchto obrazcích barvy. Vytvořením shaderu a jeho aplikováním na objekt ve hře nebo aplikaci můžete objektu dát jedinečný vzhled.

 K vytváření vlastních vizuálních efektů bez znalosti programování v HLSL můžete použít nástroj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shader Designer, což je nástroj pro návrh shaderu založený na grafu.

> [!NOTE]
> Další informace o tom, jak začít s programováním v rozhraní DirectX, najdete v tématu [DirectX](https://go.microsoft.com/fwlink/p/?LinkId=224633). Další informace o ladění aplikace založené na rozhraní DirectX najdete v tématu [Diagnostika grafiky (ladění grafiky DirectX)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá k vykreslování 2D a 3D prostředků rozhraní DirectX. Můžete vybrat buď vykreslovací modul rozhraní DirectX 11, nebo systém Windows Advanced Rastring Platform (pokřivení) softwaru. Vykreslovací modul rozhraní DirectX 11 poskytuje vysoce výkonné vykreslování s hardwarovou akcelerací na procesorech DirectX 11 a DirectX 10. Zobrazovací jednotka pro pokřivení pomáhá zajistit, aby vaše prostředky pracovaly s širokou škálou počítačů – to zahrnuje počítače, které nemají moderní grafický hardware a počítače s integrovaným grafickým hardwarem. Další informace o prostudování najdete v tématu [Příručka k platformě Windows Advanced rastring Platform (POkřivení)](https://go.microsoft.com/fwlink/p/?LinkId=224634).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje, jak použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s obrázky a texturami.|
|[Práce se 3D modely](../designers/working-with-3-d-models.md)|Popisuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s 3D modely.|
|[Práce se shadery](../designers/working-with-shaders.md)|Popisuje, jak použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Designer shader k vytváření a úpravám efektů vlastního shaderu.|
|[Používání 3D prostředků ve hře nebo aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje, jak používat assety, které jste vytvořili pomocí editoru obrázků, editoru modelů nebo návrháře shaderu ve vaší hře nebo aplikaci.|
