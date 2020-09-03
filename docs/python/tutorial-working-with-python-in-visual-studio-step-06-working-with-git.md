---
title: Python v rámci sady Visual Studio – Krok 6 – práce s Git
titleSuffix: ''
description: Krok 6 základního návodu Pythonu v aplikaci Visual Studio, pokrývající funkce související s Git sady Visual Studio.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72289716"
---
# <a name="step-6-work-with-git"></a>Krok 6: práce s Git

**Předchozí krok: [Instalace balíčků a Správa prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio poskytuje přímou integraci do místních úložišť Git a vzdálených úložišť na služby, jako je GitHub a Azure Repos. Integrace zahrnuje klonování úložiště, potvrzování změn a správu větví.

Tento článek obsahuje základní přehled o vytvoření místního úložiště Git pro existující projekt a familiarizing se s některými funkcemi souvisejícími s Git sady Visual Studio.

1. Otevřete projekt v aplikaci Visual Studio, jako je například projekt z [předchozího kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), klikněte pravým tlačítkem na řešení a vyberte možnost **Přidat řešení do správy zdrojového kódu**. Visual Studio vytvoří místní úložiště Git, které obsahuje váš kód projektu.

1. Když Visual Studio zjistí, že projekt je spravován v úložišti Git ovládací prvky související s Git v pravém dolním rohu okna Visual studia. Ovládací prvky zobrazují nedokončená potvrzení změn, změny, název úložiště a větev. Pokud chcete zobrazit další informace, najeďte myší na ovládací prvky.

    ![Další informace se zobrazí při najetí myší na ovládací prvek Git v okně sady Visual Studio.](media/working-with-git-01.png)

1. Při vytváření nového úložiště nebo výběru některého z ovládacích prvků Git otevře aplikace Visual Studio okno **Team Explorer** . (Okno můžete otevřít kdykoli pomocí **zobrazení**  >  Příkaz **Team Explorer** nabídky) Okno má tři hlavní podokna, která přepínáte pomocí rozevíracího seznamu v hlavičce **Team Explorer** . Podokno **synchronizace** , které poskytuje operace publikování, se zobrazí také po výběru ovládacího prvku **push** (ikona šipky nahoru):

    ![Team Explorer v aplikaci Visual Studio po vytvoření místního úložiště](media/working-with-git-02.png)

1. Vyberte **změny** (nebo ovládací prvek Git s ikonou tužky) a zkontrolujte nepotvrzené změny a potvrďte je v případě potřeby.

    ![Team Explorer v aplikaci Visual Studio zobrazující nepotvrzené změny](media/working-with-git-03.png)

    Dvojím kliknutím na soubor v seznamu **změn** otevřete zobrazení rozdílů pro tento soubor:

    ![Zobrazení rozdílů pro změny v souboru](media/working-with-git-05.png)

1. Vyberte možnost **pobočky** (nebo ovládací prvek Git s názvem větve), abyste prozkoumali větve a prováděli operace sloučení a přenesení změn:

    ![Team Explorer v aplikaci Visual Studio zobrazující větve](media/working-with-git-04.png)

1. Výběr ovládacího prvku Git s názvem úložiště (**CosineWave** na předchozím obrázku) **Team Explorer** zobrazuje rozhraní **připojení** , se kterým můžete úplně rychle přepnout na jiné úložiště.

1. Při použití místního úložiště přejde potvrzené změny přímo do úložiště. Pokud jste připojení ke vzdálenému úložišti, vyberte v **Team Explorer**záhlaví rozevíracího seznamu, zvolte **synchronizovat** , abyste přešli na oddíl **synchronizace** , a pracujte s uvedenými příkazy pro **vyžádání** a **načtení** .

## <a name="go-deeper"></a>Přejít hlouběji

Krátký návod, jak vytvořit projekt ze vzdáleného úložiště Git, najdete v tématu [rychlý Start: klonování úložiště kódu Pythonu v aplikaci Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Pro mnohem komplexnější kurz, včetně zpracování konfliktů při sloučení, revize kódu pomocí žádostí o přijetí změn, reodvození a výběrů mezi větvemi najdete informace v článku [Začínáme s Git a Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Kurz – přezkoumání

Blahopřejeme k dokončení tohoto kurzu na Pythonu v aplikaci Visual Studio. V tomto kurzu jste se naučili, jak:

- Vytváření projektů a zobrazení obsahu projektu.
- Použijte Editor kódu a spusťte projekt.
- **Interaktivní** okno použijte k vývoji nového kódu a ke snadnému zkopírování tohoto kódu do editoru.
- Spusťte dokončený program v ladicím programu sady Visual Studio.
- Nainstalujte balíčky a spravujte prostředí Pythonu.
- Práce s kódem v úložišti Git

Tady si Prozkoumejte koncepty a návody, včetně následujících článků:

- [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilace](profiling-python-code-in-visual-studio.md)
- [Testování jednotek](unit-testing-python-in-visual-studio.md)
