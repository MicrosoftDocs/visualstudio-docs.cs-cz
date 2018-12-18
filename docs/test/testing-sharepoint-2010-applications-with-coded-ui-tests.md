---
title: Testování aplikací pro SharePoint pomocí programových testů uživatelského rozhraní
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d17857f1d20508041ad6c5daa90a962d6d30e6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895441"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testování aplikací pro SharePoint pomocí programových testů uživatelského rozhraní

Zahrnutí programových testů UI v aplikaci SharePoint slouží k ověření, že celá aplikace včetně jeho ovládacích prvků uživatelského rozhraní pracuje správně. Programové testy uživatelského rozhraní můžete také ověřit, hodnoty a logiku v uživatelském rozhraní.

Další informace o výhodách používání programové testy UI, naleznete v tématu [automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Vytvořit programový test uživatelského rozhraní pro aplikace SharePoint

[Vytvořit programový test UI](../test/use-ui-automation-to-test-your-code.md) aplikací služby SharePoint je stejné jako vytvoření testů pro ostatní typy aplikací. Záznam a přehrávání je podporován pro všechny ovládací prvky **webových úprav** rozhraní. Rozhraní pro výběr kategorie a webové části jsou všechny standardní webové ovládací prvky.

![Webové části služby SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Pokud záznam akce ověření akce před generováním kódu. Vzhledem k tomu, že existují různé chování spojené s myší najedete, je ve výchozím nastavení. Nezapomeňte odebrat redundantní ukazatele z programových testů uživatelského rozhraní. Provedete to tak, že upravíte kód testu, nebo pomocí [editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Ovládací prvky Office testu v rámci aplikace služby SharePoint

Pokud chcete povolit automatizaci některých webových částí office v aplikaci SharePoint, budete muset provést některé změny drobné úpravy v kódu.

> [!NOTE]
> Testování aplikace Visio a PowerPoint ovládacích prvků v aplikaci služby SharePoint není podporován.

### <a name="excel-cell-controls"></a>Ovládací prvky Excelu buňky

Zahrnout ovládací prvky Excelu buňky, je třeba provést některé změny v kódu programového testu uživatelského rozhraní.

> [!WARNING]
> Zadávání textu v libovolnou buňku aplikace Excel, za nímž následuje klíče akci šipku, nezaznamenává správně. Vyberte buňky pomocí myši.

Záznamu akce na prázdnou buňku, je třeba upravit kód, double klikněte na buňku a následnému provedením operace text nastavení. To je potřeba proto klikněte na buňku, následované žádnou akci klávesnice aktivuje `textarea` v buňce. Jednoduše záznam `setvalue` na prázdnou buňku by vyhledejte `editbox` která není k dispozici, dokud se kliklo na buňku. Příklad:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Pokud se nahrávání akcí na prázdné buňky, pak záznam získá o něco složitější, protože v okamžiku, přidejte text do buňky, nový \<div > ovládací prvek je přidán jako podřízený objekt buňky. Nové \<div > ovládací prvek obsahuje text, který jste právě zadali. Záznam je potřeba zaznamenat akce na novém \<div > ovládací prvek; ale není toho schopen, protože nový \<div > ovládací prvek neexistuje až po zadání testu. Musíte ručně provést následující změny kódu tak, aby vyhovovaly tento problém.

1. Přejděte do buňky inicializace a ujistěte se, `RowIndex` a `ColumnIndex` primární vlastnosti:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Najít `HtmlDiv` podřízené buňky:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Přidejte kód pro myši dvakrát klikněte na akci na `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Přidejte kód pro nastavení na text `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
