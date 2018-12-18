---
title: Přehled vlastních částí XML
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71720ef96ee7d17bd52ea118a8c44a8f4b117cad
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671726"
---
# <a name="custom-xml-parts-overview"></a>Přehled vlastních částí XML
  Vložit XML data do dokumentů pro některé aplikace Microsoft Office. Při vložení dat XML v dokumentu s názvem data *vlastní část XML*.  
  
 Můžete vytvořit a upravit vlastní části XML v dokumentu s použitím doplňku VSTO nebo řešení v sadě Visual Studio na úrovni dokumentu. Není nutné ke spuštění aplikace Microsoft Office, vytvářet a upravovat vlastní části XML.  
  
 **Platí pro:** informace v tomto tématu se vztahují na projekty na úrovni dokumentu a projekty doplňku VSTO pro Excel, PowerPoint a Word. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio také umožňuje datové objekty mezipaměti v přizpůsobeních na úrovni dokumentu. Tato funkce se liší od vlastní části XML, i když existují určité podobnosti. Další informace najdete v tématu [data v přizpůsobeních na úrovni dokumentu v mezipaměti](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Vysvětlení vlastní části XML  
 Vlastní části XML byly zavedeny v systému Microsoft Office 2007, spolu s otevřených formátů XML. Tyto formáty patří nové formáty souborů založený na formátu XML pro Excel, PowerPoint a Word (například *.xlsx*, *PPTX*, a *.docx*). Dokumenty v tyto formáty obsahují soubory XML (také s názvem *částí XML*), která jsou uspořádané do složek v archivu ZIP. Většina částí XML jsou integrované součásti, které vám pomohou definovat strukturu a její stav dokumentu. Dokumenty, ale může také obsahovat vlastní části XML, které můžete použít k ukládání libovolných dat XML v dokumentech.  
  
 Formáty souborů XML přípravě aplikací k práci s dokumenty takovým způsobem, který neumožňuje ve starších formátech binárního souboru (například *.xls*, *PPT*, a *doc*). Všechny aplikace, který může číst archivy ZIP můžete prozkoumat a upravit obsah dokumentů, i když není nainstalována aplikace Microsoft Office.  
  
 Další informace o struktuře Open XML a vlastní části XML najdete v následujících článcích:  
  
-   [Úvod do formátů souborů Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [Postupy: manipulace s dokumenty formáty Open XML](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [Návod: Formát XML aplikace Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [Vytváření dokumentů aplikace Word 2007 pomocí formáty Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Aplikace Excel, Word a PowerPoint také umožňují používat vlastní části XML v dokumentech, které jsou uloženy v binárním formátu. Pokud dokument je uložený v binárním formátu, nelze však přidat ani upravit vlastní části XML bez spuštění aplikace Microsoft Office.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Vytvářet a upravovat vlastní části XML  
 Můžete vytvořit nebo upravit vlastní části XML, když je dokument otevřen v aplikaci Office nebo při zavření dokumentu – i když není nainstalována aplikace Microsoft Office.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Upravit části XML, když je spuštěná aplikace Office  
 Vlastní části XML můžete pracovat s použitím přizpůsobení úrovni dokumentu nebo doplňku VSTO. Pokud používáte přizpůsobení úrovni dokumentu, budete obvykle pracovat s vlastní části XML, které jsou v upravený dokument. Pokud používáte doplňku VSTO, můžete vytvořit nebo upravit vlastní části XML v libovolném dokumentu, který je otevřen v aplikaci.  
  
 Pokud chcete vytvořit vlastní část XML pomocí sady Visual Studio, přidejte novou <xref:Microsoft.Office.Core.CustomXMLPart> k <xref:Microsoft.Office.Core.CustomXMLParts> kolekce v dokumentu. Další informace naleznete v následujících tématech:  
  
-   [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Úprava částí XML bez spuštění aplikace sady Office  
 Můžete přidat nebo upravit vlastní část XML bez spuštění aplikace Excel, PowerPoint nebo Word. To je užitečné, pokud budete chtít pracovat s daty XML v dokumentu na počítači, na kterém není nainstalovaný, například server aplikace Microsoft Office.  
  
 Chcete-li přidat vlastní část XML bez spuštění aplikace Microsoft Office, použijte třídy v sadě SDK Open XML. Tyto třídy jsou navržené pro poskytování přístupu k obsahu Open XML, který je specifický pro dokumenty Office. Například, chcete-li přidat vlastní část XML k Excelovému sešitu, použijete <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metodu <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> objektu. Další informace najdete v tématu [Open XML SDK](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Vlastní části XML svázat ovládací prvky obsahu aplikace Word  
 K elementům ve vlastní část XML lze svázat ovládací prvky obsahu v řešení aplikace Word. Když je vytvořena vazba ovládacího prvku obsahu na vlastní část XML, data ve vlastní část XML se zobrazí v uživatelském rozhraní (UI) obsahu ovládacího prvku. Pokud uživatel upravuje text v ovládacím prvku, se automaticky aktualizuje odpovídající element XML. Podobně pokud se změní hodnot prvků objektu vlastní části XML, ovládací prvky obsahu, které jsou vázány na prvky XML zobrazit nová data. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Viz také:  
 [Schémata XML a data v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Postupy: Přidání vlastních částí XML do dokumentů s použitím doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Ovládací prvky obsahu](../vsto/content-controls.md)   
 [Návod: Vazba ovládacích prvků obsahu s vlastní části XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
