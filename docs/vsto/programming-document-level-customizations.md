---
title: Programování přizpůsobení na úrovni dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d9c7fa658c24caa65b3c955002ffeeaff6573c55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812228"
---
# <a name="program-document-level-customizations"></a>Programování přizpůsobení na úrovni dokumentu
  Když rozšíříte pomocí přizpůsobení úrovni dokumentu aplikace Microsoft Office Word nebo Microsoft Office Excel, můžete provádět následující úlohy:  
  
- Pomocí jeho objektového modelu automatizace aplikace.  
  
- Přidání ovládacích prvků na plochu dokumentu.  
  
- Volání jazyka Visual Basic pro kód Applications (VBA) v dokumentu z vlastního nastavení sestavení.  
  
- Volání kódu v sestavení přizpůsobení z jazyka VBA.  
  
- Spravovat některé aspekty dokumentu, když je na serveru, který nemá nainstalovanou sadu Microsoft Office.  
  
- Přizpůsobení uživatelského rozhraní (UI) aplikace.  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  Některé aspekty psaní kódu v projektech na úrovni dokumentu se liší od ostatních typů projektů v sadě Visual Studio. Mnohé z těchto rozdílů jsou způsobeny tím, jak Office objektové modely jsou přístupné pro spravovaný kód. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
  Obecné informace o přizpůsobení na úrovni dokumentu a jiné druhy řešení můžete vytvořit pomocí nástroje pro vývoj pro Office v sadě Visual Studio najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-generated-classes-in-document-level-projects"></a>Použít vygenerovaných tříd v projektech na úrovni dokumentu  
 Při vytváření projektu úrovni dokumentu, Visual Studio automaticky vygeneruje třídu v projektu, který vám pomůže začít s psaním kódu. Visual Studio generuje různých tříd pro aplikace Word a Excel:  
  
- Na projekty na úrovni dokumentu pro Word, třída nazývá `ThisDocument` ve výchozím nastavení.  
  
- Projekty na úrovni dokumentu pro Excel mít více generované třídy: jeden pro sešit samotný a jeden pro každý list nástroje. Ve výchozím nastavení tyto třídy mají následující názvy:  
  
  -   `ThisWorkbook`  
  
  -   `Sheet1`  
  
  -   `Sheet2`  
  
  -   `Sheet3`  
  
  Generované třídy obsahuje obslužné rutiny událostí, které jsou volány, když je dokument otevřel nebo zavřel. Ke spuštění kódu při otevření dokumentu, přidejte kód pro `Startup` obslužné rutiny události. Chcete-li spustit kód bezprostředně před zavřením dokumentu, přidejte kód pro `Shutdown` obslužné rutiny události. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="understand-the-design-of-the-generated-classes"></a>Pochopení návrhu vygenerovaných tříd  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], napíše hostitelský objekt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jsou rozhraní, takže generované třídy nemůže odvozovat jejich provádění z nich. Místo toho generované třídy odvozeny většinu jejich členů z následujících základních tříd:  
  
