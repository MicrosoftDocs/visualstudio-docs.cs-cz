---
title: Práce s shadery | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a22be61d5f4c05720a5ff223806f2e14a8bfbc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663949"
---
# <a name="working-with-shaders"></a>Práce se shadery
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí Návrháře shaderu založeného na grafech v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete navrhovat efekty vlastních shaderů. Tyto shadery můžete použít ve hře nebo aplikaci založené na rozhraní DirectX.

## <a name="shaders"></a>Shadery
 *Shader* je počítačový program, který provádí výpočty grafiky, například transformace vrcholů nebo barevné vybarvení pixelů a obvykle běží na grafickém procesoru (GPU) místo procesoru. Vzhledem k tomu, že většina fází tradičního kanálu grafiky s pevnou funkcí je teď prováděná programy shaderu, můžete je použít k vytvoření kanálu, který je specifický pro potřeby vaší aplikace.

 Nejběžnější druhy shaderů jsou funkce *vertex shadery*, které provádějí výpočty podle vrcholu a nahrazují transformaci s pevnou funkcí a obvody osvětlení v neprogramovatelném grafickém hardwaru a funkce *pixel shadery*, které provádějí výpočty v pixelech, které určují barvu v pixelech a nahrazují dopravné barvy v kombinaci s pevnou funkcí v neprogramovatelném grafickém hardwaru. Moderní grafický hardware vytvořil ještě více druhů shaderů –*shadery trupu*, *shadery domény*a *geometrické shadery* pro výpočty grafiky a *výpočetní shadery* pro výpočty, které nepoužívají grafiku. Žádná z těchto fází není ani k dispozici v neprogramovatelném grafickém hardwaru. Shadery se původně vytvořily pomocí jazyka podobného sestavením, který poskytuje pokyny pro paralelní zpracování dat (SIMD) a grafiky zaměřené na grafiku (produkt). Nyní se shadery většinou vytvářejí pomocí vysoce kvalitních jazyků, jako je HLSL (jazyk shaderu na vysoké úrovni).

 Návrhář shaderu můžete použít k interaktivnímu vytvoření pixel shaderů namísto zadání a kompilování kódu. V Návrháři shaderu je shader definován pomocí řady uzlů, které reprezentují data a operace, a propojení mezi uzly, které reprezentují tok hodnot dat a mezilehlé výsledky prostřednictvím shaderu. Pomocí tohoto přístupu a verze Preview v reálném čase v Návrháři shaderu můžete vizualizovat provádění shaderu snadněji a "zjistit" zajímavou odchylku shaderu prostřednictvím experimentování.

## <a name="dgsl-documents"></a>Dokumenty DGSL
 Návrhář shaderu ukládá shadery ve formátu DGSL (Direct Graph shader Language), což je formát XML založený na jazyku DGML (Direct Graph Markup Language). Shadery DGSL můžete použít přímo na 3D modely v editoru modelů. Před použitím shaderu DGSL v aplikaci je však nutné exportovat do formátu, který rozhraní DirectX zná – například HLSL.

 Vzhledem k tomu, že DGSL je kompatibilní s DGML, můžete použít nástroje navržené k analýze dokumentů DGML pro analýzu vašich DGSL shaderů. Další informace o DGML najdete v tématu [principy jazyka DGML (Directed Graph Markup Language)](https://msdn.microsoft.com/library/ee842619.aspx).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Návrhář shaderů](../designers/shader-designer.md)|Popisuje, jak použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Designer shaderu pro práci s shadery.|
|[Uzly návrháře shaderů](../designers/shader-designer-nodes.md)|Popisuje druhy uzlů Návrháře shaderů, které lze použít k dosažení grafických efektů.|
|[Příklady návrháře shaderů](../designers/shader-designer-examples.md)|Obsahuje odkazy na témata, která ukazují, jak používat návrháře shaderu k dosažení běžných grafických efektů.|
