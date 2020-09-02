---
title: Rozšiřování diagramů vrstev | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315275"
---
# <a name="extend-layer-diagrams"></a>Rozšíření diagramů vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete napsat kód pro vytváření a aktualizaci diagramů vrstev a k ověření struktury kódu programu pro diagramy vrstev v aplikaci Visual Studio. Můžete přidat příkazy, které se zobrazí v místní nabídce (kontextové) diagramu, upravit gesta přetažení a přistupovat k modelu vrstvy z textových šablon. Tato rozšíření můžete zabalit do rozšíření integrace sady Visual Studio (VSIX) a distribuovat je ostatním uživatelům aplikace Visual Studio.

 Další informace o diagramech vrstev najdete v tématech:

- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a> Požadavků
 V počítači, na kterém chcete vyvíjet rozšíření vrstev, je nutné mít nainstalované následující:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Sada Modeling SDK pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  V počítači, na kterém chcete spustit rozšíření vrstvy, musíte mít nainstalovanou vhodnou verzi sady Visual Studio. Další informace najdete v tématu [nasazení rozšíření modelu vrstvy](../modeling/deploy-a-layer-model-extension.md).

  Chcete-li zjistit, které verze sady Visual Studio podporují diagramy vrstev, přečtěte si téma [podpora verzí pro architektury a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>V tomto oddílu
 [Přidávání příkazů a gest do diagramů vrstev](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Přidání ověřování vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Přidání vlastních vlastností do diagramů vrstev](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Procházení a aktualizace modelů vrstev v programovém kódu](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Nasazení rozšíření pro modelování vrstev](../modeling/deploy-a-layer-model-extension.md)

 [Řešení potíží s rozšířeními pro diagramy vrstev](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Viz také
 [Definování a instalace diagramů rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md) [: diagramy referenčních](../modeling/layer-diagrams-reference.md) [vrstev: pokyny](../modeling/layer-diagrams-guidelines.md) [k vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md) [ověření kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md) [generují soubory z modelu UML](../modeling/generate-files-from-a-uml-model.md) [otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
