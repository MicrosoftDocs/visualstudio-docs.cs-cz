---
title: Rozšíření diagramů závislostí
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302943"
---
# <a name="extend-dependency-diagrams"></a>Rozšíření diagramů závislostí

Můžete napsat kód pro vytvoření a aktualizaci diagramů závislostí a ověření struktury kódu programu proti diagramům závislostí v sadě Visual Studio. Můžete přidat příkazy, které se zobrazí v místní (kontextové) nabídce diagramů, přizpůsobit gesta přetažení a získat přístup k modelu vrstvy ze šablon textu. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX) a distribuovat je ostatním uživatelům sady Visual Studio.

## <a name="requirements"></a>Požadavky

V počítači, ve kterém chcete vyvinout rozšíření vrstev, musíte mít nainstalované následující:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modelování sady SDK pro sady Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

V počítači, ve kterém chcete spustit rozšíření vrstev, musí být nainstalována vhodná edice sady Visual Studio. Informace o tom, které edice sady Visual Studio podporují diagramy závislostí, naleznete [v tématu Podpora edice pro architekturu a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Viz také

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)
