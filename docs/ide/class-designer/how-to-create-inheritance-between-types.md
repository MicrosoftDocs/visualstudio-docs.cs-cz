---
title: 'Postupy: Definice dědičnosti mezi typy (Návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: fbf540056318e092db13521dc80478cc7eb91948
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590368"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Postup: Vytvoření dědičnosti mezi typy v Návrháři tříd

Chcete-li vytvořit vztah dědičnosti mezi dvěma typy v diagramu **třídpomocí Návrháře tříd**, připojte základní typ k odvozenému typu nebo typům. Můžete mít vztah dědičnosti mezi dvěma třídami, mezi třídou a rozhraním nebo mezi dvěma rozhraními.

## <a name="to-create-an-inheritance-between-types"></a>Vytvoření dědičnosti mezi typy

1. V projektu v **Průzkumníku řešení**otevřete soubor diagramu tříd (.cd).

     Pokud nemáte diagram třídy, vytvořte jej. Postup: [Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md).

2. V **panelu nástrojů**klikněte v části **Návrhář e-potomkem**na **položku Dědičnost**.

3. V diagramu třídy nakreslete čáru dědičnosti mezi požadovanými typy, počínaje:

    - Odvozená třída základní třídy

    - Implementující třída implementovaného rozhraní

    - Rozšiřující se rozhraní k rozšířenému rozhraní

4. Volitelně pokud máte odvozený typ z obecného typu, klepněte na řádek dědičnosti. V okně **Vlastnosti** nastavte vlastnost **Typ argumentů** tak, aby odpovídala požadovanému typu obecného typu.

    > [!NOTE]
    > Pokud nadřazená abstraktní třída obsahuje alespoň jeden abstraktní člen, jsou všechny abstraktní členy implementovány jako neabstraktní dědící třídy.
    >
    >  Přestože můžete vizualizovat existující obecné typy, nelze vytvořit nové obecné typy. Také nelze změnit parametry typu pro existující obecné typy.

## <a name="see-also"></a>Viz také

- [Dědičnost](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Základní informace o dědičnosti](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Postup: Zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Třídy jazyka Visual C++ v návrháři tříd](visual-cpp-classes.md)
