---
title: Události v projektech pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8e8aca881ba25df134c675ac504ea0794c4b051
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986120"
---
# <a name="events-in-office-projects"></a>Události v projektech pro systém Office
  Každá šablona projektu Office automaticky generuje několik obslužných rutin událostí. Obslužné rutiny událostí pro přizpůsobení na úrovni dokumentu se mírně liší od obslužných rutin událostí pro doplňky VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projekty na úrovni dokumentu
 Visual Studio poskytuje generovaný kód za novými nebo existujícími dokumenty nebo listy v přizpůsobení na úrovni dokumentu. Tento kód vyvolává dvě různé události: **spuštění** a **vypnutí**.

### <a name="startup-event"></a>událost spuštění
 Událost **po spuštění** je vyvolána pro každou položku hostitele (dokument, sešit nebo list) po spuštění dokumentu a veškerý inicializační kód v sestavení byl spuštěn. Je to poslední věc, která se má spustit v konstruktoru třídy, ve které je váš kód spuštěný. Další informace o položkách hostitelů naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

 Když vytváříte projekt na úrovni dokumentu, Visual Studio vytvoří obslužné rutiny události pro událost **spuštění** v generovaných souborech kódu:

- V případě systém Microsoft Officech projektů aplikace Word je obslužná rutina události pojmenována `ThisDocument_Startup` .

- Pro systém Microsoft Office excelové projekty mají obslužné rutiny událostí následující názvy:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>událost vypnutí
 Událost **vypnutí** je vyvolána pro každou položku hostitele (dokument nebo list), když je doména aplikace, v níž je načten váš kód, chystá uvolnění. Je to poslední věc, která se má volat ve třídě při uvolnění.

 Když vytvoříte projekt na úrovni dokumentu, Visual Studio vytvoří obslužné rutiny události pro událost **vypnutí** ve vygenerovaných souborech kódu:

- V případě systém Microsoft Officech projektů aplikace Word je obslužná rutina události pojmenována `ThisDocument_Shutdown` .

- Pro systém Microsoft Office excelové projekty mají obslužné rutiny událostí následující názvy:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Neodstraňujte programově ovládací prvky během obslužné rutiny události **vypnutí** v dokumentu. Prvky uživatelského rozhraní dokumentu již nejsou k dispozici, pokud dojde k události **vypnutí** . Chcete-li odebrat ovládací prvky před zavřením aplikace, přidejte svůj kód do jiné obslužné rutiny události, jako je například **BeforeClose** nebo **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Deklarace metod obslužné rutiny událostí
 Každé deklaraci metody obslužné rutiny události jsou předány stejné argumenty: *sender* a *e*. V aplikaci Excel odkazuje argument *odesílatele* na list, jako je například `Sheet1` nebo `Sheet2` ; ve slově argument *Odesílatel* odkazuje na dokument. Argument *e* odkazuje na standardní argumenty události, které se v tomto případě nepoužívají.

 Následující příklad kódu ukazuje výchozí obslužné rutiny událostí v projektech na úrovni dokumentu ve Wordu.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 Následující příklad kódu ukazuje výchozí obslužné rutiny událostí v projektech na úrovni dokumentu v aplikaci Excel.

> [!NOTE]
> Následující příklad kódu ukazuje obslužné rutiny událostí ve `Sheet1` třídě. Názvy obslužných rutin událostí v jiných třídách hostitelů odpovídají názvu třídy. Například ve `Sheet2` třídě je obslužná rutina události **spuštění** pojmenována `Sheet2_Startup` . Ve `ThisWorkbook` třídě je obslužná rutina události **spuštění** pojmenována `ThisWorkbook_Startup` .

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Pořadí událostí v projektech Excelu na úrovni dokumentu
 Obslužné rutiny událostí **spuštění** v projektech aplikace Excel jsou volány v tomto pořadí:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Další listy v daném pořadí.

   Obslužné rutiny události **vypnutí** v řešení sešitu jsou volány v tomto pořadí:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Další listy v daném pořadí.

    Pořadí je určeno při kompilování projektu. Pokud uživatel změní uspořádání listů za běhu, nezmění pořadí, v jakém jsou události vyvolány při příštím otevření nebo zavření sešitu.

## <a name="vsto-add-in-projects"></a>Projekty doplňku VSTO
 Visual Studio poskytuje generovaný kód v doplňcích VSTO. Tento kód vyvolává dvě různé události: <xref:Microsoft.Office.Tools.AddInBase.Startup> a <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>událost spuštění
 <xref:Microsoft.Office.Tools.AddIn.Startup>Událost je vyvolána po načtení doplňku VSTO a spuštění veškerého inicializačního kódu v sestavení. Tato událost je zpracována `ThisAddIn_Startup` metodou ve vygenerovaném souboru kódu.

 Kód v `ThisAddIn_Startup` obslužné rutině události je prvním uživatelským kódem, který se má spustit, pokud doplněk VSTO nepřepisuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu. V tomto případě `ThisAddIn_Startup` je obslužná rutina události volána po <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> .

 Nepřidávejte kód do `ThisAdd-In_Startup` obslužné rutiny události, pokud kód vyžaduje otevření dokumentu. Místo toho přidejte tento kód do události, kterou aplikace Office vyvolá, když uživatel vytvoří nebo otevře dokument. Další informace najdete v tématu [přístup k dokumentu při spuštění aplikace Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Další informace o úvodní sekvenci doplňků VSTO najdete v tématu [architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>událost vypnutí
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown>Událost je vyvolána, když je doména aplikace, v níž je načten váš kód, uvolněna. Tato událost je zpracována `ThisAddIn_Shutdown` metodou ve vygenerovaném souboru kódu. Tato obslužná rutina události je poslední uživatelský kód, který se spustí při uvolnění doplňku VSTO.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Událost vypnutí v doplňkových doplňcích pro Outlook VSTO
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown>Událost se vyvolá jenom v případě, že uživatel zakáže doplněk VSTO pomocí dialogového okna doplňky modelu COM v aplikaci Outlook. Není vyvolána, když je aplikace Outlook ukončena. Pokud máte kód, který musí být spuštěn při ukončení aplikace Outlook, zpracujte jednu z následujících událostí:

- <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit>Událost <xref:Microsoft.Office.Interop.Outlook.Application> objektu.

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>Událost <xref:Microsoft.Office.Interop.Outlook.Explorer> objektu.

> [!NOTE]
> Můžete vynutit, aby aplikace Outlook vyvolala <xref:Microsoft.Office.Tools.AddInBase.Shutdown> událost při ukončení úpravou registru. Pokud však správce toto nastavení vrátí, veškerý kód, který přidáte do `ThisAddIn_Shutdown` metody, již nebude při ukončení aplikace Outlook spuštěn. Další informace najdete v tématu [vypnutí změn pro Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Viz také
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
