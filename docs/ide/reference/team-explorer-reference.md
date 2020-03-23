---
title: Referenční dokumentace k Team Exploreru
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74538572"
---
# <a name="team-explorer-reference"></a>Referenční dokumentace k Team Exploreru

Tento článek obsahuje odkazy na články Azure DevOps o různých funkcích v **Průzkumníkovi týmu**.

Okno nástroje **Průzkumník týmu** slouží ke koordinaci úsilí o kód s ostatními členy týmu k vývoji projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo projektům. **Průzkumník týmu** spojuje Visual Studio s úložišti Git a GitHub, úložištěm správy verzí Team Foundation (TFVC) a projekty hostovanými ve [službách Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) services nebo na místním [serveru Azure DevOps (dříve](/azure/devops/index-all) označovaném jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

## <a name="home-page"></a>Domovská stránka

Po [připojení k projektu](../connect-team-project.md) v **Průzkumníkovi týmu**budou v části **Project** k dispozici následující odkazy:

- [Úložiště klonování](/azure/devops/repos/git/clone)
- [Webový portál](/azure/devops/project/navigation/index)
- [Panel úkolů](/azure/devops/boards/sprints/task-board)

**Domovská** stránka má různé funkce v závislosti na tom, zda jste připojeni k úložišti [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) nebo [Team Foundation Version Control (TFVC).](/azure/devops/repos/tfvc/overview)

> [!TIP]
> Porovnání dvou systémů správy verzí najdete v [tématu Výběr správné správy verzí pro váš projekt (Azure DevOps).](/azure/devops/repos/tfvc/comparison-git-tfvc)

| **Domovská** stránka s Gitem | **Domovská** stránka s TFVC |
| - | - |
| ![Domovská stránka Průzkumníka týmu s Gitem ve Visual Studiu 2019](media/team-explorer-reference/team-explorer-git.png) | ![Domovská stránka Průzkumníka týmu s TFVC v sadě Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Stránka Změny (Git)

Viz [Ukládání práce s revizemi](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Stránka Větve (Git)

Viz [Vytvoření práce ve větvích](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Stránka Žádosti o přijetí vyžádat (Git)

Viz [Kód kontroly s žádostmi o přijetí vzbuzovat.](/azure/devops/repos/git/pullrequest)

## <a name="sync-page-git"></a>Stránka synchronizace (Git)

Viz [Aktualizace kódu s načtením a vyžádat](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Stránka Značky (Git)

Viz [Práce se značkami Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Moje pracovní stránka (TFVC)

Viz [Pozastavení/obnovení práce](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) a [revize kódu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Stránka Čekající změny (TFVC)

Viz [Správa čekajících změn](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), Hledání [shelvesets](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)a [Řešení konfliktů](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Stránka Průzkumník a řízení zdrojového kódu (TFVC)

Viz [Přidání/zobrazení souborů a složek](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Stránka Pracovní položky

**Pracovní položky** stránka umožňuje zobrazit dotazy [pracovní chod.](/azure/devops/boards/work-items/about-work-items) Přečtěte si:

- [Přidání pracovních položek](/azure/devops/boards/backlogs/add-work-items)
- [Použití editoru dotazů k vypáčování a správě dotazů](/azure/devops/boards/queries/using-queries)
- [Uspořádání složek dotazů a nastavení oprávnění dotazů](/azure/devops/boards/queries/set-query-permissions)
- [Otevření dotazu v Excelu](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otevřít dotaz v Projectu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Seznam výsledků e-mailových dotazů v Outlooku](/azure/devops/boards/queries/share-plans)
- [Vytváření sestav z dotazu v Excelu](/azure/devops/report/excel/create-status-and-trend-excel-reports) (jenom TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> V Visual Studiu 2019 je nové [pracovní prostředí.](/azure/devops/boards/work-items/set-work-item-experience-vs) Informace o zobrazení pracovních položek ve Visual Studiu 2019 najdete v tématu [Zobrazení a přidání pracovních položek](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Stránka sestavení

Sestavení **Builds** stránky umožňuje zobrazit definice sestavení pro projekt.

Přečtěte si:

- [Vytvoření kanálů sestavení](/azure/devops/pipelines/tasks/index)
- [Zobrazení a správa sestavení](/azure/devops/pipelines/overview)
- [Správa fronty sestavení](/azure/devops/pipelines/agents/pools-queues)
- [Instalace nástrojů pro průběžné doručování (CD) pro Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfigurace a provádění průběžného doručování (CD) pro vaši aplikaci](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Stránka Nastavení

Stránka **Nastavení** umožňuje konfigurovat funkce správy pro projekt nebo kolekci projektů. Viz následující články:

| Project | Kolekce projektů | Ostatní |
| - | - | - |
| [Zabezpečení, členství ve skupině](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Zabezpečení, správa zdrojového kódu (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Oblasti pracovních položek](/azure/devops/organizations/settings/set-area-paths)<br/>[Iterace pracovních položek](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Nastavení portálu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Výstrahy projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Zabezpečení, členství ve skupině](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Stojato (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Správce šablon procesů](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Globální nastavení Gitu](/azure/devops/repos/git/git-config)<br/>[Nastavení úložiště Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Viz také

- [Připojení k projektům v Průzkumníkovi týmu](../../ide/connect-team-project.md)