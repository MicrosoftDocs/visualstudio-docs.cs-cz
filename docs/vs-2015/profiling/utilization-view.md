---
title: Zobrazení využití | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 238d821795aaa4e9ef0ac06e117316450b46fda4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145374"
---
# <a name="utilization-view"></a>Zobrazení využití
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zobrazení využití** zobrazuje informace o procesoru, GPU a dalších systémových prostředcích, které jsou používány aktuálním procesem. Zobrazuje průměrné využití jádra analyzovaným procesem, nečinného procesu, systémového procesu a dalších procesů, které v systému běží v průběhu času. Nezobrazuje, které konkrétní jádro je v určitou dobu aktivní. Například pokud jsou dvě jádra spuštěny na úrovni 50% kapacity za dané časové období, pak toto zobrazení ukazuje, že je využíváno jedno logické jádro. Zobrazení je vygenerováno vydělením času profilace na krátké časové segmenty. Pro každý segment graf znázorňuje průměrný počet vláken procesů, které jsou během daného intervalu spuštěny na logických jádrech.  
  
 ![Zobrazení využití procesoru](../profiling/media/vsts-ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 Graf znázorňuje čas (na ose x) a průměrné logické jádra, které jsou využívány cílovým procesem, nečinným procesem a procesem systému. (Nečinný proces zobrazuje jádra nečinných. Systémový proces je proces ve Windows, který může provádět práci jménem jiných procesů.) Zbývající procesy, které jsou spuštěny na účtu systému pro využití všech zbývajících jader.  
  
 Počet logických jader se zobrazuje na ose y. Systém Windows zpracovává souběžnou podporu multithreadingu v hardwaru jako logické jádra (například technologie Hyper-Threading). Proto systém, který má čtyřjádrový procesor, který podporuje dvě hardwarové vlákna na jádro, se zobrazí jako systém se osm logickými jádry. To platí i pro zobrazení jader. Další informace najdete v tématu [zobrazení jader](../profiling/cores-view.md).  
  
 Graf aktivity GPU zobrazuje počet používaných modulů DirectX v průběhu času.  Modul se používá, pokud zpracovává paket DMA.  V grafu se nezobrazuje konkrétní modul DirectX (například 3D modul, video stroj a ostatní).  
  
## <a name="purpose"></a>Účel  
 Když použijete Vizualizátor souběžnosti, doporučujeme zobrazení využití jako výchozí bod pro vyšetřování výkonu. Vzhledem k tomu, že poskytuje přehled o stupních souběžnosti v aplikaci v čase, můžete ho použít k rychlé identifikaci oblastí, které vyžadují vyladění výkonu nebo paralelní zpracování.  
  
 Pokud vás zajímá ladění výkonu, možná se snažíte identifikovat chování, které nesplňuje vaše očekávání. Můžete také vyhledat existenci a příčinu oblastí, které mají nízké využití logických jader procesoru. Můžete také vyhledat vzory využití mezi CPU a GPU.  
  
 Pokud vás zajímá virtuálního aplikaci, pravděpodobně si vyhledáte oblasti spuštění vázané na procesor nebo oblasti, kde nevyužíváte procesor.  
  
 Oblasti vázané na procesor jsou zelené. Graf ukazuje, že pokud je aplikace sériová, je využívána jedním jádrem.  
  
 Oblasti, ve kterých nevyužíváte CPU, jsou šedé. Ty můžou představovat body, ve kterých je aplikace nečinná, nebo zablokované vstupně-výstupní operace, které poskytují příležitosti pro paralelismus překrývajícími se s ostatními práce vázané na procesor.  
  
 Když zjistíte chování, můžete ho v této oblasti přiblížit tak, že ho vyberete. Po přiblížení můžete přepnout do zobrazení vlákna nebo zobrazení jádra pro podrobnější analýzu.  
  
 Pokud používáte GPU pomocí C++ AMP nebo DirectX, může vás zajímat, jak zjistit počet používaných motorů GPU nebo v oblastech, ve kterých je GPU neočekávaně nečinný.  
  
## <a name="zooming"></a>Přibližování  
 Pokud se chcete přiblížit do grafu využití procesoru nebo grafu aktivity GPU, vyberte oddíl nebo použijte nástroj Lupa nad grafem. Nastavení přiblížení zůstává při přepínání na další zobrazení. K opětovnému přiblížení použijte nástroj Lupa posuvníku. Můžete také zvětšit pomocí kombinace kláves CTRL + SCROLL.  
  
## <a name="see-also"></a>Viz také  
 [Vizualizátor souběžnosti](../profiling/concurrency-visualizer.md)   
 [Zobrazení jader](../profiling/cores-view.md)
