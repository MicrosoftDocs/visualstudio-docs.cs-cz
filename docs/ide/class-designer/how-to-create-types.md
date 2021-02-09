---
title: 'Postupy: Vytváření typů pomocí návrháře tříd'
description: Naučte se navrhovat nové typy pro projekty v jazyce C# a Visual Basic vytvořením v diagramu tříd.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6102d5252564834f1de7c533e763d7b08a8f9fb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880538"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Postupy: vytváření typů pomocí Návrhář tříd

Chcete-li navrhnout nové typy pro projekty v jazyce C# a Visual Basic, vytvořte je v diagramu tříd. Chcete-li zobrazit existující typy, přečtěte si téma [Postup: zobrazení existujících typů](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Vytvořit nový typ

1. V **sadě nástrojů** v části **Návrhář tříd** přetáhněte jeden z nich do diagramu tříd:

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

     Viz [vytváření členů](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Použití vlastního atributu na typ

1. Klikněte na tvar typu v diagramu tříd.

2. V okně **vlastnosti** vedle vlastnosti **vlastní atributy** pro typ klikněte na tlačítko se třemi tečkami (...).

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou aplikovány na typ.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Použití vlastního atributu na člen typu

1. Klikněte na název člena ve tvaru jeho typu v diagramu tříd nebo na jeho řádku v okně Detaily třídy.

2. Ve **vlastnostech** Najděte vlastnost **vlastní atributy** člena.

3. Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.

   Vlastní atributy jsou aplikovány na typ.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md)
- [Postupy: vytváření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Vytváření a konfigurace členů typů](creating-and-configuring-type-members.md)
- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)
