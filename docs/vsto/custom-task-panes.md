---
title: Vlastní podokna úloh
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4e8384bc86bf59216c353b0f4610d3863445781
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889760"
---
# <a name="custom-task-panes"></a>Vlastní podokna úloh
  Panely uživatelského rozhraní, které jsou obvykle ukotven k okraji okna v aplikaci Microsoft Office jsou podokna úloh. Vlastní podokna úloh poskytují způsob, jak vytvořit vlastní podokna úloh a poskytuje uživatelům známou rozhraní pro přístup k funkcím vašeho řešení. Rozhraní může například obsahovat ovládací prvky, na kterých běží kód pro úpravy dokumentů a zobrazení dat ze zdroje dat.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  V podokně Akce se liší vlastního podokna úloh. V podokně Akce je součástí přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Word a Microsoft Office Excel. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
## <a name="benefits-of-custom-task-panes"></a>Výhody vlastních podoken úloh  
 Vlastní podokna úloh umožňuje integrovat do známé uživatelské rozhraní vaší funkce. Pomocí nástrojů sady Visual Studio můžete rychle vytvořit vlastního podokna úloh.  
  
### <a name="familiar-user-interface"></a>Známé uživatelské rozhraní  
 Uživatelé aplikací v systému Microsoft Office jsou už mají zkušenosti s pomocí podokna úloh, jako **styly a formátování** podokna úloh v aplikaci Word. Vlastní podokna úloh se chovají jako jiná podokna úloh v systému Microsoft Office. Uživatelům můžete ukotvit vlastní podokna úloh do jiné straně okna aplikace nebo vlastní podokna úloh, můžete přetáhnout do libovolného umístění v okně. Můžete vytvořit doplňku VSTO zobrazující více vlastních podoken úloh ve stejnou dobu, a uživatelé můžou řídit jednotlivě každý podokna úloh.  
  
### <a name="windows-forms-support"></a>Podpora Windows forms  
 Uživatelské rozhraní z vlastního podokna úloh, kterou vytvoříte pomocí nástroje pro vývoj pro Office v sadě Visual Studio je založená na ovládacích prvcích Windows Forms. Známé Návrhář formulářů Windows můžete použít k návrhu uživatelského rozhraní pro vlastního podokna úloh. Podpora vazeb dat můžete použít také v modelu Windows Forms k vytvoření vazby zdroje dat s ovládacími prvky v podokně úloh.  
  
## <a name="create-a-custom-task-pane"></a>Vytvoření vlastního podokna úloh  
 Můžete vytvořit základní vlastního podokna úloh ve dvou krocích:  
  
1. Přidáním ovládacích prvků Windows Forms k vytvoření uživatelského rozhraní pro vlastního podokna úloh <xref:System.Windows.Forms.UserControl> objektu.  
  
