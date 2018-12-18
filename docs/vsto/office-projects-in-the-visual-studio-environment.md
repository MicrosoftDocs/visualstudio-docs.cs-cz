---
title: Projekty pro Office v prostředí Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8149e8029dbe39d37ab3979df9af38386af84d6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867413"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Projekty pro Office v prostředí Visual Studio
  Projekty pro Microsoft Office nabízejí vývojové prostředí, které se podobá jiným typům projektů v sadě Visual Studio, například projektům modelu Windows Forms. Při vytvoření nebo otevření projektu pro Office se položky projektu zobrazí v **Průzkumníka řešení**. V případě projektů na úrovni dokumentu se dokument (tzn. dokument aplikace Word nebo sešit aplikace Excel) otevře v sadě Visual Studio a dokument se chová jako vizuální návrhář.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>Položky projektu v Průzkumníku řešení  
 V projektu úrovni dokumentu **Průzkumníka řešení** zobrazí následující výchozí položky:  
  
- Uzly pro dokument, sešit a listy, které jsou pomocí projektu přizpůsobeny. Tyto uzly slouží jako kontejnery pro soubory kódu, které jsou přidruženy k dokumentu, sešitu a listům.  
  
- Soubory kódu přidružené k dokumentu, sešitu a listům, které jsou pomocí projektu přizpůsobeny. V projektech pro aplikaci Word jsou soubory kódu přidruženy k dokumentu nebo šabloně aplikace Word. V projektech pro aplikaci Excel jsou soubory kódu přidruženy k sešitu nebo šabloně aplikace Excel a ke každému listu a listu s grafem v sešitu nebo v šabloně.  
  
