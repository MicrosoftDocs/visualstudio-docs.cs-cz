---
title: Přehled modelu objektů aplikace Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88695511d22e38262dc969d66e469441c9c3ac47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985484"
---
# <a name="visio-object-model-overview"></a>Přehled modelu objektů aplikace Visio
  Pro vývoj řešení Office pro systém Microsoft Office Visio můžete pracovat s modelem objektu aplikace Visio. Tento objektový model se skládá z tříd a rozhraní, která jsou k dispozici v primárním sestavení vzájemné spolupráce pro aplikaci Visio a jsou definována v `Microsoft.Office.Interop.Visio` oboru názvů.

 Toto téma poskytuje stručný přehled modelu objektu aplikace Visio. Informace o použití objektového modelu aplikace Visio k provádění úloh v projektech systému Office naleznete v následujících tématech:

- [Práce s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md)

- [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Principy modelu objektu aplikace Visio
 Visio poskytuje mnoho objektů, se kterými můžete pracovat. Tyto objekty jsou uspořádány v hierarchii, která úzce odpovídá uživatelskému rozhraní. V horní části hierarchie je objekt [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application) . Tento objekt představuje aktuální instanci aplikace Visio. `Microsoft.Office.Interop.Visio.Application`Objekt obsahuje `Microsoft.Office.Interop.Visio.Document` objekty a a `Microsoft.Office.Interop.Visio.Page` také `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` kolekce a. Každý z těchto objektů a kolekcí má mnoho metod a vlastností, ke kterým můžete přistupovat a pracovat s nimi.

 Další informace najdete v referenční dokumentaci k jazyku VBA pro [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)a [Microsoft. Office. Interop. Visio. Pages](/office/vba/api/Visio.Page) a také [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) a [Microsoft. Office. Interop. Visio. Pages](/office/vba/api/Visio.Pages) .

 Následující části stručně popisují objekty nejvyšší úrovně a jejich vzájemné interakce. Mezi tyto objekty patří následující objekty:

- Objekt aplikace

- Objekt dokumentu

- objekt stránky

### <a name="application-object"></a>Objekt aplikace
 Objekt Microsoft. Office. Interop. Visio. Application reprezentuje aplikaci Visio a je nadřazeným prvkem všech ostatních objektů. Její členové se obvykle vztahují na aplikaci Visio jako celek. Pomocí vlastností a metod rozhraní Microsoft. Office. Interop. Visio. Application a `Microsoft.Office.Interop.Visio.ApplicationSettings` objektů můžete řídit prostředí aplikace Visio.

 V projektech doplňku VSTO můžete získat přístup k objektu Microsoft. Office. Interop. Visio. Application pomocí `Application` pole `ThisAddIn` třídy. Další informace najdete v tématu [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Objekt dokumentu
 Objekt Microsoft.Office.Interop.Visio.Document je z centrálního programování pro aplikace Visio. Představuje výkres, vzorník nebo soubor šablony. Když otevřete dokument Visia nebo vytvoříte nový dokument, vytvoříte nový objekt Microsoft.Office.Interop.Visio.Document, který se přidá do kolekce Microsoft.Office.Interop.Visio.Documents kolekce objektu Microsoft. Office. Interop. Visio. Application.

 Dokument, který má fokus, se nazývá aktivní dokument. Je reprezentován `Microsoft.Office.Interop.Visio.Application.ActiveDocument` vlastností objektu Microsoft. Office. Interop. Visio. Application.

### <a name="page-object"></a>objekt stránky
 Objekt Microsoft. Office. Interop. Visio. Page představuje oblast vykreslování stránky popředí nebo pozadí stránky. Vlastnost lze použít `Microsoft.Office.Interop.Visio.Page.Background` k určení, zda je stránka stránkou popředí nebo pozadí.

 Chcete-li vytvořit obrazce, můžete použít metody, které `Microsoft.Office.Interop.Visio.Page.DrawSpline` obsahují `Microsoft.Office.Interop.Visio.Page.DrawOval` metody a. Kromě toho můžete načíst předlohy ze vzorníků a umístit obrazce na stránku pomocí `Microsoft.Office.Interop.Visio.Page.Drop` `Microsoft.Office.Interop.Visio.Page.DropMany` metod nebo.

## <a name="use-the-visio-object-model-documentation"></a>Použití dokumentace modelu objektu aplikace Visio
 Úplné informace o objektovém modelu aplikace Visio najdete v referenčních informacích k objektovému modelu aplikace Visio VBA. Model objektu VBA odkazuje na dokument model objektu aplikace Visio, protože je vystavený pro jazyk Visual Basic for Application kód (VBA). Další informace najdete v tématu [referenční informace o objektovém modelu aplikace Visio](/office/vba/api/overview/visio/object-model).

 Všechny objekty a členy v odkazu modelu objektu VBA odpovídají typům a členům v primárním sestavení Interop (PIA) aplikace Visio. Například `Document` objekt v odkazu modelu objektu VBA odpovídá typu Microsoft.Office.Interop.Visio.Document v PIA aplikace Visio. I když odkaz na objektový model VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu doplňku aplikace Visio VSTO, který vytvoříte pomocí sady Visual Studio.

> [!NOTE]
> V současné době neexistuje žádná referenční dokumentace pro primární definiční sestavení aplikace Visio.

 Související ukázky kódu a další nástroje pro vytváření řešení pro aplikace Visio najdete v tématu [Visio 2010 Software Development Kit](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Další typy v primárních sestaveních vzájemné spolupráce
 Můžete najít typy v primárních sestaveních spolupráce, která nejsou viditelná pro VBA z důvodu rozdílů implementace. Jazyk VBA poskytuje zobrazení modelu objektu aplikace Visio, který obsahuje pouze objekty a členy, které lze použít přímo. Primární spolupracující sestavení zveřejňují stejný objektový model, ale také obsahují další rozhraní, třídy a členy, které převádějí objekty v modelu objektu COM do spravovaného kódu. Tyto další položky nejsou určeny pro použití přímo v kódu.

 Další informace naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních spolupráce sady Office a v](/previous-versions/office/office-12/ms247299(v=office.12)) [primárních sestaveních spolupráce sady Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Práce s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md)
- [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)
