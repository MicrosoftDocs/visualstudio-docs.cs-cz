---
title: 'Postupy: vytvoření dědičnosti mezi typy (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668096"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Postupy: vytvoření dědičnosti mezi typy (Návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vytvořit vztah dědičnosti mezi dvěma typy v diagramu tříd pomocí Návrhář tříd, připojte základní typ s jeho odvozeným typem nebo typy. Můžete mít vztah dědičnosti mezi dvěma třídami, mezi třídou a rozhraním nebo mezi dvěma rozhraními.

### <a name="to-create-an-inheritance-between-types"></a>Vytvoření dědičnosti mezi typy

1. Z projektu v Průzkumník řešení otevřete soubor diagramu tříd (. CD).

     Pokud nemáte diagram tříd, vytvořte jej. Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. V **soupravě nástrojů**v části **Návrhář tříd**klikněte na **Dědičnost**.

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
 [Základní informace o dědičnosti](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) [dědičnosti](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [: zobrazení dědičnosti mezi typy (Návrhář tříd)](../ide/how-to-view-inheritance-between-types-class-designer.md) [vizuální C++ třídy v Návrhář tříd](../ide/visual-cpp-classes-in-class-designer.md)
