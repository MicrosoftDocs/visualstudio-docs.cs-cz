---
title: Navázání Test Controller nebo testovacího agenta na síťový adaptér
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 925df819b903be3de3d44127243f3b18d1e9aff5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288244"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Postupy: vytvoření vazby kontroleru testů nebo testovacího agenta na síťový adaptér

Pokud má počítač s nainstalovaným kontrolérem testu nebo softwarem testovacího agenta více síťových adaptérů, je nutné zadat IP adresu namísto názvu počítače k identifikaci tohoto kontroleru testů nebo testovacího agenta.

> [!WARNING]
> Při pokusu o nastavení testovacího agenta se může zobrazit následující chyba:
>
> **Chyba 8110. Nelze se připojit k zadanému počítači kontroléru nebo získat přístup k objektu kontroleru.**
>
> Tato chyba může být způsobena instalací kontroleru testů na počítači, který má více než jeden síťový adaptér. Je také možné úspěšně nainstalovat agenty a tento problém se neprojeví, dokud se nepokusíte spustit test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Vazba testovacího kontroléru na konkrétní síťový adaptér

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Získání IP adres síťových adaptérů

1. V systému Microsoft Windows klikněte na tlačítko **Start**, do pole **Zahájit hledání** zadejte příkaz **cmd**a klikněte na tlačítko **ENTER**.

2. Zadejte **ipconfig /all**.

     Zobrazí se IP adresy pro vaše síťové adaptéry. Poznamenejte si IP adresu síťového adaptéru, ke kterému chcete vytvořit vazby řadiče.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Vytvoření vazby síťového adaptéru k testovacímu kontroléru

1. V systému Microsoft Windows klikněte na tlačítko **Start**, do pole **Zahájit hledání** zadejte příkaz **Services. msc**a poté klikněte na tlačítko **ENTER**.

     Zobrazí se dialogové okno **služby** .

2. V podokně výsledků ve sloupci **název** klikněte pravým tlačítkem na službu **Visual Studio Test Controller** a zvolte možnost **zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte následující příkaz na příkazovém řádku:

     `net stop vsttcontroller`

3. Otevřete konfigurační soubor *QTCcontroller.exe.config* XML umístěný v umístění *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE*.

4. Vyhledejte `<appSettings>` značku.

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

5. Přidejte `BindTo` klíč k určení síťového adaptéru, který chcete použít v `<appSettings>` části.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Spusťte službu testovacího kontroléru. Pokud to chcete provést, spusťte na příkazovém řádku následující příkaz:

    `net start vsttcontroller`

    > [!WARNING]
    > Chcete-li připojit testovacího agenta k řadiči, je nutné znovu spustit instalaci testovacího agenta. Tentokrát zadejte IP adresu řadiče místo názvu kontroleru.

     To platí pro kontroler, službu agenta a proces agenta. `BindTo`Vlastnost musí být nastavena pro každý proces, který je spuštěn v počítači, který má více než jeden síťový adaptér. Postup pro nastavení `BindTo` vlastnosti je stejný pro všechny tři procesy, jak je uvedeno dříve v tomto tématu pro kontroler testů.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Svázání síťového rozhraní s testovacím agentem

1. V systému Microsoft Windows klikněte na tlačítko **Start**, do pole **Zahájit hledání** zadejte příkaz **Services. msc**a poté klikněte na tlačítko **ENTER**.

    Zobrazí se dialogové okno **služby** .

2. V podokně výsledků ve sloupci **název** klikněte pravým tlačítkem na službu **Visual Studio Test Agent** a zvolte možnost **zastavit**.

     -nebo-

     Otevřete příkazový řádek se zvýšenými oprávněními a spusťte následující příkaz na příkazovém řádku:

     **NET STOP vsttagent**

3. Otevřete konfigurační soubor *QTAgentService.exe.config* XML umístěný v umístění *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE*.

4. Vyhledejte `<appSettings>` značku.

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

5. Přidejte `BindTo` klíč k určení síťového adaptéru, který chcete použít v `<appSettings>` části.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Spusťte službu testovacího agenta. Pokud to chcete provést, spusťte na příkazovém řádku následující příkaz:

    `net start vsttagent`

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Změnit nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací kontroléry a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postupy: určení období časového limitu pro testovací kontroléry a testovací agenty](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
