---
title: Období časového limitu pro testovací kontroléry a testovací agenty
description: Přečtěte si, jak změnit hodnoty časového limitu testovacího kontroléru a testovacího agenta úpravou přidružených konfiguračních souborů XML.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dc661999eb12bb679aa3622f0f14adc3ffc661a
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330001"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Postupy: určení období časového limitu pro testovací kontroléry a testovací agenty

Testovací kontrolér a testovací agent mají několik nastavení časového limitu, které určují, jak dlouho by měly čekat na odpovědi od sebe, nebo ze zdroje dat, než se nezdaří s chybou. Za určitých okolností může být nutné upravit hodnoty časového limitu tak, aby splňovaly požadavky vaší topologie nebo jiné problémy s prostředím. Chcete-li upravit hodnoty časového limitu, upravte konfigurační soubor XML, který je přidružen buď k testovacímu kontroléru, nebo k testovacímu agentovi, jak je popsáno v následujících postupech.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li upravit nastavení časového limitu testovacího kontroléru nebo testovacího agenta, upravte následující konfigurační soubory pomocí názvů klíčů a hodnot v tabulkách:

- Kontroler testů: *QTController.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Počet sekund, po které se má počkat, než se připojení považuje za ztracené.|"n" sekund.|
    |AgentSyncTimeoutInSeconds|Když zahájíte synchronizaci testovacího běhu, počet sekund, po které se bude čekat na synchronizaci všech agentů před přerušením spuštění.|"n" sekund.|
    |AgentInitializeTimeout|Počet sekund, po které se má čekat na inicializaci všech agentů a jejich kolekcí dat na začátku testovacího běhu, než se testovací běh přeruší. Tato hodnota by měla být rozumně velká, pokud se používají sběrače dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |AgentCleanupTimeout|Počet sekund, po které se má čekat na vyčištění všech agentů a jejich kolekcí dat před dokončením testovacího běhu. Tato hodnota by měla být rozumně velká, pokud se používají sběrače dat.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|

- Testovací agent: *QTAgentService.exe.config*

    |Název klíče|Popis|Hodnota|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Počet sekund mezi pokusy o připojení k řadiči.|"n" sekund. Výchozí hodnota: "30" (třicet sekund).|
    |RemotingTimeoutSeconds|Maximální doba, po kterou může volání vzdálené komunikace trvat v sekundách.|"n" sekund. Výchozí hodnota: "600" (deset minut).|
    |StopTestRunCallTimeoutInSeconds|Počet sekund, po který se má čekat na ukončení testu.|"n" sekund. Výchozí hodnota: "120" (dvě minuty).|
    |GetCollectorDataTimeout|Počet sekund čekání na shromažďování dat|"n" sekund. Výchozí hodnota: "300" (pět minut).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Určení možností časového limitu agenta pro kontroler testů

1. Otevřete konfigurační soubor *QTCcontroller.exe.config* XML umístěný v *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značku.

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

3. Upravte existující hodnotu pro jeden z klíčů časového limitu testovacího kontroléru. Například můžete změnit výchozí hodnotu klíče `AgentConnectionTimeoutInSeconds` ze dvou minut na tři minuty:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -nebo-

    Přidejte další klíč a zadejte hodnotu časového limitu. Můžete například přidat `AgentInitializeTimeout` klíč do `<appSettings>` oddílu a zadat hodnotu pět minut:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Určení možností časového limitu agenta pro testovacího agenta

1. Otevřete konfigurační soubor *QTAgentService.exe.config* XML umístěný v *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Vyhledejte `<appSettings>` značku.

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

3. Upravte existující hodnotu pro jeden z klíčů časového limitu testovacího agenta. Můžete například změnit výchozí hodnotu klíče `ControllerConnectionPeriodInSeconds` ze třicet sekund na jednu minutu:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -nebo-

    Přidejte další klíč a zadejte hodnotu časového limitu. Můžete například přidat `RemotingTimeoutSeconds` klíč do `<appSettings>` oddílu a zadat hodnotu 15 minut:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
- [Změnit nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)
- [Konfigurace portů pro testovací kontroléry a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Postupy: vytvoření vazby kontroleru testů nebo testovacího agenta na síťový adaptér](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
