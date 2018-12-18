---
title: 'Postupy: vytváření typů pomocí návrháře tříd | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8288e17ecfb4c9169b2b9b8fb7cd5a3c3788f4d9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175029"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Postupy: Vytváření typů pomocí návrháře tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Navrhování nových typů pro projekty Visual Basic .NET a Visual C# .NET, vytvořte je v diagramu tříd. Existující typy najdete v tématu [postupy: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md).  
  
-   [Vytvořte nový typ](#CreateType)  
  
-   [Použít vlastní atribut na typ](#CustAttributeType)  
  
-   [Použít vlastní atribut na člen typu](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Vytvořte nový typ  
  
1.  V sadě nástrojů v nabídce Návrhář tříd přetáhněte jeden z nich do diagramu tříd:  
  
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
  
     Zobrazit [vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Použít vlastní atribut na typ  
  
1.  Klikněte na tvar typu v diagramu tříd.  
  
2.  V okně Vlastnosti vedle **vlastní atributy** pro daný typ klikněte na tlačítko se třemi tečkami (...).  
  
3.  Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.  
  
     Až skončíte, uživatelské atributy se použijí na typ.  
  
##  <a name="CustAttributeMember"></a> Použít vlastní atribut na člen typu  
  
1.  Klikněte na název člena ve tvaru jeho typu v diagramu tříd nebo na jeho řádku v okně Detaily třídy.  
  
2.  V okně vlastnosti vyhledejte člena **vlastní atributy** vlastnost.  
  
3.  Přidejte jeden nebo více uživatelských atributů, vždy jeden na řádek. Nevkládejte je do závorek.  
  
     Až skončíte, uživatelské atributy se použijí na typ.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření dědičnosti mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Postupy: vytvoření asociací mezi typy (návrhář tříd)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Vytvoření a konfigurace členů typů (návrhář tříd)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Práce s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)   
 [Navrhování tříd a typů (Návrhář tříd)](../ide/designing-classes-and-types-class-designer.md)



