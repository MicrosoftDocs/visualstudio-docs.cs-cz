---
title: Rozšíření diagramů závislostí
description: Přečtěte si, jak můžete napsat kód pro vytvoření a aktualizaci diagramů závislostí a jak ověřit strukturu kódu programu v diagramech závislostí v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388903"
---
# <a name="extend-dependency-diagrams"></a>Rozšíření diagramů závislostí

Můžete napsat kód pro vytváření a aktualizaci diagramů závislostí a k ověření struktury kódu programu pro diagramy závislostí v aplikaci Visual Studio. Můžete přidat příkazy, které se zobrazí v místní nabídce (kontextové) diagramu, upravit gesta přetažení a přistupovat k modelu vrstvy z textových šablon. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX) a distribuovat je ostatním uživatelům aplikace Visual Studio.

## <a name="requirements"></a>Požadavky

V počítači, na kterém chcete vyvíjet rozšíření vrstev, je nutné mít nainstalované následující:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Sada Modeling SDK pro Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

V počítači, na kterém chcete spustit rozšíření vrstvy, musíte mít nainstalovanou vhodnou verzi sady Visual Studio. Chcete-li zjistit, které edice sady Visual Studio podporují diagramy závislostí, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="see-also"></a>Viz také

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)
