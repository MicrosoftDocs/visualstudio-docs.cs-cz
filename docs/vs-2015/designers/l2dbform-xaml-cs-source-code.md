---
title: Zdrojový kód L2DBForm.XAML.cs | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6ac13d8998972ddf60576537f8b0af55d832d820
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817532"
---
# <a name="l2dbformxamlcs-source-code"></a>Zdrojový kód L2DBForm.XAML.cs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje obsah a popis zdrojový kód C# v souboru L2DBForm.xaml.cs. Částečné třídy L2XDBForm obsažené v tomto souboru je možné rozdělit do tří logických částí: datové členy a `OnRemove` a `OnAddBook` obslužné rutiny události kliknutí na tlačítko.  
  
## <a name="data-members"></a>Datové členy  
 Pro tuto třídu do okna prostředků používaných v L2DBForm.xaml přidružení se používají dva soukromé datové členy.  
  
-   Proměnná oboru názvů `myBooks` je inicializován na `"http://www.mybooks.com"`.  
  
-   Člen `bookList` je inicializována v konstruktoru na řetězec CDATA v L2DBForm.xaml tento řádek:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>Obslužná rutina události OnAddBook  
 Tato metoda obsahuje následující tři příkazy:  
  
-   První podmíněný příkaz se používá k ověření vstupu.  
  
-   Druhý příkaz vytvoří novou <xref:System.Xml.Linq.XElement> z řetězce hodnoty zadané v uživatelem **přidat nová kniha** části uživatelského rozhraní (UI).  
  
-   Poslední příkaz přidá tento nový prvek book na poskytovatele dat v L2DBForm.xaml. V důsledku toho vázání dat dynamického automaticky aktualizuje uživatelské rozhraní s touto novou položkou; není vyžadován žádný extra uživatelský kód.  
  
## <a name="onremove-event-handler"></a>Obslužná rutina události OnRemove  
 `OnRemove` Obslužná rutina je složitější než `OnAddBook` obslužné rutiny pro dva důvody. Protože nezpracovaném kódu XML obsahuje mezeru zachovaných, odpovídající vložení znaků newline musí také být nejprve odebrány s položku v seznamu. Za druhé, usnadnění výběru, která byla v odstraněné položky, resetuje na předchozí objektem v seznamu.  
  
 Základní práce odebrání položky vybrané knihy však provádí pouze dva příkazy:  
  
- Nejprve je načten prvek knihy, které jsou spojené s aktuálně vybranou položku v seznamu:  
  
  ```  
  XElement selBook = (XElement)lbBooks.SelectedItem;   
  ```  
  
- Potom tento prvek je odstraněn z poskytovatele dat:  
  
  ```  
  selBook.Remove();  
  ```  
  
  Vázání dat dynamického znovu, zajišťuje programu uživatelského rozhraní se automaticky aktualizuje.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
  
### <a name="code"></a>Kód  
  
```csharp  
using System;  
using System.Linq;  
using System.Collections;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Input;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace LinqToXmlDataBinding {  
    /// <summary>  
    /// Interaction logic for L2XDBForm.xaml  
    /// </summary>  
  
    public partial class L2XDBForm : System.Windows.Window   
    {  
        XNamespace mybooks = "http://www.mybooks.com";  
        XElement bookList;  
  
        public L2XDBForm()   
        {  
            InitializeComponent();  
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
        }  
  
        void OnRemoveBook(object sender, EventArgs e)   
        {  
            int index = lbBooks.SelectedIndex;  
            if (index < 0) return;  
  
            XElement selBook = (XElement)lbBooks.SelectedItem;  
            //Get next node before removing element.  
            XNode nextNode = selBook.NextNode;  
            selBook.Remove();  
  
            //Remove any matching newline node.  
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))  
            { nextNode.Remove(); }  
  
            //Set selected item.   
            if (lbBooks.Items.Count > 0)  
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }  
        }  
  
        void OnAddBook(object sender, EventArgs e)   
        {  
            if (String.IsNullOrEmpty(tbAddID.Text) ||  
                String.IsNullOrEmpty(tbAddValue.Text))  
            {  
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");  
                return;   
            }  
            XElement newBook = new XElement(  
                                mybooks + "book",  
                                new XAttribute("id", tbAddID.Text),  
                                tbAddValue.Text);  
            bookList.Add("  ", newBook, "\r\n");  
        }  
    }  
}  
  
```  
  
### <a name="comments"></a>Komentáře  
 Související zdroje XAML pro tyto obslužné rutiny naleznete v tématu [zdrojový kód L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Příklad LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Zdrojový kód L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)



