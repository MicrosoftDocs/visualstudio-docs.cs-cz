---
title: Přizpůsobení na úrovni dokumentu programu
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d1908f72bce01956bbb2eeb62bb9bbc30a64b0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254022"
---
# <a name="program-document-level-customizations"></a>Přizpůsobení na úrovni dokumentu programu
  Když rozšíříte systém Microsoft Office Word nebo systém Microsoft Office Excel pomocí přizpůsobení na úrovni dokumentu, můžete provádět následující úlohy:

- Automatizujte aplikaci pomocí jejího objektového modelu.

- Přidejte ovládací prvky na plochu dokumentu.

- Vyvolejte kód jazyk Visual Basic for Application (VBA) v dokumentu ze sestavení vlastního nastavení.

- Volání kódu v sestavení vlastního nastavení z jazyka VBA.

- Spravujte určité aspekty dokumentu, i když se nachází na serveru, na kterém není nainstalovaná systém Microsoft Office.

- Přizpůsobení uživatelského rozhraní (UI) aplikace.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Některé aspekty psaní kódu v projektech na úrovni dokumentu se liší od jiných typů projektů v aplikaci Visual Studio. Mnohé z těchto rozdílů způsobují způsob, jakým jsou modely objektů Office vystaveny spravovanému kódu. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).

  Obecné informace o přizpůsobení na úrovni dokumentu a dalších typech řešení, které můžete vytvořit pomocí nástrojů pro vývoj pro Office v sadě Visual Studio, najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Použití vygenerovaných tříd v projektech na úrovni dokumentu
 Když vytvoříte projekt na úrovni dokumentu, Visual Studio automaticky vygeneruje třídu v projektu, kterou můžete použít k zahájení psaní kódu. Visual Studio generuje různé třídy pro Word a Excel:

- V projektech na úrovni dokumentu ve Wordu je třída volána `ThisDocument` ve výchozím nastavení.

- Projekty na úrovni dokumentu pro aplikaci Excel mají více vygenerované třídy: jeden pro sešit samotný a druhý pro každý list. Ve výchozím nastavení mají tyto třídy následující názvy:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Vygenerovaná třída obsahuje obslužné rutiny události, které jsou volány při otevření nebo zavření dokumentu. Chcete-li spustit kód při otevření dokumentu, přidejte kód do `Startup` obslužné rutiny události. Chcete-li spustit kód těsně před zavřením dokumentu, přidejte kód do `Shutdown` obslužné rutiny události. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Pochopení návrhu vygenerovaných tříd
 V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , jsou typy položek hostitele v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozhraních rozhraní, takže generované třídy nemohou z nich odvodit jejich implementaci. Namísto toho generované třídy odvozují většinu svých členů z následujících základních tříd:

- `ThisDocument`: je odvozen z <xref:Microsoft.Office.Tools.Word.DocumentBase> .

- `ThisWorkbook`: je odvozen z <xref:Microsoft.Office.Tools.Excel.WorkbookBase> .

