---
title: Vytvoření projektu cloudové služby Azure
description: Naučte se vytvořit projekt Azure cloud service pomocí sady Visual Studio
author: ghogen
manager: jillfra
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: 722c816329c70bb2efad03f9554e201bcc9fde16
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253464"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Vytvoření projektu cloudové služby Azure v sadě Visual Studio

Nástroje Azure pro sadu Visual Studio poskytuje šablony projektu, který vám umožní vytvářet [cloudové služby Azure](/azure/cloud-services/cloud-services-choose-me), což je jednoduchá služby Azure pro obecné účely. Po vytvoření projektu sady Visual Studio umožňuje nakonfigurovat, ladit a nasadit cloudovou službu Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Kroky pro vytvoření projektu Azure cloud service v sadě Visual Studio
Tato část vás provede vytvořením projektu cloudové služby Azure v sadě Visual Studio s jeden nebo více webových rolí.

::: moniker range="vs-2017"
1. Otevřete Visual Studio jako správce.

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt**.

1. Vyberte **cloudu** z jazyka Visual C# nebo Visual Basic projektu šablony uzlů a vyberte **Azure Cloud Service** ze seznamu šablon.

    ![Nová Cloudová služba Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Určete, která verze rozhraní .NET Framework, kterou chcete použít k vývoji projektu.

1. Zadejte název a umístění pro váš projekt a název řešení.

1. Vyberte **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. Do vyhledávacího pole zadejte *Cloud*a pak zvolte **cloudová služba Azure**.

   ![Nová Cloudová služba Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Zadejte název projektu a klikněte na **vytvořit**.

   ![Zadat název projektu](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. V **nová Cloudová služba Microsoft Azure** dialogového okna, vyberte role, které chcete přidat a zvolte tlačítko se šipkou doprava a přidejte je do vašeho řešení.

    ![Vyberte nové role Azure cloud service](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Chcete-li přejmenovat roli, která jste přidali, najeďte myší na roli v **nová Cloudová služba Microsoft Azure** dialogového okna a v místní nabídce vyberte **přejmenovat**. Můžete také přejmenovat roli v rámci vašeho řešení (v **Průzkumníka řešení**) po byla přidána.

    ![Přejmenujte roli Azure cloud service](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Projekt sady Visual Studio v Azure má přiřazení k roli projekty v řešení. Projekt obsahuje také *definiční soubor služby* a *konfigurační soubor služby*:

- **Definiční soubor služby** – definuje nastavení modulu runtime pro vaši aplikaci, včetně toho, jaké role jsou povinné, koncové body a velikost virtuálního počítače.
- **Konfigurační soubor služby** – nakonfiguruje, kolik instancí role jsou spouštění a hodnoty k nastavení určenému pro roli.

Další informace o těchto souborech najdete v tématu [nakonfigurovat role cloudové služby Azure pomocí sady Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Další kroky
- [Správa rolí v Azure cloud service projektů pomocí sady Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
