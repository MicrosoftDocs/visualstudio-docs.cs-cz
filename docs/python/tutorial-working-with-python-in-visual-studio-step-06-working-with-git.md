---
title: Python v sadě Visual Studio kurz – krok 6, práce s Gitem
titleSuffix: ''
description: Krok 6 Průvodce základní jazyka Python v sadě Visual Studio, věnovaných funkcím souvisejícím s Git sady Visual Studio.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6c23a1d9835b7b065f24536c89a8f0befb03717c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054473"
---
# <a name="step-6-work-with-git"></a>Krok 6: Práce s Gitem

**Předchozí krok: [nainstalujte balíčky a správa prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio poskytuje přímou integraci se místní úložiště Git a Vzdálená úložiště na služby, jako je GitHub a úložiště Azure. Integrace zahrnuje klonování úložiště, potvrzení změn a správa větví.

Tento článek obsahuje základní přehled vytvořit místní úložiště Git pro existující projekt a seznámení se s některými funkcemi související s Git sady Visual Studio.

1. Otevřít v sadě Visual Studio, jako je například projekt z projektu [předchozího kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), klikněte pravým tlačítkem na řešení a vyberte **přidat řešení do správy zdrojových kódů**. Visual Studio vytvoří místní úložiště Git, který obsahuje projekt kódu.

1. Když Visual Studio zjistí, že projekt je spravovaná v ovládacích prvcích související s Git Git úložiště se zobrazují podél pravém dolním rohu okna nástroje Visual Studio. Ovládací prvky zobrazení čekající na potvrzení změn, změny, názvu úložiště a větve. Najeďte myší ovládací prvky zobrazíte další informace.

    ![Další informace se zobrazí, když najede myší na ovládací prvek Git v okně aplikace Visual Studio](media/working-with-git-01.png)

1. Při vytváření nového úložiště nebo vyberte některý z ovládacích prvků Git, Visual Studio otevře **Team Exploreru** okno. (V každém okamžiku se může otevřít okno **zobrazení** > **Team Exploreru** příkazu nabídky.) Má tři hlavní podoken, které můžete přepínat mezi pomocí rozevíracího seznamu na okno **Team Exploreru** záhlaví. **Synchronizace** podokno, které poskytuje operace pro publikování, také se zobrazí, když vyberete **Push** ovládací prvek (ikonu se šipkou nahoru):

    ![Průzkumník týmových projektů v sadě Visual Studio po vytvoření místního úložiště](media/working-with-git-02.png)

1. Vyberte **změny** (nebo ovládací prvek Git s na ikonu tužky) si nepotvrzené změny a potvrdíte je potřebujete.

    ![Průzkumník týmových projektů v sadě Visual Studio zobrazuje nepotvrzené změny](media/working-with-git-03.png)

    Poklikejte na soubor v **změny** seznamu rozdílové zobrazení pro tento soubor otevřít:

    ![Zobrazení změn se změny do souboru](media/working-with-git-05.png)

1. Vyberte **větví** (nebo ovládacího prvku Git s názvem větev) k prozkoumání větví a provádět operace sloučení a přenášejte změny:

    ![Průzkumník týmových projektů v sadě Visual Studio zobrazuje větví](media/working-with-git-04.png)

1. Výběrem ovládacího prvku Git s názvem úložiště (**CosineWave** v předchozím obrázku), **Team Exploreru** ukazuje **připojit** rozhraní, pomocí kterého můžete rychle přepínat na Další úložiště zcela.

1. Při použití místního úložiště, potvrzené změny přejít přímo do úložiště. Pokud jste připojeni do vzdáleného úložiště, vyberte záhlaví rozevíracího seznamu v **Team Exploreru**, zvolte **synchronizace** přepnout na **synchronizace** části a pracovat s **o přijetí změn** a **načíst** příkazy uvedené existuje.

## <a name="go-deeper"></a>Seznamte se blíž

Krátký návod k vytvoření projektu ze vzdáleného úložiště Git, naleznete v tématu [rychlý start: klonování úložiště kódu v Pythonu v sadě Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Mnohem komplexnější kurz, včetně zpracování konfliktů při sloučení, revize kódu s žádostmi o přijetí změn, probíhá přenesení změn a vybírání změny mezi větvemi, najdete v tématu [Začínáme s Git a úložiště Azure](/azure/devops/repos/git/gitquickstart?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json&view=vsts&tabs=visual-studio).

## <a name="tutorial-review"></a>Kurz revize

Blahopřejeme k dokončení tohoto kurzu o Pythonu v sadě Visual Studio. V tomto kurzu jste zjistili, jak:

- Vytváření projektů a zobrazení obsahu projektu.
- Použití editoru kódu a spuštění projektu.
- Použití **interaktivní** okna k vývoji nový kód a jednoduše zkopírujte tento kód do editoru.
- Dokončené program spusťte v ladicím programu sady Visual Studio.
- Instalovat balíčky a správa prostředí Pythonu.
- Práce s kódem v úložišti Git.

Z tohoto místa prozkoumávají koncepty a Průvodce postupy, včetně následujících článcích:

- [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilace](profiling-python-code-in-visual-studio.md)
- [Testování jednotek](unit-testing-python-in-visual-studio.md)
