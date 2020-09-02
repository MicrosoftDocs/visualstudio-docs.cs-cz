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
ms.openlocfilehash: e181500beefd32dffb9c0e8a7572a198cc9ff1f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852198"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje, které můžete použít k vytvoření nebo úpravě 3D modelů, textur a shaderů pro hry a aplikace založené na rozhraní DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací DirectX v aplikaci Visual Studio
 Aplikace DirectX obvykle kombinuje programovací logiku, rozhraní DirectX API a programy HLSL (High Level prostíning Language) spolu se zvukovým a 3D vizuálními prostředky a prezentuje bohatá interaktivní multimediální prostředí.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsahuje nástroje, které můžete použít pro práci s imagemi a texturami, 3D modely a shadery, aniž byste opustili rozhraní IDE, aby používaly jiný nástroj. Nástroje sady Visual Studio jsou zvláště vhodné pro vytváření *zástupných* prostředků, které můžete použít k testování kódu nebo prototypů sestavení před tím, než provedete proaktivované prostředky pro produkční prostředí, a pro kontrolu a úpravy prostředků připravených k produkci při ladění aplikace.

 Zde jsou další informace o druzích assetů, se kterými můžete pracovat v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

### <a name="images-and-textures"></a>Obrázky a textury
 Obrázky a textury poskytují barvy a vizuální podrobnosti ve hrách a aplikacích. V 3D grafice přicházejí textury v nejrůznějších formátech, typech a geometrií pro podporu různých použití. Například normální mapy poskytují normální plochu pro podrobnější osvětlení 3D modelů a mapy datových krychlí poskytují texturu ve všech směrech pro použití, jako jsou například Nebeský zabalení, odrazy a mapování kulové textury. Textury můžou poskytovat mapy MIP, aby podporovaly efektivní vykreslování na různých úrovních podrobností a můžou podporovat různé barevné kanály a barevné pořadí barev. Textury lze uložit v nejrůznějších komprimovaných formátech, které zabírají méně vyhrazenou paměť grafiky a umožňují efektivnější přístup k texturám GPU.

 Editor obrázků můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s obrázky a texturami v mnoha běžných typech a formátech.

### <a name="3-d-models"></a>3D modely
 3D modely vytvářejí prostor a tvar v hrách a aplikacích. Modely zakódují pozici bodů v prostorech v 3D prostoru, které jsou známé jako *vrcholy*, spolu s indexovanými daty k definování řádků nebo trojúhelníků, které představují tvar modelu. K těmto vrcholům lze přidružit další data, například informace o barvách, normální vektory nebo atributy specifické pro aplikaci. Každý model může také definovat atributy v rámci objektu, například, který shader slouží k výpočtu vzhledu povrchu objektu nebo na který texturu, na kterou se aplikuje.

 Editor modelů můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s 3D modely v několika běžných formátech.

### <a name="shaders"></a>Shadery
 Shadery jsou malé, programy specifické pro doménu, které běží na grafické jednotce procesoru (GPU). Shadery určují, jak se modely 3D modelů transformují do tvarů na obrazovce a jak jsou jednotlivé pixely v těchto obrazcích barvy. Vytvořením shaderu a jeho aplikováním na objekt ve hře nebo aplikaci můžete objektu dát jedinečný vzhled.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]K vytváření vlastních vizuálních efektů bez znalosti programování v HLSL můžete použít návrháře shaderu, což je nástroj pro návrh shaderu založený na grafu.

> [!NOTE]
> Další informace o tom, jak začít s programováním v rozhraní DirectX, najdete v tématu [DirectX](https://msdn.microsoft.com/library/ee663274(VS.85).aspx). Další informace o ladění aplikace založené na rozhraní DirectX najdete v tématu [Diagnostika grafiky (ladění grafiky DirectX)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vykreslování prostředků 2D a 3D používá rozhraní DirectX. Můžete vybrat buď vykreslovací modul rozhraní DirectX 11, nebo systém Windows Advanced Rastring Platform (pokřivení) softwaru. Vykreslovací modul rozhraní DirectX 11 poskytuje vysoce výkonné vykreslování s hardwarovou akcelerací na procesorech DirectX 11 a DirectX 10. Zobrazovací jednotka pro pokřivení pomáhá zajistit, aby vaše prostředky pracovaly s širokou škálou počítačů – to zahrnuje počítače, které nemají moderní grafický hardware a počítače s integrovaným grafickým hardwarem. Další informace o prostudování najdete v tématu [Příručka k platformě Windows Advanced rastring Platform (POkřivení)](https://msdn.microsoft.com/library/gg615082(VS.85).aspx).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s imagemi a texturami.|
|[Práce se 3D modely](../designers/working-with-3-d-models.md)|Popisuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s 3D modely.|
|[Práce se shadery](../designers/working-with-shaders.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Návrháře shaderu k vytvoření a úpravě efektů vlastního shaderu.|
|[Používání 3D prostředků ve hře nebo aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje, jak používat assety, které jste vytvořili pomocí editoru obrázků, editoru modelů nebo návrháře shaderu ve vaší hře nebo aplikaci.|
