---
title: 'Postupy: sestavení a spuštění příkladu příkladu LinqToXmlDataBinding | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5584494f65eaef72c2aa350af4e5af36155e0501
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664618"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Postupy: sestavení a spuštění příkladu příkladu LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto tématu se dozvíte, jak vytvořit a sestavit projekt příkladu LinqToXmlDataBinding sady Visual Studio a jak spustit výsledný program příkladu LinqToXmlDataBinding Windows Presentation Foundation (WPF).

 Další informace o použití sady Visual Studio k vytváření projektů naleznete v tématu [vývoj aplikací v aplikaci Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68).

## <a name="creating-and-populating-the-project"></a>Vytvoření a naplnění projektu

#### <a name="to-create-the-starting-project"></a>Vytvoření spouštěného projektu

1. Spusťte Visual Studio a vytvořte aplikaci WPF v C# s názvem příkladu LinqToXmlDataBinding. Projekt musí používat .NET Framework 3,5 (nebo novější).

2. Pokud ještě není k dispozici, přidejte odkazy na projekt pro následující sestavení .NET:

    - System.Data

    - System. data. DataSetExtensions

    - System.Xml

    - System.Xml. LINQ

3. Sestavte řešení stisknutím **Ctnrl + SHIFT + B**a potom ho spusťte stisknutím klávesy **F5**. Projekt by se měl kompilovat bez chyb a spustit jako obecná aplikace WPF.

#### <a name="to-add-custom-code-to-the-project"></a>Přidání vlastního kódu do projektu

1. V Průzkumník řešení přejmenujte zdrojový soubor Window1. XAML na L2XDBForm. XAML. Závislý zdrojový soubor Window1.xaml.cs by se měl automaticky přejmenovat na L2XDBForm.xaml.cs.

2. Nahraďte zdrojový kód, který se nachází v souboru L2XDBForm. XAML, oddílem Code v tématu [zdrojový kód L2DBForm. XAML Source Code](../designers/l2dbform-xaml-source-code.md). (Pro práci s tímto souborem použijte zobrazení zdroje XAML.)

3. Podobně nahraďte zdroj v L2XDBForm.xaml.cs kódem, který najdete ve [zdrojovém kódu L2DBForm.XAML.cs](../designers/l2dbform-xaml-cs-source-code.md).

4. V souboru App. xaml nahraďte všechny výskyty řetězce "Window1. XAML" pomocí "L2XDBForm. XAML".

5. Sestavte řešení stisknutím **kombinace kláves CTRL + SHIFT + B**.

## <a name="running-the-program"></a>Spuštění programu
 Program příkladu LinqToXmlDataBinding umožňuje uživateli zobrazit a manipulovat se seznamem knih, které jsou uloženy jako vložený prvek XML.

#### <a name="to-run-the-program-and-view-the-book-list"></a>Spuštění programu a zobrazení seznamu knih

1. Spusťte příkladu LinqToXmlDataBinding stisknutím klávesy **F5** (**Spustit ladění**) nebo **kombinací kláves CTRL + F5** (**Spustit bez ladění**). Mělo by se zobrazit okno programu s názvem **datovou vazbu WPF pomocí LINQ to XML** .

2. Všimněte si horní části uživatelského rozhraní, ve kterém se zobrazuje nezpracovaný **kód XML** , který představuje seznam knih. Zobrazuje se pomocí <xref:System.Windows.Controls.TextBlock> ovládacího prvku WPF, který neumožňuje interakci přes myš ani klávesnici.

3. Druhá svislá sekce, označená jako **seznam knihy**, zobrazuje knihy jako seznam seřazený jako prostý text. Používá <xref:System.Windows.Controls.ListBox> ovládací prvek, který umožňuje výběr i přes myš nebo klávesnici.

#### <a name="to-add-and-delete-books-from-the-list"></a>Přidání a odstranění knih ze seznamu

1. Pokud chcete odstranit existující knihu ze seznamu, vyberte ji v části **seznam knih** a pak klikněte na tlačítko **Odebrat vybranou knihu** . Všimněte si, že položka knihy byla odebrána z knihy i z nezpracovaného zdrojového seznamu XML.

2. Pokud chcete do seznamu přidat novou knihu, zadejte hodnoty do ovládacích prvků **ID** a **hodnoty** <xref:System.Windows.Controls.TextBox> v poslední části, **přidejte novou knihu**a pak klikněte na tlačítko **Přidat knihu** . Všimněte si, že se kniha připojí k seznamu v knize i ve výpisech XML. Tento program neověřuje vstupní hodnoty.

#### <a name="to-edit-an-existing-book-entry"></a>Úprava existujícího záznamu knihy

1. V části seznamu druhých **knih** vyberte položku kniha. Jeho aktuální hodnoty by se měly zobrazit ve třetí části, **Upravit vybranou knihu**.

2. Upravte hodnoty pomocí klávesnice. Jakmile některý z <xref:System.Windows.Controls.TextBox> ovládacích prvků ztratí fokus, změny se automaticky rozšíří do seznamu zdrojů a seznamů XML.

## <a name="see-also"></a>Viz také
 [Datová vazba WPF pomocí LINQ to XML ukázkový](../designers/wpf-data-binding-using-linq-to-xml-example.md) [Návod: příkladu LinqToXmlDataBinding ukázkový](../designers/walkthrough-linqtoxmldatabinding-example.md) [vývoj aplikací v aplikaci Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)
