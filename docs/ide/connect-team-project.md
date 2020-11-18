---
title: Připojení k projektům v Team Explorer
description: Naučte se používat Team Explorer v aplikaci Visual Studio pro práci se členy týmu pro vývoj a správu projektů.
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: 7d920370013b2d624430acbdbe8e38dcc9aab03d
ms.sourcegitcommit: f78960320798e2c6b33145cee77a2221f031603c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2020
ms.locfileid: "94878254"
---
# <a name="connect-to-projects-in-team-explorer"></a>Připojení k projektům v Team Explorer

::: moniker range="vs-2017"

Použijte okno **Team Explorer** Tool k koordinaci vašeho kódu s ostatními členy týmu pro vývoj projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo vašim projektům. **Team Explorer** připojuje sadu Visual Studio k úložištím Git a GitHubu, úložištím správy verzí Team Foundation (TFVC) a projektům hostovaným v [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) nebo v místní [Azure DevOps Server](/azure/devops/index-all) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

::: moniker-end

::: moniker range="vs-2019"

Můžete použít okno **Team Explorer** nástrojů k koordinaci vašeho kódu s ostatními členy týmu pro vývoj projektu a ke správě práce, která je přiřazena vám, vašemu týmu nebo vašim projektům.

> [!IMPORTANT]
> S nejnovější verzí sady Visual Studio 2019 [verze 16,8](/visualstudio/releases/2019/release-notes/)je nyní ve výchozím nastavení standardně nastaveno nové prostředí pro řízení verzí Git. Pokud ale dáváte přednost i nadále používat Team Explorer, přejděte do části **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview** a potom zaškrtněte políčko **nové uživatelské prostředí Git** . Další informace najdete na stránce věnované [prostředí Git](git-with-visual-studio.md) na stránce sady Visual Studio.

**Team Explorer** připojuje sadu Visual Studio k úložištím Git a GitHubu, úložištím správy verzí Team Foundation (TFVC) a projektům hostovaným v [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) nebo v místní [Azure DevOps Server](/azure/devops/index-all) (dříve označované jako TFS). Můžete spravovat zdrojový kód, pracovní položky a sestavení.

::: moniker-end

![Team Explorer domovskou stránku v aplikaci Visual Studio](media/team-explorer/team-explorer.png "Team Explorer – Domovská stránka v aplikaci Visual Studio.")

::: moniker range="vs-2017"

> [!TIP]
> Pokud otevřete Visual Studio a **Team Explorer** se nezobrazí, otevřete ho tak, že v řádku nabídek kliknete na **Zobrazit**  >  **Team Explorer** nebo stisknete **CTRL** + **&#92;**, **CTRL** + **M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Připojení k projektu nebo úložišti

Připojte se k projektu nebo úložišti na stránce **připojit** .

![Připojit stránku v Team Explorer](media/team-explorer/connect.png "Stránka Team Explorer-Connect v aplikaci Visual Studio")

Připojení k projektu:

1. Otevřete stránku **připojit** výběrem ikony **Spravovat připojení** .

   ![Tlačítko Spravovat připojení v Team Explorer](media/team-explorer/manage-connections.png "Tlačítko Team Explorer-spravovat připojení v aplikaci Visual Studio.")

1. Na stránce **připojit** vyberte možnost **Spravovat připojení**  >  **připojit k projektu**.

   ![Připojit se k projektu v Team Explorer](media/team-explorer/connect-project.png "Team Explorer – připojení k možnosti projektu v aplikaci Visual Studio.")

> [!TIP]
> Pokud chcete otevřít projekt z úložiště, přečtěte si téma [otevření projektu z úložiště](../get-started/tutorial-open-project-from-repo.md). Pokud chcete vytvořit nový projekt nebo přidat uživatele do projektu, přečtěte si téma [Vytvoření projektu (Azure DevOps)](/azure/devops/organizations/projects/create-project) a [Přidání uživatelů do projektu nebo týmu (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Viz také

- [Nové prostředí Git v aplikaci Visual Studio](git-with-visual-studio.md)
- [Kurz: otevření projektu z úložiště](../get-started/tutorial-open-project-from-repo.md)
- [Referenční dokumentace k Team Exploreru](reference/team-explorer-reference.md)
- [Připojení k projektu (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Řešení potíží s připojením k projektu](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
