---
title: Souběžné porovnání Gitu a Team Explorer v aplikaci Visual Studio
titleSuffix: ''
description: Porovnejte a kontrastujte použití nového prostředí Git versus Team Explorer v aplikaci Visual Studio ke správě zdrojového kódu.
ms.date: 04/01/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.openlocfilehash: 6ae09069e021ee9ff5699641bbe8662bf84ad327
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2021
ms.locfileid: "107917803"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Souběžné porovnání Gitu a Team Explorer

V aplikaci Visual Studio 2019 [verze 16,8](/visualstudio/releases/2019/release-notes/)jsme spustili první verzi nového prostředí Git. Toto nové prostředí pomáhá omezit přepínání kontextu pomocí jednoduchých oken **změn Git** , které zahrnuje běžné úlohy Git. Zahrnuje také okno **úložiště Git** na úrovni obrazovky pro pokročilejší operace Git, jako je například Správa větví a procházení úložiště.

Pokud používáte Team Explorer, najdete tady podrobný průvodce, který vysvětluje, jak můžete používat nové prostředí Git.

> [!NOTE]
> Následující část obsahuje velikost snímků obrazovky, která se vejde do sloupců tabulky. Kliknutím na jednotlivé snímky obrazovky zobrazíte větší verzi. (Pokud používáte zařízení s dotykovou obrazovkou, klepněte na jednotlivé snímky obrazovky, abyste si zobrazili větší verzi.)

## <a name="get-started"></a>Začínáme

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Klonování úložiště** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Snímek obrazovky okna připojit pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury klonování úložiště" lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. Otevřete stránku **připojit** . <br> 2. rozbalte položku **Spravovat připojení**. <br> 3. Vyberte **připojit k projektu**. | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Snímek nabídky Git v aplikaci Visual Studio 2019 s překrytím procedury klonovat úložiště" lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. Otevřete nabídku **Git** . <br>2. Vyberte **úložiště klonování**. <br><br> |
|**Přepínání mezi úložišti**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Snímek obrazovky okna připojit pro Team Explorer v aplikaci Visual Studio 2019 s překryvnou překrytím procedury mezi úložišti" lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. Otevřete stránku **připojit** . <br>2. Vyberte úložiště ze seznamu **místních úložišť** . | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Snímek obrazovky místní položky nabídky úložiště v aplikaci Visual Studio 2019 s překrytím procedury naklonování úložiště" lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. Otevřete nabídku **Git** . <br>2. Vyberte úložiště ze seznamu **místních úložišť** .  |
|**Otevřít řešení**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Snímek obrazovky domovského okna pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury otevřít řešení" lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. Otevřete **domovskou** stránku v **Team Explorer**. <br>2. ze seznamu řešení vyberte řešení.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Snímek obrazovky Průzkumník řešení v aplikaci Visual Studio 2019 s překrytím procedury otevřít řešení" lightbox="media/open-solution-new-git-lrg.png":::</p>1. Otevřete stránku **Přepnutí zobrazení** v **Průzkumník řešení**. <br>2. ze seznamu řešení vyberte řešení.  |
|**Přidání řešení do správy zdrojového kódu a vytvoření nového úložiště**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Snímek obrazovky se sadou možností Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury přidat do správy zdrojového kódu – vytvoření procesu úložiště." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. v nabídce **Přidat do zdrojového kódu** vyberte **Git** . <br>2. Vyberte **publikovat**.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Snímek obrazovky s možnostmi Git v aplikaci Visual Studio 2019 s překrytím procedury přidat do zdrojového kódu – vytvořit úložiště" lightbox="media/source-control-new-git-lrg.png":::</p>1. v nabídce **Přidat do zdrojového řádku Správa zdrojového kódu** vyberte **Git** nebo vyberte **Git**  >  **vytvořit úložiště Git** z panelu nabídek nejvyšší úrovně sady Visual Studio. <br>2. Vyberte **vytvořit a vložit**. </p> **Poznámka**: Pokud chcete přidat kód do Azure DevOps, použijte existující možnost Remote. V takovém případě musíte nejdřív vytvořit úložiště Azure DevOps. |
> [!TIP]
> [Nové prostředí Git](git-with-visual-studio.md) by se mělo automaticky připojit ke správnému úložišti Azure DevOps na základě úložiště nebo řešení, které jste otevřeli. Pokud se ale potřebujete ručně připojit k úložišti, můžete to udělat i pomocí Team Explorer. V řádku nabídek sady Visual Studio vyberte **zobrazení**  >  **Team Explorer**  >  **Spravovat připojení**  >  **připojit**.

