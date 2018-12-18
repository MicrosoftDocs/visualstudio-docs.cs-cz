---
title: 'Postupy: vytvoření a spuštění příkladu Linqtoxmldatabinding | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e299000cd8477ccc36829e806072cb25e115f8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237910"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Postupy: vytvoření a spuštění příkladu Linqtoxmldatabinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma ukazuje, jak vytvořit a sestavit projekt sady Visual Studio LinqToXmlDataBinding a spuštění výsledné program příklad LinqToXmlDataBinding Windows Presentation Foundation (WPF).  
  
 Další informace o vytváření projektů pomocí Visual Studio najdete v tématu [vývoj aplikací v sadě Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Vytváří se a naplňuje projektu  
  
#### <a name="to-create-the-starting-project"></a>Chcete-li vytvořit počáteční projekt  
  
1.  Spusťte sadu Visual Studio a vytvořte aplikaci WPF C# s názvem LinqToXmlDataBinding. Projekt musí používat rozhraní .NET Framework 3.5 (nebo novější).  
  
2.  Pokud není již k dispozici, přidejte odkazy na projekt pro následující sestavení .NET:  
  
    -   System.Data  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Sestavte řešení stisknutím kombinace kláves **Ctnrl + Shift + B**, spusťte ji stisknutím klávesy **F5**. Projekt by měl kompilovat bez chyb a spustit jako obecná aplikace WPF.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Přidání vlastního kódu do projektu  
  
1.  V Průzkumníku řešení přejmenujte zdrojový soubor Window1.xaml na L2XDBForm.xaml. Závislé zdrojový soubor Window1.xaml.cs by měl automaticky přejmenují na L2XDBForm.xaml.cs.  
  
2.  Nahradit v souboru L2XDBForm.xaml s oddílem kód z tématu nalezen zdrojový kód [zdrojový kód L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). (Použijte zobrazení zdroje XAML pro práci s tímto souborem.)  
  
3.  Podobně, nahraďte kód, který najdete ve zdroji v L2XDBForm.xaml.cs [zdrojový kód L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  V souboru App.xaml nahraďte všechny výskyty řetězce "Window1.xaml" s "L2XDBForm.xaml".  
  
5.  Sestavení řešení stisknutí **Ctrl + Shift + B**.  
  
## <a name="running-the-program"></a>Spuštění programu  
 LinqToXmlDataBinding program umožňuje uživateli zobrazit a pracovat s seznam knihy, které se ukládá jako vložený element XML.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Ke spuštění programu a zobrazení seznamu knihy  
  
1.  Spustit LinqToXmlDataBinding stisknutím klávesy **F5** (**spustit ladění**) nebo **Ctrl + F5** (**spustit bez ladění**). Okno aplikace s názvem **WPF datové vazby pomocí LINQ to XML** by se mělo zobrazit.  
  
2.  Všimněte si, že v horní části uživatelského rozhraní, které zobrazí nezpracovaný **XML** , která představuje seznam knihy. Zobrazí se pomocí WPF <xref:System.Windows.Controls.TextBlock> ovládací prvek, který neumožňuje interakce prostřednictvím klávesnice nebo myši.  
  
3.  Druhá svislý část s názvem **Book List**, zobrazuje – knihy jako prostý text seřazený seznam. Použije <xref:System.Windows.Controls.ListBox> ovládací prvek, který umožňuje výběr ale myš či klávesnice.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Můžete přidávat a odstraňovat knihy ze seznamu  
  
1.  Pokud chcete odstranit existující knihu ze seznamu, vyberte ho v **Book List** části a pak klikněte na tlačítko **odebrat vybrané knihy** tlačítko. Všimněte si, že položku v seznamu se odebral z knihy a raw výpisy zdroj XML.  
  
2.  Nová kniha přidat do seznamu, zadejte hodnoty do **ID** a **hodnotu** <xref:System.Windows.Controls.TextBox> ovládacích prvků v poslední části **přidat nová kniha**, klikněte **přidat Kniha** tlačítko. Všimněte si, že knihy se připojí k seznamu v knihy a výpisy XML. Tento program nelze ověřit vstupní hodnoty.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Chcete-li upravit existující položka adresáře  
  
1.  Vyberte položku v seznamu ve druhém **Book List** oddílu. Jeho aktuální hodnoty má být zobrazen v třetí části **upravit vybrané knihy**.  
  
2.  Upravte hodnoty pomocí klávesnice. Hned <xref:System.Windows.Controls.TextBox> ovládací prvek ztratí fokus, změny se automaticky rozšíří na zdroj a knihy uvedené XML.  
  
## <a name="see-also"></a>Viz také  
 [Datové vazby WPF pomocí LINQ to XML příklad](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Návod: Příklad LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Vývoj aplikací v sadě Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)



