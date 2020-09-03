---
title: Testování výkonu cloudové služby | Microsoft Docs
description: Testování výkonu cloudové služby pomocí profileru sady Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: b1e5a5d4d5312968571965df8c9e28d31379720d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915606"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Testování výkonu cloudové služby
## <a name="overview"></a>Přehled
Výkon cloudové služby můžete testovat následujícími způsoby:

* Pomocí Azure Diagnostics můžete shromažďovat informace o požadavcích a připojeních a kontrolovat statistiky lokality, které ukazují, jak služba vykonává z perspektivy zákazníka. Informace o tom, jak začít, najdete v tématu [Konfigurace diagnostiky pro Azure Cloud Services a Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).
* Pomocí profileru sady Visual Studio můžete získat podrobnou analýzu výpočetních aspektů, jak se služba spouští. Jak je popsáno v tomto tématu, můžete použít profiler k měření výkonu jako služby běžící v Azure. Informace o tom, jak používat profiler k měření výkonu při místním spouštění služby v emulátoru výpočtů, najdete v tématu [testování výkonu cloudové služby Azure v místním počítači v emulátoru služby COMPUTE pomocí nástroje Visual Studio Profiler](https://azure.microsoft.com/documentation/articles/cloud-services-performance-testing-visual-studio-profiler/).

## <a name="choosing-a-performance-testing-method"></a>Výběr metody testování výkonu
### <a name="use-azure-diagnostics-to-collect"></a>Pro shromáždění použijte Azure Diagnostics:
* Statistika webových stránek a služeb, jako jsou požadavky a připojení.
* Statistika rolí, například jak často je role restartována.
* Celkové informace o využití paměti, jako je například procento času, který systém uvolňování paměti využívá, nebo paměťovou sadu spuštěné role.

### <a name="use-the-visual-studio-profiler-to"></a>Použijte Profiler sady Visual Studio k těmto akcím:
* Určete, které funkce se vybírají nejvíce času.
* Změřte, kolik času má každá součást výpočetně náročného programu.
* Porovnejte podrobné sestavy výkonu pro dvě verze služby.
* Analyzovat přidělování paměti podrobněji než úroveň individuálního přidělení paměti.
* Analyzujte problémy souběžnosti v kódu s více vlákny.

Když použijete Profiler, můžete shromažďovat data, když se cloudová služba spustí místně nebo v Azure.

### <a name="collect-profiling-data-locally-to"></a>Shromažďování dat profilování místně do:
* Otestujte výkon součásti cloudové služby, jako je třeba spuštění konkrétní role pracovního procesu, která nevyžaduje reálné simulované zatížení.
* V rámci kontrolovaných podmínek otestujte výkon cloudové služby v izolaci.
* Otestujte výkon cloudové služby předtím, než ji nasadíte do Azure.
* Otestujte výkon cloudové služby soukromě, aniž by došlo k narušení stávajících nasazení.
* Otestujte výkon služby bez poplatků za provoz v Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Shromažďování dat profilace v Azure do:
* Otestujte výkon cloudové služby v simulovaném nebo reálném zatížení.
* Použijte metodu instrumentace shromažďování dat profilace, jak je popsáno dále v tomto tématu.
* Otestujte výkon služby ve stejném prostředí, jako by služba běžela v produkčním prostředí.

Obvykle se simuluje zátěž pro testování cloudových služeb v podmínkách normálního nebo zátěže.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilace cloudové služby v Azure
Když publikujete cloudovou službu ze sady Visual Studio, můžete profilovat službu a zadat nastavení profilování, které vám poskytne požadované informace. Pro každou instanci role se spustí relace profilování. Další informace o tom, jak publikovat službu ze sady Visual Studio, najdete v tématu [publikování do cloudové služby Azure ze sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

Další informace o profilování výkonu v aplikaci Visual Studio naleznete v tématu [Příručka pro začátečníky k profilaci výkonu](https://msdn.microsoft.com/library/azure/ms182372.aspx) a [Analýza výkonu aplikace pomocí nástroje pro profilaci](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Když publikujete cloudovou službu, můžete povolit buď IntelliTrace, nebo profilaci. Nemůžete povolit obojí.
> 
> 

### <a name="profiler-collection-methods"></a>Metody kolekce profileru
V závislosti na vašich problémech s výkonem můžete použít různé metody shromažďování pro profilaci:

* **Vzorkování procesoru** – Tato metoda shromažďuje statistiky aplikací, které jsou užitečné při počáteční analýze problémů s využitím procesoru. Vzorkování procesoru je navrhovaná metoda pro spuštění většiny šetření výkonu. Při shromažďování dat vzorkování procesoru má aplikace profilaci, které vytváříte, má malý vliv.
* **Instrumentace** – Tato metoda shromažďuje detailní časová data, která jsou užitečná pro cílené analýzy a pro analýzu problémů s výkonem vstupu a výstupu. Metoda instrumentace zaznamenává každé zadání, ukončení a volání funkcí v modulu během běhu profilace. Tato metoda je užitečná pro shromažďování podrobných informací o časování oddílu kódu a pro porozumění dopadu vstupních a výstupních operací na výkon aplikace. Tato metoda je zakázána pro počítač s 32 operačním systémem. Tato možnost je dostupná jenom v případě, že spustíte cloudovou službu v Azure, ne místně v emulátoru služby Compute.
* **Alokace paměti .NET** – Tato metoda shromažďuje .NET Framework data o přidělování paměti pomocí metody profilace vzorkování. Shromážděná data zahrnují počet a velikost přidělených objektů.
* **Concurrency** – Tato metoda shromažďuje data kolizí prostředků a zpracovává a zpracovává data vláken, která jsou užitečná při analýze vícevláknových a vícevláknových aplikací. Metoda souběžnosti shromažďuje data pro každou událost, která blokuje provádění kódu, například když vlákno čeká na zamčený přístup k prostředku aplikace, který se má uvolnit. Tato metoda je užitečná pro analýzu aplikací s více vlákny.
* Můžete také povolit **profilaci interakce vrstev**, která poskytuje další informace o době spuštění synchronních volání ADO.NET ve funkcích vícevrstvých aplikací, které komunikují s jednou nebo více databázemi. Data interakce vrstev můžete shromáždit pomocí kterékoli z metod profilace. Další informace o profilování interakce vrstev najdete v tématu [zobrazení interakcí vrstev](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Konfigurace nastavení profilace
Následující obrázek ukazuje, jak nakonfigurovat nastavení profilování v dialogovém okně publikovat aplikaci Azure.

![Konfigurovat nastavení profilace](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Pokud chcete povolit zaškrtávací políčko **Povolit profilaci** , musíte mít nainstalovaný Profiler na místním počítači, který používáte k publikování cloudové služby. Ve výchozím nastavení se Profiler nainstaluje při instalaci sady Visual Studio.
> 
> 

### <a name="to-configure-profiling-settings"></a>Konfigurace nastavení profilace
1. V Průzkumník řešení otevřete místní nabídku pro projekt Azure a pak zvolte **publikovat**. Podrobné pokyny, jak publikovat cloudovou službu, najdete v tématu [publikování cloudové služby pomocí nástrojů Azure](vs-azure-tools-publishing-a-cloud-service.md).
2. V dialogovém okně **publikovat aplikaci Azure** zvolte kartu **Upřesnit nastavení** .
3. Chcete-li povolit profilaci, zaškrtněte políčko **Povolit profilování** .
4. Chcete-li konfigurovat nastavení profilace, vyberte hypertextový odkaz **Nastavení** . Zobrazí se dialogové okno nastavení profilace.
5. Z **toho, jakou metodu profilace chcete použít** , vyberte typ profilace, kterou potřebujete.
6. Chcete-li shromáždit data profilování interakce vrstev, zaškrtněte políčko **Povolit Profilování interakce vrstev** .
7. Nastavení uložíte tak, že kliknete na tlačítko **OK** .
   
    Při publikování této aplikace se tato nastavení použijí k vytvoření relace profilování pro každou roli.

## <a name="viewing-profiling-reports"></a>Zobrazení sestav profilace
Relace profilování se vytvoří pro každou instanci role v cloudové službě. Chcete-li zobrazit sestavy profilace každé relace ze sady Visual Studio, můžete zobrazit okno Průzkumník serveru a pak vybrat uzel Azure COMPUTE pro výběr instance role. Pak můžete zobrazit sestavu profilace, jak je znázorněno na následujícím obrázku.

![Zobrazit sestavu profilace z Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Zobrazení sestav profilace
1. Chcete-li zobrazit okno Průzkumník serveru v aplikaci Visual Studio, na panelu nabídek vyberte možnost zobrazení, Průzkumník serveru.
2. Zvolte uzel COMPUTE Azure a pak zvolte uzel nasazení Azure pro cloudovou službu, kterou jste vybrali k profilaci při publikování ze sady Visual Studio.
3. Chcete-li zobrazit sestavy profilování pro instanci, zvolte roli ve službě, otevřete místní nabídku pro určitou instanci a pak zvolte možnost **Zobrazit sestavu profilace**.
   
    Sestava, soubor. VSP, je teď stažená z Azure a stav stahování se zobrazí v protokolu aktivit Azure. Po dokončení stahování se sestava profilace zobrazí na kartě v editoru sady Visual Studio s názvem <název role \> *<číslo \> instance*<identifikátor \> . vsp. Zobrazí se souhrnná data pro sestavu.
4. Chcete-li zobrazit různá zobrazení sestavy, vyberte v seznamu aktuální zobrazení typ zobrazení, které chcete. Další informace najdete v tématu [Nástroje pro profilaci zobrazení sestav](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Další kroky
[Cloud Services ladění](vs-azure-tools-debugging-cloud-services-overview.md)

[Publikování do cloudové služby Azure ze sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)
