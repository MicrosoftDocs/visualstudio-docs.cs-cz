---
title: Přístup k privátním cloudům Azure
description: Zjistěte, jak získat přístup k prostředkům privátního cloudu pomocí Sady Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 57f92aa797e589bd48cc52296b710617cbe8d732
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544364"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Přístup k privátním cloudům Azure pomocí Sady Visual Studio

Ve výchozím nastavení Visual Studio podporuje koncové body Azure cloudu REST. V tomto článku se dozvíte, jak používat certifikát privátního cloudu pro přístup k privátnímu cloudu a interakci s ním z Visual Studia.

1. Na webu Azure Portal pro privátní cloud si stáhněte soubor nastavení publikování nebo požádejte správce o soubor nastavení publikování. (Soubor má příponu `.publishsettings`.)

1. V **Průzkumníkovi serveru**Visual Studio klikněte pravým tlačítkem myši na uzel **Azure** a vyberte Spravovat **a filtrovat předplatná**.

    ![Spravovat předplatná, příkaz](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. V dialogovém okně **Spravovat předplatná Microsoft Azure** vyberte kartu **Certifikáty** a pak vyberte **Importovat**.

    ![Import certifikátů Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. V dialogovém okně **Importovat předplatná Microsoft Azure** vyberte **Procházet**.

    ![Tlačítko Procházet v dialogovém okně Importovat předplatná Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. V dialogovém okně **Otevřít** vyhledejte adresář, do kterého jste uložili soubor nastavení publikování, vyberte soubor a pak vyberte **Otevřít**.

    ![Výběr souboru nastavení publikování](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Po návratu do dialogového okna **Importovat předplatná Microsoft Azure** vyberte **Importovat**.

    ![Import souboru nastavení publikování](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Certifikáty se importují ze souboru nastavení publikování do sady Visual Studio a teď můžete pracovat s prostředky privátního cloudu.
