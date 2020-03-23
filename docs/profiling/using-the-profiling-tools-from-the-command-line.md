---
title: Použití nástrojů profilování z příkazového řádku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1420aa9f92e8ef7564478499c78393510ad61c23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778034"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Použití nástrojů profilování z příkazového řádku
Pomocí nástrojů příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů profilování můžete profilovat aplikace na příkazovém řádku a automatizovat profilování pomocí dávkových souborů a skriptování. Soubory sestav můžete také generovat na příkazovém řádku. Pomocí zjednodušeného samostatného profileru můžete shromažďovat data v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] počítačích, které nejsou nainstalovány.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Nastavte umístění symbolů:** Chcete-li zobrazit názvy funkcí a parametrů, profiler musí mít přístup k symbolu (.* pdb*) souborů profilovaných binárních souborů. Tyto soubory by měly obsahovat soubory symbolů pro operační systém společnosti Microsoft a aplikace, které chcete zobrazit v analýze. Veřejný server symbolů společnosti Microsoft můžete použít k zajištění správného nastavení . *pdb* soubory pro binární soubory společnosti Microsoft. | -   [Postup: Určení umístění souboru symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profilujte svou přihlášku:** Nástroje a možnosti příkazového řádku, které používáte k profilování cílové aplikace, závisí na typu aplikace, metodě profilování a na tom, zda je cíl spravovanou nebo nativní aplikací. | -   [Použití metod profilování z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilové služby](../profiling/command-line-profiling-of-services.md) |
| **Vytvořit sestavy XML a .csv:** Profilování na příkazovém řádku vytváří datové soubory, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]které lze zobrazit v rozhraní pro aplikaci . Můžete také generovat . xml *nebo* čárka-oddělené hodnoty (.* csv*) souborů dat pomocí nástroje příkazového řádku VSPerfReport. | -   [Vytvoření sestav profileru z příkazového řádku](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Kód profilu v počítačích bez sady Visual Studio:** Samostatný profiler nástroje profilování můžete použít ke shromažďování dat pro aplikace [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v počítačích, které nejsou nainstalovány. | -   [Postup: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Referenční informace
- [Odkaz na nástroje profilování příkazového řádku](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
