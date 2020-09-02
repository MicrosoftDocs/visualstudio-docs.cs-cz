---
title: Nasazení aplikací pro Windows Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177480"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Nasazení aplikací pro Windows Store ze sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí jenom pro Windows] (.. /Image/windows_only_content.png "windows_only_content")

 Funkce nasazení sady Visual Studio vytváří a registruje aplikace pro Windows Store, které jsou vytvořené pomocí sady Visual Studio na cílovém zařízení. Přesně to, jak je aplikace zaregistrovaná, závisí na tom, jestli je cílové zařízení místní nebo vzdálené:

- Pokud je cílem místní počítač sady Visual Studio, aplikace Visual Studio zaregistruje aplikaci ze své složky sestavení.

- Pokud je cílem vzdálené zařízení, Visual Studio zkopíruje požadované soubory do vzdáleného počítače a zaregistruje aplikaci na tomto zařízení.

  Nasazení je automatické při ladění aplikace ze sady Visual Studio pomocí možnosti **Spustit ladění** (klávesnice: F5) nebo možnosti **Spustit bez ladění** (klávesnice: CTRL + F5). Aplikaci můžete nasadit také ručně. Ruční nasazení je užitečné v následujících scénářích:

- Testování ad hoc na místním nebo vzdáleném počítači.

- Nasazení aplikace, která spustí jinou aplikaci, kterou chcete ladit.

- Nasazení aplikace, která se bude ladit při spuštění jinou aplikací nebo metodou

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 V tomto tématu se můžete dozvědět:

 [Nasazení aplikace pro Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Určení vzdáleného zařízení](#BKMK_How_to_specify_a_remote_device)

 [Možnosti nasazení](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Nasazení aplikace pro Windows Store
 Ruční nasazení aplikace je jednoduchý proces:

1. Pokud nasazujete na vzdálené zařízení, zadejte název nebo IP adresu zařízení na stránce projekt vlastností spouštěného projektu aplikace. (Tento postup je uveden dále v tomto tématu.).

2. Na panelu nástrojů ladicího programu sady Visual Studio v rozevíracím seznamu vedle tlačítka **Spustit ladění** vyberte cíl nasazení.

     ![Spustit na místním počítači](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. V nabídce **sestavení** klikněte na příkaz **nasadit** .

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Určení vzdáleného zařízení
 **Požadavky**

 Nasazení aplikace na vzdálené zařízení:

- Na vzdáleném zařízení musí být nainstalována licence vývojáře.

- Vzdálené nástroje sady Visual Studio musí být nainstalované na vzdáleném zařízení a Sledování vzdáleného ladění musí být spuštěná.

     Nasazení používá síťový kanál vzdáleného ladícího programu k posílání souborů aplikace na vzdálené zařízení.

#### <a name="to-specify-a-remote-device"></a>Určení vzdáleného zařízení

1. Na stránce vlastností ladění spouštěného projektu zadejte název nebo IP adresu cíle vzdáleného nasazení.

2. Chcete-li otevřít stránku vlastností ladění, zvolte projekt v Průzkumník řešení a pak v místní nabídce zvolte možnost **vlastnosti** .

3. Pak zvolte uzel **ladění** v okně stránky vlastností.

4. Můžete zadat název nebo IP adresu vzdáleného zařízení nebo můžete vybrat zařízení z dialogového okna **Vybrat připojení vzdáleného ladicího programu** .

    ![Dialogové okno vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    V dialogovém okně **Vybrat připojení vzdáleného ladicího programu** se zobrazí zařízení v podsíti místní sítě a všechna zařízení, která jsou přímo připojena k počítači sady Visual Studio pomocí kabelu Ethernet.

   **Určení vzdáleného zařízení na stránce projektu JavaScriptu nebo Visual C++**

   ![Vlastnosti projektu v jazyce C&#43;&#43; pro vzdálené ladění](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Pro spuštění seznamu vyberte možnost **vzdálený ladicí program** z **ladicího programu** .

6. Do pole **název počítače** zadejte název sítě vzdáleného zařízení. Případně můžete vybrat šipku dolů v poli a vybrat zařízení z dialogového okna Vybrat připojení vzdáleného ladicího programu.

   **Určení vzdáleného zařízení na stránce projektu Visual C# a Visual Basic**

   ![Vlastnosti spravovaného projektu pro vzdálené ladění](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. V seznamu **cílový seznam zařízení** vyberte možnost **vzdálený počítač** .

8. Zadejte síťový název vzdáleného zařízení do pole **vzdálený počítač** nebo klikněte na **Najít** a zvolte zařízení v dialogovém okně **Vybrat připojení vzdáleného ladicího programu** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Možnosti nasazení
 Na stránce vlastností ladění spouštěného projektu můžete nastavit následující možnosti nasazení.

 **Povolení zpětné smyčky sítě** Z bezpečnostních důvodů není v [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikaci, která je nainstalovaná standardním způsobem, povoleno provádět síťová volání do zařízení, na kterém je nainstalovaná. Ve výchozím nastavení vytvoří nasazení sady Visual Studio výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Před odesláním aplikace do nástroje [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] byste měli aplikaci otestovat bez výjimky.

 Odebrání výjimky zpětné smyčky sítě z aplikace:

- Na stránce vlastností ladění C# a VB zrušte zaškrtnutí políčka **zapnout smyčku sítě** .

- Na stránce vlastnosti JavaScriptu a ladit nastavte možnost zapnout hodnotu **zpětné smyčky sítě** na **ne**.

  **Nespouštět, ale ladit můj kód při spuštění (C# a VB)/spustit aplikaci (JavaScript a C++)** Konfigurace nasazení tak, aby automaticky spouštěla relaci ladění při spuštění aplikace:

- Na stránce vlastností ladění C# a VB zaškrtněte políčko **nespouštět, ale při spuštění ladit můj kód** .

- Na stránce vlastnosti JavaScriptu a ladit nastavte hodnotu **Spustit aplikaci** na **Ano**.

## <a name="see-also"></a>Viz také
 [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
