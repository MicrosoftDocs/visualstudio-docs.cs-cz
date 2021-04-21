---
title: 'Postupy: přidávání obrazců do dokumentů aplikace Visio prostřednictvím kódu programu'
description: Naučte se, jak můžete přidat obrazce do systém Microsoft Office dokumentu Visia načtením předloh ze vzorníku a přetažením obrazců na aktivní stránce.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5eabd18ac915e6cc10ff05de3d13d0263fa1eee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828407"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Postupy: přidávání obrazců do dokumentů aplikace Visio prostřednictvím kódu programu
  Systém Microsoft Office do dokumentu aplikace Visio lze přidat tvary načtením předloh ze vzorníku a přetažením obrazců na aktivní stránce.

 Další informace najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Documents. Přidejte](/office/vba/api/Visio.Documents.Add) metodu, vlastnost [Microsoft. Office. Interop. Visio. Application. ActivePage](/office/vba/api/Visio.Application.ActivePage) a metodu [Microsoft. Office. Interop. Visio. Page. drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Přidání obrazců do dokumentu Visia

### <a name="to-add-shapes-to-a-visio-document"></a>Přidání obrazců do dokumentu aplikace Visio

- Když je dokument aktivní, načtěte z kolekce Documents. Masters šablony a přetáhněte je na aktivní dokument. Hlavní stránku můžete načíst pomocí názvu indexu nebo předlohy.

     Následující příklad kódu vytvoří prázdný dokument Visia a pak ho otevře se vzorníkem **základní tvary** s ukotveným. Kód potom načte několik tvarů a obnoví je na aktivní stránce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)
- [Postupy: kopírování a vkládání tvarů v dokumentu aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