2. Vytvoření instance vlastního podokna úloh předáním uživatelský ovládací prvek <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> objektu v doplňku VSTO. Tato kolekce vrátí nový <xref:Microsoft.Office.Tools.CustomTaskPane> objekt, který můžete použít k úpravě vzhledu podokna úloh a reagovat na události uživatele.  
  
   Další informace najdete v tématu [postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 Všechny vlastní podokna úloh, které jsou vytvořeny pomocí nástroje pro vývoj pro Office v sadě Visual Studio obsahují <xref:System.Windows.Forms.UserControl> objektu. Tento uživatelský ovládací prvek poskytuje uživatelské rozhraní z vlastního podokna úloh. Můžete vytvořit uživatelský ovládací prvek v době návrhu nebo za běhu. Pokud vytvoříte uživatelský ovládací prvek v době návrhu, můžete použít Návrháře Windows Forms k vytvoření uživatelského rozhraní podokna úloh.  
  
### <a name="instantiate-the-custom-task-pane"></a>Vytvoření instance vlastního podokna úloh  
 Po vytvoření uživatelského ovládacího prvku, který obsahuje uživatelské rozhraní z vlastního podokna úloh, budete muset vytvořit instanci <xref:Microsoft.Office.Tools.CustomTaskPane>. K tomuto účelu předat uživatelského ovládacího prvku <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> v doplňku VSTO voláním jedné z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody. Tato kolekce je vystavena jako `CustomTaskPanes` pole `ThisAddIn` třídy. Následující příklad kódu je určený ke spuštění z `ThisAddIn` třídy.  
  
 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> Metody vracet novou <xref:Microsoft.Office.Tools.CustomTaskPane> objektu. Tento objekt slouží k úpravě vzhledu podokna úloh a reagovat na události uživatele.  
  
### <a name="control-the-task-pane-in-multiple-windows"></a>Ovládací prvek podokna úloh ve více oken  
 Vlastní podokna úloh jsou spojeny s oknem rámce dokumentu, který se uživateli zobrazí zobrazení dokumentu nebo položky. V podokně úloh je viditelná pouze v případě, že je přidružené okno viditelné.  
  
 Chcete-li zjistit, které v okně se zobrazí v podokně úloh, použijte odpovídající <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> přetížení metody, když vytvoříte v podokně úloh:  
  
- Chcete-li přidružit aktivní okno podokna úloh, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.  
  
- Chcete-li přidružit dokument, který je hostitelem určené okno podokna úloh, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.  
  
  Některé aplikace Office vyžadují explicitní pokyny, kdy se má vytvořit nebo zobrazit vašeho podokna úloh, když je otevřeno více než jedno okno. Díky tomu je potřeba zvážit, kde k vytvoření instance vlastního podokna úloh ve vašem kódu k zajištění, že se zobrazí v podokně úloh s odpovídající dokumenty či položky v aplikaci. Další informace najdete v tématu [Správa vlastních podoken úloh v aplikaci windows](#Managing).  
  
## <a name="access-the-application-from-the-task-pane"></a>Přístup k aplikaci z podokna úloh  
 Pokud chcete automatizovat aplikace z uživatelského ovládacího prvku, můžete přístup přímo objektový model s použitím `Globals.ThisAddIn.Application` ve vašem kódu. Statické `Globals` třídě poskytuje přístup k `ThisAddIn` objektu. `Application` Pole tohoto objektu je vstupním bodem do objektového modelu aplikace.  
  
 Další informace o `Application` pole `ThisAddIn` objektu, najdete v článku [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Názorný postup ukazuje, jak automatizovat aplikace z vlastního podokna úloh, naleznete v tématu [návod: Automatické aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Další informace o `Globals` najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="manage-the-user-interface-of-the-task-pane"></a>Správa uživatelského rozhraní aplikace podokna úloh  
 Po vytvoření podokna úloh, můžete použít vlastnosti a události <xref:Microsoft.Office.Tools.CustomTaskPane> objekt ovládací prvek uživatelského rozhraní aplikace podokna úloh a reagovat, když uživatel změní podokna úloh.  
  
### <a name="make-the-custom-task-pane-visible"></a>Zviditelnit vlastní podokna úloh  
 Ve výchozím nastavení není viditelný v podokně úloh. Ke zviditelnění podokna úloh, je nutné nastavit <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> vlastnost **true**.  
  
 Uživatele můžete kdykoli zavřít podokno úloh, kliknutím **zavřete** tlačítko (X) v horním rohu podokna úloh. Neexistuje však žádný způsob výchozí pro uživatele a znovu otevřete podokno úloh. Pokud uživatel zavře vlastního podokna úloh, tento uživatel nemůže zobrazit vlastního podokna úloh znovu pokud poskytují způsob, jak ji zobrazit.  
  
 Pokud vytvoříte vlastního podokna úloh v doplňku VSTO, měli byste také vytvořit prvek uživatelského rozhraní, jako je například tlačítko, které mohou uživatelé kliknout a zobrazit nebo skrýt vlastního podokna úloh. Pokud vytvoříte vlastního podokna úloh v aplikaci Microsoft Office, který podporuje přizpůsobení pásu karet, můžete přidat skupiny ovládacích prvků na pásu karet s tlačítkem, zobrazí nebo skryje vlastního podokna úloh. Názorný postup ukazuje, jak to provést, najdete v části [návod: synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
 Pokud vytvoříte vlastního podokna úloh v aplikaci Microsoft Office, která nepodporuje přizpůsobení pásu karet, můžete přidat <xref:Microsoft.Office.Core.CommandBarButton> , který zobrazí nebo skryje vlastního podokna úloh.  
  
### <a name="modify-the-appearance-of-the-task-pane"></a>Upravení vzhledu podokna úloh  
 Můžete řídit velikost a umístění z vlastního podokna úloh pomocí vlastnosti <xref:Microsoft.Office.Tools.CustomTaskPane> objektu. Můžete provádět mnoho dalších změn vzhledu vlastního podokna úloh s použitím vlastnosti <xref:System.Windows.Forms.UserControl> objekt, který je součástí vlastního podokna úloh. Například můžete zadat obrázek pozadí pro vlastního podokna úloh s použitím <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnosti uživatelského ovládacího prvku.  
  
 Následující tabulka uvádí změny, můžete provádět pomocí vlastního podokna úloh <xref:Microsoft.Office.Tools.CustomTaskPane> vlastnosti.  
  
|Úloha|Vlastnost|  
|----------|--------------|  
|Chcete-li změnit velikost podokna úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|  
|Chcete-li změnit umístění v podokně úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|  
|Skrýt podokno úloh nebo zprůhlední je|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|  
|Chcete-li uživateli zabránit ve změně umístění v podokně úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|  
  
### <a name="program-custom-task-pane-events"></a>Program vlastní úloha podokně události  
 Můžete chtít vaše doplňku VSTO reagovat, když uživatel změní vlastního podokna úloh. Pokud uživatel změní orientace v podokně ze svislé na vodorovnou, můžete chtít změnit umístění ovládacích prvků.  
  
 Následující tabulka uvádí události, které dokáže zpracovat reakce na změny, které uživatel provede vlastního podokna úloh.  
  
|Úloha|Událost|  
|----------|-----------|  
|Chcete-li reagovat, když uživatel změní umístění v podokně úloh.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|  
|Chcete-li reagovat, když uživatel skryje panel úkolů nebo stane viditelným.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|  
  
## <a name="clean-up-resources-used-by-the-task-pane"></a>Vyčistěte prostředky využívané třídou podokna úloh  
 Po vytvoření vlastního podokna úloh, <xref:Microsoft.Office.Tools.CustomTaskPane> objekt zůstane zachován v paměti, tak dlouho, dokud je spuštěna vaše doplňku VSTO. Objekt zůstane zachován v paměti, i když uživatel klikne **Zavřít** tlačítko (X) v horním rohu podokna úloh.  
  
 Pokud chcete vyčistit prostředky využívané třídou podokna úloh, zatímco doplňku VSTO stále běží, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> nebo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody. Tyto metody Odstraní zadaný <xref:Microsoft.Office.Tools.CustomTaskPane> objektu z `CustomTaskPanes` kolekce a jejich volání <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> metodu objektu.  
  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automaticky vyčistí prostředky využívané třídou vlastního podokna úloh, když doplňku VSTO je uvolněna. Nevolejte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> nebo <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody v `ThisAddIn_Shutdown` obslužná rutina události ve vašem projektu. Tyto metody vyvolá výjimku <xref:System.ObjectDisposedException>, protože [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vyčistí prostředky využívané třídou <xref:Microsoft.Office.Tools.CustomTaskPane> objektu před `ThisAddIn_Shutdown` je volána. Další informace o `ThisAddIn_Shutdown`, naleznete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md)  
  
##  <a name="Managing"></a> Správa vlastních podoken úloh ve více oken aplikace  
 Při vytváření vlastního podokna úloh v aplikaci, která používá více oken pro zobrazení dokumenty a další položky, budete muset udělat dodatečné kroky k zajištění, že v podokně úloh je viditelné, pokud uživatel očekává, že bude.  
  
 Vlastní podokna úloh ve všech aplikacích jsou spojeny s oknem rámce dokumentu, který se uživateli zobrazí zobrazení dokumentu nebo položky. V podokně úloh je viditelná pouze v případě, že je přidružené okno viditelné. Ale u některých aplikací není použití oken s rámečkem v dokumentu stejným způsobem.  
  
 Tyto skupiny aplikací mají vývoj pro různé požadavky:  
  
- [Aplikace Outlook](#Outlook)  
  
- [Word, aplikace InfoPath a PowerPoint](#WordAndInfoPath)  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak spravovat i podokna úloh v doplňcích VSTO pro Word?](http://go.microsoft.com/fwlink/?LinkId=136781).  
  
##  <a name="Outlook"></a> Aplikace Outlook  
 Při vytváření vlastního podokna úloh pro aplikaci Outlook souvisí s konkrétní okno Průzkumníka nebo inspektoru vlastního podokna úloh. Průzkumníci jsou windows, které zobrazují obsah složky a kontroly jsou windows, které zobrazí položky jako je například e-mailovou zprávu nebo úkol.  
  
 Pokud chcete zobrazit vlastního podokna úloh s více Průzkumníka nebo kontrola systému windows, musíte vytvořit novou instanci třídy vlastního podokna úloh po otevření Průzkumníka nebo inspektoru okno. K tomuto účelu zpracovat událost, která se vyvolá, když se vytvoří oknem Průzkumníka nebo Inspector a pak vytvořte v podokně úloh v obslužné rutině události. Můžete také zpracovávat Explorer a kontrola události ke skrytí nebo zobrazení podokna úloh v závislosti na tom, které okno je viditelný.  
  
 Chcete-li přidružit konkrétní Průzkumníka nebo inspektoru podokna úloh, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodu pro vytvoření podokna úloh a předat <xref:Microsoft.Office.Interop.Outlook.Explorer> nebo <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu *okno* parametr. Další informace o vytváření vlastních podoken úloh najdete v tématu [přehled podokna úloh Vlastní](../vsto/custom-task-panes.md).  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>  
  
  Pokud chcete monitorovat stav inspektoru windows, mohou zpracovávat následující události související s inspektor:  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>  
  
- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>  
  
### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zabránit více instancí vlastního podokna úloh v aplikaci Outlook  
 Abyste zabránili zobrazování více instancí vlastního podokna úloh Outlook windows, explicitně odebrat vlastního podokna úloh z `CustomTaskPanes` kolekce `ThisAddIn` třídy při zavření časového intervalu pro každý. Volání <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metoda ve událost, která je vyvolána při zavření okna, jako například <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> nebo <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.  
  
 Pokud je explicitně neodebírejte vlastního podokna úloh, okna aplikace Outlook se může zobrazit více instancí vlastního podokna úloh. Outlook někdy recykluje windows a windows recyklován uchovávat odkazy na všechny vlastní podokna úloh, které byly připojeny k nim.  
  
##  <a name="WordAndInfoPath"></a> Word, aplikace InfoPath a PowerPoint  
 Word, aplikace InfoPath a PowerPoint zobrazit jednotlivé dokumenty v okně s rámečkem jiného dokumentu. Při vytváření vlastního podokna úloh pro tyto aplikace vlastního podokna úloh souvisí pouze s určitým dokumentem. Pokud uživatel otevře jiný dokument, vlastního podokna úloh je skrytý, dokud starší dokumentu opět viditelný.  
  
 Pokud chcete zobrazit vlastního podokna úloh s více dokumenty, vytvořte novou instanci třídy vlastního podokna úloh, když uživatel vytvoří nový dokument nebo otevře existující dokument. K tomuto účelu zpracování událostí, které jsou vyvolány při vytvoření nebo otevření dokumentu a pak vytvořte v podokně úloh v obslužných rutinách událostí. Můžete také zpracovávat události dokumentu ke skrytí nebo zobrazení podokna úloh podle toho, který dokument je zobrazen.  
  
 Chcete-li přidružit podokna úloh s určitým dokumentem okna, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodu pro vytvoření podokna úloh a předat <xref:Microsoft.Office.Interop.Word.Window> (pro aplikaci Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (pro aplikaci InfoPath), nebo <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (pro PowerPoint) k *okno*parametru.  
  
### <a name="word-events"></a>Události aplikace Word  
 Pokud chcete monitorovat stav okna dokumentu ve Wordu, mohou zpracovávat následující události:  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>  
  
### <a name="infopath-events"></a>Události aplikace InfoPath  
 Pokud chcete monitorovat stav okna dokumentu v aplikaci InfoPath, mohou zpracovávat následující události:  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>  
  
-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>  
  
### <a name="powerpoint-events"></a>Události aplikace PowerPoint  
 Pokud chcete monitorovat stav okna dokumentu v aplikaci PowerPoint, mohou zpracovávat následující události:  
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14)) 
  
-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Návod: Automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Návod: Synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Návod: Zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
