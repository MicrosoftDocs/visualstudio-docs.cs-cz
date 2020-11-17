---
title: Připojení k procesu běžícímu na kontejneru Docker
description: Naučte se ladit aplikaci, na které běží kontejner Docker, pomocí sady Visual Studio.
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5b32b402e2bbf85cf5c028ec2dc94821ec463644
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674775"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Připojení k procesu běžícímu na kontejneru Docker 

Pomocí sady Visual Studio můžete ladit aplikace spuštěné v kontejneru Docker systému Windows nebo v kontejneru Linux .NET Core.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Připojení k procesu běžícímu na kontejneru Docker platformy Linux

Můžete připojit ladicí program sady Visual Studio k procesu běžícímu v kontejneru Docker platformy Linux .NET Core na místním nebo vzdáleném počítači pomocí dialogového okna **připojit k procesu** .

> [!IMPORTANT]
> Pokud chcete používat tuto funkci, musíte nainstalovat úlohu vývoje .NET Core pro různé platformy a mít místní přístup ke zdrojovému kódu.

**Připojení ke spuštěnému procesu v kontejneru Docker systému Linux:**

1. V aplikaci Visual Studio vyberte možnost **ladit > připojit k procesu (CTRL + ALT + P)** a otevřete dialogové okno **připojit k procesu** .

![Nabídka připojit k procesu](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Nastavte **Typ připojení** **Docker (kontejner Linux)**.
3. Vyberte **Najít...** a nastavte **cíl připojení** přes dialogové okno **Vybrat kontejner Docker** .

    Proces kontejneru Docker můžete ladit buď místně, nebo vzdáleně.

    **Postup při ladění procesu kontejneru Docker v místním prostředí:**
    1. Nastavte **hostitele Docker CLI** na **místní počítač**.
    1. Vyberte běžící kontejner, ze kterého se má připojit, a stiskněte **OK**.

    ![Vybrat nabídku kontejneru Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Postup při vzdáleném ladění procesu Docker Container:**

    > [!NOTE]
    > Existují dvě možnosti, jak se vzdáleně připojit ke spuštěnému procesu v kontejneru Docker. První možnost použití SSH je ideální, pokud na místním počítači nemáte nainstalované nástroje Docker.  Pokud máte nástroje Docker nainstalované místně a máte démona Docker, který je nakonfigurovaný tak, aby přijímal vzdálené požadavky, zkuste druhou možnost s použitím démona Docker.

    1. **_Připojení ke vzdálenému počítači přes SSH:_* _
        1. Vyberte _ *Přidat...* * pro připojení ke vzdálenému systému.<br/>
        ![Připojit ke vzdálenému systému](../debugger/media/connect-remote-system.png "Připojit ke vzdálenému systému")
        1. Vyberte běžící kontejner, ke kterému se připojíte po úspěšném připojení k SSH nebo procesu démona, a pak stiskněte **OK**.

    1. **_Nastavení cíle na vzdálený kontejner, na kterém je spuštěný proces prostřednictvím [démona Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
        1. Zadejte adresu démona (tj. přes TCP, IP adresu atd.) v části _ *hostitele Docker (volitelné)** a klikněte na odkaz aktualizovat.
        1. Vyberte běžící kontejner, ke kterému se připojíte po úspěšném připojení k procesu démona, a pak stiskněte **OK**.

4. Zvolte odpovídající proces kontejneru ze seznamu **dostupných procesů** a vyberte **připojit** a spusťte ladění procesu kontejneru C# v aplikaci Visual Studio!

    ![Nabídka připojit k Docker je dokončená](../debugger/media/docker-attach-complete.png "Nabídka připojit k systému Linux Docker je dokončená")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Připojení k procesu běžícímu na kontejneru Docker systému Windows

Můžete připojit ladicí program sady Visual Studio k procesu běžícímu v kontejneru Docker systému Windows na místním počítači pomocí dialogového okna **připojit k procesu** .

> [!IMPORTANT]
> Chcete-li tuto funkci používat s procesem .NET Core, je nutné nainstalovat úlohu vývoje .NET Core pro různé platformy a mít místní přístup ke zdrojovému kódu.

**Postup připojení ke spuštěnému procesu v kontejneru Docker systému Windows:**

1. V aplikaci Visual Studio vyberte možnost **ladit > připojit k procesu** (nebo **CTRL + ALT + P**) a otevřete dialogové okno **připojit k procesu** .

   ![Nabídka připojit k procesu](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Nastavte **Typ připojení** **Docker (kontejner Windows)**.
3. Vyberte **Najít...** a nastavte **cíl připojení** pomocí dialogového okna **Vybrat kontejner Docker** .

    > [!IMPORTANT]
    > Cílový proces musí mít stejnou architekturu procesoru jako kontejner Docker Windows, na kterém je spuštěný.

   Nastavení cíle na vzdálený kontejner prostřednictvím protokolu SSH není aktuálně dostupné a lze jej provést pouze pomocí démona Docker.

    **_Nastavení cíle na vzdálený kontejner, na kterém je spuštěný proces prostřednictvím [démona Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
    1. Zadejte adresu démona (tj. přes TCP, IP adresu atd.) v části _ *hostitele Docker (volitelné)** a klikněte na odkaz aktualizovat.

    1. Vyberte běžící kontejner, ke kterému se připojíte po úspěšném připojení k procesu démona, a zvolte OK.

4. Zvolte odpovídající proces kontejneru ze seznamu **dostupných procesů** a vyberte **připojit** a spusťte ladění procesu kontejneru C#.

    ![Nabídka připojit k Docker je dokončená](../debugger/media/docker-attach-complete-windows.png "Dokončená nabídka připojit k programu Windows Docker")

5.  Vyberte odpovídající proces kontejneru ze seznamu dostupných procesů a klikněte na tlačítko **připojit** a spusťte ladění procesu kontejneru C#.