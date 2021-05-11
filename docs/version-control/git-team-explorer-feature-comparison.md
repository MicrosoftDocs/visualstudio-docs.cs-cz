---
title: Porovnání Gitu a Team Explorer v Visual Studio
titleSuffix: ''
description: Porovnejte a porovnejte, jak používat nové prostředí Gitu Team Explorer Visual Studio správy zdrojového kódu.
ms.date: 04/01/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 7f2f8b8bca781e53ab49d34e32a2c0d5ea846ae1
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729334"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Porovnání Gitu a Team Explorer

Spustili jsme první verzi nového prostředí Git v Visual Studio 2019 [verze 16.8](/visualstudio/releases/2019/release-notes/). Toto nové prostředí pomáhá omezit přepínání kontextu pomocí jednoduchého okna **Změn Gitu,** které obsahuje běžné úlohy Gitu. Obsahuje také okno úložiště Git pro celou **obrazovku** pro pokročilejší operace Gitu, jako je správa větví a procházení úložiště.

Pokud jste už tuto Team Explorer, tady je podrobný průvodce, který vysvětluje, jak můžete používat nové prostředí Gitu.

> [!NOTE]
> Následující část obsahuje snímky obrazovky s velikostí, aby se vešly do sloupců tabulky. Kliknutím na každý snímek obrazovky zobrazíte jeho větší verzi. (Pokud používáte zařízení s dotykovou obrazovkou, klepnutím na každý snímek obrazovky zobrazíte jeho větší verzi.)

## <a name="get-started"></a>Začínáme

|         |Team Explorer  |Nové prostředí Gitu |
|---------|---------|---------|
|**Klonování repo** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Snímek obrazovky s oknem Připojit pro Team Explorer v Visual Studio 2019 s překrytím procedury klonování repo" lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. Otevřete **stránku** Připojit. <br> 2. Rozbalte **spravovat připojení.** <br> 3. Vyberte **Připojit k projektu.** | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Snímek obrazovky s nabídkou Git Visual Studio 2019 s překryvem procedury klonování úložiště" lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. Otevřete **nabídku Git.** <br>2. Vyberte **Clone Repository (Klonovat úložiště).** <br><br> |
|**Přepínání mezi úložišti**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Snímek obrazovky okna připojit pro Team Explorer v aplikaci Visual Studio 2019 s překryvnou překrytím procedury mezi úložišti" lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. Otevřete stránku **připojit** . <br>2. Vyberte úložiště ze seznamu **místních úložišť** . | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Snímek obrazovky místní položky nabídky úložiště v aplikaci Visual Studio 2019 s překrytím procedury naklonování úložiště" lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. Otevřete nabídku **Git** . <br>2. Vyberte úložiště ze seznamu **místních úložišť** .  |
|**Otevřít řešení**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Snímek obrazovky domovského okna pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury otevřít řešení" lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. Otevřete **domovskou** stránku v **Team Explorer**. <br>2. ze seznamu řešení vyberte řešení.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Snímek obrazovky Průzkumník řešení v aplikaci Visual Studio 2019 s překrytím procedury otevřít řešení" lightbox="media/open-solution-new-git-lrg.png":::</p>1. Otevřete stránku **Přepnutí zobrazení** v **Průzkumník řešení**. <br>2. ze seznamu řešení vyberte řešení.  |
|**Přidání řešení do správy zdrojového kódu a vytvoření nového úložiště**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Snímek obrazovky se sadou možností Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury přidat do správy zdrojového kódu – vytvoření procesu úložiště." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. v nabídce **Přidat do zdrojového kódu** vyberte **Git** . <br>2. Vyberte **publikovat**.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Snímek obrazovky s možnostmi Git v aplikaci Visual Studio 2019 s překrytím procedury přidat do zdrojového kódu – vytvořit úložiště" lightbox="media/source-control-new-git-lrg.png":::</p>1. v nabídce **Přidat do zdrojového řádku Správa zdrojového kódu** vyberte **Git** nebo vyberte **Git**  >  **vytvořit úložiště Git** z panelu nabídek nejvyšší úrovně sady Visual Studio. <br>2. Vyberte **vytvořit a vložit**. </p> **Poznámka:** Pokud chcete přidat kód do virtuálního počítače, použijte existující Azure DevOps. V takovém případě musíte nejprve vytvořit Azure DevOps úložiště. |
> [!TIP]
> Nové [prostředí Gitu by](git-with-visual-studio.md) se mělo automaticky připojit ke správnému Azure DevOps úložiště na základě úložiště nebo řešení, které jste otevřeli. Pokud se ale potřebujete k repo připojit ručně, můžete k tomu použít Team Explorer. V řádku Visual Studio nabídek vyberte **Zobrazit a**  >  **Team Explorer**  >  **Připojení**  >  **Připojit.**

