---
title: 'Postupy: použití diagnostiky grafiky se zařízením ARM | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5122cb009b3624388ff8825b34cae8ca44a546
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728682"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Postupy: použití diagnostiky grafiky se zařízením ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostika grafiky podporuje vzdálené ladění aplikací rozhraní Direct3D na založené na ARM zařízení se systémem Windows RT 8.1 nebo Windows Phone 8.1. Můžete zachytit informace grafiky z aplikace Direct3D při spuštění na zařízení nebo zařízení použít jako stroj přehrávání pro dříve zachycené informace grafiky.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Použití diagnostiky grafiky se zařízením založené na ARM  
 Vzhledem k tomu, že Visual Studio se nespustí na zařízení se systémem ARM, budete muset použít vzdálený ladicí program k analýze aplikace, která běží na nich. Vzdálený ladicí program podporuje zachytávání grafiky a přehrávání, takže můžete Diagnostika chyb při vykreslování a vyhodnotit grafický výkon na těchto zařízeních stejně snadno jako je ladění aplikace s nimi.  
  
 Pokud chcete používat funkce diagnostiky grafiky, nejprve povolte, vzdálené ladění na vašem zařízení.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Jak aktivovat vzdálené ladění na vašem zařízení založené na ARM  
  
1.  Nainstalujte [zásady sad ARM](http://msdn.microsoft.com/windows/desktop/dn469188) na vašem zařízení založené na ARM.  
  
2.  Nainstalujte [nástroje pro vzdálené ladění](http://go.microsoft.com/fwlink/?LinkId=393086) na vašem zařízení založené na ARM.  
  
> [!IMPORTANT]
>  Pro zařízení s Windows Phone 8.1 budete muset zaregistrovat svůj telefon pro vývoj. Uděláte to tak, musí být registrovaný vývojář. Další informace najdete v tématu [o nasazení a spuštění aplikace pro Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Po povolení vzdáleného ladění na vašem zařízení, byl váš cíl ladění a spuštění diagnostiky grafiky.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Pro konfiguraci a spuštění diagnostiky grafiky ve vašem zařízení  
  
1.  Na **platformy řešení** rozevíracího seznamu vyberte **ARM** tak, aby vaše zařízení založené na ARM, budou k dispozici jako cíl vzdáleného ladění.  
  
2.  Na **cíl ladění** rozevíracího seznamu vyberte zařízení ARM.  
  
3.  V nabídce zvolte **ladění**, **grafiky**, **spustit diagnostiku**. (Klávesnice: Alt + F5)  
  
## <a name="see-also"></a>Viz také  
 [Spustit Windows Store apps na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Postupy: Změna počítače pro přehrávání diagnostiky grafiky](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



