---
title: 'Postupy: otevírání textových souborů jako sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově otevřít textový soubor jako sešit Microsoft Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f471161a8563718f69f14ea341ab099fbf138d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525533"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Postupy: otevírání textových souborů jako sešitů prostřednictvím kódu programu
  Textový soubor můžete otevřít jako sešit. Musíte předat název textového souboru, který chcete otevřít. Můžete zadat několik volitelných parametrů, například které číslo řádku má začít s analýzou a formát sloupce dat v souboru.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Příklad
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje následující komponenty:

- Textový soubor s oddělovači s oddělovači `Test.txt` , který obsahuje alespoň tři řádky textu.

- Textový soubor `Test.txt` , který bude uložen na jednotce C.

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Postupy: otevírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-workbooks.md)
- [Postupy: vytváření nových sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md)
- [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
