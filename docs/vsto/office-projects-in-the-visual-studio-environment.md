---
title: Projekty Office v prostředí Visual Studio
description: Přečtěte si, jak systém Microsoft Office projekty mají vývojové prostředí podobné jiným typům projektů v aplikaci Visual Studio, jako jsou například projekty model Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88abd7294a96b4fe4989630753253b16f036ab7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892005"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Projekty Office v prostředí Visual Studio
  Projekty pro Microsoft Office nabízejí vývojové prostředí, které se podobá jiným typům projektů v sadě Visual Studio, například projektům modelu Windows Forms. Při vytváření nebo otevírání projektu sady Office se položky projektu zobrazí v **Průzkumník řešení**. V případě projektů na úrovni dokumentu se dokument (tzn. dokument aplikace Word nebo sešit aplikace Excel) otevře v sadě Visual Studio a dokument se chová jako vizuální návrhář.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Položky projektu v Průzkumník řešení
 V projektu na úrovni dokumentu **Průzkumník řešení** zobrazí následující výchozí položky:

- Uzly pro dokument, sešit a listy, které jsou pomocí projektu přizpůsobeny. Tyto uzly slouží jako kontejnery pro soubory kódu, které jsou přidruženy k dokumentu, sešitu a listům.

- Soubory kódu přidružené k dokumentu, sešitu a listům, které jsou pomocí projektu přizpůsobeny. V projektech pro aplikaci Word jsou soubory kódu přidruženy k dokumentu nebo šabloně aplikace Word. V projektech pro aplikaci Excel jsou soubory kódu přidruženy k sešitu nebo šabloně aplikace Excel a ke každému listu a listu s grafem v sešitu nebo v šabloně.

