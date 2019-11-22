---
title: 'Návod: Programové zachycení informací grafiky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54097420fd212ec9057f4a968e2c6d5de199e56e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296907"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Diagnostika grafiky můžete použít k programovému zachycení informací grafiky z aplikace Direct3D.  
  
 Programové zachytávání je užitečné ve scénářích, jako jsou:  
  
- Pokud vaše grafická aplikace nepoužívá swapchain k dispozici, začněte zachytit programově, například když se vykresluje na texturu.  
  
- Pokud se vaše aplikace vůbec nevykresluje, můžete zachytávání spustit programově, například když k provádění výpočtů používá DirectCompute.  
  
- Volání `CaptureCurrentFrame`v případě, že problém vykreslování je obtížné odhadnout a zachytit v manuálním testování, ale lze jej předpovědět pomocí informací o stavu aplikace za běhu.  
  
## <a name="CaptureDX11_2"></a>Programové zachycení v Windows 8.1  
 Tato část návodu ukazuje programový Capture v aplikacích, které používají rozhraní DirectX 11,2 API na Windows 8.1, které používá robustní metodu zachycení. Informace o použití programového zachycení v aplikacích, které používají starší verze rozhraní DirectX v systému Windows 8,0, najdete v tématu [programový Capture v systému windows 8,0 a dříve](#CaptureDX11_1) v tomto návodu.  
  
 V této části se dozvíte, jak provádět tyto úlohy:  
  
- Příprava aplikace pro použití programového zachycení  
  
- Získání rozhraní IDXGraphicsAnalysis  
  
- Zachycení informací grafiky  
  
> [!NOTE]
> Předchozí implementace programového zachycení se spoléhaly na vzdálené nástroje pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby poskytovaly funkci zachycení. Windows 8.1 podporuje zachycení přímo přes Direct3D 11,2. V důsledku toho už nemusíte instalovat nástroje Remote Tools for program Capture na Windows 8.1.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití programového zachycení  
 Pokud chcete ve své aplikaci použít programové zachycení, musí obsahovat potřebné hlavičky. Tato záhlaví jsou součástí sady Windows 8.1 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Zahrnutí programových hlaviček zachycení  
  
- Zahrňte tyto hlavičky do zdrojového souboru, kde budete definovat rozhraní IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    > Nezahrnovat hlavičkový soubor vsgcapture. h, který podporuje Programové zachycení na Windows 8,0 a starší verzi – k provádění programového zachycení ve vašich aplikacích Windows 8.1. Tato hlavička není kompatibilní s rozhraním DirectX 11,2. Pokud je tento soubor zahrnutý po zahrnutí hlavičky d3d11_2. h, vyvolá kompilátor upozornění. Pokud je vsgcapture. h zahrnuté před d3d11_2. h, aplikace se nespustí.  
  
    > [!NOTE]
    > Pokud je v počítači nainstalovaná sada DirectX 2010 DirectX SDK a cesta k zahrnutí vašeho projektu obsahuje `%DXSDK_DIR%includex86`, přesuňte ji na konec cesty include. Proveďte stejnou cestu ke knihovně.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Vzhledem k tomu, že sada Windows Phone 8,1 SDK neobsahuje hlavičku DXProgrammableCapture. h, bude nutné definovat rozhraní `IDXGraphicsAnalysis` sami, abyste mohli používat metody `BeginCapture()` a `EndCapture()`. Zahrňte další hlavičky, jak je popsáno v předchozí části.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Definování rozhraní IDXGraphicsAnalysis  
  
- Definujte rozhraní IDXGraphicsAnalysis ve stejném souboru, ve kterém jste zahrnuli hlavičkové soubory.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Pro usnadnění práce můžete tyto kroky provést v novém hlavičkovém souboru a pak ho zahrnout tam, kde je potřeba ve vaší aplikaci.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis  
 Předtím, než budete moci zachytit informace grafiky z rozhraní DirectX 11,2, je nutné získat rozhraní ladění DXGI.  
  
> [!IMPORTANT]
> Při použití programového zachycení je nutné pořád spustit aplikaci v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) nebo v rámci [Nástroje pro zachycení z příkazového řádku](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis  
  
- Použijte následující kód k připojení rozhraní IDXGraphicsAnalysis k ladicímu rozhraní DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Nezapomeňte zkontrolovat `HRESULT` vrácených `DXGIGetDebugInterface1`, abyste zajistili, že budete mít k dispozici platné rozhraní předtím, než ho použijete:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    > Pokud `DXGIGetDebugInterface1` vrátí `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), ujistěte se, že je aplikace spuštěná v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]).  
  
### <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Teď, když máte platné `IDXGraphicsAnalysis` rozhraní, můžete k zachycení informací grafiky použít `BeginCapture` a `EndCapture`.  
  
##### <a name="to-capture-graphics-information"></a>Zachycení informací grafiky  
  
- Chcete-li začít zachytávání informací o grafice, použijte `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Zachytávání začíná ihned při volání `BeginCapture`; nečeká na zahájení dalšího snímku. Zachycení se zastaví, když se zobrazí aktuální rámec, nebo když zavoláte `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="CaptureDX11_1"></a>Programové zachycení ve Windows 8,0 a starší verzi  
 Tato část návodu ukazuje programový Capture v aplikacích pro Windows 8,0 a starší, které používají rozhraní DirectX 11,1 API, které používá starší metodu zachycení. Informace o tom, jak používat programové zachycení v aplikacích, které používají rozhraní DirectX 11,2 na Windows 8.1, najdete v tématu [programový Capture v Windows 8.1](#CaptureDX11_2) dříve v tomto návodu.  
  
 Tato část zobrazuje tyto úlohy:  
  
- Příprava počítače na použití programového zachycení  
  
- Příprava aplikace pro použití programového zachycení  
  
- Konfigurace názvu a umístění souboru protokolu grafiky  
  
- Používání rozhraní `CaptureCurrentFrame` API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Příprava počítače na použití programového zachycení  
 Programové rozhraní API pro sběr dat využívá nástroje Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k zajištění funkcí zachycení. Počítač, ve kterém bude aplikace spuštěna, musí mít nainstalované vzdálené nástroje, i když používáte programové zachycení na místním počítači. Pokud provádíte Programové zachycení na místním počítači, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemusí běžet.  
  
 Chcete-li používat rozhraní API pro vzdálené zachytávání v aplikaci, která je spuštěna v počítači, je nejprve nutné nainstalovat nástroje Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tento počítač. Různé verze nástrojů Remote Tools podporují různé hardwarové platformy. Informace o tom, jak nainstalovat nástroje Remote Tools, najdete na [stránce stažení vzdálených nástrojů](https://go.microsoft.com/fwlink/p/?LinkId=246691) na webu Microsoft downloads.  
  
 Případně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstaluje potřebné komponenty pro vzdálené zachytávání pro 32 aplikace.  
  
> [!NOTE]
> Vzhledem k tomu, že většina aplikací pro stolní počítače s Windows (včetně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) není v [!INCLUDE[win8](../includes/win8-md.md)] pro zařízení ARM podporovaná, je jediným způsobem, jak zachytit diagnostiku grafiky na zařízeních ARM, použití vzdálených nástrojů pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] společně s rozhraním API pro programové zachycení.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití programového zachycení  
 Chcete-li použít nástroje Diagnostika grafiky, musíte nejprve zachytit informace o grafice, na kterých se spoléhá. Tyto informace můžete programově zachytit pomocí rozhraní `CaptureCurrentFrame` API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Příprava aplikace pro programové zachycení informací grafiky  
  
1. Ujistěte se, že je ve zdrojovém kódu aplikace obsažena hlavička `vsgcapture.h`. Může být součástí pouze jednoho umístění, například v souboru se zdrojovým kódem, kde budete volat programové rozhraní API pro zachycení, nebo v souboru předkompilované hlavičky pro volání rozhraní API z více souborů zdrojového kódu.  
  
2. Ve zdrojovém kódu aplikace, kdykoli chcete zachytit zbytek aktuálního rámce, zavolejte `g_pVsgDbg->CaptureCurrentFrame()`. Tato metoda nepřijímá žádné parametry a nevrací hodnotu.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Konfigurace názvu a umístění souboru protokolu grafiky  
 Protokol grafiky je vytvořen v umístění, které je definováno `DONT_SAVE_VSGLOG_TO_TEMP` a `VSG_DEFAULT_RUN_FILENAME` makra.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Konfigurace názvu a umístění souboru protokolu grafiky  
  
- Chcete-li zabránit zapsání protokolu grafiky do dočasného adresáře, přidejte před `#include <vsgcapture.h>` řádek tento příkaz:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Tuto hodnotu můžete definovat pro zápis protokolu grafiky do umístění, které je relativní vzhledem k pracovnímu adresáři, nebo na absolutní cestu, pokud je definice `VSG_DEFAULT_RUN_FILENAME` absolutní cestou.  
  
- Chcete-li uložit protokol grafiky do jiného umístění nebo zadat jiný název souboru před `#include <vsgcapture.h>`m řádkem, přidejte tento příkaz:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Pokud tento krok neprovedete, bude název souboru Default. vsglog. Pokud jste nedefinovali `DONT_SAVE_VSGLOG_TO_TEMP`, umístění souboru je relativní vzhledem k dočasnému adresáři. v opačném případě je relativní vzhledem k pracovnímu adresáři nebo v jiném umístění, pokud jste zadali absolutní název souboru.  
  
  U [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]ch aplikací je umístění dočasného adresáře specifické pro každého uživatele a aplikaci a obvykle se nachází v umístění, jako je například C:\Users\\*username*\AppData\Local\Packages\\*rodina balíčku název*\TempState\\. Pro desktopové aplikace je umístění dočasného adresáře specifické pro každého uživatele a obvykle se nachází v umístění, jako je například C:\Users\\*username*\AppData\Local\Temp\\.  
  
> [!NOTE]
> Chcete-li zapisovat do konkrétního umístění, musíte mít oprávnění k zápisu do tohoto umístění; v opačném případě dojde k chybě. Pamatujte, že aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] jsou omezenější než aplikace klasické pracovní plochy, kde mohou zapisovat data a mohou vyžadovat další konfiguraci pro zápis do určitých umístění.  
  
