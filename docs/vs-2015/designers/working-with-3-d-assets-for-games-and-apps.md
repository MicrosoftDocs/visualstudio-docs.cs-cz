---
title: Práce s 3D prostředky pro hry a aplikace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bdf19958ec7b3cfe72ee00ea84e0e23724a51458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265228"
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Práce s 3D prostředky pro hry a aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje, které můžete použít k vytvoření nebo úpravě 3D modelů, textury a shadery založené na rozhraní DirectX her a aplikací.  
  
## <a name="directx-app-development-in-visual-studio"></a>Vývoj aplikací rozhraní DirectX v sadě Visual Studio  
 Aplikace DirectX obvykle kombinuje programovou logiku, API rozhraní DirectX a programy stínování jazyka HLSL (High Level), společně s prezentovat bohatých, interaktivních multimediální zvuk a 3D vizuální prostředky.[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsahuje nástroje, které můžete použít pro práci s obrázky a textury, 3D modely a shadery, aniž byste museli opustit integrované vývojové prostředí použít jiný nástroj. Nástroje sady Visual Studio jsou obzvláště vhodný pro vytváření *zástupný symbol* prostředky, které můžete použít k testování kódu nebo vytvářet prototypy, před Komise assety připravené pro produkční prostředí a pro prohlížení a úpravy připravené pro produkční prostředí prostředky při ladění aplikace.  
  
 Zde jsou další informace o druzích prostředků, které můžete pracovat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="images-and-textures"></a>Obrazů a textur  
 Obrazů a textur poskytují barvu a vizuální podrobně hry a aplikace. V 3D grafiky pocházejí textury v různých formátech, typy a geometrie podporují různá použití. Například map normál poskytují jednotlivých pixelů normály pro podrobnější osvětlení 3D modelů a poskytují krychlové mapy textury pro použití jako sky zabalení, odrazů a mapování textur na kulovité všechny směry. Textury může poskytnout mapy mip pro podporu efektivního vykreslování na různých úrovních podrobností a může podporovat kanály různých barev a pořadí, které se barva. Textury mohou být uloženy v různých komprimovaných formátů, které zabírají méně vyhrazená paměť grafiky a pomáhají textury přístup GPU efektivněji.  
  
 Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor obrázků pro práci s obrazů a textur v mnoha běžné typy a formáty.  
  
### <a name="3-d-models"></a>3D modely  
 3D modely vytvoření místa a tvar v hry a aplikace. Minimálně modely kódování pozice body v 3D prostoru – což se označuje jako *vrcholy*– spolu s indexování dat k definování čáry nebo trojúhelníky, které představují tvar objektu modelu. Další data můžou být spojené s těmito vrcholy – například barev informace, běžné vektory nebo atributy specifické pro aplikaci. Každý model lze také definovat celý objekt atributy – například, shader, který slouží k výpočtu vzhled surface, nebo objektu textury, které se použije na ni.  
  
 Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru modelů pro práci s 3D modely v několika běžných formátů.  
  
### <a name="shaders"></a>Shadery  
 Shadery jsou malé, specifického pro doménu programy, které běží na grafický procesor (GPU). Shadery určit, jak 3D modely se transformují na obrazovce tvarů a jak jsou zobrazeny každý pixel v těchto tvarů. Vytvořením shaderu a jeho použití na objekt ve hře nebo aplikaci, můžete zadat objekt jedinečný vzhled.  
  
 Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] návrháře shaderu, které je založené na grafu shaderu návrhářský nástroj, chcete-li vytvořit vlastní vizuálních efektů bez znalosti programování HLSL.  
  
> [!NOTE]
>  Další informace o tom, jak začít s programování pro rozhraní DirectX, naleznete v tématu [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Další informace o tom, jak ladit aplikaci založené na rozhraní DirectX naleznete v tématu [diagnostiky grafiky (ladění grafiky DirectX)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## <a name="directx-version-compatibility"></a>Kompatibilita verzí DirectX  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní DirectX se používá k vykreslení 2D a 3D aktiv. Můžete vybrat zobrazovací jednotky rozhraní DirectX 11 nebo zobrazovací jednotky softwaru Windows Advanced Rasterizační platformě WARP (). Renderer rozhraní DirectX 11 poskytuje vysoce výkonné, hardwarově urychlené vykreslování na rozhraní DirectX 11 a DirectX 10 GPU. WARP renderer pomáhá, ujistěte se, že vaše prostředky fungovat s širokou škálu počítače – to zahrnuje počítače, které nemají moderní grafický hardware a počítače, které jste integrovali hardwarovou akceleraci. Další informace o WARP najdete v tématu [Windows Advanced Rasterizační platformě WARP () průvodce](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Práce s texturami a obrázky](../designers/working-with-textures-and-images.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s obrazů a textur.|  
|[Práce se 3D modely](../designers/working-with-3-d-models.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro práci s 3D modely.|  
|[Práce se shadery](../designers/working-with-shaders.md)|Popisuje způsob použití [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] návrháře shaderu vytvořit a upravit vlastní shaderu účinky.|  
|[Používání 3D prostředků ve hře nebo aplikaci](../designers/using-3-d-assets-in-your-game-or-app.md)|Popisuje postup používání prostředků, které jste vytvořili pomocí editoru obrázků, editoru modelů nebo návrháře shaderu ve hře nebo aplikaci.|



