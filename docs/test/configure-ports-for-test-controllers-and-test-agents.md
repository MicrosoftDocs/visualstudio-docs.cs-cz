---
title: Konfigurace portů pro testovací kontroléry a testovací agenty
description: Naučte se, jak změnit výchozí příchozí porty používané testovacím kontrolérem, testovacím agentem a klientem, aby nedocházelo ke konfliktům s jiným softwarem.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2726d489c0c67bffb11bc59357f6ad107a6c94ba
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441565"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurace portů pro testovací kontroléry a testovací agenty

Můžete změnit výchozí příchozí porty používané testovacím kontrolérem, testovacím agentem a klientem. To může být nutné v případě, že se pokoušíte použít testovací kontrolér, testovacího agenta nebo klienta společně s nějakým jiným softwarem, který je v konfliktu s nastavením portu. Dalším důvodem pro změnu portů je omezení brány firewall mezi testovacím kontrolérem a klientem. V takovém případě můžete port ručně nakonfigurovat tak, aby vyhovoval jeho povolení pro bránu firewall, aby řadič testu mohl odeslat výsledky klientovi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující ilustrace znázorňuje spojovací body mezi testovacím kontrolérem, testovacím agentem a klientem. Popisuje, které porty se používají pro příchozí a odchozí připojení a také omezení zabezpečení používaná na těchto portech.

![Testovací kontrolér a porty a zabezpečení testovacího agenta](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Příchozí připojení

Výchozí port používaný řadičem testu je 6901 a výchozí port testovacího agenta je 6910. Klient ve výchozím nastavení používá náhodný port, který se používá k získání výsledků testů z kontroleru testů. U všech příchozích připojení kontroler testů ověřuje volající stranu a ověřuje, že patří do konkrétní skupiny zabezpečení.

- **Test Controller** Příchozí připojení jsou na portu TCP 6901. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [Konfigurace příchozích portů](#configure-the-incoming-ports).

    Kontroler testů musí být schopný vytvořit odchozí připojení k testovacím agentům a klientovi.

    > [!NOTE]
    > Kontroler testů potřebuje otevřené příchozí připojení pro **sdílení souborů a tiskáren** .

- **Testovací agent** Příchozí připojení jsou na portu TCP 6910. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [Konfigurace příchozích portů](#configure-the-incoming-ports).

   Testovací agent musí být schopný vytvořit odchozí připojení k testovacímu kontroléru.

- **Klient** Ve výchozím nastavení se pro příchozí připojení používá náhodný port TCP. Pokud potřebujete, můžete nakonfigurovat příchozí port. Další informace najdete v tématu [Konfigurace příchozích portů](#configure-the-incoming-ports).

   Můžete obdržet oznámení brány firewall, když se testovací kontrolér pokusí poprvé připojit ke klientovi.

   V systému Windows Server 2008 jsou oznámení brány firewall ve výchozím nastavení zakázána a je nutné ručně přidat výjimky brány firewall pro klientské programy (*devenv.exe*, *mstest.exe* *mlm.exe*), aby mohl přijímat příchozí připojení.

## <a name="outgoing-connections"></a>Odchozí připojení

Pro všechna odchozí připojení se používají náhodné porty TCP.

- **Test Controller** Kontroler testů musí být schopný vytvořit odchozí připojení k agentům a klientovi.

- **Testovací agent** Testovací agent musí být schopný vytvořit odchozí připojení k řadiči.

- **Klient** Klient musí být schopný vytvořit odchozí připojení k řadiči.

## <a name="configure-the-incoming-ports"></a>Konfigurace příchozích portů

Postupujte podle těchto pokynů ke konfiguraci portů pro testovací kontrolér a testovací agenty.

- **Služba kontroleru** Upravte hodnotu portu úpravou souboru *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* :

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Služba agenta** Upravte port úpravou souboru *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* :

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Klient** Pomocí Editoru registru přidejte následující hodnoty registru (**DWORD**). Klient bude používat jeden z portů ze zadaného rozsahu pro příjem dat z kontroleru testů:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