- Skryté soubory projektu, které nelze přímo upravovat. Další informace najdete v tématu [skryté soubory projektu](#hiddenfiles).

  V projektu doplňku VSTO **Průzkumník řešení** zobrazí následující výchozí položky:

- Uzel aplikace. Tento uzel má stejný název jako hostitelská aplikace, jako je **Word**, **Excel** nebo **Outlook**. Uzel aplikace obsahuje soubor kódu ThisAddIn. Poskytuje také **obor názvů pro vlastnost položky hostitele** . Další informace o této vlastnosti naleznete v tématu [vlastnosti v projektech Office](../vsto/properties-in-office-projects.md).

- Soubor kódu ThisAddIn. Tento soubor obsahuje vygenerovanou `ThisAddIn` třídu pro doplněk VSTO. Další informace o této třídě najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

- Skryté soubory projektu, které nelze přímo upravovat. Další informace najdete v tématu [skryté soubory projektu](#hiddenfiles).

### <a name="temporary-certificates"></a>Dočasné certifikáty
 Projekty Office také obsahují dočasný certifikát s názvem *název projektu* _TemporaryKey. pfx. Tento certifikát umožňuje podepsat během vývoje projektu manifest aplikace a nasazení. Další informace najdete v tématu [udělení důvěry na řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md) a [zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md).

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> Skryté soubory projektu
 Některé soubory projektu jsou ve výchozím nastavení skryté. Tyto soubory jsou vygenerovány sadou Visual Studio a liší se podle typu projektu. Chcete-li zobrazit skryté soubory, klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení**.

 Neupravujte skryté soubory projektu. Přímé změny v těchto souborech nejsou podporovány a mohou způsobit poškození projektu. Skryté soubory projektu jsou znovu vygenerovány pokaždé, když v dokumentu dojde k určitým změnám. Pokud skrytý soubor projektu ručně změníte, budou provedené změny při opětovném vygenerování souboru ztraceny.

## <a name="document-designer-in-document-level-projects"></a>Návrhář dokumentů v projektech na úrovni dokumentu
 Projekty na úrovni dokumentu pro aplikace Excel a Word poskytují návrháře, který je v sadě Visual Studio hostitelem dokumentu přidruženého k projektu. Návrhář umožňuje upravit dokument, aniž by bylo nutné opustit prostředí sady Visual Studio.

 Chcete-li otevřít dokument v návrháři, dvakrát klikněte na soubor kódu v **Průzkumník řešení** , který je přidružen k dokumentu. Například pro otevření listu **List1** v návrháři v projektu aplikace Excel poklikejte na soubor s kódem **List1** .

 Při úpravě dokumentu v návrháři můžete využívat nativní funkce aplikace Office. Můžete například v dokumentu nebo listu zadat text nebo pomocí pásu karet provádět operace, jako je přidání tabulky nebo grafu. Ve výchozím nastavení se používá mapování klávesových zkratek sady Visual Studio. Chcete-li místo toho použít mapování klávesových zkratek sady Office, změňte nastavení v uzlu **systém Microsoft Office nastavení klávesnice** v dialogovém okně **Možnosti** v nabídce **nástroje** .

### <a name="controls-on-documents"></a>Ovládací prvky v dokumentech
 *Ovládací prvky hostitele* a ovládací prvky model Windows Forms lze přetáhnout z **panelu nástrojů** sady Visual Studio na plochu návrhu dokumentu. Hostitelské ovládací prvky jsou speciální verze objektů systému Office, například ovládací prvky obsahu aplikace Word nebo oblasti aplikace Excel, které lze používat v projektech pro Office vytvořených pomocí sady Visual Studio. Hostitelské ovládací prvky mají další funkce, které nejsou k dispozici v odpovídajících objektech systému Office, například datové vazby nebo další události.

 Další informace naleznete v tématu Přehled [hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [ovládací prvky Windows Forms v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Listy a sešity aplikace Excel v Návrháři
 Když list otevřete v návrháři, můžete jej upravovat stejně, jako byste jej otevřeli přímo v aplikaci Excel. Když dvakrát kliknete na buňku listu, přejde buňka do režimu úprav. Pokud dvakrát kliknete na buňku, která obsahuje hostitelský ovládací prvek, otevře se Editor kódu a aplikace Visual Studio vygeneruje výchozí obslužnou rutinu události pro ovládací prvek. Pokud chcete přejít na jiné listy, můžete kliknout na ouška listů v dolní části návrháře.

 Když v návrháři otevřete sešit, nezobrazí se žádná návrhová plocha. Návrhovým zobrazením sešitu je velké podokno součástí, pomocí něhož je návrhář vyplněn.

 K sešitu a každému listu v sešitu je přidružen soubor kódu. Každý soubor kódu obsahuje vygenerovanou třídu *hostitelské položky* , která představuje sešit nebo list. Další informace najdete v tématu [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).

### <a name="word-documents-in-the-designer"></a>Dokumenty aplikace Word v Návrháři
 Když dokument otevřete v návrháři, můžete jej upravovat stejně, jako byste jej otevřeli přímo v aplikaci Word. Když dvakrát kliknete na slovo v dokumentu, je toto slovo vybráno. Pokud se ale toto slovo nachází uvnitř hostitelského ovládacího prvku, otevře se editor kódu a sada Visual Studio vygeneruje obslužnou rutinu výchozí události pro tento ovládací prvek.

 K dokumentu je přidružen soubor kódu. Soubor kódu obsahuje vygenerovanou třídu *hostitelské položky* , která představuje dokument. Další informace najdete v tématu [položka hostitele dokumentu](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Režim návrhu vs. režim modulu runtime
 Když je dokument otevřen v prostředí sady Visual Studio, je vždy v *režimu návrhu*. Některé operace, například přetažení hostitelského ovládacího prvku na plochu dokumentu, lze provádět pouze v režimu návrhu.

 Chcete-li zobrazit dokument v *režimu běhu*, je nutné otevřít aplikaci a dokument mimo aplikaci Visual Studio. Můžete také sestavit a spustit projekt, čímž se dokument a aplikace automaticky otevřou mimo sadu Visual Studio.

## <a name="code-editor"></a>Editor kódu
 Editor kódu umožňuje prohlížet a upravovat viditelné soubory kódu ve vašem řešení. Tyto soubory obsahují kód, který definuje chování řešení.

 Další informace o editoru kódu naleznete [v tématu Write code in Code and Text Editor](../ide/writing-code-in-the-code-and-text-editor.md). Další informace o tom, jak psát kód v projektech pro systém Office, najdete v tématu popisujícím [Zápis kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Vlastnosti – okno
 V okně **vlastnosti** se zobrazí vlastnosti položek projektu, které jsou vybrány v **Průzkumník řešení**, a pro prvky uživatelského rozhraní, které jsou vybrány v návrháři, jako jsou například ovládací prvky nebo dokument v projektu na úrovni dokumentu. Některé vlastnosti jsou specifické pro aplikaci a dokument a některé vlastnosti jsou stejné ve všech projektech.

## <a name="data-sources-window"></a>okno Zdroje dat
 Můžete použít okno **zdroje dat** v projektech Office na úrovni dokumentu k přetažení zdroje dat do dokumentu a vytvoření ovládacího prvku, který je svázán se zdrojem dat. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Vlastnosti v projektech pro systém Office](../vsto/properties-in-office-projects.md)
