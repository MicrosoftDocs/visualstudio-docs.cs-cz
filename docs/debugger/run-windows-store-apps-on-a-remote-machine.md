---
title: Ladění aplikací pro UWP ve vzdálených počítačích | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 0350358c2225851619a84216c929b8d7435dc4e3
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750705"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Ladění aplikací pro UWP ve vzdálených počítačích ze sady Visual Studio
  
Visual Studio můžete spustit, ladění, profilování a testování aplikací pro univerzální platformu Windows (UPW) na jiném počítači nebo zařízení. Spuštění aplikace UPW na vzdáleném počítači je zvláště užitečné, pokud počítač Visual Studio nepodporuje funkce specifické pro UPW, jako jsou dotykového ovládání, geografického umístění nebo fyzická orientace. 

##  <a name="BKMK_Prerequisites"></a> Požadované součásti  

Chcete-li ladit aplikaci UPW na vzdáleném zařízení z aplikace Visual Studio:  
  
- Projekt aplikace Visual Studio musí být nakonfigurovaný pro vzdálené ladění.
- Vzdálený počítač a počítač Visual Studio musí být připojeny přes síť nebo připojeny přímo pomocí kabelu USB nebo Ethernet. Ladění po Internetu není podporováno.  
- Je nutné [zapnutí režimu pro vývojáře](/windows/uwp/get-started/enable-your-device-for-development) na počítači aplikace Visual Studio a vzdáleném počítači. 
- Vzdálených počítačích musí běžet nástrojů Remote Tools for Visual Studio. 
  - Některé verze Windows 10 spustit a automaticky spustit nástroje remote tools. V opačném případě [nainstalovat a spustit nástroje Remote Tools for Visual Studio](#BKMK_download).
  - Zařízení Windows Mobile 10 není vyžadují nebo podporu nástrojů remote tools. 

##  <a name="BKMK_ConnectVS"></a> Konfigurace projektu Visual Studio pro vzdálené ladění
<a name="BKMK_DirectConnect"></a> Použít projekt **vlastnosti** k určení vzdáleného zařízení pro připojení k. Nastavení se liší v závislosti na programovacím jazyce. 

> [!CAUTION]
> Ve výchozím nastavení, na stránce vlastností nastaví **univerzální (nešifrovaný protokol)** jako **typ ověřování** pro Windows 10 vzdálená připojení. Je nutné nastavit **bez ověřování** pro připojení vzdáleného ladicího programu. **Univerzální (nešifrovaný protokol)** a **bez ověřování** protokoly mít žádné zabezpečení sítě, takže je ohrožen dat předávaných mezi vývojem a vzdálených počítačů. Vyberte typy ověřování jenom k důvěryhodným sítím, které jste jisti nejsou ohroženy škodlivými nebo nevyžádanými daty. 
>
>Pokud se rozhodnete **ověřování Windows** pro **typ ověřování**, budete muset přihlásit ke vzdálenému počítači při ladění. Vzdálený ladicí program musí být spuštěn v rámci **ověřování Windows** režimu se stejným uživatelským účtem jako na počítač s Visual Studio.

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurace C# nebo projektu jazyka Visual Basic pro vzdálené ladění  

1. Vyberte C# nebo projektu jazyka Visual Basic v sadě Visual Studio **Průzkumníka řešení** a vyberte **vlastnosti** ikonu, stiskněte klávesu **Alt** +  **Zadejte**, nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.
  
1.  Vyberte **ladění** kartu.  
  
1.  V části **cílové zařízení**vyberte **vzdálený počítač** na vzdálený počítač nebo **zařízení** pro mobilní zařízení Windows 10 zařízení připojeného k přímo.  
  
1.  Pro vzdálený počítač, zadejte název sítě nebo IP adresu v **vzdálený počítač** pole, nebo vyberte **najít** chcete vyhledat v zařízení [dialogové okno připojení ke vzdálené](#remote-connections). 
    
    ![Spravovat vlastnosti projektu pro vzdálené ladění](../debugger/media/vsrun_managed_projprop_remote.png "spravované ladění vlastností projektu")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurace projektu pro vzdálené ladění JavaScriptu nebo C++   
  
1.  Vyberte projekt C++ nebo JavaScript v sadě Visual Studio **Průzkumníka řešení** a vyberte **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter** , nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.
  
1.  Vyberte **ladění** kartu.  
  
3.  V části **ladicí program ke spuštění**vyberte **vzdálený počítač** na vzdálený počítač nebo **zařízení** pro mobilní zařízení Windows 10 zařízení připojeného k přímo. 
  
1.  Vzdálený počítač, zadejte nebo vyberte název sítě nebo IP adresu v **název počítače** pole nebo odeberte dolů a vyberte možnost **vyhledejte** chcete vyhledat v zařízení [dialogové okno vzdálená připojení ](#remote-connections). 

    ![Vlastnosti projektu C++ pro vzdálené ladění](../debugger/media/vsrun_cpp_projprop_remote.png "ladění C++ vlastnosti projektu")
    
### <a name="remote-connections"></a> Použijte dialogové okno vzdálená připojení

V **vzdálená připojení** dialogovém okně můžete vyhledat název konkrétního vzdáleného počítače nebo IP adresu nebo automaticky rozpoznat připojení tak, že vyberete ikonu aktualizace zaoblení šipku. Dialogové okno vyhledá pouze zařízení v místní podsíti, která jsou aktuálně spuštěné vzdálený ladicí program. Ne všechna zařízení lze zjistit v **vzdálená připojení** dialogové okno. 

 ![Vzdálené připojení – dialogové okno](../debugger/media/vsrun_selectremotedebuggerdlg.png "dialogovém okně Vzdálená připojení")  

>[!TIP]
>Pokud se nemůžete připojit ke vzdálenému zařízení podle názvu, zkuste použít svou IP adresu. Chcete-li určit IP adresu, na vzdáleném zařízení, zadejte **ipconfig** v příkazovém okně. IP adresa bude zobrazovat jako **IPv4 adresu**.  
    
## <a name="BKMK_download"></a> Stáhněte a nainstalujte nástroje Remote Tools for Visual Studio

Pro Visual Studio pro ladění aplikací ve vzdáleném počítači vzdáleném počítači musí běžet nástrojů Remote Tools for Visual Studio. 

- Zařízení Windows Mobile 10 nevyžadují ani podporu nástrojů remote tools. 
- Aktualizovat spuštění Tvůrce příslušného počítače s Windows 10 (verze 1703) a novější, zařízení s Windows 10 Xbox, IoT a HoloLens instalovat nástroje remote tools automaticky při nasazení aplikace. 
- Pre-Creator Update 10 počítačů s Windows musíte ručně stáhnout, nainstalovat a být na vzdáleném počítači spuštěny nástroje remote tools, před zahájením ladění.

**Ke stažení a instalaci nástrojů remote tools:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Konfigurace nástrojů remote tools

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Vzdálené ladění aplikací pro UWP 

Vzdálené ladění funguje stejně jako místní ladění. 

1. Na verze pre Tvůrce aktualizací Windows 10, ujistěte se, že sledování vzdáleného ladění (*msvsmon.exe*) běží na vzdáleném zařízení.  
   
1. V počítači, Visual Studio, ujistěte se, že správné cíl ladění (**vzdálený počítač** nebo **zařízení**) se zobrazí vedle na zelenou šipku na panelu nástrojů. 
   
1. Spuštění ladění tak, že vyberete **ladění** > **spustit ladění**, stisknutí **F5**, nebo vyberte zelenou šipku na panelu nástrojů. 
   
   Projekt znovu zkompiluje, pak nasadí a spustí na vzdáleném zařízení. Ladicí program pozastaví provádění na zarážkách a můžete krokovat do, nad a z kódu. 
   
1. V případě potřeby vyberte **ladění** > **Zastavit ladění** nebo stiskněte klávesu **Shift**+**F5** chcete zastavit ladění a Zavřete vzdálenou aplikaci.
  
## <a name="see-also"></a>Viz také:  
 [Pokročilé možnosti vzdáleného nasazení](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testování aplikací pro UPW pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Ladění aplikací pro UWP v sadě Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
