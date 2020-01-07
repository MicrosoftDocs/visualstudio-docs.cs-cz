---
title: Časových limitů pro testovací Kontroléry a testovací agenty
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64ce566369f2c60a52e9026e8f92fc30836d523c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594757"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Postupy: nastavení časových limitů pro testovací kontroléry a testovací agenty

Testovací kontrolér a testovací agent mají několik nastavení časového limitu, které určují, jak dlouho musí čekat na odpovědi od sebe nebo od zdroje dat, než oznámí chybu. Za určitých okolností může být nutné upravit hodnoty časového limitu podle potřeb vaší topologie nebo jiných problémů prostředí. Chcete-li upravit hodnoty časového limitu, upravte konfigurační soubor XML, který je spojen s testovacím kontrolérem nebo agentem, jak je popsáno v následující postupy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li upravit testovací kontrolér nebo testovacího agenta různá nastavení časového limitu, upravte následující konfigurační soubory pomocí názvů klíčů a hodnot v tabulkách:

- Testovací kontrolér: *QTController.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Počet sekund čekání žádosti příkazu ping agenta, než bude připojení považováno ztratit.|"n" sekund.|
    |AgentSyncTimeoutInSeconds|Po spuštění synchronizace testovacího běhu, počet sekund čekání na synchronizaci před přerušením běhu všech agentů.|"n" sekund.|
    |AgentInitializeTimeout|Počet sekund čekání na všech agentech a jejich kolektorů dat inicializovat na začátku testu spusťte před přerušením testu. Tato hodnota by měla být přiměřeně velká, pokud používáte kolekce dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |AgentCleanupTimeout|Počet sekund čekání na všech agentech a jejich kolektorů dat na vyčištění před dokončením testového běhu. Tato hodnota by měla být přiměřeně velká, pokud používáte kolekce dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|

- Testovací Agent: *QTAgentService.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Počet sekund mezi jednotlivými pokusy o připojení k řadiči.|"n" sekund. Výchozí hodnota: "30" (třicet sekund).|
    |RemotingTimeoutSeconds|Maximální doba, kterou může vzdálené volání trvat během několika sekund.|"n" sekund. Výchozí hodnota: "600" (deset minut).|
    |StopTestRunCallTimeoutInSeconds|Počet sekund čekání na volání se zastavit testovací běh.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |GetCollectorDataTimeout|Počet sekund čekání na kolekce dat|"n" sekund. Výchozí hodnota: "300" (pět minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Určení možností vypršení časového limitu pro testovací kontrolér

1. Otevřít *QTCcontroller.exe.config* konfigurační soubor XML v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značky.

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

3. Upravte existující hodnotu pro jeden z klíčů časového limitu testovacího kontroléru. Například můžete změnit výchozí hodnotu pro klíč `AgentConnectionTimeoutInSeconds` ze dvou minut na tři minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -nebo-

    Přidejte další klíč a zadat hodnotu časového limitu. Například můžete přidat `AgentInitializeTimeout` klíče v `<appSettings>` části a zadejte hodnotu 5 minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Určení možností vypršení časového limitu pro testovacího agenta

1. Otevřít *QTAgentService.exe.config* konfigurační soubor XML v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značky.

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

3. Upravte existující hodnotu pro jeden z klíčů časového limitu testovacího agenta. Například můžete změnit výchozí hodnotu pro klíč `ControllerConnectionPeriodInSeconds` ze tří sekund na jednu minutu:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -nebo-

    Přidejte další klíč a zadat hodnotu časového limitu. Například můžete přidat `RemotingTimeoutSeconds` klíče v `<appSettings>` části a zadat hodnotu patnácti minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Úprava nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací kontroléry a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postupy: vytvoření vazby testovacího kontroléru nebo testovacího agenta na síťový adaptér](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