### <a name="capturing-the-graphics-information"></a>Zachytávání informací o grafice  
 Po přípravě aplikace pro programové zachycení a volitelně konfiguraci umístění a názvu souboru protokolu grafiky sestavte aplikaci a pak ji spusťte nebo Nalaďte pro zachycení dat. Při použití rozhraní API pro programové zachycení nespouštějte diagnostiku grafiky z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Protokol grafiky je zapsán do umístění, které jste zadali. Pokud chcete zachovat tuto verzi protokolu, přesuňte ji do jiného umístění; v opačném případě bude při opětovném spuštění aplikace přepsána.  
  
> [!TIP]
> Informace o grafech můžete zachytit ručně, i když používáte programové zachycení – s aplikací se zaměřením, stačí stisknout **tiskovou obrazovku**. Tento postup můžete použít k zachycení dalších grafických informací, které nejsou zachyceny rozhraním API pro programové zachycení.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukázal, jak programově zachytit informace grafiky. Jako další krok zvažte tuto možnost:  
  
- Naučte se analyzovat informace o zachycených grafikách pomocí nástrojů Diagnostika grafiky. Další informace najdete v tématu [Přehled](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: zachycení informací grafiky](../debugger/walkthrough-capturing-graphics-information.md)   
 [Zachytávání informací o grafikách](../debugger/capturing-graphics-information.md)   
 [Nástroj příkazového řádku pro zachytávání](../debugger/command-line-capture-tool.md)
