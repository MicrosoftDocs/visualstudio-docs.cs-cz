---
title: Python v výukovém kroku Visual Studia 6, práce s Gitem
titleSuffix: ''
description: Krok 6 základního návodu Pythonu v sadě Visual Studio, který zahrnuje funkce související s Gitem visual studia.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72289716"
---
# <a name="step-6-work-with-git"></a>Krok 6: Práce s Gitem

**Předchozí krok: [Instalace balíčků a správa prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio poskytuje přímou integraci s místními úložišti Git a vzdálenými úložišti ve službách, jako je GitHub a Azure Repos. Integrace zahrnuje klonování úložiště, potvrzení změn a správu větví.

Tento článek obsahuje základní přehled vytvoření místního úložiště Git pro existující projekt a seznámení se s některými funkcemi souvisejícími s Git sady Visual Studio.

1. Při otevření projektu v sadě Visual Studio, například projektu z [předchozího kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), klepněte pravým tlačítkem myši na řešení a vyberte **přidat řešení do správy zdrojového kódu**. Visual Studio vytvoří místní úložiště Git, které obsahuje kód projektu.

1. Když Visual Studio zjistí, že projekt je spravován v úložišti Git ovládací prvky související s Git se zobrazí v pravém dolním rohu okna Sady Visual Studio. Ovládací prvky zobrazují čekající potvrzení, změny, název úložiště a větev. Najeďte nad ovládacími prvky, abyste viděli další informace.

    ![Další informace se zobrazí při najetí na ovládací prvek Git v okně Sady Visual Studio](media/working-with-git-01.png)

1. Když vytvoříte nové úložiště nebo vyberete některý z ovládacích prvků Git, Visual Studio otevře okno **Průzkumníka týmu.** (Okno můžete kdykoli otevřít pomocí příkazu nabídky **Zobrazit** > **průzkumníka týmu.)** Okno má tři hlavní podokna, mezi kterými přepnete pomocí rozevíracího okna v záhlaví **Průzkumníka týmu.** Podokno **Synchronizace,** které poskytuje operace publikování, se zobrazí také při výběru ovládacího prvku **Push** (ikona šipky nahoru):

    ![Průzkumník týmu v sadě Visual Studio po vytvoření místního úložiště](media/working-with-git-02.png)

1. Vyberte **Změny** (nebo ovládací prvek Git s ikonou tužky), abyste zkontrolovali nepotvrzené změny a v případě potřeby je potvrdíte.

    ![Průzkumník týmu v sadě Visual Studio zobrazující nepotvrzené změny](media/working-with-git-03.png)

    Poklepáním na soubor v seznamu **Změny** otevřete rozdílové zobrazení tohoto souboru:

    ![Rozdílové zobrazení změn souboru](media/working-with-git-05.png)

1. Vyberte **Větve** (nebo ovládací prvek Git s názvem větve), chcete-li prozkoumat větve a provést operace sloučení a rebase:

    ![Průzkumník týmu v sadě Visual Studio zobrazující větve](media/working-with-git-04.png)

1. Výběrem ovládacího prvku Git s názvem úložiště **(CosineWave** na předchozím obrázku) **průzkumník týmu** zobrazuje rozhraní **Connect,** pomocí kterého můžete rychle přepnout do jiného úložiště úplně.

1. Při použití místního úložiště, potvrzené změny přejít přímo do úložiště. Pokud jste připojeni ke vzdálenému úložišti, vyberte rozevírací záhlaví v **Průzkumníkovi týmu**, zvolte **Synchronizovat,** chcete-li přepnout do části **Synchronizace,** a pracujte s příkazy **vyžádat** a **načíst,** které jsou tam zobrazeny.

## <a name="go-deeper"></a>Jděte hlouběji

Krátký návod k vytvoření projektu ze vzdáleného úložiště Git najdete v [tématu Úvodní příručka: Klonování úložiště kódu Pythonu v sadě Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Mnohem komplexnější kurz, včetně zpracování konfliktů sloučení, revize kódu s žádostmi o přijetí změn vyžádat, rebasing a cherry-picking změny mezi větvemi, najdete [v tématu Začínáme s Git a Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Výuková recenze

Blahopřejeme k dokončení tohoto kurzu o Pythonu ve Visual Studiu. V tomto kurzu jste se naučili:

- Vytvořte projekty a zobrazte obsah projektu.
- Použijte editor kódu a spusťte projekt.
- Pomocí **interaktivního** okna můžete vyvinout nový kód a snadno jej zkopírovat do editoru.
- Spusťte dokončený program v ladicím programu sady Visual Studio.
- Nainstalujte balíčky a spravujte prostředí Pythonu.
- Práce s kódem v úložišti Git.

Zde prozkoumejte průvodce koncepty a postupy, včetně následujících článků:

- [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilování](profiling-python-code-in-visual-studio.md)
- [Testování částí](unit-testing-python-in-visual-studio.md)
