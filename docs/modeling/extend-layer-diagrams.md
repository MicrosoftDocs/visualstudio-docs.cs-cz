---
title: Rozšíření diagramů závislostí
description: Přečtěte si, jak můžete napsat kód pro vytvoření a aktualizaci diagramů závislostí a jak ověřit strukturu kódu programu v diagramech závislostí v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d78b7005875f0544354c845cd27d187bdbf40d6d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361622"
---
# <a name="extend-dependency-diagrams"></a>Rozšíření diagramů závislostí

Můžete napsat kód pro vytváření a aktualizaci diagramů závislostí a k ověření struktury kódu programu pro diagramy závislostí v aplikaci Visual Studio. Můžete přidat příkazy, které se zobrazí v místní nabídce (kontextové) diagramu, upravit gesta přetažení a přistupovat k modelu vrstvy z textových šablon. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX) a distribuovat je ostatním uživatelům aplikace Visual Studio.

## <a name="requirements"></a>Požadavky

V počítači, na kterém chcete vyvíjet rozšíření vrstev, je nutné mít nainstalované následující:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Sada Modeling SDK pro Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

V počítači, na kterém chcete spustit rozšíření vrstvy, musíte mít nainstalovanou vhodnou verzi sady Visual Studio. Chcete-li zjistit, které edice sady Visual Studio podporují diagramy závislostí, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Viz také:

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)