## <a name="git-changes"></a>Změny Gitu

|         |Team Explorer  |Nové prostředí Gitu |
|---------|---------|---------|
|**Potvrzení a fáze** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Snímek obrazovky s oknem Změny Team Explorer v Visual Studio 2019 s překryvem procedury potvrzení a fáze" lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. Zadejte zprávu potvrzení. <br>2. Vyberte **Commit All (Potvrdit vše).** <br>3. Pokud chcete konkrétní soubory zfektovat, klikněte na ně pravým tlačítkem a vyberte **Stage (Fáze).**  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Snímek obrazovky s oknem Git Changes (Změny Gitu) Visual Studio 2019 a překryvem postupu &quot;commit and stage&quot; (potvrzení a fáze)" lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. Zadejte zprávu potvrzení. <br>2. Vyberte **Commit All (Potvrdit vše).** <br>3. Pokud chcete určité soubory zfektovat, najeďte myší na ně a potom klikněte na **+** ikonu " ". |
|**Změna potvrzení** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Snímek obrazovky s oknem Změny Team Explorer v Visual Studio 2019 s překryvem procedury &quot;pozměnit potvrzení&quot;" lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. Klikněte na **rozevírací** seznam Akce. <br>2. Vyberte **Změnit předchozí potvrzení.** | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury pro změnu potvrzení změn" lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. klikněte na zaškrtávací políčko **změnit** . <br>2. Kliknutím na **potvrdit vše** potvrďte svoje aktualizace.  |
|**Dočasně uložit změnu** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Snímek obrazovky okna změny pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury &quot;ukládání změn&quot;." lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. klikněte na rozevírací seznam **ukládání** . <br>2. Vyberte příslušnou možnost **dočasné ukládání** . | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury pro ukládání změn" lightbox="media/stash-change-new-git-lrg.png":::</p>1. klikněte na rozevírací seznam **potvrdit vše** . <br>2. Vyberte příslušnou možnost **dočasné ukládání** . |

## <a name="synchronization"></a>Synchronizace

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Načtení, vyžádání a vložení změn** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Snímek obrazovky okna synchronizace pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury Fetch, Pull a push" lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. přejděte na stránku **synchronizace** . <br>2. klikněte na síťovou operaci podle vašeho výběru. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury Fetch, Pull a push" lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. v okně **změny Git** Najděte tlačítka načíst, přijmout a vložit. <br>2. klikněte na síťovou operaci podle vašeho výběru.|
|**Zobrazení příchozích a odchozích potvrzení** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Snímek obrazovky okna synchronizace pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury zobrazit příchozí a odchozí potvrzení změn." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. Přejděte na **stránku Synchronizace.** <br>2. Zobrazení příchozích a odchozích seznamů | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Snímek obrazovky s oknem Git Changes (Změny Gitu) a oknem Git Repository (Úložiště Git) v Visual Studio 2019 a překryvem procedury view incoming and outgoing commits (zobrazit příchozí a odchozí potvrzení)" lightbox="media/view-commits-new-git-lrg.png":::</p>1. V okně Git Changes **(Změny** Gitu) klikněte na **odchozí/příchozí** odkaz. <br>2. K zobrazení příchozích a odchozích potvrzení můžete použít ikony v tabulce grafu v horní části okna **úložiště Git.** |

## <a name="branches"></a>Větve

