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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249834"
---
1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte **publikovat** (pro webové formuláře, **publikovat webovou aplikaci**).

    Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Klikněte na **Nový profil**.

1. V dialogovém okně **publikovat** vyberte možnost **Složka**, klikněte na tlačítko **Procházet** a vytvořte novou složku **C:\Publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Snímek obrazovky dialogového okna vybrat cíl publikování v aplikaci Visual Studio se složkou ' C:\Publish ' vybraný jako cíl publikování.":::

   Kliknutím na tlačítko **Dokončit** uložte profil publikování.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Snímek obrazovky dialogového okna vybrat cíl publikování v aplikaci Visual Studio se složkou ' bin\Release\Publish ' vybraný jako cíl publikování.](../media/remotedbg_publish_local.png)
   V případě aplikace webové formuláře vyberte v dialogovém okně Publikovat možnost **vlastní** , zadejte název profilu a klikněte na **tlačítko OK**.

   V rozevíracím seznamu klikněte na **vytvořit profil** (výchozí hodnota je **Publish** ).
   ::: moniker-end

1. Přepněte na konfiguraci ladění.

   ::: moniker range=">=vs-2019"
   Zvolte **Upravit** pro úpravu profilu a pak zvolte **Nastavení**. Zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   V dialogovém okně **Nastavení** Povolte ladění kliknutím na tlačítko **Další**, zvolte konfiguraci **ladění** a pak zvolte **odebrat další soubory v cílovém umístění** v možnostech **publikování souboru** .
   ::: moniker-end

   > [!NOTE]
   > Použijete-li sestavení pro vydání, zakážete ladění v souboru *web.config* při publikování.

1. Klikněte na **Publikovat**.

    ![Snímek obrazovky karty nastavení v dialogovém okně Publikovat. Konfigurace je nastavená na ladění a je vybrané tlačítko publikovat.](../media/remotedbg_publish_debug_config.png)

    Aplikace publikuje konfiguraci **ladění** projektu do místní složky. Průběh se zobrazí v okně výstup.

1. Zkopírujte adresář projektu ASP.NET z počítače sady Visual Studio do místního adresáře nakonfigurovaného pro aplikaci ASP.NET (v tomto příkladu **C:\Publish**) na počítači se systémem Windows Server. V tomto kurzu se předpokládá, že provádíte kopírování ručně, ale můžete použít i další nástroje, jako je PowerShell, XCOPY nebo Robocopy.

    > [!CAUTION]
    > Pokud potřebujete provést změny v kódu nebo znovu sestavit, musíte znovu publikovat a opakovat tento krok. Spustitelný soubor, který jste zkopírovali do vzdáleného počítače, se musí přesně shodovat s vaším místním zdrojem a symboly. Pokud to neuděláte, zobrazí se `cannot find or open the PDB file` při pokusu o ladění procesu v aplikaci Visual Studio upozornění.

1. Na Windows serveru ověřte, že aplikaci můžete správně spustit tak, že otevřete aplikaci v prohlížeči.

    Pokud aplikace nefunguje správně, může dojít ke neshodě mezi verzí ASP.NET nainstalovanou na vašem serveru a vaším počítačem v rámci sady Visual Studio, případně může dojít k potížím s konfigurací služby IIS nebo webu. Překontrolujte předchozí kroky.
