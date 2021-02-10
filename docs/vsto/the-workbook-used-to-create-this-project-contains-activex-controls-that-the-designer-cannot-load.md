---
title: Sešit obsahuje ovládací prvky ActiveX, které nelze načíst.
description: Zjistěte, jak můžete vyřešit chybu, ke které dochází, když sešit obsahuje ovládací prvky ActiveX, které se nedají načíst.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4c8039fc2a5df197446873f0b2efef82d9a5f662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940784"
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
