---
title: Práce se shadery
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ccb4f838c702cb1843d5c0f44dd7f54219f27a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589770"
---
# <a name="work-with-shaders"></a>Práce se shadery

Pomocí návrháře shaderů založených na grafech v sadě Visual Studio můžete navrhnout vlastní efekty shaderu. Tyto shadery můžete použít ve hře nebo aplikaci založené na rozhraní DirectX.

## <a name="shaders"></a>Shadery

*Shader* je počítačový program, který provádí grafické výpočty – například transformace vrcholů nebo zbarvení obrazových bodů – a obvykle běží na grafické procesoru (GPU) namísto procesoru. Vzhledem k tomu, že většinu fází tradičního grafického kanálu s pevnou funkcí teď provádějí programy shaderu, můžete je použít k vytvoření kanálu, který je specifický pro potřeby vaší aplikace.

Nejběžnějšími druhy shaderů jsou *shadery vrcholů*, které provádějí výpočty na vrchol a nahrazují transformační a světelné obvody s pevnou funkcí v neprogramovatelném grafickém hardwaru, a *shadery obrazových bodů*, které provádějí výpočty na pixel, které určují barvu pixelu a nahrazují obvody s pevnou funkcí barevného slučovače v neprogramovatelném grafickém hardwaru. Moderní grafický hardware umožnil ještě více druhů shaderů –*shadery trupu*, *shadery domén*a *geometrické shadery* pro grafické výpočty a *výpočetní shadery* pro negrafické výpočty. Žádná z těchto fází není k dispozici ani v neprogramovatelném grafickém hardwaru. Shadery byly původně vytvořeny pomocí jazyka podobného sestavení, který poskytoval pokyny pro paralelní data (SIMD) a grafické (tečkované produkty). Nyní jsou shadery obvykle vytvářeny pomocí jazyků na vysoké úrovni, c-like, jako je HLSL (High Level Shader Language).

Návrhář shaderu můžete použít k interaktivnímu vytváření shaderů obrazových bodů, nikoli zadáním a kompilací kódu. V návrháři shaderu je shader definován řadou uzlů, které představují data a operace, a připojenímezi uzly, které představují tok hodnot dat a zprostředkující výsledky prostřednictvím shaderu. Pomocí tohoto přístupu a náhledu v reálném čase v návrháři shaderu můžete snadněji vizualizovat provádění shaderu a "objevovat" zajímavé varianty shaderu prostřednictvím experimentování.

## <a name="dgsl-documents"></a>Dokumenty dgsl

Návrhář shaderu ukládá shadery ve formátu DGSL (Directed Graph Shader Language), což je formát XML založený na jazyce DGML (Directed Graph Markup Language). Stínidla DGSL můžete použít přímo na 3D modely v Editoru modelů. Než však budete moci v aplikaci použít shader SGSL, musíte ho exportovat do formátu, kterému rozhraní DirectX rozumí – například HLSL.

Vzhledem k tomu, že dgsl je kompatibilní s DGML, můžete použít nástroje, které jsou určeny k analýze dokumentů DGML k analýze shaderů DGSL. Informace o Kontrole dat naleznete v [tématu Principy jazyka značek řízeného grafu (DGML).](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Návrhář shaderu](../designers/shader-designer.md)|Popisuje, jak používat Návrhář shaderu sady Visual Studio pro práci se stínidly.|
|[Uzly Návrhářshaderu](../designers/shader-designer-nodes.md)|Popisuje druhy uzlů Shader Designer, které můžete použít k dosažení grafických efektů.|
|[Příklady návrhářů shaderů](../designers/how-to-create-a-basic-color-shader.md)|Obsahuje odkazy na témata, která ukazují, jak pomocí návrháře shaderu dosáhnout běžných grafických efektů.|
