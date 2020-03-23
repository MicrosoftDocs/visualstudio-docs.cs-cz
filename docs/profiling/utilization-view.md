---
title: Zobrazení využití | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 926c67261f91aa8787d9be4a33dadbd3a890c568
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62823518"
---
# <a name="utilization-view"></a>Zobrazení využití
**Zobrazení Využití** zobrazuje informace o procesoru, GPU a dalších systémových prostředcích, které používá aktuální proces (zvolte **Analyzovat** > **vizualizaci souběžnosti** a spusťte vizualizér souběžnosti). Zobrazuje průměrné využití jádra analyzovaným procesem, nečinným procesem, procesem systému a dalšími procesy, které jsou v systému spuštěny v průběhu času. Neukazuje, které konkrétní jádro je v daném okamžiku aktivní. Například pokud jsou dvě jádra spuštěna s kapacitou 50 procent pro dané časové období, pak toto zobrazení ukazuje, že se využívá jedno logické jádro. Zobrazení je generováno rozdělením doby profilování na krátké časové segmenty. Pro každý segment graf vykresluje průměrný počet vláken procesu, které jsou spuštěny na logických jádrech během tohoto intervalu.

 ![Zobrazení využití procesoru](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Graf zobrazuje čas (na ose x) a průměrná logická jádra, která jsou využívána cílovým procesem, nečinným procesem a procesem systému. (Nečinný proces zobrazuje nečinná jádra. Systémový proces je proces v systému Windows, který může provádět práci jménem jiných procesů.) Zbývající procesy, které jsou spuštěny v systému účet pro využití všech zbývajících jader.

 Počet logických jader je zobrazen na ose y. Systém Windows považuje podporu souběžných vícevláken v hardwaru za logická jádra (například Hyper-Threading). Proto systém, který má čtyřjádrový procesor, který podporuje dvě hardwarová vlákna na jádro, se zobrazí jako systém s osmi logickými jádry. To platí i pro zobrazení Jádra. Další informace naleznete v [tématu Cores view](../profiling/cores-view.md).

 Graf aktivity GPU zobrazuje počet motorů DirectX, které se v průběhu času používají.  Modul se používá, pokud zpracovává paket DMA.  Graf nezobrazuje konkrétní modul DirectX (například 3D engine, video engine a ostatní).

## <a name="purpose"></a>Účel
 Doporučujeme zobrazení využití jako výchozí bod pro vyšetřování výkonu při použití vizualizátoru souběžnosti. Vzhledem k tomu, že poskytuje přehled o stupni souběžnosti v aplikaci v průběhu času, můžete ji použít k rychlé identifikaci oblastí, které vyžadují ladění výkonu nebo paralelizace.

 Pokud máte zájem o ladění výkonu, můžete se pokusit identifikovat chování, které nesplňuje vaše očekávání. Můžete také hledat existenci a příčinu oblastí, které mají nízké využití logických procesorových jader. Můžete také hledat vzory využití mezi CPU a GPU.

 Pokud máte zájem o paralelizaci aplikace, pravděpodobně hledáte oblasti provádění vázané na procesor nebo oblasti, kde nepoužíváte procesor.

 Oblasti vázané na procesor jsou zelené. Graf ukazuje jedno jádro, které je využíváno, pokud je aplikace sériová.

 Oblasti, kde procesor nepoužíváte, jsou šedé. Ty mohou představovat body, ve kterých je aplikace nečinná nebo provádění blokování vstupně-výstupních, které poskytují příležitosti pro paralelismus překrýváním s jiným i min. cpu vázané práce.

 Když najdete chování, které vás zajímá, můžete tuto oblast přiblížit výběrem. Po přiblížení můžete přepnout do zobrazení vláken nebo zobrazení jader pro podrobnější analýzu.

 Pokud používáte GPU pomocí C++ AMP nebo DirectX, může vás zajímat identifikace počtu modulů GPU v provozu nebo oblastí, kde je GPU neočekávaně nečinné.

## <a name="zoom"></a>Zoom
 Chcete-li přiblížit graf využití procesoru nebo graf aktivity GPU, vyberte oddíl nebo použijte nástroj posuvník lupy nad grafem. Při přepnutí do jiných zobrazení nastavení lupy přetrvává. Chcete-li zobrazení znovu oddálit, použijte nástroj pro posuvník lupy. Můžete také přiblížit pomocí **ctrl**+**scroll**.

## <a name="see-also"></a>Viz také
- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
- [Zobrazení Jader](../profiling/cores-view.md)