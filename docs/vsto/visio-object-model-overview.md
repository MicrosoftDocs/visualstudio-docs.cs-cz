---
title: Přehled modelu objektů aplikace Visio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 872665a9af220e1b86a3d053254880e3ababa6cd
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671401"
---
# <a name="visio-object-model-overview"></a>Přehled modelu objektů aplikace Visio
  K vývoji řešení pro systém Office pro aplikaci Microsoft Office Visio, můžete pracovat s modelu objektů aplikace Visio. Tento objektový model se skládá z třídy a rozhraní, které jsou k dispozici ve primárního spolupracujícího sestavení pro aplikaci Visio a jsou definovány v `Microsoft.Office.Interop.Visio` oboru názvů.  
  
 Toto téma nabízí stručný přehled modelu objektů aplikace Visio. Informace o provádění úloh v projektech pro systém Office pomocí modelu objektů aplikace Visio naleznete v následujících tématech:  
  
-   [Práce s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md)  
  
-   [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Pochopení modelu objektů aplikace Visio  
 Visio poskytuje mnoho objektů, se kterými můžete pracovat. Tyto objekty jsou uspořádány do hierarchie, která přesně dodržuje uživatelského rozhraní. V horní části hierarchie [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) objektu. Tento objekt představuje aktuální instanci aplikace Visio. `Microsoft.Office.Interop.Visio.Application` Obsahuje objekt `Microsoft.Office.Interop.Visio.Document` a `Microsoft.Office.Interop.Visio.Page` objekty také `Microsoft.Office.Interop.Visio.Documents` a `Microsoft.Office.Interop.Visio.Pages` kolekce. Každá z těchto objektů a kolekcí obsahuje mnoho metod a vlastností, ke kterým může přistupovat k manipulaci a pracovat s ním.  
  
 Další informace najdete v tématu referenční dokumentaci jazyka VBA pro [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document), a [ Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) objekty a také [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) a [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) kolekce.  
  
 Následující části stručně popisují nejvyšší úrovně objektů a jejich vzájemné interakce mezi sebou. Mezi tyto objekty patří následující objekty:  
  
-   Objekt aplikace  
  
-   Objekt dokumentu  
  
-   objekt stránky  
  
### <a name="application-object"></a>Objekt aplikace  
 Objekt Microsoft.Office.Interop.Visio.Application představuje aplikaci Visio a je nadřazeného člena všechny ostatní objekty. Jeho členy obvykle platí pro Visio jako celek. Můžete použít vlastnosti a metody Microsoft.Office.Interop.Visio.Application a `Microsoft.Office.Interop.Visio.ApplicationSettings` objekty k řízení prostředí aplikace Visio.  
  
 V doplňku VSTO projektů, můžete přístup k objektu Microsoft.Office.Interop.Visio.Application pomocí `Application` pole `ThisAddIn` třídy. Další informace najdete v tématu [programování doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Objekt dokumentu  
 Objekt Microsoft.Office.Interop.Visio.Document je programovací Visia. Představuje kreslení, vzorníku nebo soubor šablony. Při otevírání dokumentů aplikace Visio nebo vytvořit nový dokument, vytvořit nový objekt Microsoft.Office.Interop.Visio.Document, která je přidána do kolekce Microsoft.Office.Interop.Visio.Documents Microsoft.Office.Interop.Visio.Application objektu .  
  
 Dokument, který má fokus se nazývá aktivní dokument. Je reprezentován `Microsoft.Office.Interop.Visio.Application.ActiveDocument` vlastnost Microsoft.Office.Interop.Visio.Application objektu.  
  
### <a name="page-object"></a>objekt stránky  
 Objekt Microsoft.Office.Interop.Visio.Page představuje oblasti pro kreslení popředí nebo pozadí stránky. Můžete použít `Microsoft.Office.Interop.Visio.Page.Background` a určí, zda je stránka popředí nebo pozadí stránky.  
  
 K vytvoření tvarů, použijete metody, které patří `Microsoft.Office.Interop.Visio.Page.DrawSpline` a `Microsoft.Office.Interop.Visio.Page.DrawOval` metody. Kromě toho můžete načíst hlavních serverů z vzorníky a umístit obrazce na stránku s použitím `Microsoft.Office.Interop.Visio.Page.Drop` nebo `Microsoft.Office.Interop.Visio.Page.DropMany` metody.  
  
## <a name="use-the-visio-object-model-documentation"></a>Použijte dokumentaci modelu objektů aplikace Visio  
 Podrobnější informace o modelu objektů aplikace Visio najdete referenční dokumentace objektového modelu VBA Visia. Referenční dokumentace objektového modelu VBA dokumenty modelu objektů aplikace Visio, protože je vystavena do jazyka Visual Basic pro kód Applications (VBA). Další informace najdete v tématu [referenční dokumentace objektového modelu Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v aplikaci Visio primární definiční sestavení (PIA). Například `Document` objektů v referenční dokumentace objektového modelu VBA odpovídá typu Microsoft.Office.Interop.Visio.Document ve Visiu PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C# Pokud chcete použít v projektu doplňku VSTO pro Visio, který vytvoříte pomocí Visual Studio.  
  
> [!NOTE]  
>  V současné době neexistuje žádná referenční dokumentace pro Visio primární definiční sestavení.  
  
 Související ukázky a další nástroje pro vytváření řešení pro aplikaci Visio, naleznete v tématu [sada Visio 2010](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Další typy v sestavení primární spolupráce  
 Najít typy v sestavení primární spolupráce, které nejsou viditelné pro jazyk VBA kvůli rozdílům implementace. VBA poskytuje pohled Visio – objektový model, který obsahuje pouze objekty a členy, které můžete použít přímo. Primární spolupracující sestavení vystavit stejného modelu objektu, ale také zahrnují další rozhraní, třídy a členy, které se přeloží objekty v objektovém modelu COM pro spravovaný kód. Tyto další položky nejsou určeny k použití přímo ve vašem kódu.  
  
 Další informace najdete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](http://go.microsoft.com/fwlink/?LinkId=189592) a [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Viz také:  
 [Řešení pro aplikaci Visio](../vsto/visio-solutions.md)   
 [Práce s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md)   
 [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)  
  
  