|         |Team Explorer  |Nové prostředí Gitu |
|---------|---------|---------|
|**Vytvoření větve** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Snímek obrazovky okna Větve pro Team Explorer v Visual Studio 2019 s překryvem procedury Pro vytvoření nové větve" lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. Přejděte do **okna Větve.** <br> 2. Klikněte na **Nová větev**. | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Snímek obrazovky s oknem Git Changes (Změny Gitu) Visual Studio 2019 a překryvem procedury &quot;create a new branch&quot; (vytvořit novou větev)" lightbox="media/create-branch-new-git-lrg.png"::: </p>1. V **okně Git Changes (Změny Gitu)** klikněte na rozevírací seznam branch (větev). <br>2. Klikněte na **Nová větev**. |
|**Získání nejnovějších změn ze vzdálené větve** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Snímek obrazovky s oknem Větve pro Team Explorer v Visual Studio 2019 s překryvem procedury Získat nedávné změny ze vzdálené větve" lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. Přejděte na **stránku Větve.** <br>2. Klikněte pravým tlačítkem na vzdálenou větev a vyberte **Sloučit z** nebo **Přebase Na**.  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Snímek obrazovky s oknem Git Changes (Změny Gitu) Visual Studio 2019 a překryvem procedury get recent changes from remote branch (získat nedávné změny ze vzdálené větve)" lightbox="media/sync-remote-new-git-lrg.png":::</p>1. Klikněte na rozevírací seznam větve. <br>2. Na kartě **Vzdálená připojení** klikněte na vzdálenou větev a vyberte Sloučit do Current Branch **nebo** **Rebase Current Branch na**.  |
|**Správa větví** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Snímek obrazovky okna větví pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury &quot;spravovat větve&quot;." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. Přejděte do okna **větve** . <br>2. Klikněte pravým tlačítkem na větve, které chcete spravovat. <br>3. zobrazení **Historie** větví pro správu potvrzení změn. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="Snímek obrazovky, jak tři možnosti uživatelského rozhraní použít ke správě větví v aplikaci Visual Studio 2019." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. pomocí jednoho z následujících vstupních bodů přejděte do okna úložiště Git: <br><br>a. V nabídce aplikace Visual Studio nejvyšší úrovně vyberte **Git**  >  **Spravovat větve**.<br> b. Vyberte položku **Git změny**  >  **příchozí/odchozí**. <br>c. V nabídce stavového řádku v pravém dolním rohu vyberte **Spravovat větve**.<br> <br> 2. v nabídce **Git**  >  **Spravovat větve** na nejvyšší úrovni proveďte jednu z následujících akcí: <br><br>A. Klikněte pravým tlačítkem na větve.<br>B. Vícenásobný výběr potvrzení, která chcete spravovat. |

## <a name="conflict-resolution"></a>Řešení konfliktů

|         |Team Explorer  |Nové prostředí Git |
|---------|---------|---------|
|**Přístup k seznamu souborů s konflikty** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Vzhled snímků obrazovky okna změny a okno vyřešit konflikty pro Team Explorer v aplikaci Visual Studio 2019 s překrytím procedury." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. Přejděte do okna **vyřešit konflikty** kliknutím na odkaz **konflikty** . <br> 2. k vyřešení konfliktů sloučení použijte seznam **konfliktů** . | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Snímek obrazovky s oknem změn Git v aplikaci Visual Studio 2019 s překrytím procedury vyřešit konflikty" lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. Ověřte, že se zobrazí **Probíhající sloučení s konflikty** . <br>2. v části **nesloučené změny** v okně **změn Git** se zobrazí seznam souborů s konflikty sloučení. <br>Vyřešte konflikty. |

## <a name="next-steps"></a>Další kroky

Další informace o novém prostředí Git najdete v nejnovějším videu Začínáme [s Gitem v Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc)na YouTube.

## <a name="see-also"></a>Viz také

- [Nové prostředí Gitu v Visual Studio](git-with-visual-studio.md)
- [Začínáme s Gitem a GitHubem v Visual Studio](/learn/modules/visual-studio-github-push/)
- [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)