---
title: 'Postupy: Vytváření typů pomocí návrháře tříd'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 769bcfa202961c5a492e4fcb5af8e522b9052059
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842258"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Postupy: vytváření typů pomocí návrháře tříd

K navrhování nových typů pro C# a projekty Visual Basic, vytvořte je v diagramu tříd. Existující typy najdete v tématu [postupy: zobrazení existujících typů](how-to-view-existing-types.md).

##  <a name="CreateType"></a> Vytvořte nový typ

1.  V **nástrojů**v části **návrhář tříd**, přetáhněte jeden z nich do diagramu tříd:

    -   **Třída** nebo **abstraktní třídy**

    -   **Výčet**

    -   **Rozhraní**

    -   **Struktura** (VB) nebo **struktura** (C#)

    -   **Delegát**

    -   **Modul** (pouze VB)

2.  Pojmenujte typ. Poté vyberte jeho úroveň přístupu.

3.  Vyberte soubor, do kterého chcete přidat počáteční kód pro daný typ:

    -   Chcete-li vytvořit nový soubor a přidat jej do aktuálního projektu, vyberte **vytvořit nový soubor** a název souboru.

    -   Přidání kódu do existujícího souboru, vyberte **přidat do existujícího souboru**.

         Pokud má vaše řešení projekt, které sdílejí kód mezi více aplikacemi, můžete přidat nový typ do diagramu tříd v projektu aplikace, ale pouze pokud odpovídající soubor třídy je ve stejném projektu aplikace nebo je ve sdíleném projektu.

4.  Nyní přidejte další položky pro definování typu:

    |||
    |-|-|
    |**pro**|**Add**|
    |Třídy, abstraktní třídy nebo struktury|Metody, vlastnosti, pole, události, konstruktory (metoda), destruktory (metoda) a konstanty, které určují typ|
    |Výčty|Hodnoty polí, které tvoří výčet|
    |Rozhraní|Metody, vlastnosti a události, které tvoří rozhraní|
    |Delegát|Parametry, které definují delegáta|
    |Modul|Metody, vlastnosti, pole, události, konstruktory (metoda) a konstanty, které určují modul|

     Zobrazit [vytváření členů](creating-and-configuring-type-members.md#create-members).

##  <a name="CustAttributeType"></a> Použít vlastní atribut na typ

1. Klikněte na tvar typu v diagramu tříd.

2. V **vlastnosti**vedle možnosti **vlastní atributy** pro daný typ klikněte na tlačítko se třemi tečkami (...).

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou použity k typu.

##  <a name="CustAttributeMember"></a> Použít vlastní atribut na člen typu

1. Klikněte na název člena ve tvaru jeho typu v diagramu tříd nebo na jeho řádku v okně Detaily třídy.

2. V **vlastnosti**, najít členský **vlastní atributy** vlastnost.

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou použity k typu.

## <a name="see-also"></a>Viz také:

- [Postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postupy: vytvoření asociací mezi typy](how-to-create-associations-between-types.md)
- [Vytváření a konfigurace členů typů](creating-and-configuring-type-members.md)
- [Práce s diagramy tříd](working-with-class-diagrams.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
