---
title: Značky zpráv | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b668f0331345e6a1022ef79105614f4a22e91d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830075"
---
# <a name="message-markers"></a>Značky zpráv
Značka zprávy představuje výstup protokolu. Zpráva je řetězec, který je vydán určitým vláknem v určitém čase. Zprávy můžete exportovat do textového souboru pro použití s jinými nástroji. Můžete spočívat ukazatel na zprávu v souběžnosti Vizualizér pro zobrazení řetězce zprávy. A můžete zobrazit všechny značky zpráv v [sestavě Značky](../profiling/markers-report.md).  Na následujícím obrázku je zobrazena značka zprávy.

## <a name="message-aggregation-markers"></a>Značky agregace zpráv
 Někdy více zpráv dojít tak blízko k sobě v souběžnosti Vizualizátor, že nemohou být vypracovány jednotlivě. V takovém případě se zobrazí *značka agregace zpráv,* která představuje podkladové zprávy. Když položíte ukazatel myši na jednu z těchto ikon, zobrazí se v popisku počet zobrazených podkladových zpráv. Chcete-li zprávy zobrazit, přibližte je.  Pokud přiblížíte celou cestu a stále získáte značku agregace, můžete zobrazit podkladové zprávy v [sestavě značek](../profiling/markers-report.md).

## <a name="see-also"></a>Viz také
- [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)