---
title: 'Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu'
description: Přečtěte si, jak programově vytvořit nový dokument Microsoft Visia Drawing a přidat ho do kolekce dokumentů otevřených dokumentů Visia.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825313"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu
  Když vytvoříte nový dokument systém Microsoft Office Visio Drawing, přidáte ho do `Microsoft.Office.Interop.Visio.Documents` kolekce otevřených dokumentů Visia. V důsledku toho `Microsoft.Office.Interop.Visio.Documents.Add` Metoda vytvoří nový dokument pro kreslení aplikace Visio. Další informace najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Documents. Přidat](/office/vba/api/Visio.Documents.Add) metodu.

## <a name="create-new-blank-documents"></a>Vytvoření nových prázdných dokumentů

### <a name="to-create-a-new-document"></a>Vytvoření nového dokumentu

- Použijte `Microsoft.Office.Interop.Visio.Documents.Add` metodu k vytvoření nového prázdného dokumentu, který není založen na šabloně.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Vytváření dokumentů zkopírovaných z existujících dokumentů
 `Microsoft.Office.Interop.Visio.Documents.Add`Metoda může vytvořit nový dokument, který je kopií existujícího dokumentu aplikace Visio. Je nutné, abyste zadali název souboru a plně kvalifikovanou cestu k diagramu.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Vytvoření nového dokumentu, který se zkopíruje z existujícího dokumentu

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.Add` metodu a zadejte cestu k diagramu Visia.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Vytváření vzorníků zkopírovaných z existujících vzorníků
 [Microsoft.Office.Interop.Visio.Documents. Metoda Add](/office/vba/api/Visio.Documents.Add) může vytvořit nový vzorník, který je kopií existujícího vzorníku aplikace Visio. Je nutné, abyste zadali název souboru a plně kvalifikovanou cestu vzorníku.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Vytvoření nového vzorníku, který se zkopíruje z existujícího vzorníku

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.Add` metodu a zadejte cestu k vzorníku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Vytváření dokumentů založených na existujících šablonách
 `Microsoft.Office.Interop.Visio.Documents.Add`Metoda může vytvořit nový dokument (soubor *. vsd* ), který je založen na existující šabloně aplikace Visio (soubor *. vst* ). Tato metoda zkopíruje vzorníky, styly a nastavení, které jsou součástí pracovního prostoru šablony. Je nutné, abyste zadali název souboru a plně kvalifikovanou cestu k šabloně.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Vytvoření nového dokumentu, který je založen na stávající šabloně

- Zavolejte `Microsoft.Office.Interop.Visio.Documents.Add` metodu a zadejte cestu k šabloně.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu vyžaduje následující:

- Dokument aplikace Visio s názvem `myDrawing.vsd` musí být umístěn v adresáři s názvem `Test` ve složce *dokumenty* (pro systém Windows XP a starší) nebo ve složce *dokumenty* (pro systém Windows Vista).

- Dokument aplikace Visio s názvem `myStencil.vss` musí být umístěn v adresáři s názvem `Test` ve složce *dokumenty* (pro systém Windows XP a starší) nebo ve složce *dokumenty* (pro systém Windows Vista).

- Dokument aplikace Visio s názvem `myTemplate.vst` musí být umístěn v adresáři s názvem `Test` ve složce *dokumenty* (pro systém Windows XP a starší) nebo ve složce *dokumenty* (pro systém Windows Vista).

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)
- [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)
- [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)
- [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)
