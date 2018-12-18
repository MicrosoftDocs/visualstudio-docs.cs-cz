---
title: 'Postupy: omezení instrumentace na konkrétní knihovny DLL | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 054a281d445f5910e9a2d635bb453dd283425453
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803458"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Postupy: Omezení instrumentace na konkrétní knihovny DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí metody profilace instrumentace můžete omezit shromažďování dat profilování na jeden nebo více knihovny DLL v aplikaci. Chcete-li Profilovat jeden nebo více knihoven DLL v aplikaci, vytvoříte relace výkonu, který obsahuje soubory .dll jako cíle. Můžete určit knihovny DLL, které chcete Profilovat jako projekty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení nebo jako nezávislé binární soubory.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>K omezení instrumentace na konkrétní knihovny DLL v řešení sady Visual Studio  
  
1.  Otevřete řešení, které obsahuje knihovnu DLL v [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Na **analyzovat** nabídce vyberte možnost **spustit Průvodce výkonem**.  
  
3.  Zvolte **instrumentace** jako metodu profilace a pak klikněte na tlačítko **Další**.  
  
4.  Z **které z následujících dostupných cílů chcete profil?**, vyberte název projektu knihovny DLL a potom klikněte na tlačítko **Další**.  
  
5.  Klikněte na tlačítko **Dokončit** ukončíte průvodce a zobrazí novou relaci výkonu v **prohlížeč výkonu** okna.  
  
6.  Klikněte pravým tlačítkem na **cíle** a pak vyberte **přidat cílový projekt**.  
  
7.  Z **přidat cílový projekt** vyberte spustitelný projekt, který chcete použít k knihovny DLL.  
  
     Volitelné. Můžete přidat všechny projekty knihovny DLL, které chcete do profilu.  
  
8.  Zabránění shromažďování dat pro přidání projektu, klikněte pravým tlačítkem na název projektu a poté zrušte zaškrtnutí **instrumentace** zaškrtávací políčko.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Chcete-li určit konkrétní knihovny DLL do profilu jako nezávislé binárních souborů  
  
1.  Otevřít [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2.  Na **analyzovat** nabídce vyberte možnost **spustit Průvodce výkonem**.  
  
3.  Z **které z následujících dostupných cílů chcete profil**, vyberte **Profilovat dynamickou knihovnu (. Knihovny DLL)** a potom klikněte na tlačítko **Další**.  
  
4.  Na druhé stránce průvodce proveďte následující kroky:  
  
    -   Zadejte název a cesta k souboru, který chcete profil v souboru .dll **cesta ke knihovně Dll**. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledejte soubor v **dynamické knihovny DLL do profilu** dialogové okno. Všimněte si, že je nutné zadat kopie souboru .dll, který se spustí spustitelný soubor (.exe) soubor, který zvolíte Další.  
  
    -   Zadejte název a cesta k souboru spustitelný soubor (.exe), který bude vykonávat DLL v **cesta ke spustitelnému souboru**. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledejte soubor v **spustitelný soubor ke spuštění** dialogové okno.  
  
    -   Volitelné. Zadejte jakékoli argumenty příkazového řádku, které chcete předat do spustitelného souboru v **argumenty příkazového řádku**. V případě potřeby zadejte pracovní adresář pro aplikaci v **pracovní adresář**.  
  
    -   Klikněte na tlačítko **Další**.  
  
5.  Zvolte **instrumentace** jako metodu profilace a pak klikněte na tlačítko **Další**.  
  
6.  Klikněte na tlačítko **Dokončit** ukončíte průvodce a zobrazí novou relaci výkonu v **prohlížeč výkonu** okna.  
  
7.  Volitelné. Pokud chcete přidat další soubory .dll, klikněte pravým tlačítkem na **cíle** a pak vyberte **přidat cílový binární**. Vyberte soubory z **přidat cílový binární** dialogové okno.  
  
    > [!NOTE]
    >  Nezadávejte spustitelný soubor (.exe), která zpracovává knihovny DLL.  
  
## <a name="see-also"></a>Viz také  
 [Řízení sběru dat](../profiling/controlling-data-collection.md)   
 [Postupy: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)



