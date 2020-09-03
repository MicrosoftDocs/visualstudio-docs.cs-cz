---
title: Referenční dokumentace k Team Exploreru
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: b1a956579b527de9df9d24bd09dda6ae48eff961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74538572"
---
# <a name="team-explorer-reference"></a>Referenční dokumentace k Team Exploreru

Tento článek obsahuje odkazy na články Azure DevOps o různých funkcích v **Team Explorer**.

Použijte okno **Team Explorer** Tool k koordinaci vašeho kódu s ostatními členy týmu pro vývoj projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo vašim projektům. **Team Explorer** připojuje sadu Visual Studio k úložištím Git a GitHubu, úložištím správy verzí Team Foundation (TFVC) a projektům hostovaným v [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) nebo v místní [Azure DevOps Server](/azure/devops/index-all) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

## <a name="home-page"></a>Domovská stránka

Po [připojení k projektu](../connect-team-project.md) v **Team Explorer**jsou v části **projektu** k dispozici následující odkazy:

- [Klonovat úložiště](/azure/devops/repos/git/clone)
- [Webový portál](/azure/devops/project/navigation/index)
- [Panel úloh](/azure/devops/boards/sprints/task-board)

Na **domovské** stránce jsou různé funkce v závislosti na tom, jestli jste připojení k úložišti [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) nebo [Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview) .

> [!TIP]
> Porovnání dvou systémů správy verzí najdete v tématu [Volba správného ovládacího prvku verze pro váš projekt (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Domovská** Stránka s Git | **Domovská** Stránka s TFVC |
| - | - |
| ![Team Explorer domovskou stránku pomocí Gitu v aplikaci Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Team Explorer domovské stránky s TFVC v aplikaci Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Stránka změny (Git)

Viz [Uložit práci s potvrzeními](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Stránka větve (Git)

Viz [vytvořit práci v větvích](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Stránka žádostí o přijetí změn (Git)

Viz téma [Revize kódu s žádostmi o](/azure/devops/repos/git/pullrequest)přijetí změn.

## <a name="sync-page-git"></a>Stránka synchronizace (Git)

Viz [kód aktualizace pomocí načtení a vyžádání](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Stránka značek (Git)

Viz [práce s značkami Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Stránka má práce (TFVC)

Viz [Pozastavení/obnovení práce](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) a [Revize kódu](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Stránka nedokončené změny (TFVC)

Viz téma [Správa nedokončených změn](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [hledání sad odložených](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets)změn a [řešení konfliktů](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Stránka Průzkumník správy zdrojových souborů (TFVC)

Viz téma [Přidání/zobrazení souborů a složek](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Stránka pracovní položky

Stránka **pracovní položky** vám umožní zobrazit dotazy na [pracovní položky](/azure/devops/boards/work-items/about-work-items) . Přečtěte si:

- [Přidat pracovní položky](/azure/devops/boards/backlogs/add-work-items)
- [Použití Editoru dotazů k vypsání a správě dotazů](/azure/devops/boards/queries/using-queries)
- [Uspořádání složek dotazů a nastavení oprávnění pro dotazy](/azure/devops/boards/queries/set-query-permissions)
- [Otevřít dotaz v aplikaci Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Otevřít dotaz v projektu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Seznam výsledků e-mailových dotazů pomocí Outlooku](/azure/devops/boards/queries/share-plans)
- [Vytváření sestav z dotazu v aplikaci Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (pouze TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> V aplikaci Visual Studio 2019 se nachází nové [prostředí pracovní položky](/azure/devops/boards/work-items/set-work-item-experience-vs) . Informace o zobrazení pracovních položek v aplikaci Visual Studio 2019 naleznete v tématu [zobrazení a přidání pracovních položek](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Stránka sestavení

Stránka **sestavení** vám umožní zobrazit definice sestavení pro projekt.

Přečtěte si:

- [Vytváření kanálů sestavení](/azure/devops/pipelines/tasks/index)
- [Zobrazení a správa sestavení](/azure/devops/pipelines/overview)
- [Správa fronty sestavení](/azure/devops/pipelines/agents/pools-queues)
- [Nainstalovat nástroje pro průběžné doručování (CD) pro Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Konfigurace a spuštění průběžného doručování (CD) pro vaši aplikaci](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Stránka Nastavení

Stránka **Nastavení** umožňuje nakonfigurovat funkce pro správu projektu nebo kolekce projektů. Viz následující články:

| Project | Kolekce projektů | Další |
| - | - | - |
| [Zabezpečení, členství ve skupinách](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Zabezpečení, Správa zdrojového kódu (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Oblasti pracovních položek](/azure/devops/organizations/settings/set-area-paths)<br/>[Iterace pracovních položek](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Nastavení portálu](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Výstrahy projektu](/azure/devops/notifications/howto-manage-team-notifications) | [Zabezpečení, členství ve skupinách](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Správa zdrojového kódu (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Správce šablon procesů](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Globální nastavení Gitu](/azure/devops/repos/git/git-config)<br/>[Nastavení úložiště Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Viz také

- [Připojení k projektům v Team Explorer](../../ide/connect-team-project.md)