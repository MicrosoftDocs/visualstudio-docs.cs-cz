---
title: Zaznamenání grafických informací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: 44
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a099254acd572b3fcbb437f8933c81f3d6bd45b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799831"
---
# <a name="capturing-graphics-information"></a>Zaznamenání grafických informací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zachytit informace grafiky z aplikace Direct3D analyzátoru grafiky sady Visual Studio můžete použít k diagnostice problémů s vykreslováním a problémy s výkonem.  
  
## <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Zachycení informací grafiky je dvoustupňový proces. Nejprve spusťte aplikaci v rámci Diagnostiky grafiky a následně určete jeden nebo více snímků, ze kterých budou zachyceny podrobné informace.  
  
#### <a name="to-run-your-app-under-graphics-diagnostics"></a>Spuštění aplikace v rámci Diagnostiky grafiky  
  
- V panelu nabídky zvolte **ladění**, **grafiky**, **spustit diagnostiku**. (Klávesnice: stiskněte klávesy Alt + F5)  
  
- Na **grafiky** nástrojů, zvolte **spustit diagnostiku** tlačítko.  
  
  Když je aplikace spuštěna v rámci Diagnostiky grafiky, některé druhy informací grafiky jsou zachycovány neustále. Patří mezi ně nastavení zařízení, vytváření řetězce přepnutí, vytváření grafických objektů a zdrojů a další důležité události, které ovlivňují více než jeden snímek. Zároveň můžete zachytit podrobné informace o konkrétních snímcích. Jedná se například o volání draw a rozesílání počítačového shaderu a objekty Direct3D a zdroje, které je podporují.  
  
#### <a name="to-capture-a-frame"></a>Zachycení snímku  
  
