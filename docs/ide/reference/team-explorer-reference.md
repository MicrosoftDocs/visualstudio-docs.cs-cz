---
title: Referenční dokumentace Team Explorer
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: douge
ms.openlocfilehash: 85c7e06482a751b896534c81d227dade74ffbcb5
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027497"
---
# <a name="team-explorer-reference"></a>Referenční dokumentace Team Explorer

Tento článek obsahuje odkazy na články Azure DevOps o různých funkcích **Team Exploreru**.

Použití **Team Exploreru** panel nástrojů koordinovat své úsilí kódu s ostatními členy týmu k vývoji projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo projekty. **Team Explorer** propojí aplikaci Visual Studio pro úložiště Git a Githubu, Team Foundation verze ovládacího prvku (TFVC) úložiště a projektech hostovaných ve službě [Azure DevOps služby](/azure/devops/user-guide/what-is-azure-devops-services) nebo na místě [Azure DevOps Server](/tfs/index) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

## <a name="home-page"></a>Domovská stránka

Až [připojit se k projektu](../connect-team-project.md) v **Průzkumník týmových projektů**, budou dostupné v následujících odkazů **projektu** části:

- [Klonování úložiště](/azure/devops/repos/git/clone)
- [Webový portál](/azure/devops/project/navigation/index)
- [Panel úloh](/azure/devops/boards/sprints/task-board)

**Domů** stránka má v závislosti na tom, zda jste připojeni k různým funkcím [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) nebo [Team Foundation verze ovládacího prvku (TFVC)](/azure/devops/repos/tfvc/overview) úložiště.

> [!TIP]
> Porovnání dvou verzí systémů pro správu najdete v tématu [zvolte správné správy verzí pro projekt (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Domů** stránka s Git | **Domů** stránka s TFVC |
| - | - |
| ![Team Explorer Domovská stránka s Git ve službě Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Team Explorer Domovská stránka s TFVC v sadě Visual Studio 2017](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Stránka změn (Git)

Zobrazit [uložení práce s potvrzeními](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Stránku větve (Git)

Zobrazit [vytvoření práce ve větvích](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Stránka žádosti o přijetí změn (Git)

Zobrazit [revize kódu pomocí žádosti o přijetí změn](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Stránka synchronizace (Git)

Zobrazit [aktualizace kódu pomocí načítání a vyžadování](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Stránka značky (Git)

Zobrazit [práci se značkami Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Stránka má práce (TFVC)

Zobrazit [pozastavení/obnovení práce](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) a [revize kódu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Čeká na stránce změny (TFVC)

Zobrazit [Správa nedokončených změn](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [najít sady odložených změn](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets), a [řešení konfliktů](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Stránka Průzkumník správy zdrojového (TFVC)

Zobrazit [Add/zobrazit soubory a složky](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Stránky pracovních položek

**Pracovní položky** stránce vám umožňují vidět [pracovní položku](/azure/devops/boards/work-items/about-work-items) dotazy. Další informace:

- [Přidání pracovních položek](/azure/devops/boards/backlogs/add-work-items)
- [Použití editoru dotazů k zobrazení a Správa dotazů](/azure/devops/boards/queries/using-queries)
- [Uspořádání složek dotazů a nastavení oprávnění pro dotaz](/azure/devops/boards/queries/set-query-permissions)
- [Otevřít dotaz v aplikaci Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otevřít dotaz v projektu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Seznam výsledků dotazu e-mailovou aplikaci Outlook](/azure/devops/boards/queries/share-plans)
- [Vytvoření sestavy z dotazu v aplikaci Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (pouze TFS)

> [!NOTE]
> Je tu nový [prostředí pracovních položek](/azure/devops/boards/work-items/set-work-item-experience-vs) v sadě Visual Studio. 2019 ve verzi Preview 1. Informace o zobrazení pracovních položek v sadě Visual Studio. 2019 ve verzi Preview 1, naleznete v tématu [zobrazení a přidání pracovních položek](/azure/devops/boards/work-items/view-add-work-items).

## <a name="builds-page"></a>Stránka sestavení

**Sestavení** umožňuje stránky se zobrazí definice sestavení pro projekt.

Další informace:

- [Vytvořte kanály pro sestavování](/azure/devops/pipelines/tasks/index)
- [Zobrazit a spravovat sestavení](/azure/devops/pipelines/overview)
- [Spravovat frontu sestavení](/azure/devops/pipelines/agents/pools-queues)
- [Instalace nástroje pro průběžné doručování (CD) pro Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfiguraci a provádění průběžné doručování (CD) pro vaši aplikaci](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Stránka nastavení

**Nastavení** stránka umožňuje konfigurovat funkce pro správu pro projekt nebo kolekci projektů. Naleznete v následujících článcích:

| Projekt | Kolekce projektů | Ostatní |
| - | - | - |
| [Zabezpečení, členství ve skupině](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Zabezpečení, správy zdrojového kódu (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Oblasti pracovní položky](/azure/devops/organizations/settings/set-area-paths)<br/>[Iterace pracovních položek](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Nastavení portálu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Upozornění projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Zabezpečení, členství ve skupině](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Správy zdrojového kódu (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Správce šablon procesů](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Globální nastavení Git](/azure/devops/repos/git/git-config)<br/>[Nastavení úložiště Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Viz také:

- [Připojte se k projektům v Průzkumníku týmových projektů](../../ide/connect-team-project.md)