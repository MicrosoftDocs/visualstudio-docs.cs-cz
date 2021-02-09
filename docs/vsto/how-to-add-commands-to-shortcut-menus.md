---
title: 'Postupy: přidávání příkazů do místních nabídek'
description: Přečtěte si, jak můžete přidat příkazy do místní nabídky v aplikaci Office pomocí doplňku VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2f5c244d78ab5a6b5d98550b11c280159f285db7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913457"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Postupy: přidávání příkazů do místních nabídek
  Toto téma ukazuje, jak přidat příkazy do místní nabídky v aplikaci Office pomocí doplňku VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Přidání příkazů do místních nabídek v Office

1. Přidejte položku **XML pásu karet** do projektu doplňku VSTO na úrovni dokumentu nebo VSTO. Další informace najdete v tématu [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md). V

2. **Průzkumník řešení** vyberte **ThisAddIn.cs** nebo **ThisAddIn. vb**.

3. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor třídy **ThisAddIn** .

4. Do třídy **ThisAddIn** přidejte následující kód. Tento kód přepíše `CreateRibbonExtensibilityObject` metodu a vrátí třídu XML pásu karet do aplikace sady Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. V **Průzkumník řešení** vyberte soubor XML pásu karet. Ve výchozím nastavení se soubor XML pásu karet jmenuje *Ribbon1.xml*.

6. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor XML pásu karet.

7. V editoru kódu přidejte XML, které popisuje místní nabídku a ovládací prvek, který chcete přidat do místní nabídky.

     Následující příklad přidá tlačítko, nabídku a ovládací prvek galerie do místní nabídky pro wordový dokument. ID ovládacího prvku této místní nabídky je ContextMenuText. Úplný seznam ID ovládacího prvku zástupce Office 2010 najdete v tématu soubory s [nápovědu pro office 2010: identifikátory ovládacích prvků uživatelského rozhraní](https://www.microsoft.com/download/details.aspx?id=6627)pro Office Fluent.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. V **Průzkumník řešení** vyberte **MyRibbon.cs** nebo **MyRibbon. vb**.

9. Přidejte do třídy metodu zpětného volání `Ribbon1` pro každý ovládací prvek, který chcete zpracovat.

     Následující metoda zpětného volání zpracovává tlačítko **moje tlačítko** . Tento kód přidá řetězec do aktivního dokumentu v aktuálním umístění nástroje pro vydaný kurzor.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Viz také
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Návod: Vytvoření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přizpůsobení kontextových nabídek v sadě Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
