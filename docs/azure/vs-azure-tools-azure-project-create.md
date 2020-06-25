---
title: Vytvoření projektu cloudové služby Azure
description: Naučte se vytvořit projekt cloudové služby Azure se sadou Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: ef5acada89d48ed91dbf5b0f5fe7c9801337d47f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280372"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Vytvoření projektu cloudové služby Azure v sadě Visual Studio

Visual Studio poskytuje šablonu projektu, která vám umožní vytvořit [cloudovou službu Azure](/azure/cloud-services/cloud-services-choose-me), což je jednoduchá služba Azure pro obecné účely. Po vytvoření projektu Visual Studio umožňuje konfigurovat, ladit a nasazovat cloudovou službu do Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Postup vytvoření projektu cloudové služby Azure v aplikaci Visual Studio
V této části se seznámíte s vytvořením projektu cloudové služby Azure v aplikaci Visual Studio s jednou nebo více webovými rolemi.

::: moniker range="vs-2017"
1. Otevřete Visual Studio jako správce.

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt**.

1. Vyberte **Cloud** z uzlů šablony projektu Visual C# nebo Visual Basic a v seznamu šablon vyberte **cloudovou službu Azure** .

    ![Nová cloudová služba Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Určete verzi .NET Framework, kterou chcete použít k vývoji projektu.

1. Zadejte název a umístění projektu a název řešení.

1. Vyberte **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte *Cloud*a pak zvolte **cloudová služba Azure**.

   ![Nová cloudová služba Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Zadejte název projektu a klikněte na **vytvořit**.

   ![Zadat název projektu](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. V dialogovém okně **nová Microsoft Azure cloudová služba** vyberte role, které chcete přidat, a zvolte tlačítko se šipkou vpravo a přidejte je do svého řešení.

    ![Vyberte nové role Azure Cloud Service.](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Pokud chcete přejmenovat přidanou roli, najeďte na ni v dialogovém okně **nový Microsoft Azure cloudová služba** a v místní nabídce vyberte **Přejmenovat**. Můžete také přejmenovat roli v rámci řešení (v **Průzkumník řešení**) po jejím přidání.

    ![Přejmenování role cloudové služby Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt aplikace Visual Studio Azure obsahuje přidružení k projektům rolí v řešení. Projekt obsahuje také *soubor definice služby* a *konfigurační soubor služby*:

- **Definiční soubor služby** – definuje nastavení modulu runtime pro vaši aplikaci, včetně toho, jaké role jsou povinné, koncové body a velikost virtuálního počítače.
- **Konfigurační soubor služby** – konfiguruje, kolik instancí role se spouští, a hodnoty nastavení definované pro roli.

Další informace o těchto souborech najdete v tématu [Konfigurace rolí pro cloudovou službu Azure se sadou Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Další kroky
- [Správa rolí v projektech Azure Cloud Service pomocí sady Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