- `ThisDocument`: je odvozena z <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
- `ThisWorkbook`: je odvozena z <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
- `Sheet` *n*: odvozuje od <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
  Tyto základní třídy přesměrovat na interní implementace odpovídající rozhraní položku hostitele v všechna volání do svých členů [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Například, pokud zavoláte <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> metodu `ThisDocument` třídy, <xref:Microsoft.Office.Tools.Word.DocumentBase> třídy přesměruje volání na interní implementaci <xref:Microsoft.Office.Tools.Word.Document> rozhraní v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="access-the-object-model-of-the-host-application"></a>Přístup k modelu objektu hostitelské aplikace  
 Pro přístup k modelu objektu hostitelské aplikace, použijte členy generované třídy ve vašem projektu. Každá z těchto tříd odpovídá objektu v objektovém modelu aplikace Excel nebo Word a obsahují většinu stejné vlastnosti, metody a události. Například `ThisDocument` třídy v projektu úrovni dokumentu pro Word poskytuje většinu stejné členy jako <xref:Microsoft.Office.Interop.Word.Document> objektu v objektovém modelu aplikace Word.  
  
 Následující příklad kódu ukazuje, jak používat objektovému modelu Wordu k uložení dokumentu, který je součástí přizpůsobení úrovni dokumentu pro aplikaci Word. Tento příklad je určen ke spuštění z `ThisDocument` třídy.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Chcete-li to samé udělá z mimo `ThisDocument` třídy, použijte `Globals` objektu pro přístup k `ThisDocument` třídy. Například můžete přidat tento kód do souboru kódu podokna akce Pokud chcete zahrnout **Uložit** tlačítko v podokně Akce uživatelského rozhraní.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Protože `ThisDocument` třída získá většina jejích členů z <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt, `Save` metodu, která je volána v tento kód je ve skutečnosti <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metodu <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt. Tato metoda odpovídá <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> objektu v objektovém modelu aplikace Word.  
  
 Další informace o používání modely objektů aplikace Word a Excel najdete v tématu [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md) a [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
 Další informace o `Globals` objektu, najdete v článku [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="add-controls-to-documents"></a>Přidání ovládacích prvků do dokumentů  
 Přizpůsobení uživatelského rozhraní dokumentu, můžete přidat ovládací prvky Windows Forms nebo *hostování ovládacích prvků* na plochu dokumentu. Díky kombinaci různých sad ovládací prvky a psaní kódu, že můžete svázat ovládací prvky k datům, shromažďování informací od uživatele a reagovat na akce uživatele.  
  
 Hostitelské ovládací prvky jsou třídy, které rozšiřují některé objekty v objektovém modelu aplikace Word a Excel. Například <xref:Microsoft.Office.Tools.Excel.ListObject> hostitelského ovládacího prvku poskytuje všechny funkce <xref:Microsoft.Office.Interop.Excel.ListObject> v aplikaci Excel. Ale <xref:Microsoft.Office.Tools.Excel.ListObject> hostitelský ovládací prvek má také další události a možnosti vázání dat.  
  
 Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládacích prvků na dokumenty Office – přehled Windows forms](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="combine-vba-and-document-level-customizations"></a>Kombinování přizpůsobení na úrovni dokumentu a VBA  
 Můžete použít kód VBA v dokumentu, který je součástí přizpůsobení na úrovni dokumentu. Můžete volat kód VBA v dokumentu z vlastního nastavení sestavení, a můžete taky nakonfigurovat projekt tak, aby povolit kód VBA v dokumentu k volání kódu v sestavení přizpůsobení.  
  
 Další informace najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="manage-documents-on-a-server"></a>Správa dokumentů na serveru  
 Spravujete několik různých aspektů přizpůsobení na úrovni dokumentu na serveru, který nemá žádné aplikace Microsoft Office Word nebo Microsoft Office Excel nainstalována. Můžete třeba přístup a upravovat data v mezipaměti dat dokumentu. Můžete také spravovat vlastní nastavení sestavení, který je přidružený dokument. Například můžete programově odebrat sestavení z dokumentu tak, aby dokument již nebude spustí váš kód nebo sestavení můžete programově připojit k dokumentu.  
  
 Další informace najdete v tématu [spravovat dokumenty na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Přizpůsobení uživatelského rozhraní aplikace Microsoft Office  
 S použitím přizpůsobení úrovni dokumentu, můžete přizpůsobit uživatelské rozhraní aplikace Word a Excel následujícími způsoby:  
  
- Přidáte hostitelské ovládací prvky nebo ovládacích prvků Windows Forms na plochu dokumentu.  
  
   Další informace najdete v tématu [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md), [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md), a [ovládací prvky Windows Forms v přehledu dokumenty Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
- Přidání podokna akcí do dokumentů.  
  
   Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
- Přidáte vlastní karty na pás karet.  
  
   Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
- Přidejte vlastní skupiny do předdefinované karty na pásu karet.  
  
   Další informace najdete v tématu [postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
  Další informace o přizpůsobení uživatelského rozhraní systému Microsoft Office aplikací, najdete v části [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Získat rozšířené objekty z nativních objektů sady Office v přizpůsobeních na úrovni dokumentu  
 Mnoho obslužné rutiny událostí pro události Office zobrazí nativní objekt Office, která reprezentuje sešit, listu nebo dokument, který vyvolal událost. V některých případech můžete chtít spouštět nějaký kód jenom v případě, že sešit nebo ve vašem vlastním přizpůsobení úrovni dokumentu dokument vyvolala událost. Například v přizpůsobení na úrovni dokumentu pro Excel, můžete chtít spouštět nějaký kód, když uživatel aktivuje jeden z listů v sešitu vlastní, ale ne v případě, že uživatel aktivuje na listu v jiných sešitu, který je otevřený ve stejnou dobu.  
  
 Až budete mít nativní objekt Office, můžete zkontrolovat, jestli tento objekt se prodloužila do *hostitelský objekt* nebo *hostování ovládacího prvku* v přizpůsobení na úrovni dokumentu. Hostitelských položek a hostitelských ovládacích prvků jsou typy poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] přidá funkce pro objekty, které nativně existovat v aplikaci Word nebo Excel objektové modely (volá *nativních objektů Office*). Dále souhrnně nazývané hostitelských položek a hostitelských ovládacích prvků se také označují jako *rozšířených objektů*. Další informace o hostitelských položek a hostitelských ovládacích prvků naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Porozumění metodám GetVstoObject a HasVstoObject  
 Chcete-li otestovat nativní objekt Office, použijte `HasVstoObject` a `GetVstoObject` metody ve vašem projektu:  
  
- Použití `HasVstoObject` metody, pokud chcete zjistit, zda má nativní objekt Office rozšířeného objektu ve vašem vlastním přizpůsobení. Tato metoda vrátí **true** Pokud má objekt rozšířené nativní objekt Office a **false** jinak.  
  
- Použití `GetVstoObject` metody, pokud chcete získat rozšířeného objektu pro objekt nativní Office. Tato metoda vrátí hodnotu <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, nebo <xref:Microsoft.Office.Tools.Word.Document> objektu, pokud se zadaný objekt nativní Office má jeden. V opačném případě `GetVstoObject` vrátí **null**. Například `GetVstoObject` metoda vrátí hodnotu <xref:Microsoft.Office.Tools.Word.Document> Pokud zadaný <xref:Microsoft.Office.Interop.Word.Document> je základní objekt dokumentu v projektu dokumentu aplikace Word.  
  
  V projektech na úrovni dokumentu, nelze použít `GetVstoObject` metodu pro vytvoření nového <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, nebo <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt za běhu. Tuto metodu můžete použít pouze pro přístup k existující položky hostitele, které jsou generovány v projektu v době návrhu. Pokud chcete vytvořit nové položky hostitele v době běhu, je třeba vytvořit projekt doplňku VSTO. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) a [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Použijte metody GetVstoObject a HasVstoObject  
 Volání `HasVstoObject` a `GetVstoObject` metody, použijte `Globals.Factory.GetVstoObject` nebo `Globals.Factory.HasVstoObject` metoda a předejte jí objekt nativní aplikaci Word nebo Excel (jako <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Worksheet>), který chcete testovat.  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Správa dokumentů na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  