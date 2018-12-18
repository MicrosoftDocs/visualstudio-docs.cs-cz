---
title: Nasadit pomocí nasazení webu
description: Nasazení aplikace pomocí nasazení webu v sadě Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811921"
---
Pokud jste nainstalovali, nasazení webu pomocí instalačního programu webové platformy, můžete nasadit aplikace přímo ze sady Visual Studio.

1. Spusťte sadu Visual Studio s oprávněními správce a znovu otevřete projekt.

    Nasaďte aplikaci pomocí nasazení webu jsou nutná oprávnění správce.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **publikovat**.

    Pokud jste dříve nakonfigurovali všech profilů publikování **publikovat** otevře se podokno. Klikněte na tlačítko **nový profil**.

1. Pro **vybrat cíl publikování**vyberte **služby IIS, FTP, atd.** a klikněte na tlačítko **publikovat**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Zadejte parametry opravy konfigurace pro nastavení služby IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Pokud název hostitele se nepřekládá při pokusu o ověření v další kroky **Server** textové pole, zkuste IP adresu. Zahrnout `http://` jako předponu v **Server** pole.  Ujistěte se, že používáte port 80 v **Server** textové pole a ujistěte se, že jsou v bráně firewall otevřený port 80 a 8172.

1. Zvolte **ověření**. Ověřuje se nastavení připojení, můžete publikovat.

1. Klikněte na tlačítko **publikovat** k publikování aplikace.

    Karta Výstup ukazuje, pokud publikování proběhlo úspěšně a prohlížeči otevře aplikaci.

    Pokud dojde k chybě, že zmíníte Webdeploy, spusťte opětovnou kontrolu instalační postup, který Web Deploy a ujistěte se, že jsou otevřené správné porty (nasazení webu také vyžaduje port 8172 otevřen na serveru).

    Pokud aplikace se nasadí úspěšně, ale nefunguje správně, může být problémy se konfigurace služby IIS, ASP.NET instalaci nebo konfiguraci webu. V systému Windows Server otevřete web služby IIS pro konkrétnější chybové zprávy a poté spusťte opětovnou kontrolu dřívějších krocích.
