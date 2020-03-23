---
title: 'Postupy: Vytváření typů pomocí návrháře tříd'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881a8ed7f1aceb5f97eaed1f0b9285951d1d39f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590173"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Postup: Vytváření typů pomocí Návrháře tříd

Chcete-li navrhnout nové typy pro projekty jazyka C# a Visual Basic, vytvořte je v diagramu třídy. Existující typy najdete v [tématu Jak: Zobrazit existující typy](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a>Vytvoření nového typu

1. V **panelu**nástrojů **přetáhněte**jednu z nich do diagramu třídy:

    - **Třída** nebo **abstraktní třída**

    - **Výčet**

    - **Rozhraní**

    - **Struktura** (VB) nebo **Struct** (C#)

    - **Delegát**

    - **Modul** (pouze VB)

2. Pojmenujte typ. Poté vyberte jeho úroveň přístupu.

3. Vyberte soubor, do kterého chcete přidat počáteční kód pro daný typ:

    - Chcete-li vytvořit nový soubor a přidat jej do aktuálního projektu, vyberte **Vytvořit nový soubor** a pojmenujte soubor.

    - Chcete-li přidat kód do existujícího souboru, vyberte **Přidat do existujícího souboru**.

         Pokud vaše řešení má projekt, který sdílí kód mezi více aplikacemi, můžete přidat nový typ do diagramu třídy v projektu aplikace, ale pouze v případě, že odpovídající soubor třídy je ve stejném projektu aplikace nebo je ve sdíleném projektu.

4. Nyní přidejte další položky pro definování typu:

    |||
    |-|-|
    |**Pro**|**Přidat**|
    |Třídy, abstraktní třídy nebo struktury|Metody, vlastnosti, pole, události, konstruktory (metoda), destruktory (metoda) a konstanty, které určují typ|
    |Výčty|Hodnoty polí, které tvoří výčet|
    |Rozhraní|Metody, vlastnosti a události, které tvoří rozhraní|
    |Delegát|Parametry, které definují delegáta|
    |Modul|Metody, vlastnosti, pole, události, konstruktory (metoda) a konstanty, které určují modul|

     Viz [Vytváření členů](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a>Použití vlastního atributu u typu

1. Klikněte na tvar typu v diagramu tříd.

2. Ve **vlastnostech vlastnosti Vlastnosti**vlastnosti **Vlastní atributy** pro daný typ klepněte na tlačítko tři tečky (...).

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou použity na typ.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a>Použití vlastního atributu u člena typu

1. Klikněte na název člena ve tvaru jeho typu v diagramu tříd nebo na jeho řádku v okně Detaily třídy.

2. Ve **vlastnostech**vyhledejte vlastnost **Vlastní atributy** člena.

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou použity na typ.

## <a name="see-also"></a>Viz také

- [Postup: Vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postup: Vytvoření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Vytváření a konfigurace členů typů](creating-and-configuring-type-members.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
