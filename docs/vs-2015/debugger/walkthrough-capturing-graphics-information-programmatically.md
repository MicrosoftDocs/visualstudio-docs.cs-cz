---
title: 'Návod: Zaznamenání grafických informací prostřednictvím kódu programu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: feff1af744bd9f42d2fe8af67a72ec4856a09acc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747678"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostiky grafiky k programově zachytit informace grafiky z aplikace Direct3D.  
  
 Programové zachytávání je užitečné v situacích, jako například:  
  
-   Začne sběr dat prostřednictvím kódu programu grafiky aplikace nepoužívá swapchain k dispozici, například při vykreslení textury.  
  
-   Začněte zachytávání prostřednictvím kódu programu, až vaši aplikaci nevykreslí vůbec, například když používá rozhraní DirectCompute k provádění výpočtů.  
  
-   Volání `CaptureCurrentFrame`při problému vykreslování je obtížné odhadnout a zachycení při ručním testování, ale můžete programově předpovědět s použitím informací o stavu aplikace za běhu.  
  
##  <a name="CaptureDX11_2"></a> Programové zachytávání ve Windows 8.1  
 Tato část návodu ukazuje zachytávání prostřednictvím kódu programu do aplikace, které používají rozhraní API pro rozhraní DirectX 11.2 na Windows 8.1, který používá metodu robustní zachycení. Informace o tom, jak použít v aplikacích, které používají starší verze rozhraní DirectX na Windows 8.0 zachytávání prostřednictvím kódu programu najdete v tématu [zachytávání prostřednictvím kódu programu Windows 8.0 a starší](#CaptureDX11_1) dále v tomto názorném postupu.  
  
 Tato část ukazuje, jak k provádění těchto úkolů:  
  
-   Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
  
-   Získávání rozhraní IDXGraphicsAnalysis  
  
-   Zachycení informací grafiky  
  
> [!NOTE]
>  Předchozích implementacích zachytávání prostřednictvím kódu programu spoléhat Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nakonfigurovánu zachycení, Windows 8.1 podporuje sběr dat přímo prostřednictvím rozhraní Direct3D 11.2. V důsledku toho již máte k instalaci na Windows 8.1 nástrojů Remote Tools pro zachytávání prostřednictvím kódu programu.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
 Použití zachytávání prostřednictvím kódu programu ve vaší aplikaci, musí zahrnovat potřebné hlavičky. Tyto hlavičky jsou součástí sady SDK pro Windows 8.1.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Zahrnout záhlaví zachytávání prostřednictvím kódu programu  
  
-   Obsahovat tato záhlaví ve zdrojovém souboru, ve kterém budete definovat IDXGraphicsAnalysis rozhraní:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Záhlaví souboru vsgcapture.h—which podporuje zachytávání prostřednictvím kódu programu na Windows 8.0 a výše nezahrnují – provádět zachytávání prostřednictvím kódu programu do aplikace pro Windows 8.1. Není kompatibilní s rozhraním DirectX 11.2 této hlavičky. Pokud tento soubor je zahrnuto po záhlaví d3d11_2.h je zahrnuta, kompilátor vyvolá upozornění. Pokud před d3d11_2.h je zahrnutý vsgcapture.h, aplikace se nespustí.  
  
    > [!NOTE]
    >  Pokud červen 2010 na vašem počítači je nainstalovaná rozhraní DirectX SDK a cesty zahrnutí váš projekt obsahuje `%DXSDK_DIR%includex86`, přesunout na konec cesty zahrnutí. Proveďte totéž pro vaši cestu ke knihovně.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8,1  
 Vzhledem k tomu, že Windows Phone 8.1 SDK neobsahuje záhlaví DXProgrammableCapture.h, budete muset definovat `IDXGraphicsAnalysis` sami rozhraní, aby mohli používat `BeginCapture()` a `EndCapture()` metody. Zahrnout další záhlaví, jak je popsáno v předchozí části.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Chcete-li definovat IDXGraphicsAnalysis rozhraní  
  
- Definujte rozhraní IDXGraphicsAnalysis ve stejném souboru, ve kterém jste zahrnuli soubory hlaviček.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Pro usnadnění práce můžete proveďte tyto kroky v novém souboru záhlaví a pak ji kde je třeba zahrnout do vaší aplikace.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Získávání rozhraní IDXGraphicsAnalysis  
 Než budete moct zachytit informace grafiky z rozhraní DirectX 11.2, budete muset získat rozhraní DXGI ladění.  
  
> [!IMPORTANT]
>  Při použití zachytávání prostřednictvím kódu programu, musí i nadále spuštění aplikace v rámci diagnostiky grafiky (Alt + F5 v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) nebo v části [nástroj příkazového řádku pro zachycení](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Chcete-li získat IDXGraphicsAnalysis rozhraní  
  
-   Použijte následující kód k připojení k rozhraní ladění DXGI rozhraní IDXGraphicsAnalysis.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Nezapomeňte se podívat `HRESULT` vrácený `DXGIGetDebugInterface1` zajistit získat platný rozhraní před jejich použitím:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Pokud `DXGIGetDebugInterface1` vrátí `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), ujistěte se, že je aplikace spuštěna v rámci diagnostiky grafiky (Alt + F5 v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]).  
  
### <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Teď, když máte platný `IDXGraphicsAnalysis` rozhraní, můžete použít `BeginCapture` a `EndCapture` k zachycení informací grafiky.  
  
##### <a name="to-capture-graphics-information"></a>Chcete-li zachytit informace grafiky  
  
-   Chcete-li spustit zachycení informací grafiky, použijte `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Sběr dat začne okamžitě po `BeginCapture` nazývá; nečeká na další snímek začít. Zachycení zastaví převedou aktuálního snímku nebo při volání `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Programové zachytávání Windows 8.0 a starší  
 Tato část návodu ukazuje zachytávání prostřednictvím kódu programu v aplikacích pro Windows 8.0 a starší, které používají rozhraní DirectX 11.1 API, které používá metodu starší verze zachycení. Informace o tom, jak použít zachytávání prostřednictvím kódu programu do aplikace, které používají rozhraní DirectX 11.2 na Windows 8.1 najdete v tématu [programátorské zachycení ve Windows 8.1](#CaptureDX11_2) výše v tomto názorném postupu.  
  
 Tato část ukazuje tyto úlohy:  
  
-   Příprava počítače pro zachytávání prostřednictvím kódu programu  
  
-   Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
  
-   Konfigurovat název a umístění souboru protokolu grafiky  
  
-   Použití `CaptureCurrentFrame` rozhraní API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Příprava počítače pro zachytávání prostřednictvím kódu programu  
 Programové zachytávání API používá Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nakonfigurovánu zachycení. Počítače, ve kterém se spustí aplikace musí mít nainstalovaný, i když používáte v místním počítači zachytávání prostřednictvím kódu programu remote tools. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemusí být spuštěna na místním počítači při zachytávání prostřednictvím kódu programu.  
  
 Pokud chcete používat vzdálené zachycování rozhraní API v aplikaci, která běží na počítači, je nejprve nutné instalovat nástroje Remote Tools pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tomto počítači. Různé verze nástrojů remote Tools podporují jiné hardwarové platformy. Informace o tom, jak instalovat nástroje remote tools, najdete v článku [stránce pro stažení nástroje pro vzdálenou](http://go.microsoft.com/fwlink/p/?LinkId=246691) Microsoftu soubory ke stažení webu.  
  
 Alternativně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstaluje komponenty potřebné k provedení vzdálené zachycování pro 32bitové aplikace.  
  
> [!NOTE]
>  Protože většina aplikací klasické pracovní plochy Windows – včetně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]– nejsou podporovány na [!INCLUDE[win8](../includes/win8-md.md)] ARM zařízení pomocí nástroje Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spolu s zachytávání prostřednictvím kódu programu API je jediný způsob, jak zachycení diagnostiky grafiky v zařízeních ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
 Použití nástrojů diagnostiky grafiky, je nejprve nutné zachytit informace grafiky, která ho využívá. Informace můžete zaznamenat prostřednictvím kódu programu pomocí `CaptureCurrentFrame` rozhraní API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Připravit aplikaci tak, aby zaznamenání grafických informací prostřednictvím kódu programu  
  
1.  Ujistěte se, že `vsgcapture.h` obsahovat záhlaví ve zdrojovém kódu aplikace. Mohou být součástí jenom jedno umístění – například v souboru zdrojového kódu, kde bude volat programový zachytit rozhraní API, nebo v souboru předkompilované hlavičky pro volání rozhraní API z více zdrojových souborů s kódem.  
  
2.  Ve zdrojovém kódu aplikace, kdykoli budete chtít zachytit zbytek aktuálního rámce, volání `g_pVsgDbg->CaptureCurrentFrame()`. Tato metoda nemá žádné parametry a nevrací hodnotu.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Konfigurovat název a umístění souboru protokolu grafiky  
 Protokol grafiky se vytvoří v umístění, který je definován `DONT_SAVE_VSGLOG_TO_TEMP` a `VSG_DEFAULT_RUN_FILENAME` makra.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Konfigurovat název a umístění souboru protokolu grafiky  
  
- Protokol grafiky zabránit před zápisem do dočasného adresáře `#include <vsgcapture.h>` řádek, přidejte následující:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Můžete definovat tuto hodnotu pro zápis v protokolu grafiky do umístění, která je relativní vzhledem k pracovní adresář nebo na absolutní cestu, pokud definice `VSG_DEFAULT_RUN_FILENAME` je absolutní cesta.  
  
- Chcete uložit protokol grafiky do jiného umístění nebo jí jiný název souboru, než `#include <vsgcapture.h>` řádek, přidejte následující:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Pokud není tento krok proveďte, název souboru je default.vsglog. Pokud definujete neměli `DONT_SAVE_VSGLOG_TO_TEMP`, pak umístění souboru je relativní vzhledem k adresáři temp; v opačném případě je relativní vzhledem k pracovní adresář nebo v jiném umístění případného absolutního názvu souboru.  
  
  Pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, umístění dočasného adresáře je specifická pro každého uživatele a aplikace a se obvykle nachází v umístění, jako je například C:\users\\*uživatelské jméno*\AppData\Local\Packages\\ *pfn*\TempState\\. Pro aplikace klasické pracovní plochy, umístění dočasného adresáře je specifická pro jednotlivé uživatele a obvykle nachází v umístění, jako je například C:\Users\\*uživatelské jméno*\AppData\Local\Temp\\.  
  
> [!NOTE]
>  Zapsat do určitého umístění, musíte mít oprávnění k zápisu do tohoto umístění. v opačném případě dojde k chybě. Mějte na paměti, která [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace jsou omezeny více než aplikace klasické pracovní plochy o kde umožňuje zápis dat a můžou vyžadovat další konfiguraci k zápisu do určitých umístění.  
  
### <a name="capturing-the-graphics-information"></a>Zaznamenání grafických informací  
 Po aplikace připravené pro zachytávání prostřednictvím kódu programu a volitelně nakonfigurovat umístění a název grafiky souboru protokolu, sestavení aplikace a pak spusťte nebo ladění k zaznamenání dat; Nespouštějte nástroj Diagnostika grafiky z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] při použití zachytávání prostřednictvím kódu programu rozhraní API. Protokol grafiky je zapsán do umístění, které jste zadali. Pokud chcete zachovat tuto verzi protokolu, přesuňte ho do jiného umístění; v opačném případě budou přepsány při dalším spuštění aplikace.  
  
> [!TIP]
>  Můžete stále zachytit informace grafiky ručně při použití zachytávání prostřednictvím kódu programu, s aplikací fokus, stačí stisknout kombinaci kláves **Print Screen**. Tento postup můžete použít k zachycení další grafické informace, které nejsou zachyceny pomocí zachytávání prostřednictvím kódu programu API.  
  
## <a name="next-steps"></a>Další kroky  
 Tento názorný postup ukázal, jak k zaznamenání grafických informací prostřednictvím kódu programu. V dalším kroku vezměte v úvahu tuto možnost:  
  
-   Zjistěte, jak analyzovat zachycené informace grafiky pomocí nástrojů diagnostiky grafiky. Zobrazit [přehled](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zaznamenání grafických informací](../debugger/walkthrough-capturing-graphics-information.md)   
 [Zaznamenání grafických informací](../debugger/capturing-graphics-information.md)   
 [Nástroj příkazového řádku pro zachytávání](../debugger/command-line-capture-tool.md)



