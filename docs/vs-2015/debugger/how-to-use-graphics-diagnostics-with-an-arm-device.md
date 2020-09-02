---
title: 'Postupy: použití Diagnostika grafiky se zařízením ARM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685865"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Postupy: Použití diagnostiky grafiky se zařízením ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostika grafiky podporuje vzdálené ladění aplikací Direct3D na zařízeních založených na ARM, na kterých běží Windows RT 8,1 nebo Windows Phone 8,1. Můžete zachytit informace grafiky z aplikace Direct3D během jejího spuštění na zařízení nebo použít zařízení jako počítač pro přehrávání pro dříve zachycené informace grafiky.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Použití Diagnostika grafiky se zařízením s procesorem ARM  
 Vzhledem k tomu, že Visual Studio neběží na zařízeních s procesorem ARM, je nutné použít vzdálený ladicí program k analýze aplikace, která na nich běží. Vzdálený ladicí program podporuje zachycení a přehrávání grafiky, aby bylo možné diagnostikovat chyby při vykreslování a vyhodnocovat výkon grafiky v těchto zařízeních stejně snadno, jak můžete na nich ladit aplikaci.  
  
 Pokud chcete používat funkce diagnostiky grafiky, nejdřív na svém zařízení povolte vzdálené ladění.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Povolení vzdáleného ladění na zařízení s procesorem ARM  
  
1. Na zařízení s procesorem ARM nainstalujte [zásadu ARM Kit](https://msdn.microsoft.com/windows/desktop/dn469188) .  
  
2. Nainstalujte [Nástroje pro vzdálené ladění](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) na zařízení s procesorem ARM.  
  
> [!IMPORTANT]
> U zařízení Windows Phone 8,1 možná budete muset zaregistrovat svůj telefon pro vývoj. K tomu musíte být registrovaný vývojář. Další informace najdete v tématu [nasazení a spuštění aplikace pro Windows Phone 8](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Jakmile na svém zařízení povolíte vzdálené ladění, nastavte ho jako cíl ladění a začněte Diagnostika grafiky.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Konfigurace a spuštění Diagnostika grafiky na zařízení  
  
1. V rozevíracím seznamu **platformy řešení** vyberte **ARM** , aby vaše zařízení se systémem ARM bylo dostupné jako cíl vzdáleného ladění.  
  
2. V rozevíracím seznamu **cíl ladění** vyberte zařízení ARM.  
  
3. V nabídce klikněte na položku **ladění**, **Grafika**, **Spustit diagnostiku**. (Klávesnice: ALT + F5)  
  
## <a name="see-also"></a>Viz také  
 [Spouštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Postupy: Změna počítače pro přehrávání diagnostiky grafiky](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
