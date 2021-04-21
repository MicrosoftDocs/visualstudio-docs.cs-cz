---
title: Volitelné parametry v řešeních pro systém Office
description: Zjistěte, jak není nutné předávat hodnotu pro volitelné parametry, protože výchozí hodnoty jsou automaticky použity pro každý chybějící parametr.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c95842ac2c6d77a2312ac5c4c197ba22ed2020e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825417"
---
# <a name="optional-parameters-in-office-solutions"></a>Volitelné parametry v řešeních pro systém Office
  Mnohé z metod v objektových modelech systém Microsoft Office aplikací přijímají volitelné parametry. Použijete-li Visual Basic pro vývoj řešení sady Office v sadě Visual Studio, není nutné předávat hodnotu pro volitelné parametry, protože výchozí hodnoty jsou automaticky použity pro každý chybějící parametr. Ve většině případů můžete také vynechat volitelné parametry v projektech Visual C#. Nemůžete však vynechat volitelné parametry **ref** `ThisDocument` třídy v projektech aplikace Word na úrovni dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Další informace o práci s nepovinnými parametry v jazyce Visual C# a Visual Basicch projektech naleznete v tématu [pojmenované a volitelné argumenty &#40;C&#35; programování průvodce&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) a [volitelné parametry &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> V dřívějších verzích sady Visual Studio je nutné předat hodnotu pro každý volitelný parametr v projektech Visual C#. Pro usnadnění mají tyto projekty globální proměnnou s názvem `missing` , která může být předána volitelnému parametru, pokud chcete použít výchozí hodnotu parametru. Projekty Visual C# pro Office v sadě Visual Studio stále obsahují `missing` proměnnou, ale obvykle je nemusíte používat při vývoji řešení pro systém Office v nástroji [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] s výjimkou toho, že voláte metody s volitelnými parametry **ref** ve `ThisDocument` třídě v projektech na úrovni dokumentu pro aplikaci Word.

## <a name="example-in-excel"></a>Příklad v Excelu
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Metoda má mnoho volitelných parametrů. Můžete zadat hodnoty pro některé parametry a přijmout výchozí hodnotu ostatních, jak je znázorněno v následujícím příkladu kódu. Tento příklad vyžaduje projekt na úrovni dokumentu s třídou listu s názvem `Sheet1` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Příklad ve Wordu
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>Metoda má mnoho volitelných parametrů. Můžete zadat hodnoty pro některé parametry a přijmout výchozí hodnotu ostatních, jak je znázorněno v následujícím příkladu kódu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Použití volitelných parametrů metod ve třídě ThisDocument v jazyce Visual C# projekty na úrovni dokumentu pro Word
 Objektový model aplikace Word obsahuje mnoho metod s nepovinnými parametry **ref** , které přijímají <xref:System.Object> hodnoty. Nemůžete však vynechat volitelné parametry **ref** metod generované `ThisDocument` třídy v projektech Visual C# na úrovni dokumentu pro aplikaci Word. Visual C# umožňuje vynechat volitelné parametry **ref** pouze pro metody rozhraní, nikoli třídy. Například následující příklad kódu není zkompilován, protože nelze vynechat volitelné parametry **ref** <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody `ThisDocument` třídy.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 Při volání metod `ThisDocument` třídy, postupujte podle těchto pokynů:

- Chcete-li přijmout výchozí hodnotu volitelného parametru **ref** , předejte `missing` proměnnou do parametru. `missing`Proměnná je automaticky definována v projektech aplikace Visual C# a je přiřazena k hodnotě <xref:System.Type.Missing> ve vygenerovaném kódu projektu.

- Chcete-li zadat vlastní hodnotu pro volitelný parametr **ref** , deklarujte objekt, který je přiřazen k hodnotě, kterou chcete zadat, a pak předejte objekt parametru.

  Následující příklad kódu ukazuje, jak zavolat <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodu zadáním hodnoty pro parametr *ignoreUppercase* a přijetím výchozí hodnoty pro ostatní parametry.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  Chcete-li napsat kód, který vynechává volitelné parametry **ref** metody ve `ThisDocument` třídě, můžete alternativně volat stejnou metodu u <xref:Microsoft.Office.Interop.Word.Document> objektu vráceného <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> vlastností a vynechat parametry z této metody. To lze provést, protože <xref:Microsoft.Office.Interop.Word.Document> je rozhraní, nikoli třída.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Další informace o parametrech typu hodnoty a odkazu naleznete v tématu [Pass argumentů podle hodnoty a odkaz &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pro Visual Basic) a [Pass parameters &#40;C&#35; program průvodce programováním&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Viz také
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
