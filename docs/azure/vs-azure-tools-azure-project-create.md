---
title: Vytvoření projektu cloudové služby Azure
description: Naučte se nyní vytvořit projekt cloudové služby Azure pomocí Sady Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: 23e2db0b42fb12872feb5942d9f4eeaab96d3c2d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489750"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Vytvoření projektu cloudové služby Azure v sadě Visual Studio

Visual Studio poskytuje šablonu projektu, která umožňuje vytvořit [cloudovou službu Azure](/azure/cloud-services/cloud-services-choose-me), což je jednoduchá služba Azure pro obecné účely. Po vytvoření projektu visual studio umožňuje konfigurovat, ladit a nasadit cloudovou službu do Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Postup vytvoření projektu cloudové služby Azure ve Visual Studiu
Tato část vás provede vytvořením projektu cloudové služby Azure ve Visual Studiu s jednou nebo více webovými rolemi.

::: moniker range="vs-2017"
1. Otevřete Visual Studio jako správce.

1. V hlavní nabídce vyberte **Soubor** > **nový** > **projekt**.

1. Vyberte **Cloud** z uzlů šablony projektu Visual C# nebo Visual Basic a ze seznamu šablon vyberte **Azure Cloud Service.**

    ![Nová cloudová služba Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Určete, kterou verzi rozhraní .NET Framework chcete použít k vývoji projektu.

1. Zadejte název a umístění projektu a název řešení.

1. Vyberte **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. V počátečním okně zvolte **Vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte *do cloudu*a pak zvolte **Azure Cloud Service**.

   ![Nová cloudová služba Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Pojmenujte projekt a zvolte **Vytvořit**.

   ![Pojmenujte projekt](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. V dialogovém okně **Nová cloudová služba Microsoft Azure** vyberte role, které chcete přidat, a zvolte tlačítko se šipkou vpravo, které chcete přidat do svého řešení.

    ![Výběr nových rolí cloudové služby Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Pokud chcete přejmenovat roli, kterou jste přidali, najeďte na roli v dialogovém okně **Nová cloudová služba Microsoft Azure** a v místní nabídce vyberte **Přejmenovat**. Můžete také přejmenovat roli v rámci řešení (v **Průzkumníku řešení**) po jeho přidání.

    ![Přejmenování role cloudové služby Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt Visual Studio Azure má přidružení k projektům rolí v řešení. Projekt také obsahuje *soubor definice služby* a *konfigurační soubor služby*:

- **Definiční soubor služby** – definuje nastavení běhu pro vaši aplikaci, včetně požadovaných rolí, koncových bodů a velikosti virtuálního počítače.
- **Konfigurační soubor služby** – Konfiguruje, kolik instancí role je spuštěno a hodnoty nastavení definované pro roli.

Další informace o těchto souborech najdete [v tématu Konfigurace rolí pro cloudovou službu Azure pomocí sady Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Další kroky
- [Správa rolí v projektech cloudových služeb Azure pomocí Visual Studia](./vs-azure-tools-cloud-service-project-managing-roles.md)
