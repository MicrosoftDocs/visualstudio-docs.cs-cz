---
title: Konfigurace testovacích agentů a testovací kontrolery pro zátěžové testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1f33859522ff42fc85c31261527f17ea0f765199
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068014"
---
# <a name="configure-test-agents-and-test-controllers-for-running-load-tests"></a>Konfigurace testovacích agentů a testovací kontrolery pro spouštění zátěžových testů

Visual Studio může generovat simulované zatížení pro vaši aplikaci s využitím fyzických nebo virtuálních počítačů. Tyto počítače musíte nastavit jako jediný testovací kontrolér a jeden nebo více testovacích agentů. Testovací kontrolér a testovací agenty můžete použít k vygenerování větší zátěže, než jeden počítač můžete vygenerovat samostatně.

> [!NOTE]
> Cloudové zátěžové testování můžete použít také k poskytování virtuálních počítačů, které generují zatížení odpovídající mnoha uživatelům využívajícím web ve stejnou dobu. Další informace o cloudové zátěžové testování v [spuštění zátěžových testů pomocí testovacích plánů Azure](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektura simulace zátěže

Architektura simulace zátěže se skládá z klientské aplikace Visual Studio, testovacího kontroléru a testovacích agentů.

-   Klient se používá pro vývoj a spouštění testů a zobrazování jejich výsledků.

-   Testovací kontrolér slouží ke správě testovacích agentů a shromažďování výsledků testu.

-   Testovací agenty se používají ke spouštění testů a shromažďování dat včetně systémových informací a dat profilování ASP.NET definovaných v nastavení testu.

Tato architektura přináší následující výhody:

- Možnost škálovat generování zátěže přidáváním dalších testovacích agentů k testovacímu kontroléru.

- Pružnost při instalaci softwaru klientu, testovacího kontroléru a testovacího agentu na stejném počítači i různých počítačích. Příklad:

   **Místní konfigurace:**

  - Počítač 1: Visual Studio, kontrolér, agent.

    ![Místní počítače pomocí řadiče a agentů](./media/load-test-configa.png)

    **Typická Vzdálená konfigurace:**

  - Počítač 1 a 2: Visual Studio (více testerů může používat stejný kontrolér).

  - Počítač 3: Kontrolér (může mít nainstalovány také agenty).

  - Počítač 4 n: Agent nebo agenty přidružené ke kontroleru na počítač 3.

    ![Vzdálené počítače pomocí řadiče a agentů](./media/load-test-configb.png)

Přestože testovací kontrolér obvykle spravuje několik testovacích agentů, jeden agent může být přidružen pouze k jednomu kontroléru. Každý testovací agent může být sdílen týmem vývojářů. Tato architektura umožňuje snadno zvýšit počet testovacích agentů a generovat tak větší zátěž.

## <a name="test-agent-and-test-controller-interaction"></a>Testovací agent a testovací kontroler interakce

Testovací kontrolér spravuje sadu testovacích agentů pro spouštění testů. Řadič testů komunikuje s testovacími agenty pro spouštění testů, zastavování testů, stav testovacího agenta a shromažďování výsledků testu.

### <a name="test-controller"></a>Kontroler testů

Testovací kontrolér poskytuje obecnou architekturu pro spouštění testů a zahrnuje speciální funkce pro spouštění zátěžových testů. Testovací kontrolér odesílá zátěžový test všem testovacím agentům a čeká, dokud není test inicializován všemi agenty. Jsou-li všichni testovací agenti připraveni, řadič testů jim odešle zprávu, aby zahájili test.

### <a name="test-agent"></a>Testovací agent

Testovací agent je spouštěn jako služba, která naslouchá požadavkům testovacího kontroléru na spuštění nového testu. Když testovací agent obdrží žádost, služba testovacího agentu spustí proces, na kterém chcete spustit testy. Každý testovací agent spouští stejný zátěžový test.

 Testovacím agentům je správcem přiřazována váha a zátěž je přerozdělena dle váhy jednotlivých agentů. Pokud má například testovací agent 1 váhu 30 a testovací agent 2 váhu 70, přičemž je zátěž nastavena na 1000 uživatelů, testovací agent 1 simuluje 300 virtuálních uživatelů, zatímco testovací agent 2 jich simuluje 700. Zobrazit [Správa testovacích kontrolérů a testovacích agentů v sadě Visual Studio](../test/manage-test-controllers-and-test-agents.md).

 Testovací agent přijímá jako vstup sadu testů a sadu parametrů simulace. Klíčovým konceptem je, že platí bez ohledu na počítači, kde budete spouštět testy.

## <a name="test-controller-and-test-agent-connection-points"></a>Testovací kontrolér a testovací agent spojovacích bodů

Následující obrázek znázorňuje spojovací body mezi testovacím kontrolérem, testovacím agentem a klientem. Poskytuje přehled o používaných portech pro příchozí a odchozí připojení, jakož i omezení zabezpečení použité na těchto portech.

 ![Testovací řadiče a testovací agent portů a zabezpečení](./media/test-controller-agent-firewall.png)

 Další informace najdete v části [konfigurace portů pro testovací kontrolery a testovací agenty](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informace o instalaci řadiče a agentů testu

Důležité informace o požadavcích na hardware a software pro testovací kontroléry a testovací agenty, naleznete v tématu postupy pro jejich instalace a konfigurace prostředí pro zajištění optimálního výkonu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Použít testovací kontrolér a testovací agent s testy jednotek

Po instalaci testovacího kontroléru a jednoho nebo více agentů lze v nastavení zátěžových testů určit, zda má být u kontroléru používáno vzdálené spuštění. Dále lze v nastavení testu určit datové a diagnostické adaptéry, které mají být použity spolu s rolí přidruženou k agentům.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)