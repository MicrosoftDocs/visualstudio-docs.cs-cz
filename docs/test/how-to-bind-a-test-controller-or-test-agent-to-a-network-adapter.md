---
title: Vazba testovacího řadiče nebo testovacího agenta na síťový adaptér
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6383d7a16839ba8934bb7f91664379e99da17a36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594783"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Postup: Svázání testovacího řadiče nebo testovacího agenta se síťovým adaptérem

Pokud má počítač s nainstalovaným testovacím řadičem nebo softwarem testovacího agenta nainstalováno více síťových adaptérů, je nutné místo názvu počítače zadat adresu IP, abyste identifikovali tento testovací řadič nebo testovacího agenta.

> [!WARNING]
> Při pokusu o nastavení testovacího agenta se může zobrazit následující chyba:
>
> **Chyba 8110. Nelze se připojit k zadanému počítači řadiče nebo získat přístup k objektu řadiče.**
>
> Tato chyba může být způsobena instalací testovacího řadiče do počítače, který má více než jeden síťový adaptér. Je také možné úspěšně nainstalovat agenty a tento problém se nezobrazí, dokud se nepokusíte spustit test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Svázání testovacího řadiče s konkrétním síťovým adaptérem

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Získání IP adres síťových adaptérů

1. V systému Microsoft Windows zvolte **Start**, zvolte do pole **Spustit hledání,** zadejte **příkaz cmd**a pak zvolte **Enter**.

2. Zadejte **ipconfig /all**.

     Zobrazí se adresy IP síťových adaptérů. Zaznamenejte adresu IP síťového adaptéru, se kterou chcete řadič svázat.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Vytvoření svázání síťového adaptéru s testovacím řadičem

1. V systému Microsoft Windows zvolte **Start**, zvolte do pole **Spustit hledání,** zadejte **services.msc**a pak zvolte **Enter**.

     Zobrazí se dialogové okno **Služby.**

2. V podokně výsledků klikněte ve sloupci **Název** pravým tlačítkem myši na službu **Testovací řadič sady Visual Studio** a pak zvolte **Zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte příkaz s následujícím příkazem:

     `net stop vsttcontroller`

3. Otevřete konfigurační soubor XML *QTCcontroller.exe.config* umístěný v *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. vyhledejte `<appSettings>` značku.

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

5. Přidejte `BindTo` klíč určující, který síťový `<appSettings>` adaptér se má použít v části.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Spusťte službu testovacího řadiče. Chcete-li to provést, spusťte na příkazovém řádku následující příkaz:

    `net start vsttcontroller`

    > [!WARNING]
    > Chcete-li připojit testovacího agenta k řadiči, je nutné znovu spustit instalaci testovacího agenta. Tentokrát zadejte IP adresu pro řadič namísto názvu řadiče.

     To platí pro řadič, službu agenta a proces agenta. Vlastnost `BindTo` musí být nastavena pro každý proces, který je spuštěn v počítači, který má více než jeden síťový adaptér. Postup nastavení vlastnosti `BindTo` je stejný pro všechny tři procesy, jak je uvedeno dříve v tomto tématu pro testovací řadič.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Vytvoření svázání karty síťového rozhraní s testovacím agentem

1. V systému Microsoft Windows zvolte **Start**, zvolte do pole **Spustit hledání,** zadejte **services.msc**a pak zvolte **Enter**.

    Zobrazí se dialogové okno **Služby.**

2. V podokně výsledků klikněte ve sloupci **Název** pravým tlačítkem myši na službu **Agent testu sady Visual Studio** a pak zvolte **Zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte příkaz s následujícím příkazem:

     **net stop vsttagent**

3. Otevřete konfigurační soubor XML *QTAgentService.exe.config* umístěný v *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. vyhledejte `<appSettings>` značku.

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

5. Přidejte `BindTo` klíč určující, který síťový `<appSettings>` adaptér se má použít v části.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Spusťte službu testovacího agenta. Chcete-li to provést, spusťte na příkazovém řádku následující příkaz:

    `net start vsttagent`

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Změna nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací řadiče a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postup: Zadejte časové období pro testovací řadiče a testovací agenty](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
