---
title: Začínáme s programováním doplňků VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8136a090dbf5e3c3f86ce9b4ade1321f7b36b829
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858885"
---
# <a name="get-started-programming-vsto-add-ins"></a>Začínáme s programováním doplňků VSTO
  Doplňky VSTO můžete použít k automatizaci aplikace Microsoft Office, rozšíření funkcí aplikace a přizpůsobení uživatelského rozhraní (UI) aplikace. Informace o porovnání doplňků VSTO pro jiné druhy řešení pro Office můžete vytvořit pomocí sady Visual Studio najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Vytvářejte projekty doplňku VSTO  
 Vytvořit projekty doplňku VSTO pomocí jedné z šablony projektu doplňku VSTO v **nový projekt** dialogové okno. Tyto šablony zahrnují odkazy na požadovaná sestavení a soubory projektu. Visual Studio obsahuje šablony projektů doplňků VSTO pro většinu aplikací v sadě Office.  
  
 Další informace o tom, jak vytvořit projekt doplňku VSTO v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů, naleznete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Vývoj projekty doplňků VSTO  
 Při vytváření projektu doplňku VSTO, sada Visual Studio automaticky vytvoří *ThisAddIn.vb* (v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) nebo *ThisAddIn.cs* soubor kódu (v jazyce C#). Tento soubor obsahuje `ThisAddIn` třídu, která poskytuje základ pro váš doplněk VSTO. Členové této třídy můžete použít ke spuštění kódu při doplňku VSTO načteny nebo uvolněny, pro přístup k modelu objektu hostitelskou aplikaci a rozšířit funkce aplikace. Další informace najdete v tématu [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatizace aplikací s použitím objektových modelů  
 Objektové modely aplikací sady Microsoft Office vystavit mnoho typů, které můžete programovat proti v doplňku VSTO. K automatizaci aplikace můžou používat tyto typy. Například můžete prostřednictvím kódu programu vytvořit a odeslat e-mailu v Outlooku, nebo můžete otevřít dokument a přidat obsah v aplikaci Word. Další informace o tom, jak přístup k modelu objektu hostitelské aplikace v kódu, naleznete v tématu [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Další informace o objektové modely z konkrétní aplikace Microsoft Office naleznete v následujících tématech:  
  
-   [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)  
  
-   [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)  
  
-   [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath – řešení](../vsto/infopath-solutions.md)  
  
-   [Řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Projektová řešení](../vsto/project-solutions.md)  
  
-   [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Přizpůsobení uživatelského rozhraní aplikací  
 Existuje několik různých způsobů přizpůsobení uživatelského rozhraní hostitelské aplikace pomocí doplňku VSTO:  
  
- Excelu a Wordu můžete přidat spravovaných ovládacích prvků do dokumentů. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
- Na pásu karet můžete přizpůsobit, pokud aplikace podporuje. Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
- Pokud aplikace podporuje, můžete vytvořit vlastního podokna úloh. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
- Pro aplikaci Outlook můžete vytvořit vlastní formulář regionu. Další informace najdete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
- Pro všechny aplikace Microsoft Office můžete zobrazit Windows Forms v doplňku VSTO.  
  
  Další informace o tom, jak přizpůsobit aplikace uživatelského rozhraní systému Microsoft Office, naleznete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Další kroky  
 Informace o vytváření doplňků VSTO, najdete v následujících návodech:  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Návod: Vytvoření vašeho prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
  Tyto kurzy vám představí vývojářské nástroje balíku Office v sadě Visual Studio a programovací model pro doplňky VSTO.  
  
  Seznam témat, která vás provede některé běžné úlohy v projektech pro systém Office naleznete v tématu [běžné úlohy při programování pro Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)  
  
  