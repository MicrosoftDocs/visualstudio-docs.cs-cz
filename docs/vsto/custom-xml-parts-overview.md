---
title: Přehled vlastních částí XML
description: Přečtěte si, jak můžete do dokumentů vkládat data XML pro některé aplikace systém Microsoft Office. Při vložení dat XML do dokumentu se data nazývají vlastní část XML.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7998f2a47edd85a65b1e81dd45a046de80d0cdb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844124"
---
# <a name="custom-xml-parts-overview"></a>Přehled vlastních částí XML
  Data XML můžete vložit do dokumentů pro některé aplikace systém Microsoft Office. Při vložení dat XML do dokumentu se data nazývají *vlastní část XML*.

 Vlastní části XML můžete vytvořit a upravit v dokumentu pomocí doplňku VSTO nebo řešení na úrovni dokumentu v aplikaci Visual Studio. Nemusíte spouštět aplikaci systém Microsoft Office, abyste mohli vytvářet a upravovat vlastní části XML.

 **Platí pro:** Informace v tomto tématu se vztahují na projekty na úrovni dokumentu a projekty doplňku VSTO v Excelu, PowerPointu a Wordu. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Visual Studio také umožňuje ukládat datové objekty do mezipaměti v přizpůsobení na úrovni dokumentu. Tato funkce se liší od vlastních částí XML, i když existují nějaká podobnosti. Další informace najdete v tématu [data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Principy vlastních částí XML
 Vlastní části XML byly představeny v 2007 systém Microsoft Office systému spolu s otevřenými formáty XML. Tyto formáty zahrnují nové formáty souborů založené na jazyce XML pro aplikace Excel, PowerPoint a Word (například *. xlsx*, *. pptx* a *. docx*). Dokumenty v těchto formátech se skládají ze souborů XML (také názvů *částí XML*), které jsou uspořádány do složek v archivu zip. Většina částí XML je vestavěnými součástmi, které usnadňují definování struktury a stavu dokumentu. Dokumenty však mohou obsahovat také vlastní části XML, které lze použít k uložení libovolných dat XML do dokumentů.

 Formáty souborů XML umožňují aplikacím pracovat s dokumenty způsobem, který není možné ve starších binárních formátech souborů (například *. xls*, *. ppt* a *. doc*). Všechny aplikace, které můžou číst archivy ZIP, můžou kontrolovat a upravovat obsah dokumentů, i když systém Microsoft Office není nainstalovaná.

 Další informace o struktuře Open XML a vlastních částí XML naleznete v následujících článcích:

- [Představení formátů souborů XML sady Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Postupy: manipulace s dokumenty Open XML formats](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Návod: formát XML pro Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Vytváření dokumentů aplikace Word 2007 pomocí formátů Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Aplikace Excel, Word a PowerPoint také umožňují používat vlastní části XML v dokumentech, které jsou uloženy v binárních formátech souborů. Pokud je však dokument uložen v binárním formátu, nebudete moci přidat ani upravit vlastní části XML bez spuštění aplikace systém Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Vytvoření a úprava vlastních částí XML
 Vlastní části XML můžete vytvořit nebo upravit, pokud je dokument otevřený v aplikaci Office nebo když je dokument uzavřený, i když systém Microsoft Office není nainstalovaný.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Úprava částí XML v době, kdy běží aplikace Office
 S vlastními částmi XML můžete pracovat pomocí přizpůsobení na úrovni dokumentu nebo doplňku VSTO. Pokud používáte přizpůsobení na úrovni dokumentu, obvykle budete pracovat s vlastními částmi XML, které jsou v přizpůsobeném dokumentu. Pokud používáte doplněk VSTO, můžete v jakémkoli dokumentu otevřeném v aplikaci vytvořit nebo upravit vlastní části XML.

 Chcete-li vytvořit vlastní část XML pomocí sady Visual Studio, přidejte novou <xref:Microsoft.Office.Core.CustomXMLPart> do <xref:Microsoft.Office.Core.CustomXMLParts> kolekce v dokumentu. Další informace najdete v následujících tématech:

- [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Postupy: Přidání vlastních částí XML do dokumentů pomocí doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Úprava částí XML bez spuštění aplikace Office
 Vlastní část XML můžete přidat nebo upravit bez spouštění Excelu, PowerPointu nebo Wordu. To je užitečné, pokud chcete pracovat s daty XML v dokumentu na počítači, který nemá nainstalované aplikace systém Microsoft Office, jako je například server.

 Chcete-li přidat vlastní část XML bez spuštění systém Microsoft Office, použijte třídy v Open XML SDK. Tyto třídy jsou navržené tak, aby poskytovaly přístup k otevřenému obsahu XML, který je specifický pro dokumenty Office. Chcete-li například přidat vlastní část XML do sešitu aplikace Excel, použijte <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> metodu <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> objektu. Další informace najdete v tématu [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Svázání vlastních částí XML s ovládacími prvky obsahu Wordu
 Ovládací prvky obsahu můžete navazovat v řešení aplikace Word na prvky ve vlastní části XML. Když je ovládací prvek obsahu vázaný na vlastní část XML, data v části vlastní XML se zobrazí v uživatelském rozhraní (UI) ovládacího prvku obsahu. Pokud uživatel upraví text v ovládacím prvku, odpovídající prvek XML je automaticky aktualizován. Podobně, pokud se změní hodnoty prvků ve vlastních částech XML, ovládací prvky obsahu, které jsou svázány s elementy XML, zobrazí nová data. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

## <a name="see-also"></a>Viz také
- [Schémata XML a data v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Postupy: Přidání vlastních částí XML do přizpůsobení na úrovni dokumentu](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Postupy: Přidání vlastních částí XML do dokumentů pomocí doplňků VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Ovládací prvky obsahu](../vsto/content-controls.md)
- [Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
