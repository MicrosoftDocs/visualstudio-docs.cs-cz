---
title: 'Postupy: sestavení a spuštění příkladu příkladu LinqToXmlDataBinding'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b3999ae6fb602c9877bc3f997ab922bda08565b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636879"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Postupy: sestavení a spuštění příkladu příkladu LinqToXmlDataBinding

V tomto tématu se dozvíte, jak vytvořit a sestavit projekt příkladu LinqToXmlDataBinding sady Visual Studio a jak spustit výsledný program příkladu LinqToXmlDataBinding Windows Presentation Foundation (WPF).

Další informace o aplikaci Visual Studio naleznete v tématu [Visual Studio IDE Overview](../get-started/visual-studio-ide.md).

## <a name="create-the-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte C# **aplikaci WPF** s názvem **příkladu LinqToXmlDataBinding**.

   Projekt by měl cílit na .NET Framework 3,5 (nebo novější).

1. Pokud ještě není k dispozici, přidejte odkazy na projekt pro následující sestavení .NET:

    - System.Data

    - System. data. DataSetExtensions

    - System.Xml

    - System. XML. Linq

1. Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**a pak ho spusťte stisknutím klávesy **F5**. Projekt by se měl kompilovat bez chyb a spustit jako obecná aplikace WPF.

## <a name="add-code-to-the-project"></a>Přidat kód do projektu

1. V **Průzkumník řešení**přejmenujte zdrojový soubor **Window1. XAML** na **L2XDBForm. XAML**. Závislý zdrojový soubor **Window1.XAML.cs** by se měl automaticky přejmenovat na **L2XDBForm.XAML.cs**.

1. Nahraďte zdrojový kód, který se nachází v souboru **L2XDBForm. XAML** , oddílem Code v tématu [zdrojový kód L2DBForm. XAML Source Code](../designers/l2dbform-xaml-source-code.md). Pro práci s tímto souborem použijte zobrazení zdroje XAML.

1. Podobně nahraďte zdroj v **L2XDBForm.XAML.cs** kódem, který najdete ve [zdrojovém kódu L2DBForm.XAML.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. V souboru **App. XAML**nahraďte všechny výskyty řetězce `Window1.xaml` `L2XDBForm.xaml`.

1. Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**.

## <a name="run-the-program"></a>Spustit program

Program příkladu LinqToXmlDataBinding umožňuje uživateli zobrazit a manipulovat se seznamem knih, které jsou uloženy jako vložený prvek XML.

### <a name="to-run-the-program-and-view-the-book-list"></a>Spuštění programu a zobrazení seznamu knih

Spusťte příkladu LinqToXmlDataBinding stisknutím klávesy **F5** (**Spustit ladění**) nebo **kombinací kláves CTRL** +**F5** (**Spustit bez ladění**). Zobrazí se okno programu s názvem **datová vazba WPF pomocí LINQ to XML** .

- Všimněte si horní části uživatelského rozhraní, ve kterém se zobrazuje nezpracovaný **kód XML** , který představuje seznam knih. Zobrazuje se pomocí ovládacího prvku WPF <xref:System.Windows.Controls.TextBlock>, který neumožňuje interakci přes myš ani klávesnici.

- Druhá svislá sekce, označená jako **seznam knihy**, zobrazuje knihy jako seznam seřazený jako prostý text. Používá ovládací prvek <xref:System.Windows.Controls.ListBox>, který umožňuje výběr i přes myš nebo klávesnici.

### <a name="to-add-and-delete-books-from-the-list"></a>Přidání a odstranění knih ze seznamu

- Pokud chcete do seznamu přidat novou knihu, zadejte hodnoty do pole **ID** a **hodnota** <xref:System.Windows.Controls.TextBox> ovládací prvky v poslední části, **přidejte novou knihu**a pak klikněte na tlačítko **Přidat knihu** . Všimněte si, že se kniha připojí k seznamu v knize i ve výpisech XML. Tento program neověřuje vstupní hodnoty.

- Pokud chcete odstranit existující knihu ze seznamu, vyberte ji v části **seznam knih** a pak klikněte na tlačítko **Odebrat vybranou knihu** . Všimněte si, že položka knihy byla odebrána z knihy i z nezpracovaného zdrojového seznamu XML.

### <a name="to-edit-an-existing-book-entry"></a>Úprava existujícího záznamu knihy

1. V části seznamu druhých **knih** vyberte položku kniha. Jeho aktuální hodnoty by se měly zobrazit ve třetí části, **Upravit vybranou knihu**.

1. Upravte hodnoty pomocí klávesnice. Jakmile <xref:System.Windows.Controls.TextBox> ovládací prvek ztratí fokus, změny se automaticky rozšíří do seznamů zdrojů a knih XML.

## <a name="see-also"></a>Viz také:

- [Datová vazba WPF pomocí LINQ to XMLho příkladu](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Návod: příklad příkladu LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)