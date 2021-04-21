---
title: Pozdní vazba v řešeních pro systém Office
description: Přečtěte si, jak některé typy v objektových modelech v aplikacích systém Microsoft Office poskytují funkce, které jsou k dispozici prostřednictvím funkcí s pozdní vazbou.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823883"
---
# <a name="late-binding-in-office-solutions"></a>Pozdní vazba v řešeních pro systém Office
  Některé typy v objektových modelech aplikace Office poskytují funkce, které jsou k dispozici prostřednictvím funkcí s pozdní vazbou. Například některé metody a vlastnosti mohou vracet různé typy objektů v závislosti na kontextu aplikace sady Office a některé typy mohou vystavovat různé metody nebo vlastnosti v různých kontextech.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic projekty, kde **Option Strict** je off a Visual C# projekty, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] mohou pracovat přímo s typy, které využívají tyto funkce s pozdní vazbou.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Implicitní a explicitní přetypování vrácených hodnot objektu
 Mnoho metod a vlastností v systém Microsoft Office primární definiční sestavení (PIA) vrací <xref:System.Object> hodnoty, protože mohou vracet několik různých typů objektů. Například <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> vlastnost vrací výjimku <xref:System.Object> , protože vrácená hodnota může být <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> objekt nebo, v závislosti na aktivním listu.

 Pokud metoda nebo vlastnost vrací, je <xref:System.Object> nutné explicitně převést (v Visual Basic) objekt na správný typ v Visual Basic projektů, kde **Option Strict** je on. Nemusíte explicitně přetypování <xref:System.Object> návratových hodnot v projektech Visual Basic, kde **Option Strict** je off.

 Ve většině případů Referenční dokumentace uvádí možné typy návratové hodnoty pro člena, který vrací <xref:System.Object> . Převod nebo přetypování objektu umožňuje technologii IntelliSense pro objekt v editoru kódu.

 Informace o převodu v Visual Basic naleznete v tématu [implicitní a explicitní převody &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) a [funkce CType ](/dotnet/visual-basic/language-reference/functions/ctype-function)&#40;Visual Basic.

### <a name="examples"></a>Příklady
 Následující příklad kódu ukazuje, jak přetypovat objekt na konkrétní typ v Visual Basic projektu, kde **Option Strict** je zapnuto. V tomto typu projektu musíte explicitně přetypovat <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> vlastnost na <xref:Microsoft.Office.Interop.Excel.Range> . Tento příklad vyžaduje excelový projekt na úrovni dokumentu s třídou listu s názvem `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 Následující příklad kódu ukazuje, jak implicitně přetypovat objekt na konkrétní typ v Visual Basic projektu, kde **Option Strict** je off nebo v projektu Visual C#, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . V těchto typech projektů <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> je vlastnost implicitně převedena na <xref:Microsoft.Office.Interop.Excel.Range> . Tento příklad vyžaduje excelový projekt na úrovni dokumentu s třídou listu s názvem `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Přístup ke členům, kteří jsou k dispozici pouze prostřednictvím pozdní vazby
 Některé vlastnosti a metody v Office PIA jsou k dispozici pouze prostřednictvím pozdní vazby. V Visual Basic projekty, kde **Option Strict** je vypnuto nebo v projektech Visual C#, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , můžete použít funkce pozdní vazby v těchto jazycích pro přístup k členům s pozdní vazbou. V Visual Basic projekty, kde je **možnost Option Strict** zapnuta, je nutné k přístupu k těmto členům použít reflexi.

### <a name="examples"></a>Příklady
 Následující příklad kódu ukazuje, jak získat přístup k členům s pozdní vazbou v Visual Basic projektu, kde **Option Strict** je off nebo v projektu Visual C#, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Tento příklad přistupuje k vlastnosti **název** s pozdní vazbou dialogového okna **otevřít** v aplikaci Word. Chcete-li použít tento příklad, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo ve wordovém projektu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Následující příklad kódu ukazuje, jak použít reflexi k provedení stejné úlohy v Visual Basic projektu, kde **Option Strict** je zapnuto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Viz také
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Použijte typ Dynamic &#40;Průvodce programováním&#35; C&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