## <a name="git-changes"></a>Změny Git

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Potvrzení a fáze** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Snímek obrazovky okna změny pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury potvrdit změny a fáze" lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. Zadejte zprávu potvrzení. <br>2. Vyberte **potvrdit vše**. <br>3. Pokud chcete určit konkrétní soubory, klikněte na ně pravým tlačítkem myši a vyberte **fáze**.  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury potvrdit změny a fáze" lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. Zadejte zprávu potvrzení. <br>2. Vyberte **potvrdit vše**. <br>3. Pokud chcete připravit konkrétní soubory, najeďte na ně myší a pak klikněte na **+** ikonu. |
|**Změna potvrzení změn** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Snímek obrazovky okna změny pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury pro změnu potvrzení" lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. klikněte na rozevírací seznam **Akce** . <br>2. Vyberte možnost **změnit předchozí potvrzení změn**. | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury pro změnu potvrzení změn" lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. klikněte na zaškrtávací políčko **změnit** . <br>2. Kliknutím na **potvrdit vše** potvrďte svoje aktualizace.  |
|**Dočasně uložit změnu** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Snímek obrazovky okna změny pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury &quot;ukládání změn&quot;." lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. klikněte na rozevírací seznam **ukládání** . <br>2. Vyberte příslušnou možnost **dočasné ukládání** . | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury pro ukládání změn" lightbox="media/stash-change-new-git-lrg.png":::</p>1. klikněte na rozevírací seznam **potvrdit vše** . <br>2. Vyberte příslušnou možnost **dočasné ukládání** . |

## <a name="synchronization"></a>Synchronizace

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Načtení, vyžádání a vložení změn** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Snímek obrazovky okna synchronizace pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury Fetch, Pull a push" lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. přejděte na stránku **synchronizace** . <br>2. klikněte na síťovou operaci podle vašeho výběru. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury Fetch, Pull a push" lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. v okně **změny Git** Najděte tlačítka načíst, přijmout a vložit. <br>2. klikněte na síťovou operaci podle vašeho výběru.|
|**Zobrazení příchozích a odchozích potvrzení** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Snímek obrazovky okna synchronizace pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury zobrazit příchozí a odchozí potvrzení změn." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. přejděte na stránku **synchronizace** . <br>2. Zobrazte seznamy příchozích a odchozích přenosů. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Snímek obrazovky okna změn Git a okno úložiště Git v aplikaci Visual Studio 2019 s překrytím procedury zobrazit příchozí a odchozí potvrzení změn" lightbox="media/view-commits-new-git-lrg.png":::</p>1. klikněte na odkaz **odchozí/příchozí** v okně **změny Git** . <br>2. na základě ikon v tabulce Graph v horní části okna **úložiště Git** si prohlédněte příchozí a odchozí potvrzení. |

## <a name="branches"></a>Větve

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Vytvoření větve** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Snímek obrazovky okna větví pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury ' vytvořit novou větev '." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. Přejděte do okna **větve** . <br> 2. klikněte na možnost **Nová větev**. | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury vytvořit novou větev" lightbox="media/create-branch-new-git-lrg.png"::: </p>1. v okně **změny Git** klikněte na rozevírací seznam větev. <br>2. klikněte na možnost **Nová větev**. |
|**Získá nejnovější změny ze vzdálené větve.** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Snímek obrazovky okna větví pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury načíst nedávné změny z vzdálené větve." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. přejděte na **stránku větve**. <br>2. Klikněte pravým tlačítkem na vzdálenou větev a vyberte **Sloučit z** nebo **přenést do**.  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury načíst nedávné změny z vzdálené větve" lightbox="media/sync-remote-new-git-lrg.png":::</p>1. klikněte na rozevírací seznam větev. <br>2. na kartě **vzdálené úložiště** klikněte na vzdálenou větev a vyberte **Sloučit do Current Branch** nebo přenést změny **Current Branch na**.  |
|**Správa větví** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Snímek obrazovky okna větví pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury &quot;spravovat větve&quot;." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. Přejděte do okna **větve** . <br>2. Klikněte pravým tlačítkem na větve, které chcete spravovat. <br>3. zobrazení **Historie** větví pro správu potvrzení změn. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="Snímek obrazovky, jak tři možnosti uživatelského rozhraní použít ke správě větví v aplikaci Visual Studio 2019." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. pomocí jednoho z následujících vstupních bodů přejděte do okna úložiště Git: <br><br>a. V nabídce aplikace Visual Studio nejvyšší úrovně vyberte **Git**  >  **Spravovat větve**.<br> b. Vyberte položku **Git změny**  >  **příchozí/odchozí**. <br>c. V nabídce stavového řádku v pravém dolním rohu vyberte **Spravovat větve**.<br> <br> 2. v nabídce **Git**  >  **Spravovat větve** na nejvyšší úrovni proveďte jednu z následujících akcí: <br><br>A. Klikněte pravým tlačítkem na větve.<br>B. Vícenásobný výběr potvrzení, která chcete spravovat. |

## <a name="conflict-resolution"></a>Řešení konfliktů

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Přístup k seznamu souborů s konflikty** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Vzhled snímků obrazovky okna změny a okno vyřešit konflikty pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. Přejděte do okna **vyřešit konflikty** kliknutím na odkaz **konflikty** . <br> 2. k vyřešení konfliktů sloučení použijte seznam **konfliktů** . | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury vyřešit konflikty" lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. Ověřte, že se zobrazí **Probíhající sloučení s konflikty** . <br>2. v části **nesloučené změny** v okně **změn Git** se zobrazí seznam souborů s konflikty sloučení. <br>Vyřešte konflikty. |

## <a name="next-steps"></a>Další kroky

Další informace o novém prostředí Git najdete v části nejnovější video [Začínáme s Git v aplikaci Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc)na YouTube.

## <a name="see-also"></a>Viz také

- [Nové prostředí Git v aplikaci Visual Studio](git-with-visual-studio.md)
- [Začínáme s Git a GitHubem v aplikaci Visual Studio](/learn/modules/visual-studio-github-push/)
- [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)