---
title: 'Postupy: Definice dědičnosti mezi typy (Návrhář tříd)'
description: Naučte se vytvořit vztah dědičnosti mezi dvěma typy v diagramu tříd pomocí Návrhář tříd.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 199f220529b28d4ca0c668d30564da65f6553e0e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901463"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Postupy: vytvoření dědičnosti mezi typy v Návrhář tříd

Chcete-li vytvořit vztah dědičnosti mezi dvěma typy v diagramu tříd pomocí **Návrhář tříd**, připojte základní typ s jeho odvozeným typem nebo typy. Můžete mít vztah dědičnosti mezi dvěma třídami, mezi třídou a rozhraním nebo mezi dvěma rozhraními.

## <a name="to-create-an-inheritance-between-types"></a>Vytvoření dědičnosti mezi typy

1. Z projektu v **Průzkumník řešení** otevřete soubor diagramu tříd (. CD).

     Pokud nemáte diagram tříd, vytvořte jej. Viz [Postupy: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md).

2. V **soupravě nástrojů** v části **Návrhář tříd** klikněte na **Dědičnost**.

3. V diagramu tříd nakreslete čáru dědičnosti mezi typy, které chcete, od:

    - Odvozená třída pro základní třídu

    - Implementující třída do implementovaného rozhraní

    - Rozšíření rozhraní na rozšířené rozhraní

4. Případně, pokud máte odvozený typ z obecného typu, klikněte na čáru dědičnosti. V okně **vlastnosti** nastavte vlastnost **argumenty typu** tak, aby odpovídala typu, který chcete pro obecný typ.

    > [!NOTE]
    > Pokud nadřazená abstraktní třída obsahuje alespoň jeden abstraktní člen, jsou všechny abstraktní členy implementovány jako neabstraktní třídy dědění.
    >
    >  I když můžete vizualizovat existující obecné typy, nemůžete vytvořit nové obecné typy. Nemůžete také změnit parametry typu pro existující obecné typy.

## <a name="see-also"></a>Viz také

- [Dědičnost](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Základní informace o dědičnosti](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Postupy: zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Třídy jazyka Visual C++ v návrháři tříd](visual-cpp-classes.md)
