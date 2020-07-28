---
title: Řešení chyb v řešeních pro systém Office
ms.date: 02/02/2017
ms.topic: troubleshooting
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f0d4eee6714d29a1609f6f6531ab18c132d5527
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234689"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Řešení chyb v řešeních pro systém Office
  Při vývoji řešení pro systém Office v sadě Visual Studio mohou nastat problémy při provádění následujících úloh:

- [Vytváření, upgrade a otevírání projektů](#creating)

- [Použití návrhářů](#designers)

- [Psaní kódu](#code)

- [Sestavit projekty](#building)

- [Ladit projekty](#debugging)

## <a name="create-upgrade-and-open-projects"></a><a name="creating"></a>Vytváření, upgrade a otevírání projektů
 Při vytváření nebo otevírání projektů Office se mohou vyskytnout následující chyby.

### <a name="the-project-cannot-be-created"></a>Projekt se nedá vytvořit.
 Došlo k chybě při pokusu o vytvoření nebo otevření projektu sady Office, ale sada Visual Studio neměla dostatek informací k určení příčiny. Zkuste projekt zavřít, ukončete aplikaci Visual Studio a začněte znovu.

 Pokud se pokoušíte vytvořit projekt na úrovni dokumentu, je možné, že v aplikaci Excel nebo Word je již otevřen jiný dokument se stejným názvem jako dokument v novém projektu. Přesvědčte se, zda jsou všechny ostatní instance aplikace Excel nebo Word zavřeny.

### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Vlastnosti ovládacího prvku jsou při vytváření nového projektu na základě dokumentu z existujícího projektu ztraceny.
 Pokud vytvoříte nový projekt Office založený na dokumentu z existujícího projektu, vlastnosti pro všechny ovládací prvky, které jsou v dokumentu, nebudou zkopírovány do nového projektu. Vlastnosti pro všechny existující ovládací prvky musíte resetovat ručně. Alternativně můžete zachovat vlastnosti ovládacího prvku vytvořením kopie existujícího projektu místo vytvoření nového projektu nebo načtením existujícího projektu do nového řešení (v Návrháři) a zkopírováním a vložením ovládacích prvků z existujícího dokumentu do nového dokumentu.

### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Chyby při vytváření projektu excelového sešitu na základě existujícího sešitu
 Pokud vytvoříte nový projekt sešitu aplikace Excel na základě existujícího sešitu, může se zobrazit kombinace následujících chyb.

 Z aplikace Excel: "upozornění na ochranu osobních údajů: Tento dokument obsahuje makra, ovládací prvky ActiveX, informace rozšiřovacího balíku XML nebo webové součásti. To může zahrnovat osobní informace, které není možné odebrat nástrojem Document Inspector. "

 Ze sady Visual Studio: "návrháře se nepodařilo načíst správně."

 K těmto chybám může dojít při pokusu o vytvoření projektu, který je založen na sešitu, který měl své osobní informace odebrat pomocí nástroje Document Inspector. Chcete-li se této chybě vyhnout, proveďte následující kroky před vytvořením projektu.

1. Otevřete sešit v Excelu.

2. V aplikaci Excel otevřete Centrum zabezpečení.

3. Na kartě **Možnosti ochrany osobních údajů** zrušte zaškrtnutí políčka při **ukládání odebrat osobní údaje z vlastností souboru** .

4. Uložte sešit a zavřete aplikaci Excel.

### <a name="cannot-open-a-project-after-migration"></a>Po migraci nejde otevřít projekt.
 Po migraci řešení Office na systém Microsoft Office 2010 se projekt nedá otevřít na vývojovém počítači, který má nainstalovaný jenom systém Microsoft Office systém 2007. Můžou se zobrazit následující chyby.

 Jeden nebo více projektů v řešení nebylo načteno správně. Podrobnosti najdete v okno Výstup. "

 "Nelze vytvořit projekt, protože aplikace přidružená k tomuto typu projektu není na tomto počítači nainstalována. Je nutné nainstalovat aplikaci systém Microsoft Office, která je přidružena k tomuto typu projektu. "

 Chcete-li tento problém vyřešit, upravte soubor *. vbproj* nebo *. csproj* . V případě projektu aplikace Word nahraďte HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". V případě projektu aplikace Excel nahraďte HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" výrazem HostPackage = "{825100CF-0BA7-47EA-A084-DCF3308DAF74}". V případě projektu Outlook nahraďte HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}".

 Případně se ujistěte, že migrované projekty jsou otevřeny pouze ve vývojových počítačích s již nainstalovaným systém Microsoft Office 2010.

### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Chyby v upgradovaných projektech na úrovni dokumentu Office 2003, které obsahují model Windows Forms ovládací prvky
 Pokud upgradujete projekt na úrovni dokumentu systém Microsoft Office 2003 a dokument obsahuje model Windows Forms ovládací prvky, upgradovaný projekt může obsahovat chyby kompilace nebo běhu. Chcete-li se tomuto problému vyhnout, před upgradem projektu nainstalujte do vývojového počítače Visual Studio 2005 Tools for Office Second Edition Runtime. Tato verze modulu runtime je k dispozici jako Distribuovatelný balíček z webu Microsoft Download Center v [nástroji Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 se) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

 Po dokončení upgradu projektu můžete odinstalovat modul Visual Studio 2005 Tools for Office Second Edition Runtime z vývojového počítače, pokud ho nepoužívá žádná jiná řešení pro systém Office.

## <a name="use-the-designers"></a><a name="designers"></a>Použití návrhářů
 Při práci s dokumentem, sešitem nebo návrhářem listů v projektech na úrovni dokumentu může dojít k následujícím chybám.

### <a name="designer-failed-to-load-correctly"></a>Návrhář se nepovedlo správně načíst.
 Visual Studio nemůže otevřít návrháře v následujících případech:

- Aplikace Excel nebo Word je již otevřena a zobrazuje modální dialogové okno. Chcete-li otevřít návrháře, zkontrolujte, zda je v aplikaci Excel nebo Word otevřeno modální dialogové okno a zavřete všechna otevřená modální dialogová okna. Pokud neexistují žádná modální dialogová okna, může se stát, že před tím, než aplikace Excel nebo Word odpoví, bude nutné provést nějakou akci.

- Projekt se právě ladí. Chcete-li otevřít návrháře, zastavte nebo dokončete ladění.

- Doplněk VSTO pro Excel, který je nainstalovaný ve vývojovém počítači, zobrazuje dialogové okno při spuštění Excelu. Chcete-li vytvořit projekt na úrovni dokumentu aplikace Excel, je nutné nejprve zakázat doplněk VSTO.

### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Ovládací prvky se zobrazí v dokumentu nebo listu jako černé obdélníky.
 Pokud seskupete ovládací prvky na dokument nebo list, Visual Studio již nerozpozná ovládací prvky. Seskupené ovládací prvky nejsou dostupné v okně **vlastnosti** a zobrazují se jako černé obdélníky na dokumentu nebo listu. Aby bylo možné obnovit své funkce, je nutné zrušit seskupení ovládacích prvků.

### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Ovládací prvky v šabloně aplikace Word nejsou viditelné v aplikaci Visual Studio.
 Pokud otevřete šablonu aplikace Word v návrháři aplikace Visual Studio, ovládací prvky šablony, které nejsou v řádku s textem, nemusí být viditelné. Je to proto, že Visual Studio otevře šablony aplikace Word v **normálním** zobrazení. Chcete-li zobrazit ovládací prvky, klikněte na nabídku **zobrazení** , přejděte na příkaz **systém Microsoft Office zobrazení aplikace Word** a pak klikněte na tlačítko **rozložení tisku**.

### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Příkaz Vložit klipart v návrháři sady Visual Studio nic nedělá.
 Když je Excel nebo Word otevřený v návrháři sady Visual Studio, kliknutím na **tlačítko Klipart** na kartě **ilustrace** na pásu karet se neotevře podokno úloh **klipartu** . Chcete-li přidat klipart, je nutné otevřít kopii sešitu nebo dokumentu, který je v hlavní složce projektu (nikoli kopii, která je ve složce *\Bin* ) mimo aplikaci Visual Studio, přidat klipart a následně uložit sešit nebo dokument.

## <a name="write-code"></a><a name="code"></a>Napsat kód
 Při psaní kódu v projektech pro systém Office může dojít k následujícím chybám.

### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Při použití jazyka C nejsou k dispozici některé události objektů Office.\#
 V některých případech se může při pokusu o přístup k určité události instance typu PIA (Primary Interop Assembly) v projektu jazyka Visual C# zobrazit chyba kompilátoru, například následující.

 "Nejednoznačnost mezi" Microsoft. Office. Interop. Excel. _Application. NewWorkbook "a" Microsoft. Office. Interop. Excel. AppEvents_Event. NewWorkbook ""

 Tato chyba znamená, že se pokoušíte o přístup k události, která má stejný název jako jiná vlastnost nebo metoda objektu. Chcete-li získat přístup k události, je nutné přetypovat objekt na jeho *rozhraní události*.

 Typy PIA Office, které mají události, implementují dvě rozhraní: základní rozhraní se všemi vlastnostmi a metodami a rozhraní události obsahující události, které jsou vystavené objektem. Tato rozhraní událostí používají zásady pojmenování *ObjectName*události*n*_Event, například <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> a <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> . Pokud nemůžete získat přístup k události, kterou očekáváte najít u objektu, přetypování objektu na jeho rozhraní události.

 Například <xref:Microsoft.Office.Interop.Excel.Application> objekty mají <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> událost a <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> vlastnost. Chcete-li zpracovat <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> událost, přetypování na <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> rozhraní. Následující příklad kódu ukazuje, jak to provést v projektu na úrovni dokumentu pro Excel.

 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]

 Další informace o rozhraních událostí v rámci PIA pro Office naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12//ms247299(v=office.12)).

### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-net_v40_short-or-the-net_v45"></a>Nejde odkazovat na třídy Office PIA v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo.[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]
 V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , kód, který odkazuje na třídu, která je definována v Office PIA, se ve výchozím nastavení nezkompiluje. Třídy v PIA využívají třídu *ObjectName*pro pojmenování, jako je například <xref:Microsoft.Office.Interop.Word.DocumentClass> a <xref:Microsoft.Office.Interop.Excel.WorkbookClass> . Například následující kód z projektu doplňku VSTO aplikace Word nebude zkompilován.

```vb
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;
```

 Výsledkem tohoto kódu jsou následující chyby při kompilaci:

- Visual Basic: odkaz na třídu DocumentClass není povolený, pokud je jeho sestavení propojeno pomocí režimu no-PIA.

- Visual C#: typ spolupráce Microsoft.Office.Interop.Word.DocumentClass nemůže být vložený. Místo toho použijte příslušné rozhraní. "

  Chcete-li tuto chybu vyřešit, upravte kód tak, aby odkazoval na odpovídající rozhraní. Například namísto odkazování na <xref:Microsoft.Office.Interop.Word.DocumentClass> objekt, místo toho vytvořte odkaz na instanci <xref:Microsoft.Office.Interop.Word.Document> rozhraní.

```vb
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument
```

```csharp
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;
```

 Projekty, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , ve výchozím nastavení automaticky vloží všechny typy spolupráce z PIA pro Office. K této chybě kompilace dojde, protože funkce vloženého typu spolupráce funguje pouze s rozhraními, nikoli třídy. Další informace o rozhraních a třídách v rámci PIA pro Office naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12/ms247299(v=office.12)). Další informace o funkci vložených typů spolupráce v projektech Office najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="references-to-office-classes-are-not-recognized"></a>Odkazy na třídy sady Office nejsou rozpoznány.
 Některé názvy tříd, například aplikace, jsou ve více oborech názvů, například <xref:Microsoft.Office.Interop.Word> a <xref:System.Windows.Forms> . Z tohoto důvodu příkaz **Imports** / **using** v horní části šablon projektu obsahuje zkrácený kvalifikační konstantu, například:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]

 Použití příkazu **Imports** / **using** vyžaduje, abyste odlišit odkazy na třídy Office pomocí kvalifikátoru Wordu nebo Excelu, například:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]

 Pokud použijete nekvalifikovanou deklaraci, zobrazí se chyby, například:

 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]

 I když jste naimportovali obor názvů Wordu nebo Excelu a máte přístup ke všem třídám uvnitř něj, musíte plně kvalifikovat všechny typy pomocí Wordu nebo Excelu, aby se odstranila nejednoznačnost oboru názvů.

