---
title: Konfigurace testovacích agentů a testovacích řadičů pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8824e1836d8a49de91cf0e3b9cccf2e85a7de18
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597344"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Přehled testovacích agentů a testovacích regulátorů pro spuštění zátěžových testů

Visual Studio můžete generovat simulované zatížení pro vaši aplikaci pomocí fyzických nebo virtuálních počítačů. Tyto počítače musí být nastaveny jako jeden zkušební řadič a jeden nebo více testovacích agentů. Testovací řadič a testovací agenti můžete použít ke generování většího zatížení, než může generovat jeden počítač samostatně.

> [!NOTE]
> Cloudové zátěžové testování můžete také použít k poskytování virtuálních počítačů, které generují zatížení mnoha uživatelů, kteří přistupují k vašemu webu ve stejnou dobu. Použití nastavení testovacího řadiče nebo testovacího agenta na virtuálních počítačích hostovaných v cloudu však není podporováno. Další informace o cloudové zátěžové testování na [spuštění zátěžových testů pomocí plánů testování Azure](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektura simulace zatížení

Architektura simulace zátěže se skládá z klientské aplikace Visual Studio, testovacího kontroléru a testovacích agentů.

- Klient se používá pro vývoj a spouštění testů a zobrazování jejich výsledků.

- Testovací kontrolér slouží ke správě testovacích agentů a shromažďování výsledků testu.

- Testovací agenty se používají ke spouštění testů a shromažďování dat včetně systémových informací a dat profilování ASP.NET definovaných v nastavení testu.

Tato architektura přináší následující výhody:

- Možnost škálovat generování zátěže přidáváním dalších testovacích agentů k testovacímu kontroléru.

- Pružnost při instalaci softwaru klientu, testovacího kontroléru a testovacího agentu na stejném počítači i různých počítačích. Například:

   **Místní konfigurace:**

  - Počítač 1: Visual Studio, kontrolér, agent.

    ![Místní počítač používající řadič a agenta](./media/load-test-configa.png)

    **Typická vzdálená konfigurace:**

  - Počítač 1 a 2: Visual Studio (více testerů může používat stejný kontrolér).

  - Počítač 3: Kontrolér (může mít nainstalovány také agenty).

  - Machine4-n: Agent nebo agenti jsou všichni přidruženi k ovladači na počítači3.

    ![Vzdálené stroje používající regulátor a agenty](./media/load-test-configb.png)

Přestože testovací kontrolér obvykle spravuje několik testovacích agentů, jeden agent může být přidružen pouze k jednomu kontroléru. Každý testovací agent může být sdílen týmem vývojářů. Tato architektura umožňuje snadno zvýšit počet testovacích agentů a generovat tak větší zátěž.

## <a name="test-agent-and-test-controller-interaction"></a>Interakce testovacího agenta a testovacího regulátoru

Testovací kontrolér spravuje sadu testovacích agentů pro spouštění testů. Řadič testu komunikuje s testovacími agenty, aby zahájil testy, zastavil testy, sledoval stav testovacího agenta a shromažďoval výsledky testů.

### <a name="test-controller"></a>Zkušební ovladač

Testovací kontrolér poskytuje obecnou architekturu pro spouštění testů a zahrnuje speciální funkce pro spouštění zátěžových testů. Testovací kontrolér odesílá zátěžový test všem testovacím agentům a čeká, dokud není test inicializován všemi agenty. Jsou-li všichni testovací agenti připraveni, řadič testů jim odešle zprávu, aby zahájili test.

### <a name="test-agent"></a>Testovací činidlo

Testovací agent je spouštěn jako služba, která naslouchá požadavkům testovacího kontroléru na spuštění nového testu. Když testovací agent obdrží požadavek, služba testovacího agenta spustí proces, na kterém chcete spustit testy. Každý testovací agent spouští stejný zátěžový test.

Testovacím agentům je správcem přiřazována váha a zátěž je přerozdělena dle váhy jednotlivých agentů. Pokud má například testovací agent 1 váhu 30 a testovací agent 2 váhu 70, přičemž je zátěž nastavena na 1000 uživatelů, testovací agent 1 simuluje 300 virtuálních uživatelů, zatímco testovací agent 2 jich simuluje 700. Viz [Správa testovacích řadičů a testovacích agentů pomocí sady Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Testovací agent provede sadu testů a sadu parametrů simulace jako vstup. Klíčovým konceptem je, že testy jsou nezávislé na počítači, kde jsou spuštěny.

## <a name="test-controller-and-test-agent-connection-points"></a>Testovací řadič a spojovací body testovacího agenta

Následující obrázek znázorňuje spojovací body mezi testovacím kontrolérem, testovacím agentem a klientem. Popisuje, které porty se používají pro příchozí a odchozí připojení, stejně jako omezení zabezpečení používané na těchto portech.

![Testovací řadič a porty testovacího agenta a zabezpečení](./media/test-controller-agent-firewall.png)

Další informace naleznete [v tématu Konfigurace portů pro testovací řadiče a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informace o zkušebním řadiči a instalaci agenta

Důležité informace o hardwarových a softwarových požadavcích na testovací řadiče a testovací agenty, postupech jejich instalace a konfiguraci prostředí pro optimální výkon naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Použijte zkušební regulátor a testovacího agenta s jednotkovými testy

Po instalaci testovacího kontroléru a jednoho nebo více agentů lze v nastavení zátěžových testů určit, zda má být u kontroléru používáno vzdálené spuštění. Dále lze v nastavení testu určit datové a diagnostické adaptéry, které mají být použity spolu s rolí přidruženou k agentům.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
