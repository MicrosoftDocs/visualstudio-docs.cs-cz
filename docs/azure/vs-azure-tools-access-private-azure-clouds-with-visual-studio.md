---
title: Přístup k privátním cloudům Azure
description: Přečtěte si, jak získat přístup k prostředkům privátního cloudu pomocí sady Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 6c1b46e34c688f232ee1f774ff2d19fdad7ff6bf
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280385"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Přístup k privátním cloudům Azure pomocí sady Visual Studio

Ve výchozím nastavení Visual Studio podporuje koncové body REST cloudu Azure. V tomto článku se dozvíte, jak pomocí certifikátu privátního cloudu přistupovat k privátnímu cloudu a pracovat s ním ze sady Visual Studio.

1. V Azure Portal pro privátní cloud Stáhněte soubor Publish-Settings nebo se obraťte na správce se souborem pro publikování a nastavení. (Soubor má příponu `.publishsettings` .)

1. V aplikaci Visual Studio **Průzkumník serveru**klikněte pravým tlačítkem myši na uzel **Azure** a vyberte **Spravovat a filtrovat předplatná**.

    ![Správa předplatných – příkaz](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. V dialogovém okně **spravovat předplatná Microsoft Azure** vyberte kartu **certifikáty** a pak vyberte **importovat**.

    ![Import certifikátů Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. V dialogovém okně **importovat předplatná Microsoft Azure** vyberte **Procházet**.

    ![Tlačítko Procházet v dialogovém okně Importovat Microsoft Azure předplatná](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. V dialogovém okně **otevřít** přejděte do adresáře, kam jste uložili soubor Publish-Settings, vyberte soubor a pak vyberte **otevřít**.

    ![Vybrat soubor publikování – nastavení](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Po návratu do dialogového okna **importovat předplatná Microsoft Azure** vyberte **importovat**.

    ![Import souboru Publish-Settings](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Certifikáty se importují ze souboru Publish-Settings do sady Visual Studio a teď můžete pracovat s prostředky privátního cloudu.
