---
title: 'Postupy: používání návrháře schémat XML s literály XML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 592886a1cfe9d0ffc9c7165729cede3340bc65c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218364"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Postupy: používání návrháře schémat XML s literály XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma popisuje postup zobrazení schématu přidružené k literálu v projektu jazyka Visual Basic XML.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Chcete-li vytvořit nový projekt konzolové aplikace v jazyce Visual Basic  
  
1.  Spusťte sadu Visual Studio 2010.  
  
2.  Z **souboru** nabídce vyberte možnost **nový**a pak vyberte **projektu**. **Nový projekt** zobrazí se dialogové okno. Pro **typy projektů**vyberte **jiné jazyky,** a pak vyberte **jazyka Visual Basic**. Pro **šablony**, vyberte konzolové aplikace. Zadejte `XMLLiterals` v **název** pole a umístění projektu v **umístění** pole. Klikněte na tlačítko **OK**.  
  
     Vytvoření nového projektu. Projekt XMLLiterals obsahuje jeden zdrojový soubor Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Chcete-li přidat existující soubor XSD do projektu  
  
1.  Otevřete nový textový soubor v Notepad.Copy ukázkového kódu schématu XML z [nákupní pořadí schématu](../xml-tools/sample-xsd-file-simple-schema.md) a vložte ji do souboru.  
  
2.  Uložte soubor v některém umístění s názvem PurchaseOrderSchema.xsd.  
  
3.  V Průzkumníku řešení klikněte pravým tlačítkem na název projektu, vyberte **přidat**a pak vyberte **existující položku...** . **AddExisting položky** zobrazí se dialogové okno. Přejděte k souboru PurchaseOrderSchema.xsd, vyberte ji a pak klikněte na tlačítko **přidat**.  
  
     Projekt XMLLiterals teď obsahuje dva soubory: Module1.vb a PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Přidání kódu jazyka Visual Basic s XML literál, na základě souboru XSD, které jsou součástí projektu  
  
1.  Kód v souboru Module1.vb nahraďte následujícím kódem:  
  
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
  
2.  Klikněte pravým tlačítkem na libovolný uzel XML literál XML nebo import oboru názvů XML a vyberte **zobrazit v Průzkumníkovi schémat**.  
  
     Průzkumníka schémat XML se zobrazí vedle souboru jazyka Visual Basic, který má XML literál assotiated se schématem XML nastaven.



