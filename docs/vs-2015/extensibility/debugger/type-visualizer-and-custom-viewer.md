---
title: Vizualizér typů a vlastní prohlížeč | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185309"
---
# <a name="type-visualizer-and-custom-viewer"></a>Vizualizér typů a vlastní prohlížeč
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vizualizér typů je komponenta, která zobrazuje data v velmi specifickém formátu. Tento formát je zcela až do implementátora vizualizér, jedná se o koncového uživatele nebo dodavatele vizualizují.  
  
 Vlastní prohlížeč je součástí vyhodnocovacího filtru výrazů, který zobrazuje část dat ve velmi specifickém formátu. Tento formát je zcela až do implementátora vlastního prohlížeče, což znamená, že je formát až implementátori vyhodnocení výrazu (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Podpora typů vizualizací v vyhodnocovacím filtru výrazů  
 EE může podporovat typy vizualizací podporou sady rozhraní, které jsou přístupné pro vizualizace: rozhraní jako [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) a [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Upozorňujeme však, že v EE není zodpovědný za implementaci samotného Vizualizér typu: EE umožňuje přístup k jeho informacím o typu pouze externím rozhraním pro vizualizaci. Tyto vizualizace mohou být dodávány spolu s EE a nainstalovány na vhodné místo v aplikaci Visual Studio, které poskytuje jiný dodavatel třetí strany nebo dokonce i koncovým uživatelem.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Podpora pro vlastní diváky v vyhodnocovacím filtru výrazů  
 ET EE může také podporovat vlastní diváky, ve kterých si EE sám dodá kód pro zobrazení datového typu. Vlastní prohlížeč implementuje rozhraní [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , které zpracovává všechny povinnosti zobrazovat data v jakémkoli formátu. prohlížeč má úplnou kontrolu nad displejem a může dokonce upravovat data. Všichni vlastní čtenáři dodané pomocí et EE přicházejí spolu s dodaným produktem do části EE.  
  
## <a name="see-also"></a>Viz také  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)   
 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md)   
 [Ladicí stroj](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
