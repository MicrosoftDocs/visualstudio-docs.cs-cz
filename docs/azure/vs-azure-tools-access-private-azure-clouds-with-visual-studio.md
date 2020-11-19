---
title: Přístup k privátním cloudům Azure
description: Přečtěte si, jak získat přístup k prostředkům privátního cloudu pomocí sady Visual Studio.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 92ab5ae3dc6fa5fd807203a1adf2353a20bfb666
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902828"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Přístup k privátním cloudům Azure pomocí sady Visual Studio

Ve výchozím nastavení Visual Studio podporuje koncové body REST cloudu Azure. V tomto článku se dozvíte, jak pomocí certifikátu privátního cloudu přistupovat k privátnímu cloudu a pracovat s ním ze sady Visual Studio.

1. V Azure Portal pro privátní cloud Stáhněte soubor Publish-Settings nebo se obraťte na správce se souborem pro publikování a nastavení. (Soubor má příponu `.publishsettings` .)

1. V aplikaci Visual Studio **Průzkumník serveru** klikněte pravým tlačítkem myši na uzel **Azure** a vyberte **Spravovat a filtrovat předplatná**.

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
