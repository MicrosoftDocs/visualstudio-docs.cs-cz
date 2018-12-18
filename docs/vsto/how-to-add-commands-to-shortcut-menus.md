---
title: 'Postupy: přidávání příkazů do místních nabídek'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9accca69c5d56461f07d21d25821c0f4181c8fbd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676004"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Postupy: přidávání příkazů do místních nabídek
  Toto téma ukazuje, jak přidat příkazy místní nabídky v aplikaci Office pomocí doplňku VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Přidání příkazů do místních nabídek v aplikaci Office  
  
1.  Přidat **kódu XML pásu karet** položky na úrovni dokumentu nebo projektu doplňku VSTO. Další informace najdete v tématu [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md). V  
  
2.  **Průzkumník řešení**vyberte **ThisAddin.cs** nebo **ThisAddin.vb**.  
  
3.  V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     **ThisAddin** soubor třídy se otevře v editoru kódu.  
  
4.  Přidejte následující kód, který **ThisAddin** třídy. Tento kód přepíše `CreateRibbonExtensibilityObject` třídu metodu a vrátí kódu XML pásu karet aplikace sady Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  V **Průzkumníka řešení**, vyberte soubor XML pásu karet. Ve výchozím nastavení, je název souboru XML pásu karet *Ribbon1.xml*.  
  
6.  V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     Soubor xml pásu karet se otevře v editoru kódu.  
  
7.  V editoru kódu přidejte kód XML, který popisuje místní nabídku a ovládací prvek, který chcete přidat do místní nabídky.  
  
     Následující příklad přidá tlačítko, zobrazí se nabídka a ovládací prvek galerie na místní nabídku pro wordový dokument. ID ovládacího prvku tuto nabídku je ContextMenuText. Úplný seznam ovládacího prvku Office 2010 místní ID, naleznete v tématu [soubory nápovědy Office 2010: Office fluent uživatelského rozhraní ovládacího prvku identifikátory](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
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
  
8.  V **Průzkumníka řešení**, zvolte **MyRibbon.cs** nebo **MyRibbon.vb**.  
  
9. Přidejte metodu zpětného volání pro `Ribbon1` třídy pro každý ovládací prvek, který chcete zpracovat.  
  
     Následující metoda zpracovává zpětného volání **tlačítko Moje** tlačítko. Tento kód přidá řetězec do aktivního dokumentu v aktuálním umístění kurzor.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Návod: Vytváření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Kontextové nabídky v aplikaci Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  