## <a name="build-projects"></a><a name="building"></a>Sestavit projekty
 Při sestavování projektů Office může dojít k následujícím chybám.

### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nejde sestavit projekt na úrovni dokumentu, který je založený na dokumentu s omezenými oprávněními.
 Visual Studio nemůže sestavit projekty na úrovni dokumentu, pokud má dokument omezená oprávnění. Pokud projekt obsahuje dokument, který má omezená oprávnění, projekt nebude zkompilován a v okně **Seznam chyb** se zobrazí následující zpráva.

 "Nepovedlo se přidat vlastní nastavení."

 Pokud chcete zahrnout dokument s omezenými oprávněními, použijte při vývoji a sestavení řešení neomezený dokument. Pak po publikování řešení použijte omezená oprávnění k dokumentu v umístění publikování.

### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Po odstranění ovládacího prvku NamedRange dojde k chybám kompilátoru.
 Pokud <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek odstraníte z listu, který není aktivním listem v návrháři, automaticky generovaný kód nemusí být odebrán z projektu a může dojít k chybám kompilátoru. Abyste se ujistili, že je kód odebraný, měli byste vždycky vybrat list, který obsahuje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek a nastavit ho jako aktivní list před odstraněním ovládacího prvku. Pokud se automaticky generovaný kód neodstraní při odstranění ovládacího prvku, můžete způsobit, že návrhář tento kód odstraní aktivací listu a provedením změny tak, aby byl list označený jako změněný. Při opětovném sestavování projektu se kód odebere.

