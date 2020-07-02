---
title: Sešit použitý k vytvoření tohoto projektu obsahuje ovládací prvky ActiveX, které návrhář nemůže načíst.
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537342"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Sešit použitý k vytvoření tohoto projektu obsahuje ovládací prvky ActiveX, které návrhář nemůže načíst.
  Tato chyba se zobrazí, když přidáte ovládací prvek do dokumentu aplikace Word nebo excelový list programově, uložíte dokument nebo sešit a pak vytvoříte nové řešení na úrovni dokumentu na základě dokumentu nebo sešitu.

 Informace, které popisují spravovaný typ ovládacího prvku, nejsou uloženy spolu s dokumentem nebo sešitem. Když vytvoříte nové řešení založené na tomto dokumentu nebo sešitu, Visual Studio nemá dostatek informací pro načtení ovládacího prvku v Návrháři položky hostitele.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Otevřete dokument nebo sešit.

2. Odeberte ovládací prvky, které byly přidány v době běhu. To můžete provést tak, že je vyberete v dokumentu nebo v sešitu a stisknete klávesu **Delete** .

3. Vytvořte řešení na úrovni dokumentu na základě dokumentu nebo sešitu.

## <a name="see-also"></a>Viz také:
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
