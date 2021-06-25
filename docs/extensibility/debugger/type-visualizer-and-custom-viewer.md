---
title: Vizualizér typů a vlastní | Microsoft Docs
description: Seznamte se s komponentami vizualizéru typů a vlastními prohlížeči, které zobrazují data v konkrétním formátu, a rozdíly mezi nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c18bb49c740362d42a4a54bf52f6998629acb0c0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904419"
---
# <a name="type-visualizer-and-custom-viewer"></a>Vizualizér typů a vlastní prohlížeč
Vizualizér typů je komponenta, která zobrazuje část dat v určitém formátu. Formát je zcela na tom, kdo vizualizér implementuje, bez případě koncového uživatele nebo dodavatele vizualizérů třetích stran.

 Vlastní prohlížeč je součástí vyhodnocovače vlastních výrazů, který zobrazuje část dat v určitém formátu. Tento formát je zcela na implementátoru vlastního prohlížeče, což znamená, že formát je na implementátoru vyhodnocovače výrazů (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Podpora vizualizérů typů ve vyhodnocovači výrazů
 EE podporuje vizualizéry typů tím, že podporuje sadu rozhraní přístupných pro vizualizéry: rozhraní, jako jsou [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) a [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). EE ale nezo zodpovídá za implementaci samotného vizualizéru typů: EE pouze umožňuje externím vizualizérům přístup k informacím o typu. Tyto vizualizéry mohou být dodávány společně s EE a nainstalovány na příslušném místě v Visual Studio, které dodává jiný dodavatel třetí strany nebo dokonce koncový uživatel.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Podpora vlastních prohlížečů ve vyhodnocovači výrazů
 EE může také podporovat vlastní diváky, ve kterých samotný EE poskytuje kód pro zobrazení datového typu. Vlastní prohlížeč implementuje rozhraní [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) které zpracovává všechny povinnosti zobrazení dat v požadovaném formátu. Prohlížeč má plnou kontrolu nad zobrazením a může dokonce nechat data upravit. Vlastní diváci dodávající EE se při odeslání produktu dodávají s EE.

## <a name="see-also"></a>Viz také
- [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Vyhodnocovač výrazů](../../extensibility/debugger/expression-evaluator.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
