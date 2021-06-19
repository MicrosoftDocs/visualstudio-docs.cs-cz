---
title: Čtení modelů a diagramů v jiných edicích sady Visual Studio
description: Přečtěte si o čtení modelů a diagramů v Visual Studio a také o chování jen pro čtení při použití verze Visual Studio která nepodporuje vytváření modelů.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95fbf6451a3f07581ff2bdb098428f41904d4276
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389901"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Čtení modelů a diagramů v jiných edicích sady Visual Studio

Když otevřete model ve verzi Visual Studio, která nepodporuje vytváření modelu, otevře se model v režimu jen pro čtení. V tomto režimu můžete změnit rozložení diagramů, ale nemůžete změnit model.

Informace o tom, které verze Visual Studio podporují vytváření modelů, najdete v tématu [Podpora verzí pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Získání přístupu k modelu a diagramům

Chcete-li načíst diagram závislostí, Visual Studio nejprve použít příkaz k otevření projektu modelování a pak v diagramu v rámci něj.

Z tohoto důvodu, pokud chcete číst diagram závislostí, musíte mít také přístup k projektu modelování, ve kterém byl vytvořen. Můžete to provést buď přístupem k projektu ze správy zdrojového kódu, nebo získáním kopie souborů projektu.

> [!NOTE]
> To neplatí pro mapy kódu a diagramy tříd .NET generované z kódu. Tyto diagramy lze zobrazit nezávisle na projektu modelování.

Pokud chcete načíst diagram závislostí, potřebujete minimální sadu souborů:

- Dva soubory diagramu pro diagram, který chcete číst, například **MyDiagram.classdiagram a MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > V případě diagramů závislostí byste měli mít také soubor s názvem _MyDiagram_**.layerdiagram.suppressions**.

- Soubor projektu modelování (**MyModel.modelproj**)

- Kořenový soubor modelu (**ModelDefinition\MyModel.uml**)

- Soubory balíčku pro libovolný balíček odkazovaný v diagramu (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Změny, které můžete provést v Read-Only režimu

Pokud otevřete model a jeho diagramy ve verzi Visual Studio, která nepodporuje vytváření modelů, nemůžete model změnit. To znamená, že nemůžete změnit prvky a relace, které se zobrazují v diagramech nebo v průzkumníku modelů. Rozložení diagramů ale můžete změnit:

- Uspořádání obrazců a konektorů v diagramu

- Rozbalení a sbalení obrazců

Tyto změny můžete uložit. Pokud chcete změny zviditelnit pro ostatní uživatele, musíte odeslat aspoň aktualizované **soubory .layout.**

## <a name="see-also"></a>Viz také

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