- V sadě Visual Studio na **grafiky** nástrojů, zvolte **zachytit snímek** tlačítko![zachytávání grafiky ikonu tlačítka](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
- Na klávesnici stiskněte klávesu Print Screen.  
  
  > [!NOTE]
  >  Když je aplikace spuštěna v rámci **diagnostiky grafiky**, klávesu Print Screen lze použít pouze k zachycení snímku informací grafiky; neprovádí její běžné funkci. To platí, dokud neukončíte zachycování informací grafiky – obvykle zastavením ladění nebo standardním ukončením aplikace, a to i když je aktivní jiná aplikace.  
  
- Zachycení rozhraní sady Visual Studio, zvolte **zachytit snímek** tlačítko umístěné nad **diagnostické relace** časovou osu, nebo zvolte velké **zachytit snímek** tlačítko nacházel pod **snímků za sekundu** plavecké dráhy a napravo od všechny dříve zachycené snímky. Na následujícím obrázku jsou zvýrazněné obě tlačítka.  
  
   ![Zachytit snímky pomocí nástroje využití GPU. ](../debugger/media/pix-gpu-usage-tool-capture-frame.png "pix_gpu_usage_tool_capture_frame")  
  
   Jakmile budete připraveni k prozkoumání snímky jste zaznamenali, spusťte **analyzátoru grafiky sady Visual Studio** podle **snímků...** odkaz na nad miniatury obrázků, nebo na něj poklikejte na miniaturu.  
  
  Zachytit lze pouze celé snímky, takže když zahájíte zachycování, jsou ve skutečnosti zaznamenány informace grafiky z následujícího snímku. Záznam začne okamžitě po zobrazení snímku, ve kterém jste zachycování inicializovali, a ukončí se po zobrazení zachyceného snímku. Když je aplikace spuštěna v rámci Diagnostiky grafiky, můžete zachytit libovolný počet snímků. Pokud nezachytíte žádné snímky, protokol grafiky bude zrušen.  
  
  Při zachytávání snímků, Visual Studio zobrazí okno diagnostiky relace (.diagsession). Pokud toto okno zavřít, zastavení ladění nebo zavřete aplikaci, nemůže zachytit žádné další rámce do protokolu. Chcete-li zachytit více informací grafiky, budete muset spuštění aplikace v rámci diagnostiky grafiky znovu a spusťte novou relaci diagnostiky.  
  
### <a name="graphics-diagnostics-capture-options"></a>Možnosti zachytávání diagnostiky grafiky  
 Můžete nakonfigurovat zachytávání shromažďovat zásobníky volání pro všechny události grafiky nebo omezené dílčí, zakázat zachycování HUD a povolit nebo zakázat režim kompatibility zachycení.  
  
##### <a name="to-configure-graphics-diagnostics-capture-options"></a>Konfigurace možností zachycení diagnostiky grafiky  
  
1.  V panelu nabídky zvolte Nástroje, možnosti. Zobrazí se dialogové okno Možnosti.  
  
2.  V seznamu kategorií možností na levé straně zvolte diagnostiky grafiky a pak nakonfigurujte možnosti diagnostiky grafiky, které chcete.  
  
     **Během zachytávání shromažďovat zásobníky volání (zpomaluje zachytávání)**  
     Zaškrtnutím tohoto políčka shromažďovat zásobníky volání. Ve výchozím nastavení se neshromažďují zásobníky volání. K zachycení zásobníky volání, ujistěte se, že **shromažďování volání zásobníků při zachytávání (zpomaluje zachytávání** zaškrtávací políčko je nastavena na Povolit kolekci a pak nastavte buď **pro značky kreslení, odesílání, k dispozici a výkonu**možnost (výchozí) Chcete-li shromažďovat pouze ty nejdůležitější zásobníky volání, nebo **pro všechno, co** možnost shromažďovat všechny zásobníky volání. Chcete-li zastavit shromažďování zásobníků volání později, zrušte **shromažďování volání zásobníků při zachytávání (zpomaluje zachytávání** zaškrtávací políčko.  
  
     **Během zachytávání zakázat HUD ve hře**  
     Zkontrolujte, že toto políčko Zakázat HUD překrytí, který aplikaci spuštěnou v rámci grafiky diagnostiky obvykle zobrazí. Zrušte zaškrtnutí políčka Zobrazit HUD překrytí.  
  
     **Zaznamenat v režimu kompatibility**  
     Zaškrtněte toto políčko, chcete-li zachytit informace grafiky v režimu kompatibility. Zachycení v režimu kompatibility je výchozí nastavení. V režimu kompatibility nebudou podávat Direct3D, GPU podporuje všechny další funkce nad rámec těch, definované na úrovni základní funkce. To zabrání aplikaci zachytí pomocí rozšíření specifické pro hardware jeho zachycené GPU na a zajistí, že protokol grafiky lze přehrát zpět pomocí jakékoli GPU, která podporuje úroveň funkcí stejná nebo vyšší. Zrušte zaškrtnutí tohoto políčka Zakázat režim kompatibility; protokoly zachytit pomocí režimu kompatibility zakázané se nepodaří přehrát na jakékoli GPU, který nepodporuje stejné další funkce, které byly použity aplikace při zachytávání.  
  
     **Zastavit zachytávání při nalezení chyb vrstev všechny sady SDK**  
     Zaškrtnutím tohoto políčka okamžitě zastaví sběr dat, pokud nedojde k chybám.  
  
## <a name="capturing-graphics-information-remotely"></a>Vzdálené zachycení informací grafiky  
 Informace grafiky lze zaznamenat z aplikace, která je spuštěna v místním počítači nebo ve vzdáleném počítači či zařízení. Vzdálené zachycování je podporováno pro [!INCLUDE[winblue_client_2](../includes/winblue-client-2-md.md)] počítače a [!INCLUDE[winblue_winrt_2](../includes/winblue-winrt-2-md.md)] zařízení. Chcete-li zachytit informace grafiky z aplikace, která je spuštěna vzdáleně, nakonfigurujte svůj projekt na vzdálené ladění a spusťte aplikaci v rámci Diagnostiky grafiky, jak bylo popsáno dříve. Aplikace se spustí ve vzdáleném počítači a zachycené informace grafiky se zaznamenají do vývojového počítače.  
  
 Konfigurace projektu pro vzdálené ladění závisí na typu aplikace, kterou vyvíjíte, a používaném programovacím jazyku. Informace o tom, jak konfigurovat vzdálené ladění pro aplikace Windows Store naleznete v tématu [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md). Informace o tom, jak konfigurovat vzdálené ladění pro aplikace klasické pracovní plochy Windows najdete v tématu [nastavte si vzdálené ladění pro projekt sady Visual Studio](http://msdn.microsoft.com/library/ec332dc4-400a-498b-a0e6-c8dcf10fef8a).  
  
 Později lze vzdálený počítač nebo zařízení použít k přehrání informací grafiky bez ohledu na to, odkud byly informace zachyceny. Další informace najdete v tématu [postupy: Změna počítače pro přehrávání diagnostiky grafiky](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Zaznamenání grafických informací z příkazového řádku  
 Informace grafiky lze zaznamenat z aplikace pomocí nástroje příkazového řádku. Tento nástroj DXCap.exe, můžete rychle zachytávání a přehrávání grafické informace bez použití sady Visual Studio nebo zachytávání prostřednictvím kódu programu. DXCap.exe zejména, můžete pro službu automation, nebo v testovacím prostředí. Další informace o DXCap.exe najdete v tématu [zachycení nástroj příkazového řádku](../debugger/command-line-capture-tool.md)  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zaznamenání grafických informací](../debugger/walkthrough-capturing-graphics-information.md)



