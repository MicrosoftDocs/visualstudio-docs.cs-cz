---
title: 'Postupy: omezení instrumentace na konkrétní knihovny DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc2fe8e6f9b0ed1e6970943ab5eedf1b62eb961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807730"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Postupy: Omezení instrumentace na konkrétní knihovny DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí metody profilace instrumentace můžete omezit shromažďování dat profilování na jednu nebo více knihoven DLL v aplikaci. Chcete-li profilovat jednu nebo více knihoven DLL v aplikaci, vytvořte relaci výkonu, která zahrnuje soubory. dll jako cíle. Můžete určit knihovny DLL, které chcete profilovat jako projekty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení nebo jako nezávislé binární soubory.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Omezení instrumentace na konkrétní knihovny DLL v řešení sady Visual Studio  
  
1. Otevřete řešení, které obsahuje knihovnu DLL v [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
2. V nabídce **analyzovat** vyberte možnost **Spustit Průvodce výkonem**.  
  
3. Jako metodu profilace zvolte **instrumentace** a pak klikněte na **Další**.  
  
4. Z **toho, který z následujících dostupných cílů chcete profilovat?** vyberte název projektu. dll a pak klikněte na **Další**.  
  
5. Kliknutím na tlačítko **Dokončit** ukončíte průvodce a zobrazíte novou relaci výkonu v okně **prohlížeč výkonu** .  
  
6. Klikněte pravým tlačítkem na **cíle** a pak vyberte **Přidat cílový projekt**.  
  
7. V seznamu **Přidat cílový projekt** vyberte spustitelný projekt, který chcete použít pro cvičení knihovny DLL.  
  
     Nepovinný parametr. Můžete přidat všechny projekty knihoven DLL, které chcete profilovat.  
  
8. Chcete-li zabránit shromažďování dat pro přidaný projekt, klikněte pravým tlačítkem myši na název projektu a poté zrušte zaškrtnutí políčka **instrumentace** .  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Určení specifických knihoven DLL pro profilování jako nezávislých binárních souborů  
  
1. Otevřete [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
2. V nabídce **analyzovat** vyberte možnost **Spustit Průvodce výkonem**.  
  
3. Z **toho, který z následujících dostupných cílů byste chtěli profilovat**, vyberte **profil knihovny DLL (. DLL)** a poté klikněte na tlačítko **Další**.  
  
4. Na druhé stránce průvodce proveďte následující kroky:  
  
    - Zadejte cestu a název souboru. dll, který chcete profilovat v **cestě DLL**. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledat soubor v dialogovém okně **Knihovna dynamického propojení do profilu** . Všimněte si, že je nutné zadat kopii souboru. dll, který bude spuštěn spustitelným souborem (. exe), který vyberete další.  
  
    - Zadejte cestu a název souboru spustitelného souboru (. exe), který bude v **cestě ke spustitelnému**souboru vykonat. dll. Můžete také kliknout na tlačítko se třemi tečkami (...) a vyhledat soubor v dialogovém okně **spustitelného souboru, který se má spustit** .  
  
    - Nepovinný parametr. Zadejte argumenty příkazového řádku, které chcete předat spustitelnému souboru v **argumentech příkazového řádku**. V případě potřeby zadejte pracovní adresář pro aplikaci v **pracovním adresáři**.  
  
    - Klikněte na **Next** (Další).  
  
5. Jako metodu profilace zvolte **instrumentace** a pak klikněte na **Další**.  
  
6. Kliknutím na tlačítko **Dokončit** ukončíte průvodce a zobrazíte novou relaci výkonu v okně **prohlížeč výkonu** .  
  
7. Nepovinný parametr. Chcete-li přidat další soubory DLL, klikněte pravým tlačítkem myši na možnost **cíle** a poté vyberte možnost **Přidat cílový binární soubor**. Vyberte soubory z dialogového okna **Přidat cílový binární soubor** .  
  
    > [!NOTE]
    > Nezadávejte spustitelný soubor (. exe), který vykonává knihovny DLL.  
  
## <a name="see-also"></a>Viz také  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Postupy: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
