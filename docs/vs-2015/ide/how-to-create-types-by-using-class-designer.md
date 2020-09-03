---
title: 'Postupy: vytváření typů pomocí Návrhář tříd | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f87e3a3adda270f6b78b9134c7535bda6c73d952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533143"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Postupy: Vytváření typů pomocí návrháře tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li navrhnout nové typy pro projekty Visual C# .NET a Visual Basic .NET, vytvořte je v diagramu tříd. Chcete-li zobrazit existující typy, přečtěte si téma [Postup: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md).

- [Vytvořit nový typ](#CreateType)

- [Použití vlastního atributu na typ](#CustAttributeType)

- [Použití vlastního atributu na člen typu](#CustAttributeMember)

## <a name="create-a-new-type"></a><a name="CreateType"></a> Vytvořit nový typ

1. V sadě nástrojů v nabídce Návrhář tříd přetáhněte jeden z nich do diagramu tříd:

    - **Třída** nebo **abstraktní třída**

    - **Výčet**

    - **Rozhraní**

    - **Structure** (VB) nebo **struct** (C#)

    - **Delegát**

    - **Modul** (pouze VB)

2. Pojmenujte typ. Poté vyberte jeho úroveň přístupu.

3. Vyberte soubor, do kterého chcete přidat počáteční kód pro daný typ:

    - Chcete-li vytvořit nový soubor a přidat jej do aktuálního projektu, vyberte možnost **vytvořit nový soubor** a pojmenujte soubor.

    - Chcete-li přidat kód do existujícího souboru, vyberte možnost **Přidat k existujícímu souboru**.

         Pokud má vaše řešení projekt, který sdílí kód napříč více aplikacemi, můžete přidat nový typ do diagramu tříd v projektu aplikace, ale pouze v případě, že je odpovídající soubor třídy ve stejném projektu aplikace nebo se nachází ve sdíleném projektu.

4. Nyní přidejte další položky pro definování typu:

    |**For**|**Přidat**|
    |-|-|
    |Třídy, abstraktní třídy nebo struktury|Metody, vlastnosti, pole, události, konstruktory (metoda), destruktory (metoda) a konstanty, které určují typ|
    |Výčty|Hodnoty polí, které tvoří výčet|
    |Rozhraní|Metody, vlastnosti a události, které tvoří rozhraní|
    |Delegát|Parametry, které definují delegáta|
    |Modul|Metody, vlastnosti, pole, události, konstruktory (metoda) a konstanty, které určují modul|

     Viz [vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Použití vlastního atributu na typ

1. Klikněte na tvar typu v diagramu tříd.

2. V okno Vlastnosti klikněte vedle vlastnosti **vlastní atributy** pro typ na tlačítko se třemi tečkami (...).

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

     Až skončíte, uživatelské atributy se použijí na typ.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Použití vlastního atributu na člen typu

1. Klikněte na název člena ve tvaru jeho typu v diagramu tříd nebo na jeho řádku v okně Detaily třídy.

2. V okno Vlastnosti Najděte vlastnost **vlastní atributy** člena.

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

     Až skončíte, uživatelské atributy se použijí na typ.

## <a name="see-also"></a>Viz také
 [Postupy: vytvoření dědičnosti mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md) [Postupy: vytváření přidružení mezi typy (návrhář tříd)](../ide/how-to-create-associations-between-types-class-designer.md) [vytváření a konfigurace členů typu (návrhář tříd)](../ide/creating-and-configuring-type-members-class-designer.md) [práce s diagramy tříd (Návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md) [navrhování tříd a typů (návrhář tříd)](../ide/designing-classes-and-types-class-designer.md)
