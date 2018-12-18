---
title: Řešení potíží s chybami v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bcc5600f38e2d53244d972e4c4c7094182bfa48c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672948"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Řešení potíží s chybami v řešeních pro systém Office
  Při provádění následujících úloh při vývoji řešení pro systém Office v sadě Visual Studio se můžete setkat s problémy:  
  
-   [Vytvářet, upgradovat a otevřít projekty](#creating)  
  
-   [Pomocí návrhářů](#designers)  
  
-   [Psaní kódu](#code)  
  
-   [Sestavení projektů](#building)  
  
-   [Ladění projektů](#debugging)  
  
##  <a name="creating"></a> Vytvářet, upgradovat a otevřít projekty  
 Při vytváření nebo otevírání projektů Office, mohou se vyskytnout následující chyby.  
  
### <a name="the-project-cannot-be-created"></a>Projekt nejde vytvořit.  
 Pokud jste se pokusili k vytvoření nebo otevření projektu pro Office, ale Visual Studio nemá dostatek informací k určení příčiny došlo k chybě. Zkuste zavřít projekt, ukončení sady Visual Studio a znovu spustit.  
  
 Pokud se pokoušíte vytvořit projekt úrovni dokumentu, je možné, že jiný dokument se stejným názvem jako dokument v novém projektu je již otevřen v aplikaci Excel nebo Word. Ujistěte se, že jsou uzavřeny všechny instance aplikace Excel nebo Word.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Vlastnosti ovládacích prvků budou ztraceny, když vytvoříte nový projekt založený na dokument z existujícího projektu  
 Pokud vytvoříte nový projekt Office založený na dokument z existujícího projektu, vlastnosti pro všechny ovládací prvky, které jsou v dokumentu nejsou zkopírovány do nového projektu. Je nutné ručně obnovit vlastnosti pro všechny stávající ovládací prvky. Alternativně můžete zachovat vlastnosti ovládacích prvků tak, že vytvoříte kopii existujícího projektu místo vytvoření nového projektu nebo načítání existující projekt do nového řešení (v návrháři) a zkopírováním a vložením z existující ovládací prvky dokument nový dokument.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Chyby při vytváření projektu sešitu aplikace Excel založené na existující sešit  
 Pokud vytvoříte nový projekt sešitu aplikace Excel založený na existující sešit, může se zobrazit kombinaci následující chyby.  
  
 Z aplikace Excel: "O ochraně osobních údajů upozornění: Tento dokument obsahuje makra, ovládací prvky ActiveX, informace o balíčku rozšíření XML nebo webové součásti. Ty mohou obsahovat osobní informace, které nebude moct odebrat metadat."  
  
 Ze sady Visual Studio: "Návrhář se nenačetl správně."  
  
 K těmto chybám může dojít, že se že pokusíte vytvořit projekt, který je založen na sešit, který měl jeho osobní údaje, pomocí metadat. K této chybě předejít, proveďte následující kroky před vytvořením projektu.  
  
1.  Otevřete sešit v Excelu.  
  
2.  V aplikaci Excel otevřete v Centru zabezpečení.  
  
3.  Na **možnosti ochrany osobních údajů** vymazat kartu **odebrat osobní údaje z vlastností souboru uložit** zaškrtávací políčko.  
  
4.  Sešit uložte a zavřete aplikaci Excel.  
  
### <a name="cannot-open-a-project-after-migration"></a>Projekt nejde otevřít po migraci  
 Po Office, které řešení je migrovat na systém Microsoft Office 2010 nelze projekt otevírán ve vývojovém počítači s pouze systému Microsoft Office 2007 nainstalovaný. Může se zobrazit následující chyby.  
  
 "Jeden nebo více projektů v řešení nebylo správně načteno. Podrobnosti najdete ve výstupním okně Podrobnosti."  
  
 "Nejde vytvořit projekt, protože na tomto počítači není nainstalována aplikace spojené s tímto typem projektu. Je nutné nainstalovat aplikaci Microsoft Office, která souvisí s tímto typem projektu."  
  
 Chcete-li tento problém vyřešit, upravte *.vbproj* nebo *.csproj* souboru. Projekt aplikace Word nahradit HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" s HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Projektu aplikace Excel, nahraďte HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" s HostPackage = "{825100CF-0BA7-47EA-A084-DCF3308DAF74}". Projekt aplikace Outlook, nahraďte HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" s HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}".  
  
 Další možností je zajistěte, že migrované projekty jsou otevřít jenom ve vývojových počítačích se systémem Microsoft Office 2010 už nainstalovaná.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Chyby v upgradovaných projektů Office 2003 úrovni dokumentu, které obsahují ovládací prvky Windows Forms  
 Pokud upgradujete projekt úrovni dokumentu aplikace Microsoft Office 2003 a dokument obsahuje ovládací prvky Windows Forms, upgradovaný projekt může být chyby kompilace nebo za běhu. K tomuto problému vyhnout, nainstalujte Visual Studio 2005 Tools for Office Second Edition Runtime na vývojovém počítači před upgradem projektu. Tato verze modulu runtime je k dispozici jako redistribuovatelný balíček ze služby Microsoft Download Center na [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Po dokončení upgradu projektu můžete odinstalovat Visual Studio 2005 Tools for Office Second Edition Runtime z vývojového počítače. Pokud není používán jinými řešeními sady Office.  
  
##  <a name="designers"></a> Pomocí návrhářů  
 Při práci s dokumentu, sešitu nebo listu návrháře v projekty na úrovni dokumentu, mohou se vyskytnout následující chyby.  
  
### <a name="designer-failed-to-load-correctly"></a>Návrhář se nenačetl správně  
 Visual Studio nemůže otevřít návrháře v následujících případech:  
  
-   Aplikace Excel nebo Word je již otevřen a je zobrazení modálního dialogového okna. Otevřít návrháře, zkontrolujte, zda aplikace Excel nebo Word má modální dialogové okno otevřít a zavřít všechny otevřené modálních dialogových oken. Pokud nejsou otevřeny žádné modálních dialogových oken, může být nějakou jinou akci, která je požadována aplikace Excel nebo Word reaguje.  
  
-   Projekt je momentálně laděna. Otevřete návrháři, zastavte nebo ukončete ladění.  
  
-   VSTO Excelový doplněk, který je nainstalován na vývojovém počítači je zobrazení dialogového okna, při spuštění aplikace Excel. Vytvoření projektu úrovni dokumentu aplikace Excel, musíte nejprve zakázat doplňku VSTO.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Ovládací prvky se zobrazí jako černá obdélníků v dokumentu nebo listu  
 Pokud jste skupinu pro ovládací prvky v dokumentu nebo listu, Visual Studio již nerozpoznává ovládací prvky. Seskupené ovládací prvky nelze přistupovat ve **vlastnosti** okně a zobrazí jako černá obdélníků v dokumentu nebo sešitu. Aby bylo možné obnovit jejich funkce musíte oddělit ovládací prvky.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Ovládací prvky na šablonu aplikace Word se nezobrazí v sadě Visual Studio  
 Pokud otevřete šablonu aplikace Word v návrháři aplikace Visual Studio nemusí být viditelné ovládací prvky na této šabloně, které nejsou v textu. Důvodem je, že Visual Studio otevře šablony aplikace Word v **normální** zobrazení. Chcete-li zobrazit ovládací prvky, klikněte na tlačítko **zobrazení** nabídky, přejděte k **Microsoft Office Word zobrazení** a potom klikněte na tlačítko **rozložení při tisku**.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Příkaz Insert klip obrázky neprovede v návrháři aplikace Visual Studio  
 Pokud aplikace Excel nebo Word je otevřen v návrháři aplikace Visual Studio, kliknutím na tlačítko **klipart** tlačítko **ilustrace** nelze otevřít kartu na pásu karet **klipart** podokna úloh. Chcete-li přidat klipart, je nutné otevřít kopii sešitu nebo dokument, který je ve složce hlavní projekt (nelze kopírovat, který je v *\bin* složky) mimo sadu Visual Studio, přidejte klipart a pak uložte sešit nebo dokumentu.  
  
##  <a name="code"></a> Psaní kódu  
 Pokud píšete kód v projektech Office, mohou se vyskytnout následující chyby.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Některé události z objektů sady Office nejsou přístupné, při použití jazyka C#  
 V některých případech se může zobrazit chyba kompilátoru následujícím postupem při pokusu o přístup k určité události instance Office primární sestavení vzájemné spolupráce (PIA) zadejte v projektu jazyka Visual C#.  
  
 "Byla zjištěna dvojznačnost mezi"Microsoft.Office.Interop.Excel._Application.NewWorkbook"a"Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook."  
  
 Tato chyba znamená, že se pokoušíte získat přístup k události, která má stejný název jako jiný vlastnost nebo metodu objektu. Pro přístup k události, musíte vysílat na objekt jeho *rozhraní události*.  
  
 Typy PIA sady Office, které události mají implementovat dvě rozhraní: základní rozhraní se všemi vlastnosti a metody a události rozhraní, které obsahuje události, které jsou vystaveny v objektu. Tyto události rozhraní použít zásady vytváření názvů *objectname*události*n*_událostí, jako například <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> a <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Pokud nelze získat přístup k události, ke které jste očekávali na objekt, objekt přetypujte na jeho rozhraní události.  
  
 Například <xref:Microsoft.Office.Interop.Excel.Application> objekty mají <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> událostí a <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> vlastnost. Zpracování <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> přetypovat <xref:Microsoft.Office.Interop.Excel.Application> k <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> rozhraní. Následující příklad kódu ukazuje, jak to provést v projektu úrovni dokumentu pro Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Další informace o rozhraních událostí v sestavení PIA sady Office naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](/previous-versions/office/office-12//ms247299(v=office.12)).  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>Nelze odkaz Office PIA tříd v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], ve výchozím nastavení nebude kompilovat kód, který odkazuje na třídu, která je definována v Office PIA. Třídy v sestavení PIA použít zásady vytváření názvů *objectname*třídy, jako například <xref:Microsoft.Office.Interop.Word.DocumentClass> a <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Například následující kód z projektu doplňku VSTO pro Word, nebude kompilovat.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Tento kód vrátí následující chyby kompilace:  
  
- Visual Basic: "odkaz na třídu 'Třídu DocumentClass' není povolen její sestavení odkazováno prostřednictvím režimu No-PIA."  
  
- Visual C#: "typ spolupráce, které 'Microsoft.Office.Interop.Word.DocumentClass' nemůže být vložený. Použijte příslušné rozhraní."  
  
  Chcete-li vyřešit tuto chybu, upravte kód, který odkazuje odpovídající rozhraní místo. Například místo odkazu <xref:Microsoft.Office.Interop.Word.DocumentClass> objektu, odkazovat na instanci <xref:Microsoft.Office.Interop.Word.Document> místo toho rozhraní.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Projekty, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], automaticky vložit všechny typy spolupráce ze sestavení PIA sady Office ve výchozím nastavení. Tuto chybu kompilace dochází, protože funkce vestavěné typy spolupráce funguje pouze s rozhraními, nikoliv třídy. Další informace o rozhraní a třídy v sestavení PIA sady Office naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](http://go.microsoft.com/fwlink/?LinkId=189592). Další informace o funkci vestavěné typy spolupráce na projektech pro systém Office naleznete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Odkazy na třídy Office nejsou rozpoznány.  
 V několika oborech názvů, jako jsou některé názvy tříd, například aplikace, <xref:Microsoft.Office.Interop.Word> a <xref:System.Windows.Forms>. Z tohoto důvodu **importy**/**pomocí** příkazu v horní části šablony projektu zahrnuje sdružená kvalifikaci – konstanta, například:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 Toto použití **importy**/**pomocí** vyžaduje rozlišení odkazů na třídy Office s kvalifikátorem Word nebo Excel, například:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 Chyby se zobrazí, když použijete nekvalifikované prohlášení, například:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 I když jste importovali obor názvů aplikaci Word nebo Excel a mají přístup ke všem třídám dovnitř musí plně kvalifikovat všechny typy s Word nebo Excel k odebrání oboru názvů nejednoznačnost.  
  
##  <a name="building"></a> Sestavení projektů  
 Při sestavování projektů Office, mohou se vyskytnout následující chyby.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nelze sestavit projekt úrovni dokumentu, který je založen na dokument s omezenými oprávněními  
 Visual Studio nemůže vytvořit projekty na úrovni dokumentu, pokud dokument má omezená oprávnění. Pokud váš projekt obsahuje dokument, který má omezená oprávnění, projekt nepůjde kompilovat a zobrazí se následující zpráva **seznam chyb** okna.  
  
 "Nepovedlo se přidat přizpůsobení."  
  
 Pokud chcete zahrnout dokument, který má omezená oprávnění, použijte dokument neomezený při vývoji a sestavte řešení. Po publikování řešení pak použijte omezená oprávnění k dokumentu v umístění pro publikování.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Po odstranění ovládacím prvkem namedrange dojít k chybám kompilátoru  
 Pokud odstraníte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku z listu, který není v aktivním listu v návrháři, automaticky vygenerovaný kód nemusí být odebráno z projektu a může dojít k chybám kompilátoru. Pokud chcete mít jistotu, kód se odebere, byste měli vždy vybrat list, který obsahuje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku k němu aktivního listu před odstraněním ovládacího prvku. Pokud automaticky generovaný kód není odstraněn, když odstraníte ovládací prvek, může způsobit návrháře odstranit kód tak, že aktivace listu a listu bude označena jako upravená tak, aby provedením změny. Při opětovném sestavování projektu kódu se odebere.  
  
##  <a name="debugging"></a> Ladění projektů  
 Při ladění projektů Office, mohou se vyskytnout následující chyby.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Řádek pro odinstalaci se zobrazí, když publikujete a instalaci řešení na vývojovém počítači  
 Při ladění řešení pro Office se může zobrazit následující chyba.  
  
 "Přizpůsobení nelze nainstalovat, protože jiná verze je nainstalovaná a nedá se upgradovat z tohoto umístění."  
  
 Tato chyba označuje, že jste publikována a nainstalované řešení Office na vývojovém počítači. Chcete-li zabránit zobrazování zprávu, řešení v seznamu nainstalovaných programů v počítači před odinstalujte ladění řešení. Alternativně můžete vytvořit jiný uživatelský účet na vašem vývojovém počítači a otestujte instalaci publikované řešení.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projekty na úrovni dokumentu vytvořeno v umístění v síti UNC nespouštějte ze sady Visual Studio  
 Pokud vytvoříte projekt úrovni dokumentu pro Excel nebo Word v síťovém umístění UNC, je nutné přidat umístění dokumentu do seznamu důvěryhodných umístění v aplikaci Excel nebo Word. V opačném případě přizpůsobení se nenačte při pokusu o spuštění nebo ladění projektu v sadě Visual Studio. Další informace o důvěryhodných umístění naleznete v tématu [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Vlákna nejsou správně zastavena po ladění  
 Projekty Office v sadě Visual Studio podle vlákna konvence, které umožňují ladicímu programu řádně ukončit program. Pokud vytvoříte vlákna ve vašem řešení, byste měli pojmenovat každé vlákno s předponou VSTA_ Ujistěte se, že tato vlákna jsou správně zpracovány, když zastavíte ladění. Například může být nastaven `Name` vlastnost vlákna, která čeká na událost sítě **VSTA_NetworkListener**.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nelze spustit nebo ladit jakékoli řešení Office na vývojovém počítači  
 Pokud nelze spustit nebo vývoj projektu aplikace Office na vývojovém počítači, zobrazí se následující chybová zpráva.  
  
 "Vlastního nastavení nelze načíst, protože nelze vytvořit doménu aplikace."  
  
 Visual Studio používá Fusion, zavaděč sestavení rozhraní .NET Framework, pro ukládání do mezipaměti sestavení před načtením řešení pro systém Office. Ujistěte se, že Visual Studio můžete zapsat do mezipaměti fúze a zkuste to znovu. Další informace najdete v tématu [sestavení stínových kopií](/dotnet/framework/app-domains/shadow-copy-assemblies).  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Chyba při zastavení ladicího programu v projektu úrovni dokumentu po použitím funkce upravit a pokračovat  
 Pokud používáte **upravit** a **pokračovat** provést změny kódu v projektu úrovni dokumentu pro aplikaci Excel nebo Word projekt je v režimu přerušení, může se zobrazit dialogové okno s následující chybová zpráva. Pokud jste následně ukončete ladicí program.  
  
 "Ukončení procesu v jejím aktuálním stavu způsobit nežádoucí výsledky včetně ztráty dat a nestability systému."  
  
 Určuje, zda kliknete **Ano** nebo **ne** v dialogovém okně Visual Studio ukončí proces aplikace Excel nebo Word a ladicí program se zastaví. Pokud chcete zastavit ladění projektu bez zobrazení dialogovému oknu, ukončete aplikaci Excel nebo Word přímo spíše než při zastavení ladicího programu v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také:  
 [Řešení potíží s řešení pro systém Office](../vsto/troubleshooting-office-solutions.md)   
 [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)   
 [Řešení potíží s nasazením řešení pro systém Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  