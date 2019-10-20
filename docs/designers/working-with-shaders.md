---
title: Práce se shadery
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3d2c6c745f17bbada918128fed852249e3024d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633786"
---
# <a name="work-with-shaders"></a>Práce se shadery

Pomocí Návrháře shaderu založeného na grafech v aplikaci Visual Studio můžete navrhovat efekty vlastních shaderů. Tyto shadery můžete použít ve hře nebo aplikaci založené na rozhraní DirectX.

## <a name="shaders"></a>Shadery

*Shader* je počítačový program, který provádí výpočty grafiky, například transformace vrcholů nebo barevné vybarvení pixelů a obvykle běží na grafickém procesoru (GPU) místo procesoru. Vzhledem k tomu, že většina fází tradičního kanálu grafiky s pevnou funkcí je teď prováděná programy shaderu, můžete je použít k vytvoření kanálu, který je specifický pro potřeby vaší aplikace.

Nejběžnější druhy shaderů jsou funkce *vertex shadery*, které provádějí výpočty podle vrcholu a nahrazují transformaci s pevnou funkcí a obvody osvětlení v neprogramovatelném grafickém hardwaru a funkce *pixel shadery*, které provádějí výpočty v pixelech, které určují barvu v pixelech a nahrazují dopravné barvy v kombinaci s pevnou funkcí v neprogramovatelném grafickém hardwaru. Moderní grafický hardware vytvořil ještě více druhů shaderů –*shadery trupu*, *shadery domény*a *geometrické shadery* pro výpočty grafiky a *výpočetní shadery* pro výpočty, které nepoužívají grafiku. Žádná z těchto fází není ani k dispozici v neprogramovatelném grafickém hardwaru. Shadery se původně vytvořily pomocí jazyka podobného sestavením, který poskytuje pokyny pro paralelní zpracování dat (SIMD) a grafiky zaměřené na grafiku (produkt). Nyní se shadery většinou vytvářejí pomocí vysoce kvalitních jazyků, jako je HLSL (jazyk shaderu na vysoké úrovni).

Návrhář shaderu můžete použít k interaktivnímu vytvoření pixel shaderů namísto zadání a kompilování kódu. V Návrháři shaderu je shader definován pomocí řady uzlů, které reprezentují data a operace, a propojení mezi uzly, které reprezentují tok hodnot dat a mezilehlé výsledky prostřednictvím shaderu. Pomocí tohoto přístupu a verze Preview v reálném čase v Návrháři shaderu můžete vizualizovat provádění shaderu snadněji a "zjistit" zajímavou odchylku shaderu prostřednictvím experimentování.

## <a name="dgsl-documents"></a>Dokumenty DGSL

Návrhář shaderu ukládá shadery ve formátu DGSL (Direct Graph shader Language), což je formát XML založený na jazyku DGML (Direct Graph Markup Language). Shadery DGSL můžete aplikovat přímo na 3D modely v editoru modelů. Před použitím shaderu DGSL v aplikaci je však nutné exportovat do formátu, který rozhraní DirectX zná – například HLSL.

Vzhledem k tomu, že DGSL je kompatibilní s DGML, můžete použít nástroje navržené k analýze dokumentů DGML pro analýzu vašich DGSL shaderů. Další informace o DGML najdete v tématu [principy jazyka DGML (Directed Graph Markup Language)](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje, jak používat návrháře shaderu sady Visual Studio pro práci s shadery.|
|[Uzly návrháře shaderu](../designers/shader-designer-nodes.md)|Popisuje druhy uzlů Návrháře shaderů, které lze použít k dosažení grafických efektů.|
|[Příklady návrháře shaderu](../designers/how-to-create-a-basic-color-shader.md)|Obsahuje odkazy na témata, která ukazují, jak používat návrháře shaderu k dosažení běžných grafických efektů.|