- `Sheet`*n*: je odvozen z <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

  Tyto základní třídy přesměrují všechna volání na jejich členy na interní implementace odpovídajících rozhraní hostitelských položek v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Například pokud voláte <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> metodu `ThisDocument` třídy, <xref:Microsoft.Office.Tools.Word.DocumentBase> třída přesměruje toto volání do interní implementace <xref:Microsoft.Office.Tools.Word.Document> rozhraní v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="access-the-object-model-of-the-host-application"></a>Přístup k objektovému modelu aplikace hostitele
 Pro přístup k objektovému modelu aplikace hostitele použijte členy vygenerované třídy v projektu. Každá z těchto tříd odpovídá objektu v objektovém modelu aplikace Excel nebo Word a obsahuje většinu stejných vlastností, metod a událostí. Například `ThisDocument` Třída v projektu na úrovni dokumentu pro aplikaci Word poskytuje většinu stejných členů jako <xref:Microsoft.Office.Interop.Word.Document> objekt v objektovém modelu aplikace Word.

 Následující příklad kódu ukazuje, jak použít objektový model aplikace Word k uložení dokumentu, který je součástí přizpůsobení na úrovni dokumentu pro aplikaci Word. Tento příklad je určen ke spuštění z `ThisDocument` třídy.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Chcete-li provést stejnou věc mimo `ThisDocument` třídu, použijte `Globals` objekt pro přístup ke `ThisDocument` třídě. Například můžete přidat tento kód do souboru kódu podokna akcí, pokud chcete zahrnout tlačítko **Uložit** v uživatelském rozhraní podokna akcí.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Vzhledem k tomu, že `ThisDocument` třída získává většinu členů z <xref:Microsoft.Office.Tools.Word.Document> hostitelské položky, `Save` metoda, která je volána v tomto kódu, je skutečně <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metodou <xref:Microsoft.Office.Tools.Word.Document> položky hostitele. Tato metoda odpovídá <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodě <xref:Microsoft.Office.Interop.Word.Document> objektu v objektovém modelu aplikace Word.

 Další informace o použití objektových modelů aplikace Word a Excel naleznete v tématu [Přehled modelu objektu aplikace Word](../vsto/word-object-model-overview.md) a [model objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 Další informace o `Globals` objektu naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Přidání ovládacích prvků do dokumentů
 Chcete-li přizpůsobit uživatelské rozhraní dokumentu, můžete přidat ovládací prvky model Windows Forms nebo ovládací *prvky hostitele* na plochu dokumentu. Kombinací různých sad ovládacích prvků a psaní kódu můžete navazovat ovládací prvky na data, shromažďovat informace od uživatele a reagovat na akce uživatele.

 Hostitelské ovládací prvky jsou třídy, které rozšiřuje některé objekty v objektovém modelu aplikace Word a Excel. Například <xref:Microsoft.Office.Tools.Excel.ListObject> hostitelský ovládací prvek poskytuje všechny funkce <xref:Microsoft.Office.Interop.Excel.ListObject> v aplikaci Excel. Nicméně <xref:Microsoft.Office.Tools.Excel.ListObject> hostitelský ovládací prvek má také další události a funkce vazby dat.

 Další informace naleznete v tématu Přehled [hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládací prvky Windows Forms v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Kombinování přizpůsobení na úrovni VBA a dokumentů
 Můžete použít kód VBA v dokumentu, který je součástí přizpůsobení na úrovni dokumentu. Můžete volat kód jazyka VBA v dokumentu ze sestavení přizpůsobení a můžete také nakonfigurovat projekt tak, aby povoloval kód v jazyce VBA v dokumentu pro volání kódu v sestavení přizpůsobení.

 Další informace najdete v tématu [Kombinování přizpůsobení na úrovni VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Správa dokumentů na serveru
 Na serveru, na kterém není nainstalovaná systém Microsoft Office Word nebo systém Microsoft Office Excel, můžete spravovat několik různých aspektů přizpůsobení na úrovni dokumentu. Můžete například získat přístup k datům v mezipaměti dat a upravovat je. Můžete také spravovat sestavení vlastního nastavení, které je přidruženo k dokumentu. Můžete například programově odebrat sestavení z dokumentu, aby dokument již nespouštěl váš kód, nebo můžete programově připojit sestavení k dokumentu.

 Další informace najdete v tématu [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Přizpůsobení uživatelského rozhraní aplikací systém Microsoft Office
 Uživatelské rozhraní Wordu a Excelu můžete přizpůsobit následujícími způsoby pomocí přizpůsobení na úrovni dokumentu:

- Přidejte ovládací prvky hostitele nebo model Windows Forms ovládací prvky na plochu dokumentu.

   Další informace najdete v tématech [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md), [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)a [model Windows Forms ovládacích prvků v dokumentu Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Přidejte podokno akcí do dokumentu.

   Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

- Přidejte na pás karet vlastní karty.

   Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

- Přidejte vlastní skupiny na integrovanou kartu na pásu karet.

   Další informace naleznete v tématu [How to: Customize a vestavěná karta](../vsto/how-to-customize-a-built-in-tab.md).

  Další informace o přizpůsobení uživatelského rozhraní aplikací systém Microsoft Office najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Získání rozšířených objektů z nativních objektů Office v přizpůsobeních na úrovni dokumentu
 Mnoho obslužných rutin událostí pro události Office obdrží nativní objekt Office, který představuje sešit, list nebo dokument, který událost vyvolal. V některých případech můžete chtít spustit kód pouze v případě, že se v sešitu nebo dokumentu v přizpůsobení na úrovni dokumentu vyvolala událost. Například v přizpůsobení na úrovni dokumentu v aplikaci Excel můžete chtít spustit kód, když uživatel aktivuje jeden z listů v přizpůsobeném sešitu, ale ne když uživatel aktivuje list v jiném sešitě, který je otevřen ve stejnou dobu.

 Pokud máte nativní objekt Office, můžete otestovat, zda byl tento objekt rozšířen na *položku hostitele* nebo *hostitelský ovládací prvek* v přizpůsobení na úrovni dokumentu. Položky hostitele a hostitelské ovládací prvky jsou typy poskytované rozhraním [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které přidávají funkce do objektů, které existují nativně v aplikacích Word nebo Excel Object Model (tzv. *nativní objekty Office*). Souhrnně jsou položky hostitelů a hostitelské ovládací prvky označovány také jako *rozšířené objekty*. Další informace o hostitelských položkách a hostitelských ovládacích prvcích naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Pochopení metod GetVstoObject a HasVstoObject
 Chcete-li otestovat nativní objekt Office, použijte `HasVstoObject` `GetVstoObject` v projektu metody a:

- Tuto metodu použijte, chcete `HasVstoObject` -li určit, zda má nativní objekt Office rozšířený objekt v přizpůsobení. Tato metoda vrátí **hodnotu true** , pokud má nativní objekt Office rozšířený objekt a jinak **false** .

- Použijte `GetVstoObject` metodu, pokud chcete získat rozšířený objekt pro nativní objekt Office. Tato metoda vrátí <xref:Microsoft.Office.Tools.Excel.ListObject> objekt, <xref:Microsoft.Office.Tools.Excel.Workbook> , <xref:Microsoft.Office.Tools.Excel.Worksheet> , nebo, <xref:Microsoft.Office.Tools.Word.Document> Pokud zadaný nativní objekt Office jednu z nich obsahuje. V opačném případě `GetVstoObject` vrátí **hodnotu null**. Například `GetVstoObject` Metoda vrátí hodnotu, <xref:Microsoft.Office.Tools.Word.Document> Pokud <xref:Microsoft.Office.Interop.Word.Document> je zadaný základní objekt pro dokument ve wordovém dokumentu projektu.

  V projektech na úrovni dokumentu nelze použít `GetVstoObject` metodu k vytvoření nové <xref:Microsoft.Office.Tools.Excel.Workbook> , <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> položky hostitele v době běhu. Tuto metodu lze použít pouze pro přístup ke stávajícím položkám hostitele, které jsou generovány v projektu v době návrhu. Pokud chcete vytvořit nové položky hostitele za běhu, musíte vytvořit projekt doplňku VSTO. Další informace najdete v tématech [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) a [rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Použití metod GetVstoObject a HasVstoObject
 Chcete-li `HasVstoObject` zavolat `GetVstoObject` metodu a, použijte `Globals.Factory.GetVstoObject` `Globals.Factory.HasVstoObject` metodu nebo a předejte nativní objekt Word nebo Excel (například <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Worksheet> ), který chcete otestovat.

## <a name="see-also"></a>Viz také
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
