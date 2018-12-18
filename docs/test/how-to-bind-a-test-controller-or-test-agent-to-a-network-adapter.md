---
title: Svázat testovací Kontrolér nebo testovacího agenta na síťový adaptér
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 59a71b57c76fbb0650824efb29afe585c62162f9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065944"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Postupy: vytvoření vazby testovacího kontroléru nebo testovacího agenta na síťový adaptér

Pokud počítač, který obsahuje testovací kontrolér nebo software testovacího agenta nainstalovaná má více síťových adaptérů, musíte zadat IP adresu místo názvu počítače k určení daného testovacího kontroléru nebo testovacího agenta.

> [!WARNING]
> Při pokusu o nastavení testovacího agenta, může dojít k následující chybě:
>
> **Došlo k chybě 8110. Nelze se připojit k počítači určenému kontroleru nebo přístup k objektu kontroleru**
>
> Tuto chybu může způsobovat instalace testovacího kontroléru na počítači, který má více než jeden síťový adaptér. Je také možné úspěšně nainstalovat agenty a tento problém se nezobrazují až do pokusu o spuštění testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Vazba testovacího kontroléru na konkrétní síťový adaptér

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Chcete-li získat IP adresy síťových adaptérů

1.  V Microsoft Windows, zvolte **Start**, zvolte **Zahájit hledání** zadejte **cmd**a klikněte na tlačítko **Enter**.

2.  Typ **ipconfig/all**.

     Se zobrazují IP adresy pro síťové adaptéry. Zaznamenejte adresu IP síťového adaptéru, který chcete vytvořit vazbu řadiče.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Chcete-li vytvořit vazbu na síťový adaptér do testovacího kontroléru

1.  V Microsoft Windows, zvolte **Start**, zvolte **Zahájit hledání** zadejte **services.msc**a klikněte na tlačítko **Enter**.

     **Služby** zobrazí dialogové okno.

2.  V podokně výsledků v části **název** sloupce, klikněte pravým tlačítkem na **Visual Studio Test Controller** služby a klikněte na tlačítko **Zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte následující příkaz v příkazu:

     `net stop vsttcontroller`

3.  Otevřít *QTCcontroller.exe.config* konfigurační soubor XML v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Vyhledejte `<appSettings>` značky.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5.  Přidat `BindTo` klíč k určení síťového adaptéru, který chcete použít v `<appSettings>` oddílu.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Spusťte službu testovacího řadiče. Chcete-li to provést, spusťte následující příkaz z příkazového řádku:

    `net start vsttcontroller`

    > [!WARNING]
    > Je nutné spustit instalaci testovacího agenta znovu pro připojení testovacího agenta k řadiči. Tentokrát, zadejte IP adresu řadiče, nikoli název řadiče.

     To platí pro kontrolér, službu agenta a proces agenta. `BindTo` Musí být nastavena vlastnost pro každý proces, který běží na počítači, který má více než jeden síťový adaptér. Postup pro nastavení `BindTo` vlastnost je stejný pro všechny tři procesy, jak je uvedeno výše v tomto tématu pro řadič testu.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Vytvořit vazbu karty síťového rozhraní na testovacího agenta

1.  V Microsoft Windows, zvolte **Start**, zvolte **Zahájit hledání** zadejte **services.msc**a klikněte na tlačítko **Enter**.

    **Služby** zobrazí dialogové okno.

2.  V podokně výsledků v části **název** sloupce, klikněte pravým tlačítkem na **Visual Studio Test Agent** služby a klikněte na tlačítko **Zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte následující příkaz v příkazu:

     **vsttagent net stop**

3.  Otevřít *QTAgentService.exe.config* konfigurační soubor XML v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  Vyhledejte `<appSettings>` značky.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5.  Přidat `BindTo` klíč k určení síťového adaptéru, který chcete použít v `<appSettings>` oddílu.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Spusťte službu testovacího agenta. Chcete-li to provést, spusťte následující příkaz z příkazového řádku:

    `net start vsttagent`

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Úprava nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací kontroléry a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postupy: určení maximální velikosti souboru protokolu](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Postupy: nastavení časových limitů pro testovací kontroléry a testovací agenty](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)