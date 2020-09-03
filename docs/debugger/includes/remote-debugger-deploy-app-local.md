---
title: Nasadit do místní složky
description: Nasazení aplikace do místní složky
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89323653"
---
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **publikovat** (pro webové formuláře, **publikovat webovou aplikaci**).

    Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Klikněte na **Nový profil**.

1. V dialogovém okně **publikovat** vyberte možnost **Složka**, klikněte na tlačítko **Procházet**a vytvořte novou složku **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    V případě aplikace webové formuláře vyberte v dialogovém okně Publikovat možnost **vlastní** , zadejte název profilu a klikněte na **tlačítko OK**.

1. V rozevíracím seznamu klikněte na **vytvořit profil** (výchozí hodnota je**Publish** ).

1. V dialogovém okně **publikovat** klikněte na odkaz **Nastavení** a pak vyberte kartu **Nastavení** .

1. Nastavte konfiguraci na **ladit**, vyberte **Odstranit všechny existující soubory před publikováním**a pak klikněte na **Uložit**.

    > [!NOTE]
    > Použijete-li sestavení pro vydání, zakážete ladění v souboru web.config při publikování.

1. Klikněte na **Publikovat**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    Aplikace publikuje konfiguraci **ladění** projektu do místní složky. Průběh se zobrazí v okně výstup.

1. Zkopírujte adresář projektu ASP.NET z počítače sady Visual Studio do místního adresáře nakonfigurovaného pro aplikaci ASP.NET (v tomto příkladu **C:\Publish**) na počítači se systémem Windows Server. V tomto kurzu se předpokládá, že provádíte kopírování ručně, ale můžete použít i další nástroje, jako je PowerShell, XCOPY nebo Robocopy.

    > [!CAUTION]
    > Pokud potřebujete provést změny v kódu nebo znovu sestavit, musíte znovu publikovat a opakovat tento krok. Spustitelný soubor, který jste zkopírovali do vzdáleného počítače, se musí přesně shodovat s vaším místním zdrojem a symboly.    Pokud to neuděláte, zobrazí se `cannot find or open the PDB file` při pokusu o ladění procesu v aplikaci Visual Studio upozornění.

1. Na Windows serveru ověřte, že aplikaci můžete správně spustit tak, že otevřete aplikaci v prohlížeči.

    Pokud aplikace nefunguje správně, může dojít ke neshodě mezi verzí ASP.NET nainstalovanou na vašem serveru a vaším počítačem v rámci sady Visual Studio, případně může dojít k potížím s konfigurací služby IIS nebo webu. Překontrolujte předchozí kroky.
