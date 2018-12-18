---
title: Události v projektech pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85cbee61cde596831d06aa83af326cc0a0534f0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949679"
---
# <a name="events-in-office-projects"></a>Události v projektech pro systém Office
  Každá šablona projektu Office automaticky vygeneruje několik obslužných rutin událostí. Obslužné rutiny událostí pro přizpůsobení na úrovni dokumentu se mírně liší od obslužné rutiny událostí pro doplňky VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="document-level-projects"></a>Projekty na úrovni dokumentu  
 Visual Studio poskytuje generovaný kód za novou nebo existující dokumenty nebo listů v přizpůsobeních na úrovni dokumentu. Tento kód vyvolává dvě různé události: **spuštění** a **vypnutí**.  
  
### <a name="startup-event"></a>událost spuštění  
 **Spuštění** událost se vyvolá, pro každou z položek hostitele (dokumentu, sešitu nebo listu) po spuštění dokumentu a veškerého inicializačního kódu v sestavení byl spuštěn. Je to poslední věcí, kterou pro spuštění v konstruktoru třídy, na kterém běží váš kód v. Další informace o hostitelských položkách naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
 Při vytváření projektu úrovni dokumentu, sada Visual Studio vytvoří obslužné rutiny událostí pro **spuštění** události v souborech generovaného kódu:  
  
-   Pro projekty Microsoft Office Word je obslužná rutina události s názvem `ThisDocument_Startup`.  
  
-   Obslužné rutiny událostí pro projekty Microsoft Office Excel, mají následující názvy:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### <a name="shutdown-event"></a>událost vypnutí  
 **Vypnutí** událost se vyvolá pro každou z položek hostitele (dokumentu nebo listu), když je doména aplikace, který váš kód je načten v Chystáte se odinstalovat. Je to poslední věcí, kterou má být volána ve třídě, jako je uvolněn.  
  
 Při vytváření projektu úrovni dokumentu, sada Visual Studio vytvoří obslužné rutiny událostí pro **vypnutí** události v souborech generovaného kódu:  
  
-   Pro projekty Microsoft Office Word je obslužná rutina události s názvem `ThisDocument_Shutdown`.  
  
-   Obslužné rutiny událostí pro projekty Microsoft Office Excel, mají následující názvy:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Neodebírejte ovládacích prvků při prostřednictvím kódu programu **vypnutí** obslužná rutina události dokumentu. Prvky uživatelského rozhraní dokumentu již nejsou k dispozici při **vypnutí** dojde k události. Pokud chcete odebrání ovládacích prvků, než aplikaci zavře, přidejte svůj kód na jinou obslužnou rutinu události, jako například **BeforeClose** nebo **BeforeSave**.  
  
### <a name="event-handler-method-declarations"></a>Deklarace metody obslužné rutiny událostí  
 Všechny deklarace metody obslužné rutiny události má stejné argumenty předány: *odesílatele* a *e*. V aplikaci Excel *odesílatele* argument odkazuje na listu, jako například `Sheet1` nebo `Sheet2`; v aplikaci Word *odesílatele* argument odkazuje na dokument. *e* argument odkazuje na standardní argumenty události, které se nepoužívají v tomto případě.  
  
 Následující příklad kódu ukazuje výchozích obslužných rutin událostí v projektech na úrovni dokumentu pro aplikaci Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 Následující příklad kódu ukazuje výchozích obslužných rutin událostí v projektech na úrovni dokumentu pro Excel.  
  
> [!NOTE]  
>  Následující příklad kódu ukazuje obslužné rutiny událostí v `Sheet1` třídy. Názvy obslužných rutin událostí v jiných třídách položku hostitele odpovídat názvu třídy. Například v `Sheet2` třídy, **spuštění** má název obslužné rutiny události `Sheet2_Startup`. V `ThisWorkbook` třídy, **spuštění** má název obslužné rutiny události `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### <a name="order-of-events-in-document-level-excel-projects"></a>Řazení událostí v projektech aplikace Excel úrovni dokumentu  
 **Spuštění** jsou volány obslužné rutiny události v projektech aplikace Excel v tomto pořadí:  
  
1. `ThisWorkbook_Startup`.  
  
2. `Sheet1_Startup`.  
  
3. `Sheet2_Startup`.  
  
4. `Sheet3_Startup`.  
  
5. Jiné listy v pořadí.  
  
   **Vypnutí** jsou volány obslužné rutiny událostí v sešitu řešení v tomto pořadí:  
  
6. `ThisWorkbook_Shutdown`.  
  
7. `Sheet1_Shutdown`.  
  
8. `Sheet2_Shutdown`.  
  
9. `Sheet3_Shutdown`.  
  
10. Jiné listy v pořadí.  
  
    Pořadí je určeno při kompilaci projektu. Pokud uživatel změní uspořádání listy v době běhu, nezmění pořadí, že události jsou vyvolány při příštím otevření nebo zavření sešitu.  
  
## <a name="vsto-add-in-projects"></a>Projekty doplňků VSTO  
 Visual Studio poskytuje generovaného kódu v doplňcích VSTO. Tento kód vyvolává dvě různé události: <xref:Microsoft.Office.Tools.AddInBase.Startup> a <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### <a name="startup-event"></a>událost spuštění  
 <xref:Microsoft.Office.Tools.AddIn.Startup> Událost se vyvolá po načtení doplňku VSTO a veškerého inicializačního kódu v sestavení byl spuštěn. Tato událost se zpracovává souborem `ThisAddIn_Startup` metody v souboru generovaného kódu.  
  
 Kód v `ThisAddIn_Startup` obslužná rutina události je první uživatelský kód pro spuštění, pokud váš doplněk VSTO přepsání <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. V takovém případě `ThisAddIn_Startup` obslužná rutina události je volána po <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Nepřidávejte kód `ThisAdd-In_Startup` obslužná rutina události, pokud kód vyžaduje dokument otevřen. Místo toho přidejte tento kód na událost, která aplikace Office se vyvolá, když uživatel vytvoří nebo otevře dokument. Další informace najdete v tématu [přístup k dokumentu, při spuštění aplikace Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Další informace o spouštění doplňků VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="shutdown-event"></a>událost vypnutí  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Událost se vyvolá, když je doména aplikace, který váš kód je načten v zařízení bude uvolněna. Tato událost se zpracovává souborem `ThisAddIn_Shutdown` metody v souboru generovaného kódu. Tato obslužná rutina události je poslední uživatelský kód spustit, když doplňku VSTO je uvolněna.  
  
#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Událost vypnutí v doplňcích VSTO pro Outlook  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Událost se vyvolá pouze v případě, že uživatel zakáže doplňku VSTO pomocí dialogového okna Doplňky modelu COM v Outlooku. Není vyvolána při ukončení aplikace Outlook. Pokud máte kód, který musí být spuštěn při ukončení aplikace Outlook, zpracujte jeden z následujících událostí:  
  
-   <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> Událost <xref:Microsoft.Office.Interop.Outlook.Application> objektu.  
  
-   <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> Událost <xref:Microsoft.Office.Interop.Outlook.Explorer> objektu.  
  
> [!NOTE]  
>  Můžete vynutit, Outlook, aby se vyvolala <xref:Microsoft.Office.Tools.AddInBase.Shutdown> událostí při jejím ukončení úpravou registru. Nicméně pokud toto nastavení se vrátí správcem, libovolný kód přidat do `ThisAddIn_Shutdown` metoda už nespouští při ukončení aplikace Outlook. Další informace najdete v tématu [vypnutí změní pro aplikaci Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## <a name="see-also"></a>Viz také:  
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  