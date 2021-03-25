---
title: Vizualizér typů a vlastní prohlížeč | Microsoft Docs
description: Přečtěte si informace o komponentách Vizualizér typů a vlastních čtenářích, které zobrazují data v konkrétním formátu a rozdíly mezi nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 869f0997ee166b9b7eb29c1a313854437d670ee4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057816"
---
# <a name="type-visualizer-and-custom-viewer"></a>Vizualizér typů a vlastní prohlížeč
Vizualizér typů je komponenta, která zobrazuje určitou část dat v určitém formátu. Formát je zcela na to, kdo implementuje vizualizér, jedná se o koncového uživatele nebo dodavatelem třetích stran pro vizualizuje.

 Vlastní prohlížeč je součástí vyhodnocovacího filtru výrazů, který zobrazuje část dat v určitém formátu. Tento formát je zcela až do implementátora vlastního prohlížeče, což znamená, že je formát až implementátori vyhodnocení výrazu (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Podpora typů vizualizací v vyhodnocovacím filtru výrazů
 EE podporuje vizualizace typů prostřednictvím podpory sady rozhraní, které jsou přístupné pro vizualizuje: rozhraní jako [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) a [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). EE ale nezodpovídá za implementaci samotného Vizualizér typu: EE pouze umožňuje externím přístupovým modulům pro přístup k informacím o typu. Tyto vizualizace mohou být dodávány spolu s EE a nainstalovány na vhodné místo v aplikaci Visual Studio, které poskytuje jiný dodavatel třetí strany nebo dokonce i koncovým uživatelem.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Podpora pro vlastní diváky v vyhodnocovacím filtru výrazů
 ET EE může také podporovat vlastní diváky, ve kterých si EE sám dodá kód pro zobrazení datového typu. Vlastní prohlížeč implementuje rozhraní [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , které zpracovává všechny povinnosti zobrazovat data v jakémkoli formátu. prohlížeč má úplnou kontrolu nad displejem a může dokonce upravovat data. Všichni vlastní čtenáři dodané pomocí et EE přicházejí spolu s dodaným produktem do části EE.

## <a name="see-also"></a>Viz také
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md)
- [Ladicí stroj](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
