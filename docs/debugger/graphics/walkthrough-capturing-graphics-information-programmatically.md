---
title: 'Návod: Zaznamenání grafických informací prostřednictvím kódu programu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 659e370d664b3db2c3624d73164b4489cc2680a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933284"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu
Můžete použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostiky grafiky k programově zachytit informace grafiky z aplikace Direct3D.  
  
 Programové zachytávání je užitečné v situacích, jako například:  
  
-   Začne sběr dat prostřednictvím kódu programu grafiky aplikace nepoužívá swapchain k dispozici, například při vykreslení textury.  
  
-   Začněte zachytávání prostřednictvím kódu programu, až vaši aplikaci nevykreslí vůbec, například když používá rozhraní DirectCompute k provádění výpočtů.  
  
-   Volání `CaptureCurrentFrame`při problému vykreslování je obtížné odhadnout a zachycení při ručním testování, ale můžete programově předpovědět s použitím informací o stavu aplikace za běhu.  
  
##  <a name="CaptureDX11_2"></a> Programové zachytávání ve Windows 10  
 Tato část návodu ukazuje zachytávání prostřednictvím kódu programu do aplikace, které používají rozhraní API pro rozhraní DirectX 11.2 ve Windows 10, která používá metodu robustní zachycení.
  
 Tato část ukazuje, jak k provádění těchto úkolů:  
  
-   Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
  
-   Získávání rozhraní IDXGraphicsAnalysis  
  
-   Zachycení informací grafiky  
  
> [!NOTE]
>  Předchozích implementacích zachytávání prostřednictvím kódu programu spoléhat Remote Tools for Visual Studio pro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nakonfigurovánu zachycení.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití zachytávání prostřednictvím kódu programu  
 Použití zachytávání prostřednictvím kódu programu ve vaší aplikaci, musí zahrnovat potřebné hlavičky. Tyto hlavičky jsou součástí sady Windows 10 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Zahrnout záhlaví zachytávání prostřednictvím kódu programu  
  
-   Obsahovat tato záhlaví ve zdrojovém souboru, ve kterém budete definovat IDXGraphicsAnalysis rozhraní:  
  
    ```cpp
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Záhlaví souboru vsgcapture.h—which podporuje zachytávání prostřednictvím kódu programu na Windows 8.0 a výše nezahrnují – provádět zachytávání prostřednictvím kódu programu do vaší aplikace pro Windows 10. Není kompatibilní s rozhraním DirectX 11.2 této hlavičky. Pokud tento soubor je zahrnuto po záhlaví d3d11_2.h je zahrnuta, kompilátor vyvolá upozornění. Pokud před d3d11_2.h je zahrnutý vsgcapture.h, aplikace se nespustí.  
  
    > [!NOTE]
    >  Pokud červen 2010 na vašem počítači je nainstalovaná rozhraní DirectX SDK a cesty zahrnutí váš projekt obsahuje `%DXSDK_DIR%includex86`, přesunout na konec cesty zahrnutí. Proveďte totéž pro vaši cestu ke knihovně.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Získávání rozhraní IDXGraphicsAnalysis  
 Než budete moct zachytit informace grafiky z rozhraní DirectX 11.2, budete muset získat rozhraní DXGI ladění.  
  
> [!IMPORTANT]
>  Při použití zachytávání prostřednictvím kódu programu, musí i nadále spuštění aplikace v rámci diagnostiky grafiky (Alt + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) nebo v části [nástroj příkazového řádku pro zachycení](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Chcete-li získat IDXGraphicsAnalysis rozhraní  
  
- Použijte následující kód k připojení k rozhraní ladění DXGI rozhraní IDXGraphicsAnalysis.  
  
  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;  
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
  ```  
  
   Nezapomeňte se podívat `HRESULT` vrácený [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) zajistit získat platný rozhraní před jejich použitím:  
  
  ```cpp
  if (FAILED(getAnalysis))  
  {  
      // Abort program or disable programmatic capture in your app.  
  }  
  ```  
  
  > [!NOTE]
  >  Pokud `DXGIGetDebugInterface1` vrátí `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), ujistěte se, že je aplikace spuštěna v rámci diagnostiky grafiky (Alt + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Zachycení informací grafiky  
 Teď, když máte platný `IDXGraphicsAnalysis` rozhraní, můžete použít `BeginCapture` a `EndCapture` k zachycení informací grafiky.  
  
##### <a name="to-capture-graphics-information"></a>Chcete-li zachytit informace grafiky  
  
- Chcete-li spustit zachycení informací grafiky, použijte `BeginCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Sběr dat začne okamžitě po `BeginCapture` nazývá; nečeká na další snímek začít. Zachycení zastaví převedou aktuálního snímku nebo při volání `EndCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  

- Po volání `EndCapture`, uvolnění objektu grafiky. 
  
## <a name="next-steps"></a>Další kroky  
 Tento názorný postup ukázal, jak k zaznamenání grafických informací prostřednictvím kódu programu. V dalším kroku vezměte v úvahu tuto možnost:  
  
-   Zjistěte, jak analyzovat zachycené informace grafiky pomocí nástrojů diagnostiky grafiky. Zobrazit [přehled](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)   
 [Zaznamenání grafických informací](capturing-graphics-information.md)   
 [Nástroj příkazového řádku pro zachytávání](command-line-capture-tool.md)
