---
title: Značky zpráv | Microsoft Docs
description: Přečtěte si, jak můžete exportovat zprávy do textového souboru pro použití s jinými nástroji a když na zprávu v Vizualizátor souběžnosti vynecháte zobrazení řetězce zprávy.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0ce91a47bb2158f3cf684e1634a684f372a044d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879940"
---
# <a name="message-markers"></a>Značky zpráv
Značka zprávy představuje výstup protokolu. Zpráva je řetězec, který je vydaný konkrétním vláknem v určitou dobu. Zprávy můžete exportovat do textového souboru, aby je bylo možné použít s jinými nástroji. Pokud chcete zobrazit řetězec zprávy, můžete na zprávu v Vizualizátor souběžnosti ponechit ukazatel. A můžete zobrazit všechny značky zpráv v [sestavě značek](../profiling/markers-report.md).  Následující obrázek znázorňuje značku zprávy.

## <a name="message-aggregation-markers"></a>Značky agregace zpráv
 V některých případech se může stát, že v Vizualizátor souběžnosti dojde k několika zprávám, které se nedají kreslit jednotlivě. V takovém případě je zobrazena *značka agregace zprávy* , která představuje podkladové zprávy. Když umístíte ukazatel myši na jednu z těchto ikon, zobrazí se popis, který znázorňuje počet základních zpráv, které jsou reprezentovány. Chcete-li zobrazit zprávy, přiblížte se.  Pokud se přiblížíte ke všemu způsobem a stále získáte značku agregace, můžete zobrazit podkladové zprávy v [sestavě značek](../profiling/markers-report.md).

## <a name="see-also"></a>Viz také
- [Značky Vizualizátor souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)