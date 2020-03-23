---
title: Rozšířit diagramy vrstev | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302334"
---
# <a name="extend-layer-diagrams"></a>Rozšíření diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete napsat kód pro vytvoření a aktualizaci diagramů vrstev a ověření struktury kódu programu proti diagramům vrstev v sadě Visual Studio. Můžete přidat příkazy, které se zobrazí v místní (kontextové) nabídce diagramů, přizpůsobit gesta přetažení a získat přístup k modelu vrstvy ze šablon textu. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX) a distribuovat je ostatním uživatelům sady Visual Studio.

 Další informace o diagramech vrstev naleznete v následujících tématech:

- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Požadavky
 V počítači, ve kterém chcete vyvinout rozšíření vrstev, musíte mít nainstalované následující:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Modelování sady SDK pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  V počítači, ve kterém chcete spustit rozšíření vrstev, musíte mít nainstalovanou vhodnou verzi sady Visual Studio. Další informace naleznete [v tématu Deploy a layer model extension](../modeling/deploy-a-layer-model-extension.md).

  Informace o tom, které verze diagramů vrstev podpory sady Visual Studio podporují, naleznete [v tématu Podpora verzí pro architekturu a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>V tomto oddílu
 [Přidávání příkazů a gest do diagramů vrstev](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Přidání ověřování vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Přidání vlastních vlastností do diagramů vrstev](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Procházení a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Nasazení rozšíření pro modelování vrstev](../modeling/deploy-a-layer-model-extension.md)

 [Řešení potíží s rozšířeními pro diagramy vrstev](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Viz také
 [Definování a instalace](../modeling/define-and-install-a-modeling-extension.md) diagramů vrstev rozšíření [modelování: Diagramy](../modeling/layer-diagrams-reference.md) [referenčních vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md) Vytvoření [diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md) Ověřit kód pomocí [diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md) Generování souborů z modelu [UML](../modeling/generate-files-from-a-uml-model.md) Otevření modelu [UML pomocí rozhraní API Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