## <a name="debug-projects"></a><a name="debugging"></a>Ladit projekty
 Při ladění projektů Office může dojít k následujícím chybám.

### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Při publikování a instalaci řešení na vývojovém počítači se zobrazí výzva k odinstalaci.
 Při ladění řešení pro systém Office se může zobrazit následující chyba.

 "Přizpůsobení se nedá nainstalovat, protože je aktuálně nainstalovaná jiná verze a nedá se upgradovat z tohoto umístění."

 Tato chyba znamená, že jste již dříve publikovali a nainstalovali řešení Office na vývojovém počítači. Chcete-li zabránit zobrazení zprávy, odinstalujte řešení ze seznamu nainstalovaných programů v počítači před laděním řešení. Případně můžete na svém vývojovém počítači vytvořit jiný uživatelský účet, který otestuje instalaci publikovaného řešení.

### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projekty na úrovni dokumentu vytvořené v umístění UNC do sítě se nespouštějí ze sady Visual Studio.
 Pokud vytvoříte projekt na úrovni dokumentu pro aplikaci Excel nebo Word v umístění v síti UNC, je nutné přidat umístění dokumentu do seznamu důvěryhodných umístění v aplikaci Excel nebo Word. V opačném případě se přizpůsobení nenačte při pokusu o spuštění nebo ladění projektu v aplikaci Visual Studio. Další informace o důvěryhodných umístěních najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Po ladění se vlákna nezastavila správně.
 Projekty Office v sadě Visual Studio následují konvence vytváření názvů vláken, která umožňuje ladicímu programu program správně zavřít. Pokud vytvoříte vlákna ve vašem řešení, měli byste pojmenovat každé vlákno s předponou VSTA_, abyste zajistili, že tato vlákna budou zpracována správně při zastavení ladění. Například můžete nastavit `Name` vlastnost vlákna, která čeká na **VSTA_NetworkListener**události sítě.

### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nejde spustit ani ladit žádné řešení Office na vývojovém počítači.
 Pokud nemůžete spustit nebo vyvíjet projekt sady Office na vývojovém počítači, může se zobrazit následující chybová zpráva.

 "Přizpůsobení nelze načíst, protože doménu aplikace nelze vytvořit."

 Sada Visual Studio používá rozhraní Fusion, .NET Framework zavaděč sestavení, aby sestavení mohla ukládat do mezipaměti před načtením řešení pro systém Office. Zajistěte, aby aplikace Visual Studio mohla zapisovat do mezipaměti Fusion, a akci opakujte. Další informace najdete v tématu [sestavení stínových kopií](/dotnet/framework/app-domains/shadow-copy-assemblies).

### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Chyba při zastavování ladicího programu v projektu na úrovni dokumentu po použití operace Upravit a pokračovat
 Použijete-li příkaz **Upravit** a **pokračovat** k provedení změn kódu v projektu na úrovni dokumentu aplikace Excel nebo Word v době, kdy je projekt v režimu pozastavení, může se zobrazit dialogové okno s následující chybovou zprávou, pokud následně zastavíte ladicí program.

 "Ukončení procesu v jeho aktuálním stavu může způsobit neočekávané výsledky, včetně ztráty dat a nestability systému."

 Bez ohledu na to, zda v dialogovém okně kliknete na tlačítko **Ano** nebo **ne** , aplikace Visual Studio ukončí proces aplikace Excel nebo Word a zastaví ladicí program. Chcete-li zastavit ladění projektu bez zobrazení tohoto dialogového okna, ukončete aplikaci Excel nebo Word přímo místo zastavení ladicího programu v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:
- [Řešení potíží s řešeními pro systém Office](../vsto/troubleshooting-office-solutions.md)
- [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)
- [Řešení potíží s nasazením řešení pro systém Office](../vsto/troubleshooting-office-solution-deployment.md)
- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
