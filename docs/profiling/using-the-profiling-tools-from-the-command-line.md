---
title: Použití Nástroje pro profilaci z Command-Line | Microsoft Docs
description: Pomocí nástrojů příkazového řádku sady Visual Studio Nástroje pro profilaci můžete Profilovat aplikace a automatizovat profilaci pomocí dávkových souborů a skriptování.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6cfb8f26486c731d3900522d72ac62ff6997005e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885947"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Použití Nástroje pro profilaci z příkazového řádku
Pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci můžete Profilovat aplikace na příkazovém řádku a automatizovat profilaci pomocí dávkových souborů a skriptování. Soubory sestav můžete také vygenerovat na příkazovém řádku. Pomocí zjednodušeného samostatného profileru můžete shromažďovat data na počítačích, které nejsou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nainstalované.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Nastavte umístění symbolů:** Chcete-li zobrazit názvy funkcí a parametrů, musí mít Profiler přístup k symbolu (.*PDB*) souborů profilování binárních souborů. Tyto soubory by měly obsahovat soubory symbolů pro operační systém a aplikace společnosti Microsoft, které chcete zobrazit ve vaší analýze. Pomocí veřejného serveru Microsoft symbol server se ujistěte, že máte správnou možnost. soubory *PDB* pro binární soubory Microsoftu | -   [Postupy: určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profilování aplikace:** Nástroje příkazového řádku a možnosti, které slouží k profilování cílové aplikace, závisí na typu aplikace, metodě profilování a na tom, zda je cílem spravovaná nebo nativní aplikace. | -   [Použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilovací služby](../profiling/command-line-profiling-of-services.md) |
| **Vytváření sestav. XML a. CSV:** Profilování v příkazovém řádku vytvoří datové soubory, které lze zobrazit v rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Můžete také vygenerovat. *XML* nebo hodnota oddělená čárkou (.*CSV*) souborů dat pomocí nástroje příkazového řádku VSPerfReport. | -   [Vytváření sestav profileru z příkazového řádku](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Profilování kódu na počítačích bez sady Visual Studio:** K shromažďování dat pro aplikace na počítačích, které nejsou nainstalované, můžete použít Nástroje pro profilaci samostatného profileru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . | -   [Postupy: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Reference
- [Odkaz na Nástroje pro profilaci příkazového řádku](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
