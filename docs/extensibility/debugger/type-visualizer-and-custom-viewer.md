---
title: Typ vizualizéru a vlastního prohlížeče | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712470"
---
# <a name="type-visualizer-and-custom-viewer"></a>Typ vizualizéru a vlastního prohlížeče
Vizualizér typu je komponenta, která zobrazuje část dat v určitém formátu. Formát je zcela na tom, kdo implementuje vizualizér, ať už je to koncový uživatel nebo dodavatel vizualizérů třetí strany.

 Vlastní prohlížeč je součástí vlastního vyhodnocení výrazu, který zobrazuje část dat v určitém formátu. Tento formát je zcela na implementátoru vlastního prohlížeče, což znamená, že formát je na implementátoru vyhodnocení výrazu (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Podpora vizualizérů typu v evaluátoru výrazů
 EE podporuje vizualizéry typu tím, že podporuje sadu rozhraní přístupná vizualizátorům: rozhraní, jako je [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) a [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). EE však není zodpovědný za implementaci samotného vizualizéru typu: EE pouze umožňuje externívizizátory přístup k informacím o typu. Tyto vizualizéry mohou být dodávány spolu s EE a nainstalovány na příslušném místě v sadě Visual Studio, poskytované jiným dodavatelem třetí strany nebo dokonce koncovým uživatelem.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Podpora vlastních prohlížečů v hodnotiteli výrazů
 EE může také podporovat vlastní prohlížeče, ve kterých EE sám dodává kód pro zobrazení datového typu. Vlastní prohlížeč implementuje rozhraní [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) které zpracovává všechny povinnosti zobrazení dat v libovolném formátu je žádoucí; prohlížeč má plnou kontrolu nad displejem a může dokonce nechat data upravit. Všechny vlastní prohlížeče dodávané EE jsou dodávány s EE, když je produkt dodáván.

## <a name="see-also"></a>Viz také
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md)
- [Ladicí modul](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
