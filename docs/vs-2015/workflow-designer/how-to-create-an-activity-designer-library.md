---
title: 'Postupy: Vytvoření knihovny návrháře aktivit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662875"
---
# <a name="how-to-create-an-activity-designer-library"></a>Postupy: Vytvoření knihovny návrháře aktivit
Vlastní návrháři aktivit umožňují vytvořit uživatelské rozhraní pro standardní nebo vlastní aktivitu. Můžete ovládat složitost uživatelského rozhraní a mít možnost vytvořit více než jednoho návrháře aktivit pro aktivitu. Tento scénář umožňuje vytvářet návrháře, které jsou přizpůsobené pro více cílových skupin.

### <a name="to-create-an-activity-designer-library"></a>Vytvoření knihovny návrháře aktivit

1. Spusťte [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt...** pro otevření dialogového okna **Nový projekt** .

3. V podokně **typy projektů** vyberte možnost **pracovní postup** ze seskupení  **C# vizuálů** nebo **Visual Basic** podle preferovaného jazyka.

4. V podokně **šablony** vyberte možnost **Knihovna návrháře aktivit**.

5. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

6. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

7. Do pole **řešení** zadejte popisný název vašeho řešení a pak klikněte na **OK**.

    > [!NOTE]
    > Pokud chcete přidat konzolovou aplikaci pracovního postupu do existujícího řešení, otevřete toto řešení v [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumník řešení**a vyberte **Přidat**a **Nový projekt...** pro otevření dialogového okna **Nový projekt** . Pokračujte postupem uvedeným výše v tomto postupu.

8. Šablona projektu vytvoří definici návrháře aktivit v jazyce XAML a soubor implementace kódu na pozadí ve zdrojovém kódu. @No__t_0 se otevře a zobrazí plátno pro návrháře aktivit.

9. Přetáhněte ovládací prvky [!INCLUDE[avalon1](../includes/avalon1-md.md)] z **panelu nástrojů** na návrhovou plochu, aby je bylo možné použít v Návrháři vlastní aktivity.  Příklad implementace vlastního návrháře aktivit naleznete v tématu [How to: Create a Custom Activity Designer](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Vlastní návrháře aktivit lze použít pro vlastní aktivity i pro výchozí [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]activities.

## <a name="see-also"></a>Viz také
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)