---
title: Sešit obsahuje ovládací prvky ActiveX, které nelze načíst.
titleSuffix: ''
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
ms.openlocfilehash: 09182fb354ad3ae8937b66952a0acd376d54fe0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584448"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Sešit obsahuje ovládací prvky ActiveX, které nelze načíst.

  Chyba "sešit použitý k vytvoření tohoto projektu obsahuje ovládací prvky ActiveX, které Návrhář nemůže načíst", se zobrazí, když přidáte ovládací prvek do dokumentu aplikace Word nebo excelový list programově, uložíte dokument nebo sešit a pak vytvoříte nové řešení na úrovni dokumentu na základě dokumentu nebo sešitu.

 Informace, které popisují spravovaný typ ovládacího prvku, nejsou uloženy spolu s dokumentem nebo sešitem. Když vytvoříte nové řešení založené na tomto dokumentu nebo sešitu, Visual Studio nemá dostatek informací pro načtení ovládacího prvku v Návrháři položky hostitele.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Otevřete dokument nebo sešit.

2. Odeberte ovládací prvky, které byly přidány v době běhu. To můžete provést tak, že je vyberete v dokumentu nebo v sešitu a stisknete klávesu **Delete** .

3. Vytvořte řešení na úrovni dokumentu na základě dokumentu nebo sešitu.

## <a name="see-also"></a>Viz také
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