- Skryté soubory projektu, které nelze přímo upravovat. Další informace najdete v tématu [skryté soubory projektu](#hiddenfiles).  
  
  V projektu doplňku VSTO **Průzkumníka řešení** zobrazí následující výchozí položky:  
  
- Uzel aplikace. Tento uzel má stejný název jako hostitelská aplikace, jako například **slovo**, **Excel**, nebo **Outlook**. Uzel aplikace obsahuje soubor kódu ThisAddIn. Poskytuje také **Namespace pro hostitelský objekt** vlastnost. Další informace o této vlastnosti naleznete v tématu [vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md).  
  
- Soubor kódu ThisAddIn. Tento soubor obsahuje vygenerovanou `ThisAddIn` třídu pro váš doplněk VSTO. Další informace o této třídy najdete v tématu [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
- Skryté soubory projektu, které nelze přímo upravovat. Další informace najdete v tématu [skryté soubory projektu](#hiddenfiles).  
  
### <a name="temporary-certificates"></a>Dočasné certifikáty  
 Projekty Office zahrnují také dočasný certifikát s názvem *název projektu*_TemporaryKey.pfx. Tento certifikát umožňuje podepsat během vývoje projektu manifest aplikace a nasazení. Další informace najdete v tématu [zajištění důvěryhodnosti řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md) a [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Skryté soubory projektu  
 Některé soubory projektu jsou ve výchozím nastavení skryté. Tyto soubory jsou vygenerovány sadou Visual Studio a liší se podle typu projektu. Chcete-li zobrazit skryté soubory, klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníka řešení**.  
  
 Neupravujte skryté soubory projektu. Přímé změny v těchto souborech nejsou podporovány a mohou způsobit poškození projektu. Skryté soubory projektu jsou znovu vygenerovány pokaždé, když v dokumentu dojde k určitým změnám. Pokud skrytý soubor projektu ručně změníte, budou provedené změny při opětovném vygenerování souboru ztraceny.  
  
## <a name="document-designer-in-document-level-projects"></a>Návrhář dokumentu v projektech na úrovni dokumentu  
 Projekty na úrovni dokumentu pro aplikace Excel a Word poskytují návrháře, který je v sadě Visual Studio hostitelem dokumentu přidruženého k projektu. Návrhář umožňuje upravit dokument, aniž by bylo nutné opustit prostředí sady Visual Studio.  
  
 V Návrháři otevřete dokument, dvakrát klikněte na soubor kódu v **Průzkumníka řešení** , který je přidružený dokument. Například otevřete list **List1** v Návrháři projektu aplikace Excel, dvakrát klikněte **List1** soubor kódu.  
  
 Při úpravě dokumentu v návrháři můžete využívat nativní funkce aplikace Office. Můžete například v dokumentu nebo listu zadat text nebo pomocí pásu karet provádět operace, jako je přidání tabulky nebo grafu. Ve výchozím nastavení se používá mapování klávesových zkratek sady Visual Studio. Office používat mapování klávesových zkratek místo toho změnit nastavení v části **nastavení klávesnice sady Microsoft Office** uzlu **možnosti** dialogové okno v **nástroje** nabídky .  
  
### <a name="controls-on-documents"></a>Ovládací prvky v dokumentech  
 Můžete přetáhnout *hostování ovládacích prvků* a ovládací prvky Windows Forms z aplikace Visual Studio **nástrojů** na návrhovou plochu dokumentu. Hostitelské ovládací prvky jsou speciální verze objektů systému Office, například ovládací prvky obsahu aplikace Word nebo oblasti aplikace Excel, které lze používat v projektech pro Office vytvořených pomocí sady Visual Studio. Hostitelské ovládací prvky mají další funkce, které nejsou k dispozici v odpovídajících objektech systému Office, například datové vazby nebo další události.  
  
 Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládacích prvků na dokumenty Office – přehled Windows forms](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Listy a sešity v návrháři aplikace Excel  
 Když list otevřete v návrháři, můžete jej upravovat stejně, jako byste jej otevřeli přímo v aplikaci Excel. Když dvakrát kliknete na buňku listu, přejde buňka do režimu úprav. Pokud dvakrát kliknete na buňku, která obsahuje hostitelský ovládací prvek, otevře se Editor kódu a sady Visual Studio vygeneruje obslužnou rutinu výchozí události pro ovládací prvek. Pokud chcete přejít na jiné listy, můžete kliknout na ouška listů v dolní části návrháře.  
  
 Když v návrháři otevřete sešit, nezobrazí se žádná návrhová plocha. Návrhovým zobrazením sešitu je velké podokno součástí, pomocí něhož je návrhář vyplněn.  
  
 K sešitu a každému listu v sešitu je přidružen soubor kódu. Každý soubor kódu obsahuje vygenerovanou *hostitelský objekt* třídu, která reprezentuje sešit nebo list. Další informace najdete v tématu [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).  
  
### <a name="word-documents-in-the-designer"></a>Dokumenty aplikace Word v Návrháři  
 Když dokument otevřete v návrháři, můžete jej upravovat stejně, jako byste jej otevřeli přímo v aplikaci Word. Když dvakrát kliknete na slovo v dokumentu, je toto slovo vybráno. Pokud se ale toto slovo nachází uvnitř hostitelského ovládacího prvku, otevře se editor kódu a sada Visual Studio vygeneruje obslužnou rutinu výchozí události pro tento ovládací prvek.  
  
 K dokumentu je přidružen soubor kódu. Soubor kódu obsahuje vygenerovanou *hostitelský objekt* třídu, která představuje dokument. Další informace najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md).  
  
### <a name="design-mode-vs-runtime-mode"></a>Režim návrhu a režim runtime  
 Když je dokument otevřen v prostředí sady Visual Studio, je vždy v *režimu návrhu*. Některé operace, například přetažení hostitelského ovládacího prvku na plochu dokumentu, lze provádět pouze v režimu návrhu.  
  
 Chcete-li zobrazit dokumentu v *režimu runtime*, je nutné otevřít aplikaci a dokument mimo sadu Visual Studio. Můžete také sestavit a spustit projekt, čímž se dokument a aplikace automaticky otevřou mimo sadu Visual Studio.  
  
## <a name="code-editor"></a>Editor kódu  
 Editor kódu umožňuje prohlížet a upravovat viditelné soubory kódu ve vašem řešení. Tyto soubory obsahují kód, který definuje chování řešení.  
  
 Další informace o editoru kódu naleznete v tématu [psaní kódu v editoru kódu a textovém](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Další informace o tom, jak psát kód v projektech pro systém Office naleznete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="properties-window"></a>Vlastnosti – okno  
 **Vlastnosti** okně zobrazí vlastnosti pro položky projektu, které jsou vybrány v **Průzkumníka řešení**a pro prvky uživatelského rozhraní, které jsou vybrány v návrháři, jako je například ovládací prvky nebo dokument v projekt na úrovni dokumentu. Některé vlastnosti jsou specifické pro aplikaci a dokument a některé vlastnosti jsou stejné ve všech projektech.  
  
## <a name="data-sources-window"></a>okno Zdroje dat  
 Můžete použít **zdroje dat** okna v projektech pro systém Office úrovni dokumentu přetáhnout zdroje dat do dokumentu a vytvoření ovládacího prvku, který je vázán na zdroj dat. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
## <a name="see-also"></a>Viz také:  
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md)  
  
  