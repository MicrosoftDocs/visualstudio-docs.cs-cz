---
title: 'Postupy: ochrana listů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí funkce ochrany v aplikaci Microsoft Excel zabránit uživatelům a kódu v úpravách objektů v listu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31c0184cbf8f29db6d33d135cf295f8277b55f2e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827094"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Postupy: ochrana listů prostřednictvím kódu programu
  Funkce Ochrana v aplikaci systém Microsoft Office Excel pomáhá zabránit uživatelům a kódu v úpravách objektů v listu. Ve výchozím nastavení jsou všechny buňky po zapnutí ochrany zamčené.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V přizpůsobení na úrovni dokumentu můžete listy chránit pomocí aplikace Excel Designer. List lze také chránit programově za běhu v jakémkoli typu projektu.

> [!NOTE]
> Do oblastí uzamknutého listu nelze přidat ovládací prvky model Windows Forms.

## <a name="use-the-designer"></a>Použití designeru

### <a name="to-protect-a-worksheet-in-the-designer"></a>Ochrana listu v Návrháři

1. Ve skupině **změny** na kartě **Revize** klikněte na **Zamknout list**.

    Zobrazí se dialogové okno **Zamknout list** . Můžete nastavit heslo a volitelně zadat určité akce, které můžou uživatelé s listem provádět, například formátovat buňky nebo vkládat řádky.

   Uživatelům můžete také dovolit upravovat konkrétní rozsahy v chráněných listech.

### <a name="to-allow-editing-in-specific-ranges"></a>Povolení úprav v určitých rozsahech

1. Ve skupině **změny** na kartě **Revize** klikněte na možnost **dovolit uživatelům upravovat rozsahy**.

     Zobrazí se dialogové okno **Povolení úprav oblastí uživatelům** . Můžete určit rozsahy, které jsou odemčené heslem, a uživatele, kteří můžou upravovat rozsahy bez hesla.

## <a name="use-code-at-run-time"></a>Použít kód v době běhu
 Následující kód nastaví heslo (pomocí proměnné getPasswordFromUser, která obsahuje heslo získané od uživatele) a povoluje pouze řazení.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Ochrana listu pomocí kódu v přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodu listu. V tomto příkladu se předpokládá, že pracujete s listem s názvem `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet27":::

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Ochrana listu pomocí kódu v doplňku VSTO

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> metodu aktivního listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet17":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: odebrání ochrany z listů prostřednictvím kódu programu](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Postupy: Ochrana sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-workbooks.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
