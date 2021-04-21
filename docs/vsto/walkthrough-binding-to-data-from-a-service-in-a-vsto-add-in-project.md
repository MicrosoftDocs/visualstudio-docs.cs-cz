---
title: Vytvoření vazby na data ze služby v projektu doplňku VSTO
description: Naučte se přidávat ovládací prvky do dokumentu Microsoft Wordu, navazovat ovládací prvky na data získaná ze služby obsahu MSDN a reagovat na události v době běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b6993cb3eebc7641f4486bdc617ecb78e40aa05c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824525"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Návod: vytvoření vazby na data ze služby v projektu doplňku VSTO
  Data můžete navazovat na hostitelské ovládací prvky v projektech doplňku VSTO. Tento návod ukazuje, jak přidat ovládací prvky do dokumentu aplikace systém Microsoft Office Word, navazovat ovládací prvky na data získaná ze služby obsahu MSDN a reagovat na události v době běhu.

 **Platí pro:** Informace v tomto tématu se vztahují na projekty na úrovni aplikace ve Wordu 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 Tento návod znázorňuje následující úlohy:

- Přidání <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku do dokumentu v době běhu.

- Navázání <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku na data z webové služby.

- Reakce na <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> událost <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]:

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Prvním krokem je vytvoření projektu doplňku VSTO aplikace Word.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt doplňku VSTO aplikace Word s názvem **služba obsahu MTPS Content** pomocí Visual Basic nebo C#.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře `ThisAddIn.vb` soubor nebo `ThisAddIn.cs` a přidá projekt do **Průzkumník řešení**.

## <a name="add-a-web-service"></a>Přidat webovou službu
 Pro tento návod použijte webovou službu s názvem MTPS Content Service. Tato webová služba vrátí informace ze zadaného článku na webu MSDN ve formě řetězce XML nebo prostého textu. V pozdějším kroku se dozvíte, jak zobrazit vrácené informace v ovládacím prvku obsahu.

### <a name="to-add-the-mtps-content-service-to-the-project"></a>Přidání služby obsahu MTPS do projektu

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

2. V **Průvodci konfigurací zdroje dat** klikněte na možnost **Služba** a poté klikněte na tlačítko **Další**.

3. Do pole **adresa** zadejte následující adresu URL:

   `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

4. Klikněte na **Přejít**.

5. Do pole **obor názvů** zadejte **contentservice** a klikněte na **OK**.

6. V dialogovém okně **Průvodce přidáním odkazu** klikněte na tlačítko **Dokončit**.

## <a name="add-a-content-control-and-bind-to-data-at-run-time"></a>Přidání ovládacího prvku obsahu a vazba na data v době běhu
 V projektech doplňku VSTO přidáte a svážete ovládací prvky v době běhu. Pro tento návod nakonfigurujte ovládací prvek obsahu, aby načetl data z webové služby, když uživatel klikne dovnitř ovládacího prvku.

### <a name="to-add-a-content-control-and-bind-to-data"></a>Přidání ovládacího prvku obsahu a vytvoření vazby na data

1. Ve `ThisAddIn` třídě deklarujte proměnné pro službu obsahu MTPS, ovládací prvek obsahu a datovou vazbu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet2":::

2. Do třídy přidejte následující metodu `ThisAddIn` . Tato metoda vytvoří ovládací prvek obsahu na začátku aktivního dokumentu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet4":::

3. Do třídy přidejte následující metodu `ThisAddIn` . Tato metoda inicializuje objekty potřebné k vytvoření a odeslání žádosti webové službě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet6":::

4. Vytvořte obslužnou rutinu události pro načtení dokumentu knihovny MSDN o ovládacích prvcích obsahu, když uživatel klikne dovnitř ovládacího prvku obsahu a sváže data s ovládacím prvkem Content.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet5":::

5. Zavolejte `AddRichTextControlAtRange` metody a `InitializeServiceObjects` z `ThisAddIn_Startup` metody. Pro programátory v jazyce C# přidejte obslužnou rutinu události.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb" id="Snippet3":::

## <a name="test-the-add-in"></a>Test doplňku
 Po otevření aplikace Word <xref:Microsoft.Office.Tools.Word.RichTextContentControl> se zobrazí ovládací prvek. Text v ovládacím prvku se změní po kliknutí dovnitř.

### <a name="to-test-the-vsto-add-in"></a>Test doplňku VSTO

1. Stiskněte klávesu **F5**.

2. Klikněte do ovládacího prvku Content (obsah).

     Informace se stáhnou ze služby obsahu MTPS a zobrazují se v rámci ovládacího prvku obsahu.

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
