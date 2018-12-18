---
title: 'Postupy: použití hledání v Návrháři postupu provádění'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ecf4839cec08e9ffb0419aebcff9da145214b117
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943060"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Postupy: použití hledání v Návrháři postupu provádění

Pro usnadnění vytváření rozsáhlejších, složitějších pracovních postupů, můžete vyhledat v Návrháři pracovních postupů pro vyhledání položek podle klíčového slova. Všimněte si, že návrhář nepodporuje nahrazení.

## <a name="quick-find"></a>Rychlé hledání

Rychlé vyhledání najde v Návrháři následující:

-   Vlastnosti <xref:System.Activities.Activity> objekty, <xref:System.Activities.Statements.FlowNode> objekty, <xref:System.Activities.Statements.State> objekty, přechodů a další položky vlastní řízení toku.

-   Proměnné

-   Arguments

-   Výrazy

### <a name="use-quick-find"></a>Použití rychlého hledání

1. Otevřít Návrhář pracovního postupu, stiskněte **Ctrl + F**, nebo vyberte **upravit** > **najít a nahradit** > **rychlé hledání**.

2. Zadejte hledaný termín do **najít** textového pole a klikněte na tlačítko **najít další**.

3. Hledaný termín se nachází v aktuálním pracovním postupu. Zobrazovaný název aktivity se nachází v Návrháři na následujícím obrázku:

   ![Výsledek hledání v Návrháři postupu provádění](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Najít v souborech

Hledání v souborech vyhledává řetězce v soubory pracovního postupu, včetně souborů XAML.

### <a name="use-find-in-files"></a>Používání funkce najít v souborech

1.  V sadě Visual Studio, stiskněte klávesu **Ctrl**+**Shift**+**F**, nebo vyberte **upravit**  >   **Najít a nahradit** > **najít v souborech**.

2.  Zadejte hledaný termín do **najít** textového pole a klikněte na tlačítko **najít všechny**.

3.  Výsledek hledání se zobrazí v **najít výsledek** zobrazení. Dvojitým kliknutím položku výsledek přejde na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.