---
title: 'Postupy: použití návrháře schémat XML s literály XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656295"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Postupy: použití návrháře schémat XML s literály XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak zobrazit schéma přidružené k literálu XML v projektu Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Vytvoření nového projektu konzolové aplikace Visual Basic

1. Spusťte Visual Studio 2010.

2. V nabídce **soubor** vyberte **Nový**a pak vyberte **projekt**. Zobrazí se dialogové okno **Nový projekt** . Pro **typy projektů**vyberte **jiné jazyky** a pak vyberte **Visual Basic**. V případě **šablon**vyberte Konzolová aplikace. Pak zadejte `XMLLiterals` do pole **název** a do umístění projektu v poli **umístění** . Klikněte na tlačítko **OK**.

     Vytvoří se nový poject. Projekt XMLLiterals obsahuje jeden Visual Basic zdrojový soubor Module1. vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Přidání existujícího souboru XSD do projektu

1. Otevřete v programu Poznámkový blok nový textový soubor. Zkopírujte ukázkový kód schématu XML ze [schématu nákupních objednávek](../xml-tools/sample-xsd-file-simple-schema.md) a vložte ho do souboru.

2. Uložte soubor do nějakého umístění s názvem PurchaseOrderSchema. xsd.

3. V Průzkumník řešení klikněte pravým tlačítkem myši na název projektu, vyberte možnost **Přidat**a vyberte možnost **existující položka...** . Zobrazí se dialogové okno **položka AddExisting** . Přejděte k souboru PurchaseOrderSchema. xsd, vyberte ho a pak klikněte na **Přidat**.

     Projekt XMLLiterals nyní obsahuje dva soubory: Module1. vb a PurchaseOrderSchema. xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Přidání kódu Visual Basic s literálem XML na základě souboru XSD zahrnutého v projektu

1. Nahraďte kód v souboru Module1. vb následujícím kódem:

    ```
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

    Module Module1
        Sub Main()

            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                                 <ns:ShipTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:ShipTo>
                                 <ns:BillTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:BillTo>
                             </ns:PurchaseOrder>

        End Sub
    End Module
    ```

2. Klikněte pravým tlačítkem na libovolný uzel XML v literálu XML nebo importujte obor názvů XML a **v Průzkumníku schémat vyberte Zobrazit**.

     Průzkumník schémat XML se zobrazí vedle sebe s Visual Basic souborem, který má literál XML assotiated se sadou schémat XML.
